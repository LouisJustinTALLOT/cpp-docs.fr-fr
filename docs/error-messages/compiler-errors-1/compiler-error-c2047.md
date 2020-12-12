---
description: 'En savoir plus sur : erreur du compilateur C2047'
title: Erreur du compilateur C2047
ms.date: 11/04/2016
f1_keywords:
- C2047
helpviewer_keywords:
- C2047
ms.assetid: 686a5a81-3857-4753-84a0-5c2e7149cbee
ms.openlocfilehash: 40df340017b134a3d2abe092478658f92142298d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175116"
---
# <a name="compiler-error-c2047"></a>Erreur du compilateur C2047

instruction default non conforme

Le mot clé **`default`** ne peut apparaître que dans une **`switch`** instruction.

L’exemple suivant génère l’erreur C2047 :

```cpp
// C2047.cpp
int main() {
   int i = 0;
   default:   // C2047
   switch(i) {
      case 0:
      break;
   }
}
```

Solution possible :

```cpp
// C2047b.cpp
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
