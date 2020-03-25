---
title: Avertissement du compilateur (niveau 1) C4097
ms.date: 11/04/2016
f1_keywords:
- C4097
helpviewer_keywords:
- C4097
ms.assetid: 2525be51-fac2-43b2-b57c-3bbf1a2268f7
ms.openlocfilehash: ac5030715bd65c17902f4ad3cd0006d9f0477094
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163882"
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
