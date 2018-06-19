---
title: 2.3 construction parallèle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 121454f6a98901a6c1b695a80c6ec774737b95e0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692744"
---
# <a name="23-parallel-construct"></a>2.3 Construction parallèle
La directive suivante définit une région parallèle, qui est une région du programme qui doit être exécutée par plusieurs threads en parallèle. Il s’agit de la construction fondamentale qui démarre l’exécution en parallèle.  
  
```  
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block  
```  
  
 Le *clause* est une des opérations suivantes :  
  
 **if(** *scalar-expression* **)**  
  
 **privé (** *variable-list* **)**  
  
 **firstprivate(** *variable-list* **)**  
  
 **par défaut (partagée &#124; none)**  
  
 **partagé (** *variable-list* **)**  
  
 **copyin(** *variable-list* **)**  
  
 **reduction(** *operator* **:**  *variable-list* **)**  
  
 **num_threads (** *entier* **)**  
  
 Lorsqu’un thread rencontre une construction parallèle, une équipe de threads est créée si une des situations suivantes est vraie :  
  
-   Ne **si** clause n’est présente.  
  
-   Le **si** expression correspond à une valeur différente de zéro.  
  
 Ce thread devient le thread principal de l’équipe, avec un nombre de threads de 0, et tous les threads de l’équipe, y compris le thread principal, exécutent la région en parallèle. Si la valeur de la **si** expression est égale à zéro, la région est sérialisée.  
  
 Pour déterminer le nombre de threads qui sont demandées, les règles suivantes sont considérées dans l’ordre. La première règle dont la condition est remplie est appliquée :  
  
1.  Si le **num_threads** clause est spécifiée, la valeur de l’expression d’entier est le nombre de threads demandé.  
  
2.  Si le **omp_set_num_threads** fonction de bibliothèque a été appelée, la valeur de l’argument dans l’appel exécuté le plus récemment est le nombre de threads demandé.  
  
3.  Si la variable d’environnement **OMP_NUM_THREADS** est défini, la valeur de cette variable d’environnement est le nombre de threads demandé.  
  
4.  Si aucune des méthodes ci-dessus ont été utilisés, le nombre de threads demandé est défini par l’implémentation.  
  
 Si le **num_threads** clause est présente, il remplace le nombre de threads demandé par le **omp_set_num_threads** fonction de la bibliothèque ou le **OMP_NUM_THREADS** variable d’environnement uniquement pour la région parallèle, il est appliqué à. Les régions parallèles suivantes ne sont pas affectées par celui-ci.  
  
 Le nombre de threads qui s’exécutent de la région parallèle dépend également de l’ajustement dynamique du nombre de threads est activé ou non. Si l’ajustement dynamique est désactivée, le nombre demandé de threads exécutera la région parallèle. Si l’ajustement dynamique est activé le nombre demandé de threads est le nombre maximal de threads qui peuvent s’exécuter à la région parallèle.  
  
 Si une région parallèle est rencontrée pendant que l’ajustement dynamique du nombre de threads est désactivé, et le nombre de threads demandé pour la région parallèle dépasse le nombre qui peut fournir un système d’exécution, le comportement du programme est défini par l’implémentation. Une implémentation d’interruption peut, par exemple, l’exécution du programme, ou il peut sérialiser la région parallèle.  
  
 Le **omp_set_dynamic** fonction de bibliothèque et la **OMP_DYNAMIC** variable d’environnement peut être utilisée pour activer et désactiver l’ajustement dynamique du nombre de threads.  
  
 Le nombre de processeurs physiques hébergeant les threads à un moment donné est défini par l’implémentation. Une fois créé, le nombre de threads de l’équipe reste constant pour la durée de cette région parallèle. Il peut être modifié explicitement par l’utilisateur ou automatiquement par le système d’exécution à partir d’une région parallèle à l’autre.  
  
 Les instructions contenues dans l’étendue dynamique de la région parallèle sont exécutées par chaque thread, et chaque thread peut exécuter un chemin d’accès d’instructions qui est différent des autres threads. Directives rencontrés en dehors de l’étendue lexicale d’une région parallèle sont appelés des directives orphelins.  
  
 Il existe une barrière implicite à la fin d’une région parallèle. Seul le thread principal de l’équipe poursuit l’exécution à la fin d’une région parallèle.  
  
 Si un thread dans une équipe de l’exécution d’une région parallèle rencontre une autre construction parallèle, il crée une nouvelle équipe, et il devient le maître de cette nouvelle équipe. Les régions parallèles imbriquées sont sérialisées par défaut. Par conséquent, par défaut, une région parallèle imbriquée est exécutée par une équipe composée d’un thread. Le comportement par défaut peut être modifié à l’aide de la fonction de bibliothèque runtime **omp_set_nested** ou la variable d’environnement **OMP_NESTED**. Toutefois, le nombre de threads qui s’exécutent une région parallèle imbriquée dans une équipe est défini par l’implémentation.  
  
 Restrictions à le **parallèles** directive sont les suivantes :  
  
-   Au plus un **si** clause peut s’afficher dans la directive.  
  
-   Il n’est pas spécifié si un côté d’effets dans le cas expression ou **num_threads** expression se produisent.  
  
-   A **lever** exécutée à l’intérieur d’une région parallèle doit provoquer l’exécution de reprise dans l’étendue dynamique de la même bloc structuré, et elle doit être interceptée par le même thread que celui qui a levé l’exception.  
  
-   Un seul **num_threads** clause peut s’afficher dans la directive. Le **num_threads** expression est évaluée en dehors du contexte de la région parallèle et doit correspondre à une valeur entière positive.  
  
-   L’ordre d’évaluation de la **si** et **num_threads** clauses n’est pas spécifié.  
  
## <a name="cross-references"></a>Références externes :  
  
-   **privé**, **firstprivate**, **par défaut**, **partagé**, **copyin**, et **réduction**clauses, consultez [Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.  
  
-   **OMP_NUM_THREADS** variable d’environnement, [Section 4.2](../../parallel/openmp/4-2-omp-num-threads.md) page 48.  
  
-   **omp_set_dynamic** fonction de bibliothèque, consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.  
  
-   **OMP_DYNAMIC** voir variable d’environnement [Section 4.3](../../parallel/openmp/4-3-omp-dynamic.md) page 49.  
  
-   **omp_set_nested** , consultez [Section 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) page 40.  
  
-   **OMP_NESTED** voir variable d’environnement [Section 4.4](../../parallel/openmp/4-4-omp-nested.md) page 49.  
  
-   **omp_set_num_threads** fonction de bibliothèque, consultez [Section 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) sur la page 36.