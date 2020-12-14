---
description: 'En savoir plus sur : assignation simple (C)'
title: Assignation simple (C)
ms.date: 11/04/2016
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
ms.openlocfilehash: bf8637268c810ed6a75095774ca6ff7b7d3d9e67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229897"
---
# <a name="simple-assignment-c"></a>Assignation simple (C)

L’opérateur d’assignation simple assigne son opérande droit à son opérande gauche. La valeur de l’opérande droit est convertie dans le type de l’expression d’assignation et remplace la valeur stockée dans l’objet désigné par l’opérande gauche. Les règles de conversion relatives à l'assignation sont applicables (consultez [Conversions d'assignation](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

Dans cet exemple, la valeur de `y` est convertie en type **`double`** et assignée à `x` .

## <a name="see-also"></a>Voir aussi

[Opérateurs d’assignation C](../c-language/c-assignment-operators.md)
