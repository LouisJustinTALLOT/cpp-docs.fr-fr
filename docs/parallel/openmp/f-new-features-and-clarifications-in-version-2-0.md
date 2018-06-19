---
title: F. Nouvelles fonctionnalités et les éclaircissements dans la Version 2.0 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e48f299e66ed1b4c075757a9cd143d0afe897db
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693141"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nouvelles fonctionnalités et les éclaircissements dans la Version 2.0
Cette annexe résume les principales modifications apportées à la spécification OpenMP C/C++ lors du déplacement de la version 1.0 vers la version 2.0. Les éléments suivants sont les nouvelles fonctionnalités ajoutées à la spécification :  
  
-   Des virgules sont autorisés dans les directives OpenMP ([Section 2.1](../../parallel/openmp/2-1-directive-format.md) page 7).  
  
-   Ajout de la `num_threads` clause. Cette clause permet à un utilisateur demander un certain nombre de threads d’une construction parallèle ([Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8).  
  
-   Le `threadprivate` la directive a été étendue pour accepter les variables static de portée de bloc ([Section 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) à la page 23).  
  
-   Les tableaux de longueur Variable C99 sont des types complets et par conséquent, vous pouvez spécifier n’importe où types complets sont autorisés, par exemple dans les listes de `private`, `firstprivate`, et `lastprivate` clauses ([Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25).  
  
-   Une variable privée dans une région parallèle peut être marqué comme privée dans une directive imbriquée ([Section 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) page 25).  
  
-   Le `copyprivate` clause a été ajoutée. Il fournit un mécanisme permettant d’utiliser une variable privée pour diffuser une valeur à partir d’un membre d’une équipe aux autres membres. Il est plutôt que d’utiliser une variable partagée pour la valeur lorsque fournissant cette variable partagée serait difficile (par exemple, dans une récursivité nécessitant une variable différente à chaque niveau). Le `copyprivate` clause peut uniquement apparaître sur le **unique** directive ([Section 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) à la page 32).  
  
-   Ajout de routines de minutage `omp_get_wtick` et `omp_get_wtime` similaire aux routines MPI. Ces fonctions sont nécessaires à l’exécution d’horloge murale ([Section 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) sur la page 44 et [Section 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) sur la page 45).  
  
-   Une annexe avec une liste de comportements définis par l’implémentation dans OpenMP C/C++ a été ajoutée. Une implémentation est requise pour définir et son comportement dans ces cas de document ([annexe E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) page 97).  
  
-   Les modifications suivantes permettent de clarifier ou de corriger les fonctionnalités de la spécification API OpenMP précédente pour C/C++ :  
  
    -   Clarification du fait que le comportement de `omp_set_nested` et `omp_set_dynamic` lorsque `omp_in_parallel` retourne différente de zéro n’est pas défini ([Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39 et [Section 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) page 40).  
  
    -   Clarification de la directive imbrication lorsque imbriquée parallèle est utilisé ([Section 2.9](../../parallel/openmp/2-9-directive-nesting.md) sur la page 33).  
  
    -   Les fonctions de destruction d’initialisation et de verrou de verrou peuvent être appelées dans une région parallèle ([Section 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) sur la page 42 et [Section 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) sur la page 42).  
  
    -   Nouveaux exemples ont été ajoutés ([annexe A](../../parallel/openmp/a-examples.md) page 51).