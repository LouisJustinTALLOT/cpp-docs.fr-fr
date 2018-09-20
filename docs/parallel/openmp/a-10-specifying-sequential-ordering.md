---
title: A.10 spécification de l’ordre séquentiel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5c65a9b1-0fc5-4cad-a5a9-9ce10b25d25c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29f2089760e9aef6f9e992c5725eab12b7be3b20
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432228"
---
# <a name="a10---specifying-sequential-ordering"></a>A.10   Spécification de l'ordre séquentiel

Classés sections ([Section 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) à la page 22) sont utiles pour le classement de manière séquentielle la sortie de travail est effectué en parallèle. Le programme suivant imprime les index dans un ordre séquentiel :

```
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```