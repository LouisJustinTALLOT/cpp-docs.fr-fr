---
description: 'En savoir plus sur : erreur du compilateur C2400'
title: Erreur du compilateur C2400
ms.date: 11/04/2016
f1_keywords:
- C2400
helpviewer_keywords:
- C2400
ms.assetid: 1ba441ee-73f9-42a5-bfe9-fbeab93808eb
ms.openlocfilehash: 64582d04e232c574dd132741dd1663e4055fe05f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145364"
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
