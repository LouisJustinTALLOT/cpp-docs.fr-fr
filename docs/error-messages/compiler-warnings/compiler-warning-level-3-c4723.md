---
title: Compilateur avertissement (niveau 3) C4723 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4723
dev_langs:
- C++
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ca6715e26705632dc3187cb6db7deed8636cd82
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033145"
---
# <a name="compiler-warning-level-3-c4723"></a>Avertissement du compilateur (niveau 3) C4723

division potentielle par 0

Le second opérande dans une opération de division évalué à zéro au moment de la compilation, ce qui donne des résultats indéfinis.

Cet avertissement est émis uniquement lorsque vous utilisez [/Og](../../build/reference/og-global-optimizations.md) ou une option d’optimisation qui implique /Og.

Le compilateur peut avoir générée à l’opérande de zéro.