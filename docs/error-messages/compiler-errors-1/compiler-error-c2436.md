---
title: Erreur du compilateur C2436
ms.date: 11/04/2016
f1_keywords:
- C2436
helpviewer_keywords:
- C2436
ms.assetid: ca4cc813-bc1d-4c0a-9a2c-3a5fe673d084
ms.openlocfilehash: 335d4a304e16814243894c9524a9e4a2a7356110
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627355"
---
# <a name="compiler-error-c2436"></a>Erreur du compilateur C2436

'identificateur' : fonction membre ou classe imbriquée dans une liste d’initialiseurs de constructeur

Fonctions membres ou les classes locales dans la liste d’initialiseurs de constructeur ne peut pas être initialisés.

L’exemple suivant génère l’erreur C2436 :

```
// C2436.cpp
struct S{
   int f();
   struct Inner{
      int i;
   };
   S():f(10), Inner(0){}   // C2436
};
```