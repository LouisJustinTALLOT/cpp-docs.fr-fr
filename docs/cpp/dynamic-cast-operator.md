---
title: Opérateur dynamic_cast | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- dynamic_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8e25564d89eaf665baa473d7725ab69e2355ccb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406303"
---
# <a name="dynamiccast-operator"></a>dynamic_cast, opérateur
Convertit l’opérande `expression` à un objet de type `type-id`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dynamic_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Notes  
 Le `type-id` doit être un pointeur ou une référence à un type de classe précédemment définie ou un « pointeur vers void ». Le type de `expression` doit être un pointeur si `type-id` est un pointeur ou une l-value si `type-id` est une référence.  
  
 Consultez [static_cast](../cpp/static-cast-operator.md) pour obtenir une explication de la différence entre les conversions de casting statiques et dynamiques, et quand il convient d’utiliser chacune.  
  
 Il existe deux modifications avec rupture dans le comportement de **dynamic_cast** dans du code managé :  
  
-   **dynamic_cast** vers un pointeur vers le type sous-jacent d’un enum boxed échoue lors de l’exécution, la méthode retournant 0 au lieu du pointeur converti.  
  
-   **dynamic_cast** ne lève plus une exception lorsque `type-id` est un pointeur intérieur vers un type valeur, avec le cast échoue lors de l’exécution.  Le cast retourne désormais la valeur de pointeur 0 au lieu de lever.  
  
 Si `type-id` est un pointeur vers un non équivoque accessible directe ou indirecte classe de base de `expression`, un pointeur vers le sous-objet unique de type `type-id` est le résultat. Exemple :  
  
```cpp 
// dynamic_cast_1.cpp  
// compile with: /c  
class B { };  
class C : public B { };  
class D : public C { };  
  
void f(D* pd) {  
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class  
                                   // pc points to C subobject of pd   
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class  
                                   // pb points to B subobject of pd  
}  
```  
  
 Ce type de conversion est appelé un « upcast », car il passe un pointeur d’une hiérarchie de classes, à partir d’une classe dérivée à une classe, qu'il est dérivé. Un upcast est une conversion implicite.  
  
 Si `type-id` est void *, une vérification de l’exécution est effectuée pour déterminer le type réel de `expression`. Le résultat est un pointeur vers l’objet complet vers lequel pointé `expression`. Exemple :  
  
```cpp 
// dynamic_cast_2.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
  
void f() {  
   A* pa = new A;  
   B* pb = new B;  
   void* pv = dynamic_cast<void*>(pa);  
   // pv now points to an object of type A  
  
   pv = dynamic_cast<void*>(pb);  
   // pv now points to an object of type B  
}  
```  
  
 Si `type-id` n’est pas void *, une vérification de l’exécution est effectuée pour déterminer si l’objet vers lequel pointe `expression` peut être converti vers le type vers lequel pointé `type-id`.  
  
 Si le type de `expression` est une classe de base du type de `type-id`, une vérification de l’exécution est effectuée pour déterminer si `expression` réellement pointe vers un objet complet du type de `type-id`. Si la valeur est true, le résultat est un pointeur vers un objet complet du type de `type-id`. Exemple :  
  
```cpp 
// dynamic_cast_3.cpp  
// compile with: /c /GR  
class B {virtual void f();};  
class D : public B {virtual void f();};  
  
void f() {  
   B* pb = new D;   // unclear but ok  
   B* pb2 = new B;  
  
   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D  
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D  
}  
```  
  
 Ce type de conversion est appelé un « effectuer un downcast », car il déplace un pointeur vers le bas d’une hiérarchie de classes, à partir d’une classe donnée d’une classe dérivée de celui-ci.  
  
 En cas d’héritage multiple, les possibilités d’ambiguïté sont introduites. Envisagez la hiérarchie de classes illustrée à la figure suivante.  
  
 Pour les types CLR, **dynamic_cast** se traduit par une absence d’opération si la conversion peut être effectuée implicitement, ou d’un code MSIL `isinst` instruction, qui effectue une vérification dynamique et retourne **nullptr** si le la conversion échoue.  
  
 L’exemple suivant utilise **dynamic_cast** pour déterminer si une classe est une instance de type particulier :  
  
```cpp 
// dynamic_cast_clr.cpp  
// compile with: /clr  
using namespace System;  
  
void PrintObjectType( Object^o ) {  
   if( dynamic_cast<String^>(o) )  
      Console::WriteLine("Object is a String");  
   else if( dynamic_cast<int^>(o) )  
      Console::WriteLine("Object is an int");  
}  
  
int main() {  
   Object^o1 = "hello";  
   Object^o2 = 10;  
  
   PrintObjectType(o1);  
   PrintObjectType(o2);  
}  
```  
  
 ![Hiérarchie qui montre l’héritage multiple de classes](../cpp/media/vc39011.gif "vc39011")  
Hiérarchie de classes montrant des héritages multiples  
  
 Un pointeur vers un objet de type `D` pouvant être casté en toute sécurité en `B` ou `C`. Toutefois, si `D` est converti pour pointer vers un `A` de l’objet, instance de `A` provoquerait ? Cela entraînerait une erreur de conversion ambiguë. Pour contourner ce problème, vous pouvez effectuer deux casts non équivoque. Exemple :  
  
```cpp 
// dynamic_cast_4.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
class D : public B {virtual void f();};  
  
void f() {  
   D* pd = new D;  
   B* pb = dynamic_cast<B*>(pd);   // first cast to B  
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous  
}  
```  
  
 Ambiguïtés supplémentaires peuvent être introduites lorsque vous utilisez des classes de base virtuelles. Envisagez la hiérarchie de classes illustrée à la figure suivante.  
  
 ![Classe de hiérarchie qui montre les classes de base virtuelles](../cpp/media/vc39012.gif "vc39012")  
