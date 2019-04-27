---
title: Erreur du compilateur C3745
ms.date: 11/04/2016
f1_keywords:
- C3745
helpviewer_keywords:
- C3745
ms.assetid: 1e64aec5-7e53-47e5-bc7d-3905230cfc66
ms.openlocfilehash: da80a10cbf7246ad0aeaecffe20992d2050abb3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208254"
---
# <a name="compiler-error-c3745"></a>Erreur du compilateur C3745

'fonction' : seul un événement peut être 'déclenché'

Seule une fonction définie par le [__event](../../cpp/event.md) mot clé peut être passé à la [__raise](../../cpp/raise.md) mot clé.

L’exemple suivant génère l’erreur C3745 :

```
// C3745.cpp
struct E {
   __event void func();
   void func(int) {
   }

   void func2() {
   }

   void bar() {
      __raise func();
      __raise func(1);   // C3745
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func();
   __raise e.func(1);   // C3745
   __raise e.func2();   // C3745
}
```