---
title: Erreur du compilateur C2050
ms.date: 11/04/2016
f1_keywords:
- C2050
helpviewer_keywords:
- C2050
ms.assetid: 66aaed7d-00db-4ce1-a9d6-4447c1cf07ce
ms.openlocfilehash: e2eb6f323b5ae377c42bee4ad6ff8d83a1d3c16b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221300"
---
# <a name="compiler-error-c2050"></a>Erreur du compilateur C2050

expression de switch non intégrale

L' **`switch`** expression correspond à une valeur non entière. Pour résoudre l’erreur, utilisez uniquement des valeurs intégrales dans les instructions Switch.

L’exemple suivant génère l’C2050 :

```cpp
// C2050.cpp
int main() {
   int a = 1;
   switch ("a") {   // C2050
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```

Solution possible :

```cpp
// C2050b.cpp
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
