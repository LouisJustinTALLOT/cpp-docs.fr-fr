---
title: Avertissement du compilateur (niveau 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 38b93c83f822bc5b856a46f0dd62ea275d2bf207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198716"
---
# <a name="compiler-warning-level-3-c4334"></a>Avertissement du compilateur (niveau 3) C4334

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
