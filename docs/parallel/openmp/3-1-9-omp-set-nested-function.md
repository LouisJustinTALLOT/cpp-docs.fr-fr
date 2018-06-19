---
title: 3.1.9 fonction omp_set_nested | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df08d6eb1a93ff5852c239757d5f917e9777919b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687281"
---
# <a name="319-ompsetnested-function"></a>3.1.9 Fonction omp_set_nested
Le **omp_set_nested** fonction active ou désactive le parallélisme imbriqué. Le format est le suivant :  
  
```  
#include <omp.h>  
void omp_set_nested(int nested);  
```  
  
 Si *imbriquée* prend la valeur 0, imbriqués parallélisme est désactivé, ce qui est la valeur par défaut, et les régions parallèles imbriquées sont sérialisées et exécutées par le thread actuel. Si *imbriquée* prend une valeur différente de zéro, parallélisme imbriquée est activée, et les régions parallèles imbriquées peuvent déployer des threads supplémentaires pour les équipes imbriquée.  
  
 Cette fonction a les effets décrits ci-dessus, lorsqu’elle est appelée à partir d’une partie du programme où la **omp_in_parallel** fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la **omp_in_parallel** fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.  
  
 Cet appel est prioritaire sur la **OMP_NESTED** variable d’environnement.  
  
 Lorsque le parallélisme imbriqué est activé, le nombre de threads utilisés pour exécuter les régions parallèles imbriquées est défini par l’implémentation. Par conséquent, les implémentations conformes OpenMP sont autorisées à sérialiser les régions parallèles imbriquées, même lorsque le parallélisme imbriquée est activée.  
  
## <a name="cross-references"></a>Références externes :  
  
-   **OMP_NESTED** voir variable d’environnement [Section 4.4](../../parallel/openmp/4-4-omp-nested.md) page 49.  
  
-   **omp_in_parallel** , consultez [Section 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) sur la page de 38.