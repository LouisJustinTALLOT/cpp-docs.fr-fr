---
description: 'En savoir plus sur : utilisation des opérateurs additifs'
title: Utilisation des opérateurs additifs
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: d56a1b2e2696ae88598306271ed02c417ef63b0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318362"
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
