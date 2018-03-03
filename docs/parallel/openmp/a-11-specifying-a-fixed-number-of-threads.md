---
title: "A.11 spécifiant un nombre fixe de Threads | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72c8aca2b90f021771ba9f9fc8a86d784ffe24a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11   Détermination du nombre fixe de threads
Certains programmes reposent sur un nombre fixe, spécifiée à l’avance de threads pour exécuter correctement.  Car le paramètre par défaut pour l’ajustement dynamique du nombre de threads est défini par l’implémentation, ces programmes peuvent choisir de désactiver la fonctionnalité de threads dynamiques et de définir le nombre de threads explicitement pour garantir la portabilité. L’exemple suivant montre comment effectuer cette opération à l’aide de `omp_set_dynamic` ([Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39), et `omp_set_num_threads` ([Section 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) sur la page 36) :  
  
```  
omp_set_dynamic(0);  
omp_set_num_threads(16);  
#pragma omp parallel shared(x, npoints) private(iam, ipoints)  
{  
    if (omp_get_num_threads() != 16)   
      abort();  
    iam = omp_get_thread_num();  
    ipoints = npoints/16;  
    do_by_16(x, iam, ipoints);  
}  
```  
  
 Dans cet exemple, le programme s’exécute correctement uniquement s’il est exécuté par les threads de 16. Si l’implémentation n’est pas capable de prendre en charge 16 threads, le comportement de cet exemple est défini par l’implémentation.  
  
 Notez que le nombre de threads de l’exécution d’une région parallèle reste constant pendant une région parallèle, quel que soit les paramètre de threads dynamiques. Le mécanisme de threads dynamiques détermine le nombre de threads à utiliser au début de la région parallèle et maintient constant pour la durée de la région.