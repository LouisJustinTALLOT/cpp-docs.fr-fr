---
title: Compilateur avertissement (niveau 1) C4401 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4401
dev_langs:
- C++
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f9f7bfcf826b9bda4232a8f4068d8be45dc3ab5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043545"
---
# <a name="compiler-warning-level-1-c4401"></a>Avertissement du compilateur (niveau 1) C4401

« champ de bits » : membre est un champ de bits

Le code assembleur inline tente d’accéder à un membre champ de bits. L’assembleur inline ne peut pas accéder membres de champ de bits, donc la dernière limite de compression avant le membre champ de bits est utilisée.

Pour éviter cet avertissement, vous devez effectuer un cast du champ de bits avec un type approprié avant d’effectuer la référence dans le code assembleur inline. L’exemple suivant génère l’erreur C4401 :

```
// C4401.cpp
// compile with: /W1
// processor: x86
typedef struct bitfield {
   signed bit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bf.bit = 0;
   __asm {
      mov bf.bit,0;   // C4401
   }

   /* use the following __asm block to resolve the warning
   int i = (int)bf.bit;
   __asm {
      mov i,0;
   }
   */
}
```