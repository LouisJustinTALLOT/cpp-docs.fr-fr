---
title: Erreur du compilateur C3740
ms.date: 11/04/2016
f1_keywords:
- C3740
helpviewer_keywords:
- C3740
ms.assetid: edb17a90-2307-4df6-943d-580460d26d2b
ms.openlocfilehash: 4e32c37853f4c877e6260e38daa0c8357ca54a25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752663"
---
# <a name="compiler-error-c3740"></a>Erreur du compilateur C3740

les modèles ne peuvent pas recevoir d’événements source ou Receive

Une classe ou un struct basé sur un modèle ne peut pas contenir d' [événements](../../cpp/event-handling.md).

L’exemple suivant génère l’C3740 :

```cpp
// C3740.cpp
template <typename T>   // Delete the template specification
struct E {
   __event void f();   // C3740
};

int main() {
}
```
