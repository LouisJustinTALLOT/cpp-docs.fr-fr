---
title: F. Nouvelles fonctionnalités et clarifications de la version 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 2e186bbc82f4f43e831dd05cdded2a9e946d1dd2
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087208"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nouvelles fonctionnalités et clarifications de la version 2.0

Cette annexe résume les modifications clées apportées à la spécification OpenMP C/C++ dans le passage de la version 1.0 vers la version 2.0. Les éléments suivants sont ajoutées à la spécification de nouvelles fonctionnalités :

- Des virgules sont autorisés dans OpenMP [directives](2-directives.md#21-directive-format).

- Ajout de la `num_threads` clause. Cette clause permet à un utilisateur demander un certain nombre de threads pour un [construction parallèle](2-directives.md#23-parallel-construct).

- Le [threadprivate](2-directives.md#271-threadprivate-directive) directive a été étendue pour accepter les variables de portée de bloc statique.

- Tableaux de longueur Variable C99 sont des types complets et vous pouvez spécifier n’importe où types complets sont autorisés, comme dans les listes de `private`, `firstprivate`, et `lastprivate` clauses (consultez [section 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Une variable privée dans une région parallèle peut être marquée [privé](2-directives.md#2721-private) dans une directive imbriquée.

- Le `copyprivate` clause a été ajoutée. Il fournit un mécanisme pour utiliser une variable privée pour diffuser une valeur à partir d’un membre d’une équipe aux autres membres. Il est une alternative à l’utilisation d’une variable partagée pour la valeur lors de la fourniture de ce type d’une variable partagée serait difficile (par exemple, dans une récursivité nécessitant une variable différente à chaque niveau). Le [copyprivate](2-directives.md#2728-copyprivate) clause ne peut apparaître qu’à la `single` directive.

- Ajout de routines de minutage [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) et [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) similaire aux routines MPI. Ces fonctions sont nécessaires pour d’horloge de mur.

- Une annexe avec une liste de [comportements définis par l’implémentation](e-implementation-defined-behaviors-in-openmp-c-cpp.md) dans OpenMP C/C++ a été ajouté. Une implémentation est requise pour définir et documenter son comportement dans ces cas.

- Les modifications suivantes servent à clarifier ou de corriger les fonctionnalités dans la spécification API OpenMP précédente pour C/C++ :

  - Clarification du fait que le comportement de [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) et [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) lorsque `omp_in_parallel` retourne différente de zéro n’est pas défini.

  - Clarification de [imbrication de directives](2-directives.md#29-directive-nesting) lorsque imbriquée parallèle est utilisé.

  - Le [verrouiller l’initialisation](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) et [verrouiller destruction](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) fonctions peuvent être appelées dans une région parallèle.

  - Nouveaux exemples ont été ajoutées à [annexe A](a-examples.md).