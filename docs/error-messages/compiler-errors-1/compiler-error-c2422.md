---
title: Erreur du compilateur C2422 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17421f2d4a7823c0e2fbb34a54a7c562223c798c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047029"
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