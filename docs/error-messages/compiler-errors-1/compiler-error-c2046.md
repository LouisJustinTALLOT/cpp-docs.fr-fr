---
title: Erreur du compilateur C2046
ms.date: 11/04/2016
f1_keywords:
- C2046
helpviewer_keywords:
- C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
ms.openlocfilehash: e83860e9f69bab864ad2cf02503d9af802e86d29
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740362"
---
# <a name="compiler-error-c2046"></a>Erreur du compilateur C2046

instruction case non conforme

Le mot clé `case` ne peut être spécifié que dans une instruction `switch` .

L’exemple suivant génère l’erreur C2046 :

```cpp
// C2046.cpp
int main() {
   case 0:   // C2046
}
```

Solution possible :

```cpp
// C2046b.cpp
int main() {
   int i = 0;

   switch(i) {
      case 0:
      break;

      default:
      break;
   }
}
```
