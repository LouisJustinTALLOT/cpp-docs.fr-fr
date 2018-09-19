---
title: Erreur du compilateur C2048 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2048
dev_langs:
- C++
helpviewer_keywords:
- C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dca0cf7e95f2a876760415d5c628287fab47227c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055830"
---
# <a name="compiler-error-c2048"></a>Erreur du compilateur C2048

plusieurs 'default'

Une instruction `switch` contient plusieurs étiquettes `default` . Supprimez l’une des étiquettes `default` pour résoudre l’erreur.

L’exemple suivant génère l’erreur C2048 :

```
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

```
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