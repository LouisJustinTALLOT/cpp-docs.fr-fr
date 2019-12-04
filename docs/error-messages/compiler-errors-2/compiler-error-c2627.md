---
title: Erreur du compilateur C2627
ms.date: 11/04/2016
f1_keywords:
- C2627
helpviewer_keywords:
- C2627
ms.assetid: 7fc6c5ac-c7c9-4f0b-ad52-f52252526458
ms.openlocfilehash: 6b0471aaead1b56f51e4393784306aa6ed928eec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754730"
---
# <a name="compiler-error-c2627"></a>Erreur du compilateur C2627

'fonction' : fonction membre non autorisée dans une Union anonyme

Une [Union anonyme](../../cpp/unions.md#anonymous_unions) ne peut pas avoir de fonctions membres.

L’exemple suivant génère l’C2627 :

```cpp
// C2627.cpp
int main() {
   union { void f(){} };   // C2627
   union X { void f(){} };
}
```
