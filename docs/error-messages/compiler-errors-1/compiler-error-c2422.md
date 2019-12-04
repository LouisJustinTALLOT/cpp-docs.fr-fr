---
title: Erreur du compilateur C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 39f779ee846cf4f328f9c7af59ae394d97d7a3ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744730"
---
# <a name="compiler-error-c2422"></a>Erreur du compilateur C2422

substitution de segment non conforme dans’Operand'

Le code assembleur inline utilise incorrectement un opérateur de substitution de segment (deux-points) sur un opérande.  Les causes possibles sont les suivantes :

- Le Registre qui précède l’opérateur n’est pas un registre de segment.

- Le Registre qui précède l’opérateur n’est pas le seul registre de segment dans l’opérande.

- L’opérateur de substitution de segment apparaît dans un opérateur d’indirection (crochets).

- L’expression qui suit l’opérateur de substitution de segment n’est pas un opérande immédiat ou un opérande de mémoire.

L’exemple suivant génère l’C2422 :

```cpp
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```
