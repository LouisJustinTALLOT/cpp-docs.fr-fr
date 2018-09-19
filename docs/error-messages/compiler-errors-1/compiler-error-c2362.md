---
title: Erreur du compilateur C2362 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2362
dev_langs:
- C++
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f78b850f95614255fed372570742a0f88a9e30e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035979"
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