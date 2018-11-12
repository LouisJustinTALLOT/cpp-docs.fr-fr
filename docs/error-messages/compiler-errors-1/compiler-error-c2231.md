---
title: Erreur du compilateur C2231
ms.date: 11/04/2016
f1_keywords:
- C2231
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
ms.openlocfilehash: 0d6519bd12cdb5ee5a86fa4a6915b51b0dc59fc5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592801"
---
# <a name="compiler-error-c2231"></a>Erreur du compilateur C2231

'.' : opérande gauche pointe vers 'class-key', utilisez '->'

L’opérande à gauche de l’opération de sélection de membres (.) est un pointeur au lieu d’une classe, une structure ou une union.

L’exemple suivant génère l’erreur C2231 :

```
// C2231.c
struct S {
   int member;
} s, *ps = &s;
int main() {
   ps.member = 0;   // C2231

   // OK
   ps->member = 0;   // crash
   s.member = 0;
}
```