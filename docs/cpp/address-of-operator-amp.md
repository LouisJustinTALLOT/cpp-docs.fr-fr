---
title: 'Opérateur address-of : &amp; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f194041633b251320ae5fb7889e569a105230373
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019820"
---
# <a name="address-of-operator-amp"></a>Opérateur address-of : &amp;

## <a name="syntax"></a>Syntaxe

```
& cast-expression
```

## <a name="remarks"></a>Notes

L’opérateur unaire address-of (**&**) prend l’adresse de son opérande. L’opérande de l’opérateur address-of peut être un désignateur de fonction ou une l-value qui désigne un objet qui n’est pas un champ de bits.

L’opérateur d’adresse peut être appliqué uniquement aux variables dotées de types fondamentaux, structure, classe ou union qui sont déclarées au niveau de la portée du fichier, ou aux références indicées de tableau. Dans ces expressions, une expression constante qui n'inclut pas l'opérateur d'adresse peut être ajoutée ou soustraite dans l'expression d'adresse.

Lorsqu’il est appliqué à des fonctions ou des l-values, le résultat de l’expression est un type pointeur (une r-value) dérivé du type de l’opérande. Par exemple, si l’opérande est de type **char**, le résultat de l’expression est de type pointeur vers **char**. L’opérateur d’adresse, appliqué à **const** ou **volatile** objets, la valeur de `const type *` ou `volatile type *`, où **type** est le type de l’original objet.

Lorsque l’opérateur address-of est appliqué à un nom qualifié, le résultat varie selon que le *nom qualifié* spécifie un membre statique. Si oui, le résultat est un pointeur vers le type spécifié dans la déclaration du membre. Si le membre n’est pas statique, le résultat est un pointeur vers le membre *nom* de la classe indiquée par *qualified-class-name*. (Consultez [Expressions primaires](../cpp/primary-expressions.md) pour plus d’informations *qualified-class-name*.) Le fragment de code ci-dessous montre comment le résultat diffère si le membre est statique ou non :

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

Dans cet exemple, l'expression `&PTM::fValue` permet d'obtenir le type `float *` à la place du type `float PTM::*`, car `fValue` est un membre statique.

L'adresse d'une fonction surchargée peut être prise uniquement lorsque vous savez clairement quelle version de la fonction est référencée. Consultez [surcharge de fonction](function-overloading.md) pour plus d’informations sur la façon d’obtenir l’adresse d’un particulier fonction surchargée.

L'application de l'opérateur d'adresse à un type référence fournit le même résultat que l'application de l'opérateur à l'objet auquel la référence est liée. Exemple :

## <a name="example"></a>Exemple

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

## <a name="output"></a>Sortie

```Output
&d equals &rd
```

L'exemple ci-dessous utilise l'opérateur d'adresse pour passer un argument de pointeur à une fonction :

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

## <a name="output"></a>Sortie

```Output
25
```

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Déclarateur de référence Lvalue : &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Opérateurs d’indirection et d’adresse](../c-language/indirection-and-address-of-operators.md)