Hiérarchie de classes montrant des Classes de Base virtuelles  
  
 Dans cette hiérarchie, `A` est une classe de base virtuelle. Une instance donnée de la classe `E` et un pointeur vers le `A` sous-objet, un **dynamic_cast** vers un autre pointeur vers `B` échoue en raison de l’ambiguïté. Vous devez commencer par caster à l’ensemble `E` de l’objet, puis progressez sauvegarder la hiérarchie, de manière non équivoque, pour atteindre le bon `B` objet.  
  
 Envisagez la hiérarchie de classes illustrée à la figure suivante.  
  
 ![Hiérarchie montrant des classes de base en double de classes](../cpp/media/vc39013.gif "vc39013")  
Hiérarchie de classes montrant des Classes de Base en double  
  
 Étant donné un objet de type `E` et un pointeur vers le `D` sous-objet, accéder à partir de la `D` sous-objet à l’extrême gauche `A` sous-objet, trois conversions peuvent être effectuées. Vous pouvez effectuer un **dynamic_cast** conversion à partir de la `D` pointeur vers un `E` pointeur, puis une conversion (soit **dynamic_cast** ou une conversion implicite) à partir de `E`à `B`et enfin une conversion implicite de `B` à `A`. Exemple :  
  
```cpp 
// dynamic_cast_5.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B : public A {virtual void f();};  
class C : public A { };  
class D {virtual void f();};  
class E : public B, public C, public D {virtual void f();};  
  
void f(D* pd) {  
   E* pe = dynamic_cast<E*>(pd);  
   B* pb = pe;   // upcast, implicit conversion  
   A* pa = pb;   // upcast, implicit conversion  
}  
```  
  
 Le **dynamic_cast** opérateur peut également être utilisé pour effectuer un « cast croisé ». À l’aide de la même hiérarchie de classe, il est possible d’effectuer un cast d’un pointeur, par exemple, à partir de la `B` sous-objet à la `D` sous-objet, tant que l’objet complet est de type `E`.  
  
 Envisagez d’utiliser entre les casts, il est en fait possible d’effectuer la conversion d’un pointeur vers `D` vers un pointeur vers l’extrême gauche `A` sous-objet en deux étapes seulement. Vous pouvez effectuer une croix effectuer un cast du `D` à `B`, puis une conversion implicite de `B` à `A`. Exemple :  
  
```cpp 
// dynamic_cast_6.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B : public A {virtual void f();};  
class C : public A { };  
class D {virtual void f();};  
class E : public B, public C, public D {virtual void f();};  
  
void f(D* pd) {  
   B* pb = dynamic_cast<B*>(pd);   // cross cast  
   A* pa = pb;   // upcast, implicit conversion  
}  
```  
  
 Une valeur de pointeur null est convertie à la valeur de pointeur null du type de destination par **dynamic_cast**.  
  
 Lorsque vous utilisez `dynamic_cast < type-id > ( expression )`si `expression` ne peut pas être converti en toute sécurité en type `type-id`, la vérification de l’exécution provoque la conversion en échec. Exemple :  
  
```cpp 
// dynamic_cast_7.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
  
void f() {  
   A* pa = new A;  
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;  
   // B not derived from A  
}  
```  
  
 La valeur d’un échec de cast en type pointeur est le pointeur null. Un échec de cast pour référencer le type lève une [bad_cast, Exception](../cpp/bad-cast-exception.md).   Si `expression` ne pas pointer vers ou référencer un objet valid, un `__non_rtti_object` exception est levée.  
  
 Consultez [typeid](../cpp/typeid-operator.md) pour une explication de la `__non_rtti_object` exception.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée le pointeur de la classe de base (struct A), à un objet (struct C).  Ceci, ainsi que le fait il sont des fonctions virtuelles, Active le polymorphisme de runtime.  
  
 L’exemple appelle également une fonction non virtuelle dans la hiérarchie.  
  
```cpp 
// dynamic_cast_8.cpp  
// compile with: /GR /EHsc  
#include <stdio.h>  
#include <iostream>  
  
struct A {  
    virtual void test() {  
        printf_s("in A\n");  
   }  
};  
  
struct B : A {  
    virtual void test() {  
        printf_s("in B\n");  
    }  
  
    void test2() {  
        printf_s("test2 in B\n");  
    }  
};  
  
struct C : B {  
    virtual void test() {  
        printf_s("in C\n");  
    }  
  
    void test2() {  
        printf_s("test2 in C\n");  
    }  
};  
  
void Globaltest(A& a) {  
    try {  
        C &c = dynamic_cast<C&>(a);  
        printf_s("in GlobalTest\n");  
    }  
    catch(std::bad_cast) {  
        printf_s("Can't cast to C\n");  
    }  
}  
  
int main() {  
    A *pa = new C;  
    A *pa2 = new B;  
  
    pa->test();  
  
    B * pb = dynamic_cast<B *>(pa);  
    if (pb)  
        pb->test2();  
  
    C * pc = dynamic_cast<C *>(pa2);  
    if (pc)  
        pc->test2();  
  
    C ConStack;  
    Globaltest(ConStack);  
  
   // will fail because B knows nothing about C  
    B BonStack;  
    Globaltest(BonStack);  
}  
```  
  
```Output  
in C  
test2 in B  
in GlobalTest  
Can't cast to C  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs de casting](../cpp/casting-operators.md)   
 [Mots clés](../cpp/keywords-cpp.md)