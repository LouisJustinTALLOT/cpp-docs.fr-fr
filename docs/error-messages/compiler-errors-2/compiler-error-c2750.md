---
title: Erreur du compilateur C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 34d19e8e9f51c90c48ec0d429f98bb82e3d829d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228536"
---
# <a name="compiler-error-c2750"></a>Erreur du compilateur C2750

'type' : Impossible d’utiliser 'new' sur le type de référence ; Utilisez 'gcnew' à la place

Pour créer une instance d’un type CLR, ce qui provoque l’instance peut être placée sur le tas de garbage collection, vous devez utiliser [gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C2750 :

```
// C2750.cpp
// compile with: /clr
ref struct Y1 {};

int main() {
   Y1 ^ x = new Y1;   // C2750

   // try the following line instead
   Y1 ^ x2 = gcnew Y1;
}
```