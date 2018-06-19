---
title: 4.3 OMP_DYNAMIC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f376fe639d9bca58b6e2bd55fd081b88921a7342
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686670"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC
Le **OMP_DYNAMIC** variable d’environnement Active ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution des régions parallèles, sauf si l’ajustement dynamique est explicitement activée ou désactivée en appelant le **omp_set_dynamic** routine de bibliothèque. Sa valeur doit être **TRUE** ou **FALSE**.  
  
 Si la valeur **TRUE**, le nombre de threads utilisés pour exécuter les régions parallèles peut-être être modifié par l’environnement d’exécution pour optimiser l’utilisation de ressources système.  Si la valeur **FALSE**, ajustement dynamique est désactivée. La condition par défaut est défini par l’implémentation.  
  
 Exemple :  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## <a name="cross-references"></a>Références externes :  
  
-   Pour plus d’informations sur les régions parallèles, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.  
  
-   **omp_set_dynamic** , consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.