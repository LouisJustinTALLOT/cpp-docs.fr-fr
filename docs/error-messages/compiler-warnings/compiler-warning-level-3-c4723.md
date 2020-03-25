---
title: Avertissement du compilateur (niveau 3) C4723
ms.date: 11/04/2016
f1_keywords:
- C4723
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
ms.openlocfilehash: 3a47c6f7e83abfc785d602d8ee0734be5d0fa962
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174087"
---
# <a name="compiler-warning-level-3-c4723"></a>Avertissement du compilateur (niveau 3) C4723

Division potentielle par 0

Le second opérande d’une opération de division est évalué à zéro au moment de la compilation, ce qui donne des résultats indéfinis.

Cet avertissement est émis uniquement lors de l’utilisation d' [/og](../../build/reference/og-global-optimizations.md) ou d’une option d’optimisation qui implique/og.

Le compilateur a peut-être généré l’opérande zéro.
