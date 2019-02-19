---
title: Opérateurs arithmétiques unaires
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], unary
- tilde (~) one's complement operator
- bitwise-complement operator
- arithmetic operators [C++], unary
- + operator, unary operators
- unary operators
- exclamation points
- ~ operator, one's complement operator
- logical negation
- '! operator, unary arithmetic operators'
ms.assetid: 78c91415-d469-499e-9dfe-4435350fd333
ms.openlocfilehash: f64bc5107cf0df55fd445d04d557e952702deaee
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150829"
---
# <a name="unary-arithmetic-operators"></a>Opérateurs arithmétiques unaires

Les opérateurs unaires plus C, de négation arithmétique, de complément et de négation logique sont présentés dans la liste suivante :

|Opérateur|Description|
|--------------|-----------------|
|**+**|L'opérateur unaire plus précédant une expression entre parenthèses force le regroupement des opérations entre parenthèses. Il est utilisé avec des expressions qui impliquent plusieurs opérateurs binaires associatifs ou commutatifs. L'opérande doit être de type arithmétique. Le résultat est la valeur de l'opérande. Un opérande intégral entraîne la promotion d'un intégral. Le type du résultat est le type de l’opérande promu.|
|**-**|L’opérateur de négation arithmétique produit la partie négative (complément à deux) de son opérande. L'opérande doit être une valeur intégrale ou flottante. Cet opérateur exécute les conversions arithmétiques classiques.|
|`~`|L’opérateur de compléments de bits (ou opérateur de bits Not) produit le complément de bits de son opérande. L'opérande doit être de type intégral. Cet opérateur exécute les conversions arithmétiques classiques. Le résultat a le type de l’opérande après conversion.|
|**!**|L’opérateur de négation logique (opérateur NOT logique) produit la valeur 0 si son opérande est true (différente de zéro) et si la valeur 1 de son opérande est false (0). Le résultat a le type `int`. L'opérande doit être une valeur intégrale, flottante ou pointeur.|

Les opérations arithmétiques unaires sur les pointeurs ne sont pas conformes.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent les opérateurs arithmétiques unaires :

```
short x = 987;
    x = -x;
```

Dans l’exemple ci-dessus, la nouvelle valeur de `x` est la partie négative de 987, ou -987.

```
unsigned short y = 0xAAAA;
    y = ~y;
```

Dans cet exemple, la nouvelle valeur assignée à `y` est un complément à 1 de la valeur non signée 0xAAAA ou 0x5555.

```
if( !(x < y) )
```

Si `x` est supérieur ou égal à `y`, le résultat de l'expression est 1 (true). Si `x` est inférieur à `y`, le résultat est 0 (false).

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)
