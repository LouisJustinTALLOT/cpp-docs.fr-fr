---
description: 'En savoir plus sur : opérateur d’indice []'
title: Opérateur d’indice []
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: e11e94bdf516d830020c4844be2a4c3bfc4a8774
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221200"
---
# <a name="subscript-operator-"></a>Opérateur d’indice []

## <a name="syntax"></a>Syntaxe

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>Notes

Une expression postfix (qui peut également être une expression primaire) suivie de l’opérateur d’indice, **[]**, spécifie l’indexation de tableau.

Pour plus d’informations sur les tableaux managés en C++/CLI, consultez [tableaux](../extensions/arrays-cpp-component-extensions.md).

En règle générale, la valeur représentée par *postfix-expression* est une valeur de pointeur, par exemple un identificateur de tableau, et *expression* est une valeur intégrale (y compris les types énumérés). Toutefois, sur le plan de la syntaxe, il est requis que l'une des expressions soit de type pointeur et l'autre de type intégral. La valeur intégrale peut donc se trouver dans la position *postfix-expression* et la valeur de pointeur peut être entre crochets dans l' *expression* ou la position d’indice. Prenons le fragment de code suivant :

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

Dans l'exemple précédent, l'expression `nArray[2]` est identique à `2[nArray]`. La raison en est que le résultat d’une expression d’indice `e1[e2]` est donné par :

`*((e2) + (e1))`

L’adresse obtenue par l’expression n’est pas *E2* octets à partir de l’adresse *E1*. Au lieu de cela, l’adresse est mise à l’échelle pour générer l’objet suivant dans le tableau *E2*. Par exemple :

```cpp
double aDbl[2];
```

Les adresses de `aDb[0]` et `aDb[1]` sont séparées de 8 octets, c’est-à-dire la taille d’un objet de type **`double`** . Cette mise à l’échelle selon le type d’objet est effectuée automatiquement par le langage C++ et est définie dans [opérateurs additifs](../cpp/additive-operators-plus-and.md) , où l’addition et la soustraction des opérandes de type pointeur sont discutées.

Une expression d'indice peut également avoir plusieurs indices, comme suit :

*expression1* **[** *Expression2* **] [** *expression3* **]** ...

Les expressions d'indice s'associent de gauche à droite. L’expression d’indice la plus à gauche, *expression1* **[** *Expression2* **]**, est évaluée en premier. L'adresse qui résulte de l'ajout *d'expression1* et *expression2* forme une expression de pointeur. Ensuite, *expression3* est ajouté à cette expression de pointeur pour former une nouvelle expression de pointeur, et ainsi de suite jusqu'à ce que la dernière expression d'indice ait été ajoutée. L’opérateur d’indirection ( <strong>\*</strong> ) est appliqué après l’évaluation de la dernière expression de script, sauf si la valeur de pointeur finale traite un type de tableau.

Les expressions à indices multiples font référence à des éléments de tableaux multidimensionnels. Un tableau multidimensionnel est un tableau dont les éléments sont des tableaux. Par exemple, le premier élément d'un tableau tridimensionnel est un tableau à deux dimensions. L'exemple suivant déclare et initialise un tableau de caractères simple à deux dimensions :

```cpp
// expre_Subscript_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
#define MAX_ROWS 2
#define MAX_COLS 2

int main() {
  char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };
  for ( int i = 0; i < MAX_ROWS; i++ )
     for ( int j = 0; j < MAX_COLS; j++ )
        cout << c[ i ][ j ] << endl;
}
```

## <a name="positive-and-negative-subscripts"></a>Indices positifs et négatifs

Le premier élément d'un tableau est l'élément 0. La plage d’un tableau C++ est comprise entre *Array*[0] et *Array*[*Size* -1]. Toutefois, C++ prend en charge les indices positifs et négatifs. Les indices négatifs doivent rester dans les limites du tableau. Sinon, les résultats sont imprévisibles. Le code suivant montre des indices de tableau positifs et négatifs :

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

L’indice négatif dans la dernière ligne peut générer une erreur d’exécution, car il pointe vers une adresse 256 **`int`** positions plus basse dans la mémoire que l’origine du tableau. Le pointeur `midArray` est initialisé au milieu de `intArray` ; il est donc possible (mais dangereux) d’utiliser à la fois des index de tableau positifs et négatifs. Les erreurs d’indice de tableau ne génèrent pas d’erreurs au moment de la compilation, mais ils produisent des résultats imprévisibles.

L'opérateur d'indice est commutatif. Par conséquent, les expressions *Array*[*index*] et *index*[*Array*] sont garanties comme équivalentes tant que l’opérateur d’indice n’est pas surchargé (consultez [opérateurs surchargés](../cpp/operator-overloading.md)). La première forme constitue la pratique de codage la plus courante, mais les deux fonctionnent.

## <a name="see-also"></a>Voir aussi

[Expressions suffixées](../cpp/postfix-expressions.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Tableaux](../cpp/arrays-cpp.md)<br/>
[Tableaux unidimensionnels](../c-language/one-dimensional-arrays.md)<br/>
[Tableaux multidimensionnels](../c-language/multidimensional-arrays-c.md)<br/>
