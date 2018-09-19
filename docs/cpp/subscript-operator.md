---
title: Opérateur d’indice [] | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '[]'
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf12d517647e36c8a0d9428b818f3812bfea2e1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020613"
---
# <a name="subscript-operator-"></a>Opérateur d’indice]

## <a name="syntax"></a>Syntaxe

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>Notes

Une expression suffixée (qui peut également être une expression primaire) suivie de l’opérateur d’indice, **[]**, spécifie l’indexation de tableau.

Pour plus d’informations sur les tableaux managés, consultez [tableaux](../windows/arrays-cpp-component-extensions.md).

En règle générale, la valeur représentée par *postfix-expression* est une valeur de pointeur, par exemple un identificateur de tableau, et *expression* est une valeur intégrale (y compris les types énumérés). Toutefois, sur le plan de la syntaxe, il est requis que l'une des expressions soit de type pointeur et l'autre de type intégral. La valeur intégrale peut donc se trouver dans le *postfix-expression* position et la valeur de pointeur peut être entre crochets, dans le *expression* ou la position d’indice. Prenons le fragment de code suivant :

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

Dans l'exemple précédent, l'expression `nArray[2]` est identique à `2[nArray]`. La raison est que le résultat d’une expression d’indice `e1[e2]` est donnée par :

`*((e2) + (e1))`

L’adresse transmise par l’expression n’est pas *e2* octets à partir de l’adresse *e1*. Au lieu de cela, l’adresse est à l’échelle pour transmettre l’objet suivant dans le tableau *e2*. Exemple :

```cpp
double aDbl[2];
```

Les adresses de `aDb[0]` et `aDb[1]` sont 8 octets séparés, la taille d’un objet de type **double**. Cette mise à l’échelle en fonction du type d’objet est effectuée automatiquement par le langage C++ et est défini dans [opérateurs additifs](../cpp/additive-operators-plus-and.md) où l’addition et la soustraction des opérandes de type pointeur est abordée.

Une expression d'indice peut également avoir plusieurs indices, comme suit :

*expression1* **[** *expression2* **] [** *expression3* **]** ...

Les expressions d'indice s'associent de gauche à droite. L’expression d’indice la plus à gauche, *expression1* **[** *expression2* **]**, est évaluée en premier. L'adresse qui résulte de l'ajout *d'expression1* et *expression2* forme une expression de pointeur. Ensuite, *expression3* est ajouté à cette expression de pointeur pour former une nouvelle expression de pointeur, et ainsi de suite jusqu'à ce que la dernière expression d'indice ait été ajoutée. L’opérateur d’indirection (<strong>\*</strong>) est appliqué après la dernière expression d’indice est évaluée, sauf si la valeur de pointeur finale traite un type tableau.

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

Le premier élément d'un tableau est l'élément 0. La plage d’un tableau C++ est comprise entre *tableau*[0] à *tableau*[*taille* - 1]. Toutefois, C++ prend en charge les indices positifs et négatifs. Les indices négatifs doivent rester dans les limites du tableau. Sinon, les résultats sont imprévisibles. Le code suivant montre des indices de tableau positifs et négatifs :

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

L’indice négatif dans la dernière ligne peut produire une erreur d’exécution, car elle pointe vers une adresse 256 **int** positions inférieur dans la mémoire à l’origine du tableau. Le pointeur `midArray` est initialisé au milieu de `intArray`; il est donc possible (mais dangereux) à utiliser les deux index de tableau négatifs et positifs sur celui-ci. Les erreurs d’indice de tableau ne génèrent pas d’erreurs au moment de la compilation, mais ils produisent des résultats imprévisibles.

L'opérateur d'indice est commutatif. Par conséquent, les expressions *tableau*[*index*] et *index*[*tableau*] sont obligatoirement équivalentes aussi longtemps que l’indice opérateur n’est pas surchargé (consultez [opérateurs surchargés](../cpp/operator-overloading.md)). La première forme constitue la pratique de codage la plus courante, mais les deux fonctionnent.

## <a name="see-also"></a>Voir aussi

[Expressions suffixées](../cpp/postfix-expressions.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Tableaux](../cpp/arrays-cpp.md)<br/>
[Tableaux unidimensionnels](../c-language/one-dimensional-arrays.md)<br/>
[Tableaux multidimensionnels](../c-language/multidimensional-arrays-c.md)<br/>
