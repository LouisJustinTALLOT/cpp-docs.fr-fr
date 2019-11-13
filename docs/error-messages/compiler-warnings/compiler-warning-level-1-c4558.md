---
title: Avertissement du compilateur (niveau 1) C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: d47e2a619cb84838144b3be6fd45d1f79ecc8661
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966003"
---
# <a name="compiler-warning-level-1-c4558"></a>Avertissement du compilateur (niveau 1) C4558

la valeur de l’opérande’valeur’est hors limites’inférieures-supérieures'

La valeur passée à une instruction de langage d’assembly est en dehors de la plage spécifiée pour le paramètre. La valeur sera tronquée.

L’exemple suivant génère l’C4558 :

```cpp
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```