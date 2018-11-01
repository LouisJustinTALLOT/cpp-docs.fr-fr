---
title: Erreur du compilateur C2794
ms.date: 11/04/2016
f1_keywords:
- C2794
helpviewer_keywords:
- C2794
ms.assetid: d508191c-9044-4c6a-9119-4bca668c0b93
ms.openlocfilehash: 1e9d3ee84b72dc9a4f83337f79f38c0237e0b505
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432953"
---
# <a name="compiler-error-c2794"></a>Erreur du compilateur C2794

'fonction' : n’est pas un membre de n’importe quelle classe de base directe ou indirecte de 'class'

Vous avez essayé d’utiliser [super](../../cpp/super.md) pour appeler une fonction membre qui n’existe pas.

L’exemple suivant génère C2794

```
// C2794.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::f();  // C2794
   }
};
```