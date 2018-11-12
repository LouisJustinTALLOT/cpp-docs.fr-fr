---
title: Erreur du compilateur C2047
ms.date: 11/04/2016
f1_keywords:
- C2047
helpviewer_keywords:
- C2047
ms.assetid: 686a5a81-3857-4753-84a0-5c2e7149cbee
ms.openlocfilehash: 50a8ce4ab9d88312b7f91ebb9df068a07fa21aa6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440558"
---
# <a name="compiler-error-c2047"></a>Erreur du compilateur C2047

instruction default non conforme

Le mot clé `default` ne peut être spécifié que dans une instruction `switch` .

L’exemple suivant génère l’erreur C2047 :

```
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

```
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