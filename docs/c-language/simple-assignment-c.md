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
ms.openlocfilehash: 77c61101e9540a0d9469e7176eb15992a73b4b09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158278"
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

[Opérateurs d'assignation C](../c-language/c-assignment-operators.md)
