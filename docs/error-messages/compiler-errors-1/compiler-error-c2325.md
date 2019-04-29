---
title: Erreur du compilateur C2325
ms.date: 11/04/2016
f1_keywords:
- C2325
helpviewer_keywords:
- C2325
ms.assetid: e6b0a186-3f2a-4adf-beae-fadd75492bf7
ms.openlocfilehash: 28b291bd68971d7759589a75d8bafbf6e873dd39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300953"
---
# <a name="compiler-error-c2325"></a>Erreur du compilateur C2325

'type' : type inattendu à droite de 'name'

Un appel est effectué à un destructeur de type incorrect.

L’exemple suivant génère l’erreur C2325 :

```
// C2325.cpp
// compile with: /c
class A {};
typedef A* pA_t;
void f() {
    A** ppa = new A *;
    ppa->~A*;   // C2325

   pA_t *ppa2 = new pA_t;
   ppa2->~pA_t();   // OK
}
```