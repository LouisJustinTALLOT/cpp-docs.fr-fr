---
title: A.15 détermination du nombre de Threads utilisés | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1042b4871f53bddb5cff894330f3afe7d8a088ef
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428737"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   Détermination du nombre de threads utilisés

Prenons l’exemple suivant incorrecte (pour [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) sur page 37) :

```
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

Le `omp_get_num_threads()` appeler retourne 1 dans la section de série du code, par conséquent, *np* sera toujours égal à 1 dans l’exemple précédent. Pour déterminer le nombre de threads qui seront déployées pour la région parallèle, l’appel doit être à l’intérieur de la région parallèle.

L’exemple suivant montre comment réécrire ce programme sans inclure une requête pour le nombre de threads :

```
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```