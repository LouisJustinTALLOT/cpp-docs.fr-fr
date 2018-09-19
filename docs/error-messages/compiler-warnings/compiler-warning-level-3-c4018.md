---
title: Compilateur avertissement (niveau 3) C4018 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4018
dev_langs:
- C++
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99ca94a47925a64c91077ad5b363e953def186b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041322"
---
# <a name="compiler-warning-level-3-c4018"></a>Compilateur avertissement (niveau 3) C4018

'expression' : incompatibilité signed/unsigned

Comparaison d’un nombre signé et non signé requis au compilateur de convertir la valeur signée non signé.

Cet avertissement peut être résolu si vous transformez un des deux types lors du test de types signés et non signés.

L’exemple suivant génère l’erreur C4018 :

```
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```