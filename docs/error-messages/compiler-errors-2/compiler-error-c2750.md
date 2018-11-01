---
title: Erreur du compilateur C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 943220fae035da8d6fc861d2abae435051381e1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453740"
---
# <a name="compiler-error-c2750"></a>Erreur du compilateur C2750

'type' : Impossible d’utiliser 'new' sur le type de référence ; Utilisez 'gcnew' à la place

Pour créer une instance d’un type CLR, ce qui provoque l’instance peut être placée sur le tas de garbage collection, vous devez utiliser [gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md).

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