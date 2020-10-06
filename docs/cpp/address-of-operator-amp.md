---
title: 'Opérateur d’adresse : &amp;'
description: Opérateur d’adresse en langage C++.
ms.date: 10/02/2020
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: 8ef7ad065281e4de58ddbdebea25950f8eb9dd06
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765287"
---
# <a name="address-of-operator-amp"></a>Opérateur d’adresse : &amp;

## <a name="syntax"></a>Syntaxe

> **`&`** *`cast-expression`*

## <a name="remarks"></a>Notes

L’opérateur unaire Address-of ( **`&`** ) prend l’adresse de son opérande. L’opérande de l’opérateur d’adresse peut être un désignateur de fonction ou une l-value qui désigne un objet qui n’est pas un champ de bits.

L’opérateur d’adresse peut être appliqué uniquement aux variables de types fondamentaux, de structure, de classe ou d’Union déclarés au niveau de la portée du fichier, ou aux références de tableau en indice. Dans ces expressions, une expression constante qui n’inclut pas l’opérateur d’adresse peut être ajoutée ou soustraite de l’expression d’adresse.

Lorsqu’il est appliqué à des fonctions ou des l-values, le résultat de l’expression est un type pointeur (une r-value) dérivé du type de l’opérande. Par exemple, si l’opérande est de type **`char`** , le résultat de l’expression est de type pointeur vers **`char`** . L’opérateur d’adresse, appliqué aux **`const`** objets ou **`volatile`** , `const type *` `volatile type *` a la valeur ou, où `type` est le type de l’objet d’origine.

L’adresse d’une fonction surchargée ne peut être utilisée que lorsqu’il est clair que la version de la fonction est référencée. Consultez [surcharge de fonction](function-overloading.md) pour plus d’informations sur l’obtention de l’adresse d’une fonction surchargée particulière.

Lorsque l’opérateur address-of est appliqué à un nom qualifié, le résultat varie selon que le *nom qualifié* spécifie ou non un membre statique. Si oui, le résultat est un pointeur vers le type spécifié dans la déclaration du membre. Pour un membre qui n’est pas statique, le résultat est un pointeur vers le *nom* de membre de la classe indiquée par *Qualified-Class-Name*. Pour plus d’informations sur *Qualified-Class-Name*, consultez [expressions primaires](../cpp/primary-expressions.md).

## <a name="example-address-of-static-member"></a>Exemple : adresse d’un membre statique

Le fragment de code suivant montre comment le résultat de l’opérateur d’adresse diffère selon qu’un membre de classe est statique ou non :

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

## <a name="example-address-of-a-reference-type"></a>Exemple : adresse d’un type référence

L'application de l'opérateur d'adresse à un type référence fournit le même résultat que l'application de l'opérateur à l'objet auquel la référence est liée. Par exemple :

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

```Output
&d equals &rd
```

## <a name="example-function-address-as-parameter"></a>Exemple : adresse de fonction en tant que paramètre

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

```Output
25
```

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs, priorité et associativité C++ intégrés](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Déclarateur de référence Lvalue : &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Opérateurs d’indirection et d’adresse](../c-language/indirection-and-address-of-operators.md)
