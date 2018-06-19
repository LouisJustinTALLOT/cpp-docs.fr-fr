---
title: Clauses OpenMP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7abe5a637a2a32c696f19f5ab9988f1be361f647
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692836"
---
# <a name="openmp-clauses"></a>Clauses OpenMP
Fournit des liens vers les clauses utilisées dans l’API OpenMP.  
  
 Visual C++ prend en charge les clauses OpenMP suivantes :  
  
|Clause|Description|  
|------------|-----------------|  
|[copyin](../../../parallel/openmp/reference/copyin.md)|Permet aux threads d’accéder à valeur du thread principal, pour un [threadprivate](../../../parallel/openmp/reference/threadprivate.md) variable.|  
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.|  
|[default](../../../parallel/openmp/reference/default-openmp.md)|Spécifie le comportement de variables non délimités dans une région parallèle.|  
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Spécifie que chaque thread doit avoir sa propre instance d’une variable, et que la variable doit être initialisée avec la valeur de la variable, car il existe avant la construction parallèle.|  
|[if](../../../parallel/openmp/reference/if-openmp.md)|Spécifie si une boucle doit être exécutée en parallèle ou en série.|  
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Spécifie que la version du contexte englobant de la variable est définie égale à la version privée du thread exécute la dernière itération (construction de la boucle for) ou la dernière section (sections #pragma).|  
|[nowait](../../../parallel/openmp/reference/nowait.md)|Remplace le cloisonnement implicite dans une directive.|  
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|Définit le nombre de threads dans une équipe de thread.|  
|[commandée](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Requis sur un parallèle [pour](../../../parallel/openmp/reference/for-openmp.md) instruction si un [classés](../../../parallel/openmp/reference/ordered-openmp-directives.md) directive est à utiliser dans la boucle.|  
|[private](../../../parallel/openmp/reference/private-openmp.md)|Spécifie que chaque thread doit avoir sa propre instance d’une variable.|  
|[reduction](../../../parallel/openmp/reference/reduction.md)|Spécifie qu’une ou plusieurs variables qui sont privés pour chaque thread font l’objet d’une opération de réduction à la fin de la région parallèle.|  
|[schedule](../../../parallel/openmp/reference/schedule.md)|S’applique à la [pour](../../../parallel/openmp/reference/for-openmp.md) la directive.|  
|[Partagé](../../../parallel/openmp/reference/shared-openmp.md)|Spécifie qu’une ou plusieurs variables doivent être partagées entre tous les threads.|  
  
## <a name="see-also"></a>Voir aussi  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)