---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4343'
title: Avertissement du compilateur (niveau 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: 906dee40eb0e9ef55c67657e93f42a6e2279a9d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294494"
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
