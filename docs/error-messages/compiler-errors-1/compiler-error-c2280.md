---
title: C2280 d’erreur du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 04/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
dev_langs:
- C++
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b55e07a7109c090126dfdec61bbc18bdaf5ef710
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33177643"
---
# <a name="compiler-error-c2280"></a>C2280 d’erreur du compilateur  
  
'*déclaration*' : tentative de référencement d’une fonction supprimée  
  
Le compilateur a détecté une tentative pour faire référence à un `deleted` (fonction). Cette erreur peut résulter d’un appel à une fonction membre qui a été explicitement marquée comme `= deleted` dans le code source. Cette erreur peut également être provoquée par un appel à une fonction membre spéciale implicite d’un struct ou une classe qui est déclarée et marquée comme automatiquement `deleted` par le compilateur. Pour plus d’informations sur lorsque le compilateur génère automatiquement `default` ou `deleted` fonctions membres spéciales, consultez [fonctions membres spéciales](../../cpp/special-member-functions.md).  
  
## <a name="example-explicitly-deleted-functions"></a>Exemple : Supprimer explicitement des fonctions  

Un appel à une explicitement `deleted` fonction provoque cette erreur. Un explicitement `deleted` fonction membre implique que la classe ou structure est délibérément conçu pour empêcher son utilisation, par conséquent, pour résoudre ce problème, vous devez modifier votre code pour l’éviter.  
  
```cpp  
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```  
  
## <a name="example-uninitialized-data-members"></a>Exemple : Données membres non initialisées  
  
Un membre de données de type référence sans être initialisé ou `const` membre de données, le compilateur déclarent implicitement un `deleted` constructeur par défaut. Pour résoudre ce problème, initialisez le membre de données lorsqu’il est déclaré.  
  
```cpp  
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```  
  
## <a name="example-reference-and-const-data-members"></a>Exemple : Référence et les données membres const  
  
A `const` ou membre de données de type référence, le compilateur déclarer un `deleted` opérateur d’assignation de copie. Une fois initialisée, ces membres ne peut pas être assignées, donc une simple copie ou déplacement ne peut pas fonctionner. Pour résoudre ce problème, nous vous recommandons de que modifier votre logique pour supprimer les opérations d’assignation qui provoquent l’erreur.  
  
```cpp  
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes 
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```  
  
## <a name="example-movable-deletes-implicit-copy"></a>Exemple : Mobile supprime la copie implicite  
  
Si une classe déclare un constructeur de déplacement ou un opérateur d’assignation de déplacement, mais ne déclare pas explicitement un constructeur de copie, le compilateur implicitement déclare un constructeur de copie et définit en tant que `deleted`. De même, si une classe déclare un constructeur de déplacement ou un opérateur d’assignation de déplacement, mais ne déclare pas explicitement un opérateur d’assignation de copie, le compilateur implicitement déclare un opérateur d’assignation de copie et définit en tant que `deleted`. Pour résoudre ce problème, vous devez déclarer explicitement ces membres.  
 
Lorsque vous voyez l’erreur C2280 conjointement avec un `unique_ptr`, il y a certainement parce que vous tentez d’appeler son constructeur de copie, qui est un `deleted` (fonction). Par défaut, un `unique_ptr` ne peut pas être copié. Utilisez un constructeur de déplacement pour transférer la propriété à la place.  

```cpp  
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base  
{  
public:  
    base();  
    ~base(); 
    base(base&&); 
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this 
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};  

void copy(base *p)  
{  
    base b{*p};  // C2280
}  
```  

## <a name="example-variant-and-volatile-members"></a>Exemple : Les membres Variant et volatiles  
  
Versions du compilateur avant Visual Studio 2015 Update 2 ont des constructeurs par défaut généré et non conformes et les destructeurs pour les unions anonymes. Celles-ci sont maintenant implicitement déclarées comme `deleted`. Ces versions également autorisaient non conforme de définition implicite de `default` copier et déplacer des constructeurs et `default` copier et déplacer des opérateurs d’assignation dans les classes et structs ont `volatile` les variables de membre. Le compilateur considère qu’elles aient des constructeurs non triviaux et opérateurs d’assignation maintenant et ne génère pas de `default` implémentations. Lorsqu’une telle classe est un membre d’une union ou une union anonyme à l’intérieur d’une classe, les constructeurs de copie et de déplacement et opérateurs d’assignation de copie et de déplacement de l’union ou la classe sont implicitement définis en tant que `deleted`. Pour résoudre ce problème, vous devez déclarer explicitement les fonctions membres spéciales requises.  
  
```cpp  
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {  
    A() = default;
    A(const A&);
};  

struct B {  
    union {  
        A a;  
        int i;  
    };
    // To fix this issue, declare the required 
    // special member functions:
    // B(); 
    // B(const B& b);
};  

int main() {
    B b1;  
    B b2(b1);  // C2280  
}
```  
  
## <a name="example-indirect-base-members-deleted"></a>Exemple : Membres base indirectes de suppression  
  
Versions du compilateur avant Visual Studio 2015 Update 2 ont été non conforme et autorisé d’une classe dérivée d’appeler des fonctions d’indirectement dérivés de membres spéciales `private virtual` classes de base. Le compilateur émet désormais l’erreur du compilateur C2280 lorsqu’un appel est effectué.  
  
Dans cet exemple, la classe `top` dérive indirectement de privé virtuel `base`. Dans le code conforme, cela rend les membres de `base` inaccessible aux `top`; un objet de type `top` ne peut pas être par défaut construit ou détruit. Pour résoudre ce problème dans le code qui reposait sur l’ancien comportement du compilateur, modifiez la classe intermédiaire à utiliser `protected virtual` dérivation ou modifiez la `top` classe à utiliser la dérivation directe :  

```cpp  
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base  
{  
protected:  
    base();  
    ~base();  
};  

class middle : private virtual base {}; 
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};   

void destroy(top *p)  
{  
    delete p;  // C2280  
}  
```  
  