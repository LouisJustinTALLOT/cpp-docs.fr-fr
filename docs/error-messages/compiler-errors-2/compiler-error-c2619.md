---
title: Erreur du compilateur C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: 3ca5ea4612091f1e3eee8fead2b1eaebb264b696
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754769"
---
# <a name="compiler-error-c2619"></a>Erreur du compilateur C2619

'identificateur' : un membre de données statique n'est pas autorisé dans un struct ou union anonyme

Un membre d'un struct ou d'une union anonyme est déclaré `static`.

L'exemple suivant génère l'erreur C2619 et montre comment résoudre le problème en supprimant le mot clé static.

```cpp
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```
