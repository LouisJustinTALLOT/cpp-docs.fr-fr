---
title: E. Comportements dans OpenMP C/C++ défini par l’implémentation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 598964ec6a12ac4c357efc04df78bfbe3af798a5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688698"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Défini par l’implémentation de comportements dans OpenMP C/C++
Cette annexe résume les comportements qui sont décrites comme « défini par l’implémentation » dans cette API.  Chaque comportement est une référence croisée à sa description dans la spécification principale.  
  
## <a name="remarks"></a>Notes  
 Une implémentation est requise pour définir et son comportement dans ces cas de document, mais cette liste peut être incomplet.  
  
-   **Nombre de threads :** si une région parallèle est rencontrée pendant que l’ajustement dynamique du nombre de threads est désactivé, et le nombre de threads demandé pour la région parallèle dépasse le nombre que le système d’exécution peut fournir, le comportement de le programme est défini par l’implémentation (voir page 9).  
  
     Dans Visual C++, pour une région parallèle non imbriqués, les 64 threads (maximum) seront fournies.  
  
-   **Nombre de processeurs :** le nombre de processeurs physiques hébergeant les threads à un moment donné est défini par l’implémentation (voir la page 10).  
  
     Dans Visual C++, ce numéro n’est pas constant et est contrôlé par le système d’exploitation.  
  
-   **Création d’équipes de threads :** le nombre de threads qui s’exécutent une région parallèle imbriquée dans une équipe est défini par l’implémentation. () consultez la page 10).  
  
     Dans Visual C++, cela est déterminé par le système d’exploitation.  
  
-   **Schedule (Runtime) :** la décision en matière de planification est différée jusqu'à l’exécution. La taille de segment et de type de planification peut être choisie au moment de l’exécution en définissant le `OMP_SCHEDULE` variable d’environnement. Si cette variable d’environnement n’est pas définie, la planification qui en résulte est défini par l’implémentation (voir page 13).  
  
     Dans Visual C++, le type de planification est `static` avec aucune taille de segment.  
  
-   **Planification par défaut :** en l’absence de la clause de la planification, la planification par défaut est défini par l’implémentation (voir page 13).  
  
     Dans Visual C++, le type de planification par défaut est `static` avec aucune taille de segment.  
  
-   **ATOMIQUE :** qu’il est défini par l’implémentation indique si une implémentation remplace toutes les `atomic` directives avec **critique** directives qui portent le même nom unique (voir page 20).  
  
     Dans Visual C++, si les données modifiées par [atomique](../../parallel/openmp/reference/atomic.md) n’est pas sur un alignement naturel ou s’il s’agit de 1 ou 2 octets long toutes les opérations atomiques qui répondent à cette propriété utilisera une section critique. Sinon, les sections critiques ne seront pas utilisées.  
  
-   **omp_get_num_threads :** si le nombre de threads n’a pas été explicitement défini par l’utilisateur, la valeur par défaut est défini par l’implémentation (voir page 9, et [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) à la page 37).  
  
     Dans Visual C++, le nombre par défaut de threads est égal au nombre de processeurs.  
  
-   **omp_set_dynamic :** la valeur par défaut pour l’ajustement de thread dynamique est défini par l’implémentation (voir [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39).  
  
     Dans Visual C++, la valeur par défaut est `FALSE`.  
  
-   **omp_set_nested :** lorsque parallélisme imbriquée est activée, le nombre de threads utilisés pour exécuter les régions parallèles imbriquées est défini par l’implémentation (voir [Section 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) page 40).  
  
     Dans Visual C++, le nombre de threads est déterminé par le système d’exploitation.  
  
-   `OMP_SCHEDULE` variable d’environnement : la valeur par défaut pour cette variable d’environnement est défini par l’implémentation (voir [Section 4.1](../../parallel/openmp/4-1-omp-schedule.md) page 48).  
  
     Dans Visual C++, le type de planification est `static` avec aucune taille de segment.  
  
-   `OMP_NUM_THREADS` variable d’environnement : si aucune valeur n’est spécifiée pour le `OMP_NUM_THREADS` variable d’environnement, ou si la valeur spécifiée n’est pas un entier positif, ou si la valeur est supérieure au nombre maximal de threads que le système peut prendre en charge, le nombre de threads à utiliser est défini par l’implémentation (voir [Section 4.2](../../parallel/openmp/4-2-omp-num-threads.md) page 48).  
  
     Dans Visual C++, si la valeur spécifiée est égale à zéro ou moins, le nombre de threads est égal au nombre de processeurs.  Si la valeur est supérieure à 64, le nombre de threads est 64.  
  
-   `OMP_DYNAMIC` variable d’environnement : la valeur par défaut est défini par l’implémentation (voir [Section 4.3](../../parallel/openmp/4-3-omp-dynamic.md) page 49).  
  
     Dans Visual C++, la valeur par défaut est `FALSE`.