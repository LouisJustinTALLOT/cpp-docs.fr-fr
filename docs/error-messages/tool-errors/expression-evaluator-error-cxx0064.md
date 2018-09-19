---
title: Évaluateur d’expression, erreur CXX0064 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b16133484af5a2225f79c5d293a2c8edd948bdb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025891"
---
# <a name="expression-evaluator-error-cxx0064"></a>Évaluateur d'expression, erreur CXX0064

ne peut pas définir le point d’arrêt sur fonction membre virtuelle liée

Un point d’arrêt a été défini sur une fonction membre virtuelle via un pointeur vers un objet, tel que :

```
pClass->vfunc( int );
```

Peut indiquer un point d’arrêt sur une fonction virtuelle en entrant la classe, par exemple :

```
Class::vfunc( int );
```

Cette erreur est identique à CAN0064.