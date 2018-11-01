---
title: Erreur du compilateur C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: 66a111ea6fe2ca5acfbc473d19da62d9de67372a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666607"
---
# <a name="compiler-error-c2791"></a>Erreur du compilateur C2791

utilisation non conforme de 'super' : 'classe' n’a pas de classes de base

Le mot clé [super](../../cpp/super.md) a été utilisé dans le contexte d’une fonction membre d’une classe qui n’a pas de classes de base.

L’exemple suivant génère l’erreur C2791 :

```
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```