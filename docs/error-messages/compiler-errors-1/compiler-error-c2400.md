---
title: Erreur du compilateur C2400
ms.date: 11/04/2016
f1_keywords:
- C2400
helpviewer_keywords:
- C2400
ms.assetid: 1ba441ee-73f9-42a5-bfe9-fbeab93808eb
ms.openlocfilehash: 61043f3f97d4d91b66c3902cc33ed4be526541ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744769"
---
# <a name="compiler-error-c2400"></a>Erreur du compilateur C2400

erreur de syntaxe d’assembleur inline dans’Context'; 'Token’trouvé

Le jeton a provoqué une erreur de syntaxe dans le contexte spécifié.

L’exemple suivant génère l’C2400 :

```cpp
// C2400.cpp
// processor: x86
int main() {
   __asm {
      heh ax,bx;   // C2400, heh is not a valid x86 instruction
      mov ax,bx;   // OK
   }
}
```
