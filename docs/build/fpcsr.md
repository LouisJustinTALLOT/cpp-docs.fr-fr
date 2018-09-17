---
title: MxFpCsrCsr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6ed0500d0382563878d0751ba5386e4cc637fdb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718287"
---
# <a name="fpcsr"></a>FpCsr

L’état du Registre inclut également le x87 mot de contrôle FPU. La convention d’appel définit ce Registre comme non volatil.

Le x87 Registre du mot de contrôle FPU est défini sur les valeurs standards suivantes au début de l’exécution du programme :

```
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)
FPCSR[7]: Reserved - 0
FPCSR[8:9]: Precision Control - 10B (double precision)
FPCSR[10:11]: Rounding  control - 0 (round to nearest)
FPCSR[12]: Infinity control - 0 (not used)
```

Un appelant qui modifie l’un des champs dans FPCSR doit restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doit les restaurer à leurs valeurs standards avant d’appeler un appelant, sauf si le contrat de l’appelé attend les valeurs modifiées.

Il existe deux exceptions aux règles relatives à la rémanence des indicateurs de contrôle :

1. Dans les fonctions dont l’objectif de la fonction donnée documenté consiste à modifier le MxFpCsrCsr non volatile indicateurs.

1. Lorsqu’il est prouvé corriger que les résultats de la violation de ces règles dans un programme qui se comporte/signifie que le même comme un programme où ces règles ne sont pas violées, par exemple, via l’analyse de la totalité du programme.

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)