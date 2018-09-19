---
title: Erreur du compilateur C3120 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3120
dev_langs:
- C++
helpviewer_keywords:
- C3120
ms.assetid: 9b6b210f-9948-4517-a4cc-b4aaadebde68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae515dcf7f6eae8af1a6356c58f38e69cb039441
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136138"
---
# <a name="compiler-error-c3120"></a>Erreur du compilateur C3120

'nom_méthode' : les méthodes d’interface ne peut pas prendre une liste d’arguments variable

Une méthode d’interface ne peut pas prendre une liste d’arguments variable. Par exemple, la définition d’interface suivante génère C3120 :

```
// C3120.cpp
__interface A {
int X(int i, ...);    // C3120
};

int main(void) { return(0); }
```