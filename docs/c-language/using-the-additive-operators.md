---
title: Utilisation des opérateurs additifs
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 78dc559a83626057603027e30742435b1128e31c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557688"
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