---
title: Avertissement du compilateur (niveau 1) C4080
ms.date: 11/04/2016
f1_keywords:
- C4080
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
ms.openlocfilehash: a91963d524300c8768768a8a4615b1ab27e033e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599795"
---
# <a name="compiler-warning-level-1-c4080"></a>Avertissement du compilateur (niveau 1) C4080

identificateur attendu pour le nom du segment ; 'symbol' trouvé

Le nom du segment dans [#pragma alloc_text](../../preprocessor/alloc-text.md) doit être une chaîne ou un identificateur. Le compilateur ignore le pragma si un identificateur valide est introuvable.

L’exemple suivant génère l’avertissement C4080 :

```
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```