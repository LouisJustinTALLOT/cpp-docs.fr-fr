---
title: dynamic_cast, opérateur
description: Vue d’ensemble C++ de l’opérateur Language dynamic_cast.
ms.date: 02/03/2020
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 0073aaa886bba33a0ec6c07fb89d6eee032765c8
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972219"
---
# <a name="dynamic_cast-operator"></a>dynamic_cast, opérateur

Convertit l’opérande `expression` en un objet de type `type-id`.

## <a name="syntax"></a>Syntaxe

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>Notes

Le `type-id` doit être un pointeur ou une référence à un type de classe précédemment défini ou un « pointeur vers void ». Le type de `expression` doit être un pointeur si `type-id` est un pointeur ou une l-value si `type-id` est une référence.

Consultez [static_cast](../cpp/static-cast-operator.md) pour obtenir une explication de la différence entre les conversions de cast statique et dynamique, et à quel moment il convient d’utiliser chacune d’elles.

Il existe deux modifications importantes dans le comportement de **dynamic_cast** dans du code managé :

- **dynamic_cast** à un pointeur vers le type sous-jacent d’un enum boxed échoue au moment de l’exécution, ce qui retourne 0 au lieu du pointeur converti.

- **dynamic_cast** ne lève plus d’exception quand `type-id` est un pointeur intérieur vers un type valeur, avec le cast qui échoue au moment de l’exécution.  La conversion retourne maintenant la valeur du pointeur 0 au lieu de la levée.

Si `type-id` est un pointeur vers une classe de base directe ou indirecte accessible non ambiguë de `expression`, un pointeur vers le sous-objet unique de type `type-id` est le résultat. Par exemple :

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

Ce type de conversion est appelé « upcast », car il déplace un pointeur vers le haut d’une hiérarchie de classes, d’une classe dérivée vers une classe dérivée de. Un upcast est une conversion implicite.

Si `type-id` est void *, une vérification au moment de l’exécution est effectuée pour déterminer le type réel de `expression`. Le résultat est un pointeur vers l’objet complet pointé par `expression`. Par exemple :

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

Si `type-id` n’est pas void *, une vérification au moment de l’exécution est effectuée pour déterminer si l’objet vers lequel pointe `expression` peut être converti vers le type désigné par `type-id`.

Si le type de `expression` est une classe de base du type de `type-id`, une vérification au moment de l’exécution est effectuée pour déterminer si `expression` pointe en fait vers un objet complet du type de `type-id`. Si la valeur est true, le résultat est un pointeur vers un objet complet du type de `type-id`. Par exemple :

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

Ce type de conversion est appelé « downcast », car il déplace un pointeur vers le dessous d’une hiérarchie de classes, d’une classe donnée vers une classe dérivée de celui-ci.

En cas d’héritage multiple, des possibilités d’ambiguïté sont introduites. Examinez la hiérarchie de classes illustrée dans la figure suivante.

Pour les types CLR, **dynamic_cast** produit une absence d’opération si la conversion peut être effectuée implicitement, ou une instruction MSIL `isinst`, qui effectue une vérification dynamique et retourne **nullptr** si la conversion échoue.

L’exemple suivant utilise **dynamic_cast** pour déterminer si une classe est une instance d’un type particulier :

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

![Hiérarchie de classes qui affiche plusieurs héritages](../cpp/media/vc39011.gif "Hiérarchie de classes montrant un héritage multiple") <br/>
Hiérarchie de classes montrant un héritage multiple

Un pointeur vers un objet de type `D` peut être casté en toute sécurité en `B` ou `C`. Toutefois, si `D` est casté pour pointer vers un objet `A`, quelle instance de `A` produira-t-elle ? Cela entraînerait une erreur de conversion ambiguë. Pour contourner ce problème, vous pouvez effectuer deux casts non ambigus. Par exemple :

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A {virtual void f();};
class D : public B, public C {virtual void f();};

void f() {
   D* pd = new D;
   A* pa = dynamic_cast<A*>(pd);   // C4540, ambiguous cast fails at runtime
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

D’autres ambiguïtés peuvent être introduites lorsque vous utilisez des classes de base virtuelles. Examinez la hiérarchie de classes illustrée dans la figure suivante.

![Hiérarchie de classes qui affiche les classes de base virtuelles](../cpp/media/vc39012.gif "Hiérarchie de classes montrant des classes de base virtuelles") <br/>
Hiérarchie de classes montrant des classes de base virtuelles

Dans cette hiérarchie, `A` est une classe de base virtuelle. À partir d’une instance de la classe `E` et d’un pointeur vers le sous-objet `A`, un **dynamic_cast** vers un pointeur vers `B` échouera en raison d’une ambiguïté. Vous devez d’abord effectuer un cast vers l’objet complet `E`, puis travailler de manière non ambiguë pour sauvegarder la hiérarchie afin d’atteindre l’objet de `B` approprié.

Examinez la hiérarchie de classes illustrée dans la figure suivante.

![Hiérarchie de classes qui affiche des classes de base en double](../cpp/media/vc39013.gif "Hiérarchie de classes montrant des classes de base en double") <br/>
Hiérarchie de classes montrant des classes de base en double

En fonction d’un objet de type `E` et d’un pointeur vers le sous-objet `D`, pour naviguer du sous-objet `D` vers le sous-objet `A` le plus à gauche, trois conversions peuvent être effectuées. Vous pouvez effectuer une conversion **dynamic_cast** du pointeur `D` vers un pointeur `E`, puis une conversion ( **dynamic_cast** ou une conversion implicite) de `E` à `B`, et enfin une conversion implicite de `B` en `A`. Par exemple :

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

L’opérateur **dynamic_cast** peut également être utilisé pour effectuer un « cross cast ». À l’aide de la même hiérarchie de classes, il est possible d’effectuer un cast d’un pointeur, par exemple, du sous-objet `B` vers le sous-objet `D`, à condition que l’objet complet soit de type `E`.

Si vous envisagez des transtypages croisés, il est possible d’effectuer la conversion d’un pointeur vers `D` en un pointeur vers le sous-objet `A` le plus à gauche en deux étapes. Vous pouvez effectuer une conversion croisée de `D` à `B`, puis une conversion implicite de `B` en `A`. Par exemple :

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

Une valeur de pointeur null est convertie en valeur de pointeur null du type de destination par **dynamic_cast**.

Lorsque vous utilisez `dynamic_cast < type-id > ( expression )`, si `expression` ne peut pas être converti en toute sécurité en type `type-id`, le contrôle au moment de l’exécution provoque l’échec de la conversion. Par exemple :

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

La valeur d’un cast ayant échoué en type pointeur est le pointeur null. Un échec de conversion en type référence lève une [Exception bad_cast](../cpp/bad-cast-exception.md).   Si `expression` ne pointe pas vers un objet valide ou ne fait pas référence à celui-ci, une exception `__non_rtti_object` est levée.

Consultez [typeid](../cpp/typeid-operator.md) pour obtenir une explication de l’exception `__non_rtti_object`.

## <a name="example"></a>Exemple

L’exemple suivant crée le pointeur de classe de base (struct A) dans un objet (struct C).  Cela, plus le fait qu’il existe des fonctions virtuelles, active le polymorphisme du Runtime.

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

[Opérateurs de casting](../cpp/casting-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)