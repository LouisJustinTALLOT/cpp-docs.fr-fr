---
title: Opérateurs d'assignation
description: Syntaxe et utilisation des opérateurs d’assignation de langage C++ standard.
ms.date: 07/24/2020
f1_keywords:
- =
- '*='
- /=
- '%='
- +=
- -=
- <<=
- '>>='
- '&='
- ^=
- '|='
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
- ^= operator
- += operator
- '>>= operator'
- '|= operator'
- operator>>=
- '*= operator'
- '%= operator'
- ^= operator
- operator >>=
- = operator
- -= operator
- /= operator
- <<= operator
ms.assetid: b028cf35-2ff1-4f14-9027-fd53ebec8aa0
ms.openlocfilehash: 91346d06c6fab4f3cd83c5318c88e738daf8d249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229218"
---
# <a name="assignment-operators"></a>Opérateurs d'assignation

## <a name="syntax"></a>Syntaxe

*expression* d’assignation d' *expression* *-opérateur*

*assignment-operator* : un des éléments suivants :<br/>
&emsp;**`=`**&emsp;**`*=`**&emsp;**`/=`**&emsp;**`%=`**&emsp;**`+=`**&emsp;**`-=`**&emsp;**`<<=`**&emsp;**`>>=`**&emsp;**`&=`**&emsp;**`^=`**&emsp;**`|=`**

## <a name="remarks"></a>Notes

Les opérateurs d’assignation stockent une valeur dans l’objet spécifié par l’opérande gauche. Il existe deux types d’opérations d’assignation :

- *assignation simple*, dans laquelle la valeur du deuxième opérande est stockée dans l’objet spécifié par le premier opérande.

- *assignation composée*, dans laquelle une opération arithmétique, de décalage ou de bits est effectuée avant le stockage du résultat.

Tous les opérateurs d’assignation dans le tableau suivant, à l’exception de l' **`=`** opérateur, sont des opérateurs d’assignation composée.

### <a name="assignment-operators-table"></a>Table des opérateurs d’assignation

| Opérateur | Signification |
|--|--|
| **`=`** | Enregistre la valeur du deuxième opérande dans l’objet spécifié par le premier opérande (assignation simple). |
| **`*=`** | Multiplie la valeur du premier opérande par la valeur du deuxième opérande ; enregistre le résultat dans l’objet spécifié par le premier opérande. |
| **`/=`** | Divise la valeur du premier opérande par la valeur du deuxième opérande ; enregistre le résultat dans l’objet spécifié par le premier opérande. |
| **`%=`** | Accepte le module du premier opérande spécifié par la valeur du deuxième opérande ; enregistre le résultat dans l’objet spécifié par le premier opérande. |
| **`+=`** | Ajoute la valeur du deuxième opérande à la valeur du premier opérande ; enregistre le résultat dans l’objet spécifié par le premier opérande. |
| **`-=`** | Soustrait la valeur du deuxième opérande de la valeur du premier opérande ; enregistre le résultat dans l’objet spécifié par le premier opérande. |
| **`<<=`** | Déplace la valeur du premier opérande à gauche du nombre de bits spécifiés par la valeur du deuxième opérande ; enregistre le résultat dans l’objet spécifié par le premier opérande. |
| **`>>=`** | Déplace la valeur du premier opérande à droite du nombre de bits spécifiés par la valeur du deuxième opérande ; enregistre le résultat dans l'objet spécifié par le premier opérande. |
| **`&=`** | Obtient l'opérateur de bits AND du premier et du deuxième opérandes ; enregistre le résultat dans l'objet spécifié par le premier opérande. |
| **`^=`** | Obtient l'opérateur de bits OR exclusif du premier et du deuxième opérandes ; enregistre le résultat dans l'objet spécifié par le premier opérande. |
| **`|=`** | Obtient l’opérateur de bits OR inclusif du premier et du deuxième opérandes ; enregistre le résultat dans l’objet spécifié par le premier opérande. |

### <a name="operator-keywords"></a>Mots clés des opérateurs

Trois des opérateurs d’assignation composée ont des équivalents de mots clés. Il s'agit de :

| Opérateur | Équivalent |
|--|--|
| **`&=`** | **`and_eq`** |
| **`|=`** | **`or_eq`** |
| **`^=`** | **`xor_eq`** |

C++ spécifie ces mots clés d’opérateur comme autres orthographes pour les opérateurs d’assignation composée. En C, les autres orthographes sont fournies sous forme de macros dans l' \<iso646.h> en-tête. En C++, l’orthographe alternative est le mot clé. l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

## <a name="example"></a>Exemple

```cpp
// expre_Assignment_Operators.cpp
// compile with: /EHsc
// Demonstrate assignment operators
#include <iostream>
using namespace std;
int main() {
   int a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555;

   a += b;      // a is 9
   b %= a;      // b is 6
   c >>= 1;      // c is 5
   d |= e;      // Bitwise--d is 0xFFFF

   cout  << "a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555" << endl
         << "a += b yields " << a << endl
         << "b %= a yields " << b << endl
         << "c >>= 1 yields " << c << endl
         << "d |= e yields " << hex << d << endl;
}
```

