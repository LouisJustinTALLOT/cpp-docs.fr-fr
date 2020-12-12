---
description: 'En savoir plus sur : erreur du compilateur C2422'
title: Erreur du compilateur C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 4fb35b7613e523c750d6c3f15a8071117edba46a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120241"
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
