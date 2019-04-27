---
title: Erreur du compilateur C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: f82b315a3e7ae4bb1f6d281e1d80ddc2c7fb0dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208426"
---
# <a name="compiler-error-c2619"></a>Erreur du compilateur C2619

'identificateur' : un membre de données statique n'est pas autorisé dans un struct ou union anonyme

Un membre d'un struct ou d'une union anonyme est déclaré `static`.

L'exemple suivant génère l'erreur C2619 et montre comment résoudre le problème en supprimant le mot clé static.

```
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```