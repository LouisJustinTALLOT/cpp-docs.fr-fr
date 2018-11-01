---
title: Compilateur avertissement (niveau 2) C4056
ms.date: 11/04/2016
f1_keywords:
- C4056
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
ms.openlocfilehash: 59c66f2f7dcbd1e20463df613b1b7deae6a1c349
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586899"
---
# <a name="compiler-warning-level-2-c4056"></a>Compilateur avertissement (niveau 2) C4056

débordement arithmétique à virgule flottante constante

Opération arithmétique de constante à virgule flottante génère un résultat qui dépasse la valeur maximale autorisée.

Cet avertissement peut être provoqué par des optimisations du compilateur effectuées au cours de l’opération arithmétique de constante. Vous pouvez ignorer cet avertissement s’il disparaît lorsque vous désactivez l’optimisation ([/Od](../../build/reference/od-disable-debug.md)).

L’exemple suivant génère l’erreur C4056 :

```
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```