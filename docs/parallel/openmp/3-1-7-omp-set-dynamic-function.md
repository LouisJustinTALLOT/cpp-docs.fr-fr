---
title: 3.1.7 fonction omp_set_dynamic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d1e22a1eb9aff32bfaf07350daf1cb397e18eb3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687866"
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 Fonction omp_set_dynamic
Le **omp_set_dynamic** fonction active ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution des régions parallèles. Le format est le suivant :  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 Si *dynamic_threads* prend une valeur différente de zéro, le nombre de threads utilisés pour exécuter les régions parallèles suivantes peut être ajusté automatiquement par l’environnement d’exécution pour optimiser l’utilisation de ressources système. Par conséquent, le nombre de threads spécifié par l’utilisateur est le nombre maximal de threads. Le nombre de threads dans l’équipe de l’exécution d’une région parallèle reste fixe pour la durée de cette région parallèle et est signalé par le **omp_get_num_threads** (fonction).  
  
 Si *dynamic_threads* prend la valeur 0, l’ajustement dynamique est désactivée.  
  
 Cette fonction a les effets décrits ci-dessus, lorsqu’elle est appelée à partir d’une partie du programme où la **omp_in_parallel** fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la **omp_in_parallel** fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.  
  
 Un appel à **omp_set_dynamic** est prioritaire sur la **OMP_DYNAMIC** variable d’environnement.  
  
 La valeur par défaut pour l’ajustement dynamique de threads est défini par l’implémentation. Par conséquent, les codes utilisateur qui dépendent d’un certain nombre de threads d’exécution correcte doivent désactiver explicitement les threads dynamiques. Les implémentations ne sont pas requises pour fournir la possibilité d’ajuster dynamiquement le nombre de threads, mais ils sont requis pour fournir l’interface pour prendre en charge la portabilité sur toutes les plateformes.  
  
## <a name="cross-references"></a>Références externes :  
  
-   **omp_get_num_threads** , consultez [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) à la page 37.  
  
-   **OMP_DYNAMIC** voir variable d’environnement [Section 4.3](../../parallel/openmp/4-3-omp-dynamic.md) page 49.  
  
-   **omp_in_parallel** , consultez [Section 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) sur la page de 38.