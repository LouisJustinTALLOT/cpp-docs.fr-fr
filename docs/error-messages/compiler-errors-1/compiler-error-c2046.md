---
description: 'En savoir plus sur : erreur du compilateur C2046'
title: Erreur du compilateur C2046
ms.date: 11/04/2016
f1_keywords:
- C2046
helpviewer_keywords:
- C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
ms.openlocfilehash: 7d1735c4f27c80f2830b7f36a9f3533033119535
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175155"
---
# <a name="compiler-error-c2046"></a>Erreur du compilateur C2046

instruction case non conforme

Le mot clé `case` ne peut apparaître que dans une **`switch`** instruction.

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
