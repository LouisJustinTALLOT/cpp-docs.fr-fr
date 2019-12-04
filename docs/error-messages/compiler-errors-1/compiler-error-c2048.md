---
title: Erreur du compilateur C2048
ms.date: 11/04/2016
f1_keywords:
- C2048
helpviewer_keywords:
- C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
ms.openlocfilehash: 039be85541a7cd3864187433e5b3299bca7d067e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740128"
---
# <a name="compiler-error-c2048"></a>Erreur du compilateur C2048

plusieurs 'default'

Une instruction `switch` contient plusieurs étiquettes `default` . Supprimez l’une des étiquettes `default` pour résoudre l’erreur.

L’exemple suivant génère l’erreur C2048 :

```cpp
// C2048.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
      default:   // C2048
         a = 3;
   }
}
```

Solution possible :

```cpp
// C2048b.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```
