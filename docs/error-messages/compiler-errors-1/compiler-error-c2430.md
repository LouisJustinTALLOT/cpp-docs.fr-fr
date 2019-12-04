---
title: Erreur du compilateur C2430
ms.date: 11/04/2016
f1_keywords:
- C2430
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
ms.openlocfilehash: f82eb4914ec36aa513822964f551a05fbb77aa97
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744574"
---
# <a name="compiler-error-c2430"></a>Erreur du compilateur C2430

plus d’un registre d’index dans’identifier'

Plusieurs registres sont mis à l’échelle. Le compilateur prend en charge l’indexation mise à l’échelle, mais vous pouvez uniquement mettre à l’échelle un registre.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2430.

```cpp
// C2430.cpp
// processor: x86
int main() {
   _asm mov eax, [ebx*2+ecx*4] // C2430
}
```
