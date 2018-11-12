---
title: 'Opérateurs de pointeur vers membre : .* et -&gt;*'
ms.date: 11/04/2016
f1_keywords:
- .*
- ->*
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators [C++]
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
ms.openlocfilehash: 60dad0e3134662957ee21396d330af795e80918e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620829"
---
# <a name="pointer-to-member-operators--and--gt"></a>Opérateurs de pointeur vers membre : .* et -&gt;*

## <a name="syntax"></a>Syntaxe

```
expression .* expression
expression ->* expression
```

## <a name="remarks"></a>Notes

Les opérateurs de pointeur vers membre,. * et ->\*, retourner la valeur d’un membre de classe spécifique pour l’objet spécifié sur le côté gauche de l’expression.  Le côté droit doit spécifier un membre de la classe.  L'exemple ci-dessous illustre l'utilisation de ces opérateurs :

```cpp
// expre_Expressions_with_Pointer_Member_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

class Testpm {
public:
   void m_func1() { cout << "m_func1\n"; }
   int m_num;
};

// Define derived types pmfn and pmd.
// These types are pointers to members m_func1() and
// m_num, respectively.
void (Testpm::*pmfn)() = &Testpm::m_func1;
int Testpm::*pmd = &Testpm::m_num;

int main() {
   Testpm ATestpm;
   Testpm *pTestpm = new Testpm;

// Access the member function
   (ATestpm.*pmfn)();
   (pTestpm->*pmfn)();   // Parentheses required since * binds
                        // less tightly than the function call.

// Access the member data
   ATestpm.*pmd = 1;
   pTestpm->*pmd = 2;

   cout  << ATestpm.*pmd << endl
         << pTestpm->*pmd << endl;
   delete pTestpm;
}
```

## <a name="output"></a>Sortie

```Output
m_func1
m_func1
1
2
```

Dans l'exemple précédent, un pointeur vers un membre, `pmfn`, est utilisé pour appeler la fonction membre `m_func1`. Un autre pointeur vers un membre, `pmd`, est utilisé pour accéder au membre `m_num`.

L’opérateur binaire .* associe son premier opérande, qui doit être un objet de type classe, avec son second opérande, qui doit être un type pointeur vers membre.

L’opérateur binaire -> * associe son premier opérande, qui doit être un pointeur vers un objet de type classe, avec son second opérande, qui doit être un type pointeur vers membre.

Dans une expression contenant l’opérateur .*, le premier opérande doit être du type classe du pointeur vers le membre spécifié dans le second opérande, et accessible à ce dernier, ou d’un type accessible clairement dérivé de cette classe et accessible à cette dernière.

Dans une expression contenant le-> * (opérateur), le premier opérande doit être de type « pointeur vers le type de classe » du type spécifié dans le second opérande, ou il doit être d’un type sans ambiguïté dérivée de cette classe.

## <a name="example"></a>Exemple

Considérez les classes et le fragment de programme suivants :

```cpp
// expre_Expressions_with_Pointer_Member_Operators2.cpp
// C2440 expected
class BaseClass {
public:
   BaseClass(); // Base class constructor.
   void Func1();
};

// Declare a pointer to member function Func1.
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;

class Derived : public BaseClass {
public:
   Derived();  // Derived class constructor.
   void Func2();
};

// Declare a pointer to member function Func2.
void (Derived::*pmfnFunc2)() = &Derived::Func2;

int main() {
   BaseClass ABase;
   Derived ADerived;

   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to
                           // access pointers to members of
                           // derived classes.

   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously
                              // derived from BaseClass.
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.
}
```

Le résultat de la. * ou ->\* opérateurs pointeur vers membre est un objet ou une fonction du type spécifié dans la déclaration de pointeur vers membre. Ainsi, dans l'exemple précédent, le résultat de l'expression `ADerived.*pmfnFunc1()` est un pointeur vers une fonction qui retourne void. Ce résultat est une l-value si le second opérande est une l-value.

> [!NOTE]
>  Si le résultat d’un des opérateurs de pointeur vers membre est une fonction, le résultat peut être utilisé uniquement comme opérande pour l’opérateur d’appel de fonction.

## <a name="see-also"></a>Voir aussi

[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)