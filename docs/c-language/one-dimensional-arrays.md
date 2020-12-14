---
description: En savoir plus sur les tableaux de One-Dimensional
title: Tableaux unidimensionnels
ms.date: 11/04/2016
helpviewer_keywords:
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
ms.openlocfilehash: 6c75d4b8d9a64f95f3698e6953949a71df60cad6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256898"
---
# <a name="one-dimensional-arrays"></a>Tableaux unidimensionnels

Une expression suffixée suivie d'une expression entre crochets (**[ ]**) est une représentation indicée d'un élément d'un objet tableau. Une expression d'indice représente la valeur à l'adresse qui correspond aux positions de *expression* au-delà de *postfix-expression* une fois exprimée comme

```
postfix-expression [ expression ]
```

Généralement, la valeur représentée par *postfix-expression* est une valeur de pointeur, par exemple un identificateur de tableau, et *expression* est une valeur intégrale. Toutefois, sur le plan de la syntaxe, il est requis que l'une des expressions soit de type pointeur et l'autre de type intégral. La valeur intégrale peut donc se trouver dans la position *postfix-expression* et la valeur de pointeur peut être entre crochets, dans la position *expression* ou d'indice. Par exemple, ce code est conforme :

```c
// one_dimensional_arrays.c
int sum, *ptr, a[10];
int main() {
   ptr = a;
   sum = 4[ptr];
}
```

Les expressions d'indice servent généralement à faire référence à des éléments de tableau, mais vous pouvez appliquer un indice à n'importe quel pointeur. Quel que soit l'ordre des valeurs, *expression* doit être placé entre crochets (**[ ]**).

L’expression d’indice est évaluée en ajoutant la valeur intégrale à la valeur de pointeur, puis en appliquant l’opérateur d’indirection ( <strong>\*</strong> ) au résultat. (Pour plus d’informations sur l’opérateur d’indirection, consultez opérateurs d’indirection [et d’adresse](../c-language/indirection-and-address-of-operators.md) .) En effet, pour un tableau unidimensionnel, les quatre expressions suivantes sont équivalentes, en supposant que `a` est un pointeur et qu’il `b` s’agit d’un entier :

```
a[b]
*(a + b)
*(b + a)
b[a]
```

Selon les règles de conversion applicables à l'opérateur d'addition (données dans [Opérateurs additifs](../c-language/c-additive-operators.md)), la valeur intégrale est convertie en décalage d'adresse en la multipliant par la longueur du type adressé par le pointeur.

Par exemple, supposons que l’identificateur `line` fait référence à un tableau de **`int`** valeurs. La procédure suivante est utilisée pour évaluer l'expression d'indice `line[ i ]` :

1. La valeur entière `i` est multipliée par le nombre d’octets définis comme longueur d’un **`int`** élément. La valeur convertie de `i` représente des `i` **`int`** positions.

1. Cette valeur convertie est ajoutée à la valeur de pointeur d’origine ( `line` ) pour produire une adresse qui correspond aux `i` **`int`** positions de décalage à partir de `line` .

1. L'opérateur d'indirection est appliqué à la nouvelle adresse. Le résultat est la valeur de l'élément de tableau à cette position (intuitivement, `line [ i ]`).

L'expression d'indice `line[0]` représente la valeur du premier élément de line, puisque le décalage à partir de l'adresse représentée par `line` est 0. De même, une expression telle que `line[5]` fait référence à l'élément décalé de cinq positions par rapport à line, ou au sixième élément du tableau.

## <a name="see-also"></a>Voir aussi

[Opérateur d’indice :](../cpp/subscript-operator.md)
