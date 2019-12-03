---
title: Avertissement du compilateur (niveau 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: acc14d9679aed932b65041bf3eb109a8d0964c89
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683275"
---
# <a name="compiler-warning-level-4-c4343"></a>Avertissement du compilateur (niveau 4) C4343

\#pragma optimize (« g », OFF) remplace l’option/og

Cet avertissement, qui s’applique uniquement aux compilateurs de processeurs Itanium (IPF), signale qu’un pragma [optimize](../../preprocessor/optimize.md) a remplacé une option [/Og](../../build/reference/og-global-optimizations.md) du compilateur.

L’exemple suivant génère l’avertissement C4343 :

```cpp
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```