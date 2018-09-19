---
title: Erreur du compilateur C2891 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d81662cb02fa3c8f6af75009daf4dab9b70196
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016557"
---
# <a name="compiler-error-c2891"></a>Erreur du compilateur C2891

'paramètre' : ne peut pas prendre l’adresse d’un paramètre de modèle

Vous ne pouvez pas prendre l’adresse d’un paramètre de modèle, sauf si elle est une lvalue. Paramètres de type ne sont pas des lvalues, car ils n’ont aucun adresse. Également, les valeurs non-type dans les listes de paramètres de modèle qui ne sont pas des lvalues n’ont pas d’une adresse. Il s’agit d’un exemple de code qui provoque l’erreur du compilateur C2891, étant donné que la valeur passée comme paramètre de modèle est une copie générée par le compilateur de l’argument de modèle.

```
template <int i> int* f() { return &i; }
```

Paramètres de modèle qui sont des lvalues, tels que les types référence, peut avoir leur adresse prises.

```
template <int& r> int* f() { return &r; }
```

Pour corriger cette erreur, ne prennent pas l’adresse d’un paramètre de modèle, sauf si elle est une lvalue.