---
title: A.1 exécution d’une boucle Simple en parallèle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5446f72cc5ee0577385527be24bc912297aec0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418942"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   Exécution d'une boucle simple en parallèle

L’exemple suivant montre comment paralléliser une boucle simple à l’aide de la `parallel for` directive ([Section 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) page 16). La variable d’itération de boucle est privée par défaut, il est donc pas nécessaire de spécifier explicitement dans une clause privée.

```
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```