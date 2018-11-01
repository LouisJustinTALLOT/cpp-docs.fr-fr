---
title: Avertissement du compilateur (niveau 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 55512bf28c8c20512d0d245810d3e5c1fec36939
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600692"
---
# <a name="compiler-warning-level-3-c4334"></a>Avertissement du compilateur (niveau 3) C4334

'opérateur' : résultat du décalage 32 bits converti implicitement en 64 bits (était décalage 64 bits destiné ?)

Le résultat du décalage 32 bits a été implicitement converti en 64 bits et le compilateur soupçonne qu’un décalage 64 bits a été conçu.  Pour résoudre cet avertissement, utilisez le décalage 64 bits, ou explicitement convertir le résultat de la touche MAJ enfoncée en 64 bits.

## <a name="example"></a>Exemple

L’exemple suivant génère C4334.

```
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```