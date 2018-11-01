---
title: Erreur du compilateur C3120
ms.date: 11/04/2016
f1_keywords:
- C3120
helpviewer_keywords:
- C3120
ms.assetid: 9b6b210f-9948-4517-a4cc-b4aaadebde68
ms.openlocfilehash: 99d6280420111fde1a2e2187e3cbaeb529652d01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602668"
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