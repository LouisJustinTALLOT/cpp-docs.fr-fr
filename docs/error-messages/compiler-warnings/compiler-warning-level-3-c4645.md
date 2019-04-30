---
title: Avertissement du compilateur (niveau 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: a3e5c834a3f14b9a125176dcddd5bcc355cf1faa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401642"
---
# <a name="compiler-warning-level-3-c4645"></a>Avertissement du compilateur (niveau 3) C4645

la fonction déclarée avec __declspec(noreturn) a une instruction return

A [return](../../cpp/return-statement-in-program-termination-cpp.md) instruction a été trouvée dans une fonction qui est marquée avec le modificateur [noreturn](../../cpp/noreturn.md) `__declspec` . L’instruction `return` a été ignorée.

L’exemple suivant génère l’avertissement C4645 :

```
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```