---
description: 'En savoir plus sur : erreur du compilateur C2423'
title: Erreur du compilateur C2423
ms.date: 11/04/2016
f1_keywords:
- C2423
helpviewer_keywords:
- C2423
ms.assetid: 8797fb8b-b58b-4add-b6e6-2a9a3cd9084d
ms.openlocfilehash: 902a02d4bad34b3a386b95a72c8eca59dac19156
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120228"
---
# <a name="compiler-error-c2423"></a>Erreur du compilateur C2423

'Number' : échelle non conforme

Le code assembleur inline utilise un nombre autre que 1, 2, 4 ou 8 pour mettre à l’échelle un registre.

L’exemple suivant génère l’C2423 :

```cpp
// C2423.cpp
// processor: x86
int main() {
   _asm {
      lea EAX, [EAX*3]   // C2423
      lea EAX, [EAX+EAX*2]   // OK
   }
}
```
