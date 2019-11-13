---
title: Avertissement du compilateur (niveau 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: ebebfe9994be3dd136e3924cb2aea60c0c901926
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051633"
---
# <a name="compiler-warning-level-3-c4334"></a>Avertissement du compilateur (niveau 3) C4334

'opérateur' : résultat de l’utilisation d’un décalage de 32 bits converti implicitement en bits 64 (passage de 64 bits intentionnel)

Le résultat de l’équipe 32 bits a été converti implicitement en 64 bits, et le compilateur soupçonne qu’un décalage de 64 bits était prévu.  Pour résoudre cet avertissement, utilisez le décalage 64 bits ou effectuez un cast explicite du résultat du décalage vers 64 bits.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4334.

```cpp
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```