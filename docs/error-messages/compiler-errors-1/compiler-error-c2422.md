---
title: Erreur du compilateur C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 524eeadb6cf066d3eba3a7e88c45a9e2b993c0ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509133"
---
# <a name="compiler-error-c2422"></a>Erreur du compilateur C2422

substitution de segment non conforme dans 'opérande'

Le code assembleur inline utilise incorrectement un opérateur de substitution de segment (deux-points) sur un opérande.  Plusieurs causes sont possibles :

- Le Registre précédant l’opérateur n’est pas un Registre de segment.

- Le Registre précédant l’opérateur n’est pas le seul Registre de segment de l’opérande.

- L’opérateur de substitution de segment apparaît au sein d’un opérateur d’indirection (crochets).

- L’expression qui suit l’opérateur de substitution de segment n’est pas un opérande immédiat ou un opérande de mémoire.

L’exemple suivant génère l’erreur C2422 :

```
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```