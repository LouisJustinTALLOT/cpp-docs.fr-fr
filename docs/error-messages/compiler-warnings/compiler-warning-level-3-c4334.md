---
title: Compilateur avertissement (niveau 3) C4334 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b7bb16ea38b2c2112c12c561398341a7d1adbfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044013"
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