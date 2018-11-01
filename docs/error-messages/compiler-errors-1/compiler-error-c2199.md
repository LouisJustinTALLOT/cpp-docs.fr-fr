---
title: Erreur du compilateur C2199
ms.date: 11/04/2016
f1_keywords:
- C2199
helpviewer_keywords:
- C2199
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
ms.openlocfilehash: e5892a537cbf337b23ff2356583cec4bf5925677
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530970"
---
# <a name="compiler-error-c2199"></a>Erreur du compilateur C2199

Erreur de syntaxe : trouvé ' identificateur (' avec une portée globale (lieu d’une déclaration ?)

Le contexte spécifié a provoqué une erreur de syntaxe. Syntaxe de déclaration incorrect est peut-être.

L’exemple suivant génère l’erreur C2199 :

```
// C2199.cpp
// compile with: /c
int j = int(1) int(1);   // C2199
int j = 1;   // OK
```