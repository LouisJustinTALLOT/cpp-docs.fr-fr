---
title: Utilisation des opérateurs additifs
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 0e2d802a77c56b8f458b614b29e86e2e1d30a55e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151427"
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

La valeur de `i` est multipliée par la longueur d’un **float** et ajoutée à `&x[4]`. La valeur de pointeur résultante est l'adresse de `x[8]`.

```
j = &x[i] - &x[i-2];
```

Dans cet exemple, l'adresse du troisième élément de `x` (donné par `x[i-2]`) est ensuite soustraite dans l'adresse du cinquième élément de `x` (donné par `x[i]`). La différence est divisée par la longueur d’un **float** ; le résultat est la valeur entière 2.

## <a name="see-also"></a>Voir aussi

[Opérateurs additifs C](../c-language/c-additive-operators.md)
