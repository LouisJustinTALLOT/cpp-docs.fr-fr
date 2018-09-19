---
title: Erreur du compilateur C2264 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2264
dev_langs:
- C++
helpviewer_keywords:
- C2264
ms.assetid: 158b72cc-cee9-4a08-bd79-b7a5955345a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5b6f2cdf7a0c9708a34acd3e73241e942b2194b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045872"
---
# <a name="compiler-error-c2264"></a>Erreur du compilateur C2264

'fonction' : erreur dans la définition ou déclaration ; fonction non appelée

La fonction ne peut pas être appelée en raison d’une définition ou déclaration incorrecte.

L’exemple suivant génère l’erreur C2264 :

```
// C2264.cpp
struct C {
   // Delete the following line to resolve.
   operator int(int = 0){}   // incorrect declaration
};

struct D {
   operator int(){return 0;}   // OK
};

int main() {
   int i;

   C c;
   i = c;   // C2264

   D d;
   i = d;   // OK
}
```