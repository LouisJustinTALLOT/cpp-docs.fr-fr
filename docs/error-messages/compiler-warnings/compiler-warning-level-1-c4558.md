---
title: Compilateur avertissement (niveau 1) C4558 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4558
dev_langs:
- C++
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 404f4a343b35081a64267424c436063c085958e7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056649"
---
# <a name="compiler-warning-level-1-c4558"></a>Avertissement du compilateur (niveau 1) C4558

valeur de l’opérande 'value' est hors limites 'inférieures - supérieures'

La valeur passée à une instruction de langage assembleur est hors de la plage spécifiée pour le paramètre. La valeur sera tronquée.

L’exemple suivant génère l’erreur C4558 :

```
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```