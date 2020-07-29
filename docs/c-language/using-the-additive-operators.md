---
title: Utilisation des opérateurs additifs
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 06d71f3ad1944976a8d415be9487cb5ea365fa26
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213682"
---
# <a name="using-the-additive-operators"></a>Utilisation des opérateurs additifs

Les exemples suivants, qui illustrent les opérateurs d'addition et de soustraction, utilisent ces déclarations :

```
int i = 4, j;
float x[10];
float *px;
```

Ces instructions sont équivalentes :

```
px = &x[4 + i];
px = &x[4] + i;
```

La valeur de `i` est multipliée par la longueur d’un **`float`** et ajoutée à `&x[4]` . La valeur de pointeur résultante est l'adresse de `x[8]`.

```
j = &x[i] - &x[i-2];
```

Dans cet exemple, l'adresse du troisième élément de `x` (donné par `x[i-2]`) est ensuite soustraite dans l'adresse du cinquième élément de `x` (donné par `x[i]`). La différence est divisée par la longueur d’un **`float`** ; le résultat est la valeur entière 2.

## <a name="see-also"></a>Voir aussi

[Opérateurs additifs C](../c-language/c-additive-operators.md)
