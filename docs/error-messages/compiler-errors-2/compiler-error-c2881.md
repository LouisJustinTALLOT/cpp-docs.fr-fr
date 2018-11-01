---
title: Erreur du compilateur C2881
ms.date: 11/04/2016
f1_keywords:
- C2881
helpviewer_keywords:
- C2881
ms.assetid: b49c63c2-b064-4d4b-a75e-ddd2af947522
ms.openlocfilehash: 82a4fbe94bc7250244d57f549e52037d6a54c784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610520"
---
# <a name="compiler-error-c2881"></a>Erreur du compilateur C2881

'espace de noms1' : est déjà utilisé comme alias pour 'espace de noms2'

Vous ne pouvez pas utiliser le même nom en tant qu’alias pour deux espaces de noms.

L’exemple suivant génère C2881 :

```
// C2881.cpp
// compile with: /c
namespace A {
   int k;
}

namespace B {
   int i;
}

namespace C = A;
namespace C = B;   // C2881 C is already an alias for A
```