---
description: 'En savoir plus sur : tableaux multidimensionnels (C)'
title: Tableaux multidimensionnels (C)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
ms.openlocfilehash: e940ccdd61aa6c2c4b3b5f85b355b80f86c8a165
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243365"
---
# <a name="multidimensional-arrays-c"></a>Tableaux multidimensionnels (C)

Une expression d'indice peut également avoir plusieurs indices, comme suit :

```
expression1 [ expression2 ] [ expression3 ] ...
```

Les expressions d'indice s'associent de gauche à droite. L’expression d’indice la plus à gauche, *expression1* **[** *Expression2* **]**, est évaluée en premier. L'adresse qui résulte de l'ajout *d'expression1* et *expression2* forme une expression de pointeur. Ensuite, *expression3* est ajouté à cette expression de pointeur pour former une nouvelle expression de pointeur, et ainsi de suite jusqu'à ce que la dernière expression d'indice ait été ajoutée. L’opérateur d’indirection ( <strong>\*</strong> ) est appliqué après l’évaluation de la dernière expression de script, sauf si la valeur de pointeur finale traite un type tableau (voir les exemples ci-dessous).

Les expressions à indices multiples font référence à des éléments de tableaux multidimensionnels. Un tableau multidimensionnel est un tableau dont les éléments sont des tableaux. Par exemple, le premier élément d'un tableau tridimensionnel est un tableau à deux dimensions.

## <a name="examples"></a>Exemples

Pour les exemples suivants, un tableau nommé `prop` est déclaré avec trois éléments, chacun d’eux étant un tableau de 4 par 6 **`int`** .

```
int prop[3][4][6];
int i, *ip, (*ipp)[6];
```

Une référence au tableau `prop` ressemble à ceci :

```
i = prop[0][0][1];
```

L’exemple ci-dessus montre comment faire référence au deuxième **`int`** élément individuel de `prop` . Les tableaux sont stockés par ligne, le dernier indice variant ainsi plus rapidement. L'expression `prop[0][0][2]` fait référence à l'élément suivant (le troisième), et ainsi de suite.

```
i = prop[2][1][3];
```

Cette instruction est une référence plus complexe à un élément de `prop` individuel. L'expression est évaluée de la manière suivante :

1. Le premier indice, `2` , est multiplié par la taille d’un tableau de 4 par 6 **`int`** et ajouté à la valeur du pointeur `prop` . Le résultat pointe vers le tableau de 4 par 6 de `prop`.

1. Le deuxième indice, `1` , est multiplié par la taille du tableau de 6 éléments **`int`** et ajouté à l’adresse représentée par `prop[2]` .

1. Chaque élément du tableau de 6 éléments est une **`int`** valeur, donc l’indice final, `3` , est multiplié par la taille d’un avant d' **`int`** être ajouté à `prop[2][1]` . Le pointeur résultant traite le quatrième élément du tableau de 6 éléments.

1. L'opérateur d'indirection est appliqué à la valeur du pointeur. Le résultat est l' **`int`** élément à cette adresse.

Les deux exemples suivants présentent des cas où l'opérateur d'indirection n'est pas appliqué.

```
ip = prop[2][1];

ipp = prop[2];
```

Dans la première de ces instructions, l'expression `prop[2][1]` est une référence valide au tableau tridimensionnel `prop`. Elle fait référence à un tableau de 6 éléments (déclaré ci-dessus). La valeur de pointeur adressant un tableau, l'opérateur d'indirection n'est pas appliqué.

De même, le résultat de l'expression `prop[2]` dans la deuxième instruction `ipp = prop[2];` est une valeur de pointeur adressant un tableau à deux dimensions.

## <a name="see-also"></a>Voir aussi

[Opérateur d’indice :](../cpp/subscript-operator.md)
