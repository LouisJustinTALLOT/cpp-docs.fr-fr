---
title: Erreur du compilateur C2362
ms.date: 11/04/2016
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 17656b2a48a3680a9269d3ca300fd4188eda6b84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661108"
---
# <a name="compiler-error-c2362"></a>Erreur du compilateur C2362

l’initialisation de 'identificateur' est ignorée par 'étiquette goto'

Lors de la compilation avec [/Za](../../build/reference/za-ze-disable-language-extensions.md), l’accès à l’étiquette empêche l’identificateur en cours d’initialisation.

Impossible d’aller au-delà d’une déclaration avec un initialiseur, sauf si la déclaration est englobée dans un bloc qui n’est pas entré ou la variable a déjà été initialisée.

L’exemple suivant génère l’erreur C2326 :

```
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

Solution possible :

```
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```