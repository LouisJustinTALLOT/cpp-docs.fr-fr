---
title: Avertissement du compilateur (niveau 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: c8f0bb514a3da932500f986e50a20af0947827c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475801"
---
# <a name="compiler-warning-level-4-c4343"></a>Avertissement du compilateur (niveau 4) C4343

\#pragma optimize("g",off) remplace l’option /Og

Cet avertissement, qui s’applique uniquement aux compilateurs de processeurs Itanium (IPF), signale qu’un pragma [optimize](../../preprocessor/optimize.md) a remplacé une option [/Og](../../build/reference/og-global-optimizations.md) du compilateur.

L’exemple suivant génère l’avertissement C4343 :

```
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```