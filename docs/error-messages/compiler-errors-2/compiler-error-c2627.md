---
title: Erreur du compilateur C2627
ms.date: 11/04/2016
f1_keywords:
- C2627
helpviewer_keywords:
- C2627
ms.assetid: 7fc6c5ac-c7c9-4f0b-ad52-f52252526458
ms.openlocfilehash: dc976a0c16d19d1fd2340676e43eb71903163aa5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659055"
---
# <a name="compiler-error-c2627"></a>Erreur du compilateur C2627

'fonction' : fonction membre non autorisée dans une union anonyme

Un [union anonyme](../../cpp/unions.md#anonymous_unions) ne peut pas avoir de fonctions membres.

L’exemple suivant génère l’erreur C2627 :

```
// C2627.cpp
int main() {
   union { void f(){} };   // C2627
   union X { void f(){} };
}
```