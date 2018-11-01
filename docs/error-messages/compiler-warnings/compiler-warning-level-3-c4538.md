---
title: Avertissement du compilateur (niveau 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: 81634ed45ad7d09a35f8399774920f6445628dee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569362"
---
# <a name="compiler-warning-level-3-c4538"></a>Avertissement du compilateur (niveau 3) C4538

'type' : les qualificateurs const/volatile pour ce type ne sont pas pris en charge.

Un mot clé d’un qualificateur de nom a été correctement appliqué à un tableau. Pour plus d'informations, consultez [tableau](../../windows/arrays-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C4538 :

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```