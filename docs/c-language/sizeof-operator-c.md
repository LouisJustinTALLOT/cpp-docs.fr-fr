---
title: sizeof, opérateur (C)
ms.date: 11/04/2016
f1_keywords:
- sizeof
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
ms.openlocfilehash: 0b5d25e0316c710ce758479ad9417c92201d929d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577630"
---
# <a name="sizeof-operator-c"></a>sizeof, opérateur (C)

L'opérateur `sizeof` donne la quantité de stockage, en octets, obligatoire pour stocker un objet du type de l'opérande. Cet opérateur vous permet d'éviter de spécifier les tailles de données dépendantes de l'ordinateur dans vos programmes.

## <a name="syntax"></a>Syntaxe

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>Notes

L’opérande est un identificateur qui est une *expression unaire* ou une expression de cast de type (c’est-à-dire, un spécificateur de type entre parenthèses). L’*expression unaire* ne peut pas représenter un objet de champ de bits, un type incomplet ou un indicateur de fonction. Le résultat est une constante intégrale non signée. L’en-tête standard STDDEF.H définit ce type comme **size_t**.

Lorsque vous appliquez l'opérateur `sizeof` à un identificateur du tableau, le résultat est la taille du tableau entier plutôt que la taille du pointeur représenté par l'identificateur du tableau.

Lorsque vous appliquez l'opérateur `sizeof` à un nom de type structure ou union, ou à un identificateur de type structure ou union, le résultat est le nombre d'octets de la structure ou de l'union, y compris le remplissage interne et à droite. Cette taille peut inclure le remplissage interne et à droite utilisé pour aligner les membres de la structure ou de l'union sur des limites de mémoire. Ainsi, le résultat peut ne pas correspondre à la taille calculée en additionnant les exigences en matière de stockage des membres individuels.

Si un tableau non dimensionné est le dernier élément d'une structure, l'opérateur `sizeof` retourne la taille de la structure sans le tableau.

```
buffer = calloc(100, sizeof (int) );
```

Cet exemple utilise l'opérateur `sizeof` pour passer la taille d'un `int`, qui varie suivant les ordinateurs, comme argument à une fonction runtime nommée `calloc`. La valeur retournée par la fonction est stockée dans `buffer`.

```
static char *strings[] = {
      "this is string one",
      "this is string two",
      "this is string three",
   };
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );
```

Dans cet exemple, `strings` est un tableau de pointeurs vers `char`. Le nombre de pointeurs est le nombre d'éléments du tableau, mais n'est pas spécifié. Il est facile de déterminer le nombre de pointeurs à l'aide de l'opérateur `sizeof` pour calculer le nombre d'éléments du tableau. La valeur entière **const** `string_no` est initialisée à ce nombre. Comme il s’agit d’une valeur **const**, `string_no` ne peut pas être modifié.

## <a name="see-also"></a>Voir aussi

[Opérateurs C](c-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
