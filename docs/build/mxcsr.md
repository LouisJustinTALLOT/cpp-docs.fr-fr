---
title: MxCsr
ms.date: 11/04/2016
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
ms.openlocfilehash: d411223634aec6d11413ac1f5b1fb04dba7498e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497370"
---
# <a name="mxcsr"></a>MxCsr

L’état du Registre inclut également MxCsr. La convention d’appel divise ce Registre en une partie volatile et une partie non volatile. La partie volatile se compose des indicateurs de 6 état, MXCSR [0:5], tandis que le reste du Registre, MXCSR [6:15], est considéré comme non volatile.

La partie non volatile est définie sur les valeurs standards suivantes au début de l’exécution du programme :

```
MXCSR[6]         : Denormals are zeros - 0
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)
```

Un appelant qui modifie l’un des champs non volatiles dans MXCSR doit restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doit les restaurer à leurs valeurs standards avant d’appeler un appelant, sauf si le contrat de l’appelé attend les valeurs modifiées.

Il existe deux exceptions aux règles relatives à la rémanence des indicateurs de contrôle :

- Dans les fonctions dont l’objectif de la fonction donnée documenté consiste à modifier le Registre MxCsr non volatil indicateurs.

- Lorsqu’il est prouvé corriger que les résultats de la violation de ces règles dans un programme qui se comporte/signifie que le même comme un programme où ces règles ne sont pas violées, par exemple, via l’analyse de la totalité du programme.

Aucune hypothèse ne peut être effectuée concernant l’état de la partie volatile de MXCSR au-delà d’une limite de fonction, sauf spécification contraire dans la documentation d’une fonction.

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)