---
title: Erreur du compilateur C2706
ms.date: 11/04/2016
f1_keywords:
- C2706
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
ms.openlocfilehash: bca86d3c0cf886c64a1d668468c793d0e77b2867
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757460"
---
# <a name="compiler-error-c2706"></a>Erreur du compilateur C2706

__except non conforme sans _try de \_correspondant ('} 'manquant dans \_bloc de _try ?)

Le compilateur n’a pas trouvé d’accolade fermante pour un bloc `__try`.

L’exemple suivant génère l’C2706 :

```cpp
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```
