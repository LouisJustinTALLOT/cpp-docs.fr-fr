---
title: Erreur du compilateur C2104
ms.date: 11/04/2016
f1_keywords:
- C2104
helpviewer_keywords:
- C2104
ms.assetid: 2ea78896-72a6-4901-a1fa-f33ea88ad61b
ms.openlocfilehash: 2945f35379f29f2a163e654aae1f682a0914e40e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752221"
---
# <a name="compiler-error-c2104"></a>Erreur du compilateur C2104

' & 'sur un champ de bits ignoré

Vous ne pouvez pas prendre l’adresse d’un champ de bits.

L’exemple suivant génère l’C2104 :

```cpp
// C2104.cpp
struct X {
   int sb : 1;
};

int main() {
   X x;
   &x.sb;   // C2104
   x.sb;   // OK
}
```
