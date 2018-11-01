---
title: Avertissement du compilateur (niveau 3) C4723
ms.date: 11/04/2016
f1_keywords:
- C4723
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
ms.openlocfilehash: b970c9ee02339fa3b48135d321638db7e64baf82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505883"
---
# <a name="compiler-warning-level-3-c4723"></a>Avertissement du compilateur (niveau 3) C4723

division potentielle par 0

Le second opérande dans une opération de division évalué à zéro au moment de la compilation, ce qui donne des résultats indéfinis.

Cet avertissement est émis uniquement lorsque vous utilisez [/Og](../../build/reference/og-global-optimizations.md) ou une option d’optimisation qui implique /Og.

Le compilateur peut avoir générée à l’opérande de zéro.