---
title: A.15 déterminer le nombre de Threads utilisés | Documents Microsoft
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
ms.openlocfilehash: b50858a3384fa5f8d867f13a699e1fc271c101ef
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686384"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   Détermination du nombre de threads utilisés
Prenons l’exemple incorrect suivant (pour [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) à la page 37) :  
  
```  
np = omp_get_num_threads(); // misplaced   
#pragma omp parallel for schedule(static)  
    for (i=0; i<np; i++)  
        work(i);  
```  
  
 Le `omp_get_num_threads()` appeler renvoie la valeur 1 dans la section série du code, par conséquent, *np* sera toujours égal à 1 dans l’exemple précédent. Pour déterminer le nombre de threads qui seront déployées pour la région parallèle, l’appel doit être à l’intérieur de la région parallèle.  
  
 L’exemple suivant montre comment réécrire ce programme sans inclure une requête pour le nombre de threads :  
  
```  
#pragma omp parallel private(i)  
{  
    i = omp_get_thread_num();  
    work(i);  
}  
```