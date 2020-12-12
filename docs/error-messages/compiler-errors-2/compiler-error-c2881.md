---
description: 'En savoir plus sur : erreur du compilateur C2881'
title: Erreur du compilateur C2881
ms.date: 11/04/2016
f1_keywords:
- C2881
helpviewer_keywords:
- C2881
ms.assetid: b49c63c2-b064-4d4b-a75e-ddd2af947522
ms.openlocfilehash: a1bc3922ce315d29f84309849660b2574631b2fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194356"
---
# <a name="compiler-error-c2881"></a>Erreur du compilateur C2881

'noms1 ' : est déjà utilisé comme alias pour’noms2 '

Vous ne pouvez pas utiliser le même nom qu’un alias pour deux espaces de noms.

L’exemple suivant génère l’C2881 :

```cpp
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
