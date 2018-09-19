---
title: Utilisation des opérateurs additifs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 050db08d00d79e3cfee0ab7549532d78a51b1ade
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078866"
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