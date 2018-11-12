---
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
ms.openlocfilehash: 76c48fc6774f97bab69f916ad7e5176e91d004ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574913"
---
# <a name="simple-assignment-c"></a>Assignation simple (C)

L’opérateur d’assignation simple assigne son opérande droit à son opérande gauche. La valeur de l’opérande droit est convertie dans le type de l’expression d’assignation et remplace la valeur stockée dans l’objet désigné par l’opérande gauche. Les règles de conversion relatives à l'assignation sont applicables (consultez [Conversions d'assignation](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

Dans cet exemple, la valeur de `y` est convertie en type **double** et assignée à `x`.

## <a name="see-also"></a>Voir aussi

[Opérateurs d’assignation C](../c-language/c-assignment-operators.md)