## <a name="simple-assignment"></a>Assignation simple

L’opérateur d’assignation simple ( **`=`** ) entraîne le stockage de la valeur du second opérande dans l’objet spécifié par le premier opérande. Si les deux objets sont de type arithmétique, l’opérande de droite est converti vers le type de gauche, avant le stockage de la valeur.

Les objets **`const`** de **`volatile`** types et peuvent être assignés à des l-values de types qui sont uniquement **`volatile`** , ou qui ne sont pas **`const`** ou **`volatile`** .

L’assignation aux objets de type classe **`struct`** ( **`union`** types, et **`class`** ) est effectuée par une fonction nommée `operator=` . Le comportement par défaut de cette fonction d'opérateur consiste à effectuer une copie de bits ; toutefois, ce comportement peut être modifié à l'aide d'opérateurs surchargés. Pour plus d’informations, consultez [Surcharge d’opérateur](../cpp/operator-overloading.md). Les types de classe peuvent également avoir des opérateurs d’assignation de *copie* et de *déplacement* . Pour plus d’informations, consultez [constructeurs de copie et opérateurs d’assignation de copie](copy-constructors-and-copy-assignment-operators-cpp.md) et opérateurs de déplacement et opérateurs d’assignation de [déplacement](move-constructors-and-move-assignment-operators-cpp.md).

Un objet de toute classe clairement dérivée d'une classe de base donnée peut être assigné à un objet de la classe de base. L’inverse n’est pas vrai, car il existe une conversion implicite de la classe dérivée vers la classe de base, mais pas de la classe de base vers la classe dérivée. Par exemple :

```cpp
// expre_SimpleAssignment.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
class ABase
{
public:
    ABase() { cout << "constructing ABase\n"; }
};

class ADerived : public ABase
{
public:
    ADerived() { cout << "constructing ADerived\n"; }
};

int main()
{
    ABase aBase;
    ADerived aDerived;

    aBase = aDerived; // OK
    aDerived = aBase; // C2679
}
```

Les assignations aux types référence se comportent comme si l'assignation était effectuée à l'objet auquel la référence pointe.

Pour les objets de type classe, l'assignation est différente de l'initialisation. Pour illustrer les différences entre l'assignation et l'initialisation, prenez le code

```cpp
UserType1 A;
UserType2 B = A;
```

Le code précédent illustre un initialiseur ; il appelle le constructeur de `UserType2` qui accepte un argument de type `UserType1`. Étant donné le code

```cpp
UserType1 A;
UserType2 B;

B = A;
```

l'instruction d'assignation

```cpp
B = A;
```

peut avoir l'un des effets suivants :

- Appelez la fonction `operator=` pour `UserType2` , à condition qu' `operator=` un argument soit fourni `UserType1` .

- Appelez la fonction de conversion explicite `UserType1::operator UserType2`, si une telle fonction existe.

- Appelez un constructeur `UserType2::UserType2`, si un tel constructeur existe, qui accepte un argument `UserType1` et copie le résultat.

## <a name="compound-assignment"></a>Assignation composée

Les opérateurs d’assignation composée sont affichés dans le [tableau opérateurs d’affectation](#assignment-operators-table). Ces opérateurs ont le format *E1* *op* =  *E2*, où *E1* est une **`const`** l-value non modifiable et *E2* est :

- type arithmétique

- pointeur, si *op* est **`+`** ou**`-`**

La forme *E1* *op* =  *E2* se comporte comme *E1* **`=`** *E1* *op* *E2*, mais *E1* n’est évalué qu’une seule fois.

L'assignation composée en type énuméré génère un message d'erreur. Si l’opérande de gauche est d’un type pointeur, l’opérande de droite doit être d’un type pointeur ou il doit s’agir d’une expression constante qui prend la valeur 0. Lorsque l’opérande de gauche est d’un type intégral, l’opérande de droite ne doit pas être d’un type pointeur.

## <a name="result-of-assignment-operators"></a>Résultat des opérateurs d'assignation

Les opérateurs d'assignation retournent la valeur de l'objet spécifié par l'opérande gauche après l'assignation. Le type résultant est le type de l’opérande gauche. Le résultat d'une expression d'assignation est toujours une l-value. Ces opérateurs ont une associativité de droite à gauche. L’opérande gauche doit être une l-value modifiable.

En C ANSI, le résultat d’une expression d’assignation n’est pas une l-value. Cela signifie que l’expression C++ légale `(a += b) += c` n’est pas autorisée en C.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)<br/>
[Opérateurs, priorité et associativité C++ intégrés](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[opérateurs d'assignation C](../c-language/c-assignment-operators.md)
