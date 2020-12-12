---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4401'
title: Avertissement du compilateur (niveau 1) C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: c6314b64ef9a675f8838cc7c3f4c89c2d6063231
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212738"
---
# <a name="compiler-warning-level-1-c4401"></a>Avertissement du compilateur (niveau 1) C4401

'champ de bits' : le membre est un champ de bits

Le code assembleur inline tente d’accéder à un membre de champ de bits. L’assembly inline ne peut pas accéder aux membres de champ de bits, donc la dernière limite de compactage avant le membre de champ de bits est utilisée.

Pour éviter cet avertissement, effectuez un cast du champ de bits en un type approprié avant de faire de la référence dans le code assembleur inline. L’exemple suivant génère l’C4401 :

```cpp
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
