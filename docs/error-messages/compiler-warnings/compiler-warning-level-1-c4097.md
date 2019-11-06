---
title: Avertissement du compilateur (niveau 1) C4097
ms.date: 11/04/2016
f1_keywords:
- C4097
helpviewer_keywords:
- C4097
ms.assetid: 2525be51-fac2-43b2-b57c-3bbf1a2268f7
ms.openlocfilehash: 1a96f7d7d70919410cb7291ed2784a41d244ff2b
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627106"
---
# <a name="compiler-warning-level-1-c4097"></a>Avertissement du compilateur (niveau 1) C4097

le paramètre pragma attendu doit être 'restore' ou 'off'

Un pragma a reçu une valeur non valide.

L’exemple suivant génère l’avertissement C4097 :

```cpp
// C4097.cpp
// compile with: /W1
#pragma runtime_checks("",test)   // C4097
// try the following line instead
// #pragma runtime_checks("",off)

int main() {
}
```