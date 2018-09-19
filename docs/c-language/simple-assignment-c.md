---
title: Assignation simple (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff4e032e205680da84369075514e3177fa5fb33e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051020"
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