---
title: Erreur du compilateur C3748
ms.date: 11/04/2016
f1_keywords:
- C3748
helpviewer_keywords:
- C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
ms.openlocfilehash: ef1c446f9feb3d40add62513a31fc81a382b98e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226841"
---
# <a name="compiler-error-c3748"></a>Erreur du compilateur C3748

'interface' : les interfaces gérées ne peuvent pas déclencher les événements

Le [__event](../../cpp/event.md) mot clé ne peut pas apparaître à l’intérieur d’une interface.

L’exemple suivant génère l’erreur C3748 :

```
// C3748.cpp
__interface I {
// try the following line instead
// struct I {
   __event void f();   // C3748
};

int main() {
}
```