---
description: 'En savoir plus sur : F. Nouvelles fonctionnalités et clarifications dans la version 2,0'
title: F. Nouvelles fonctionnalités et clarifications de la version 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 77a27ed6d15986f787297b37a904d4625d649ced
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342463"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nouvelles fonctionnalités et clarifications de la version 2.0

Cette annexe résume les principales modifications apportées à la spécification C/C++ OpenMP lors du passage de la version 1,0 à la version 2,0. Les éléments suivants sont de nouvelles fonctionnalités ajoutées à la spécification :

- Les virgules sont autorisées dans les [directives](2-directives.md#21-directive-format)OpenMP.

- Ajout de la `num_threads` clause. Cette clause permet à un utilisateur de demander un nombre spécifique de threads pour une [construction parallèle](2-directives.md#23-parallel-construct).

- La directive [threadprivate](2-directives.md#271-threadprivate-directive) a été étendue pour accepter des variables de portée de bloc statiques.

- Les tableaux de longueur variable C99 sont des types complets et peuvent être spécifiés partout où les types complets sont autorisés, par exemple dans les listes des `private` `firstprivate` `lastprivate` clauses, et (voir la [section 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Une variable privée dans une région parallèle peut être marquée à nouveau comme [privée](2-directives.md#2721-private) dans une directive imbriquée.

- La `copyprivate` clause a été ajoutée. Il fournit un mécanisme permettant d’utiliser une variable privée pour diffuser une valeur d’un membre d’une équipe vers les autres membres. C’est une alternative à l’utilisation d’une variable partagée pour la valeur lors de la fourniture d’une telle variable partagée serait difficile (par exemple, dans une récurrence nécessitant une variable différente à chaque niveau). La clause [copyprivate](2-directives.md#2728-copyprivate) ne peut apparaître que dans la `single` directive.

- L’ajout de routines de minutage [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) et [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) similaires aux routines MPI. Ces fonctions sont nécessaires pour effectuer des minutages d’horloge du mur.

- Une annexe contenant la liste des [comportements définis par l’implémentation](e-implementation-defined-behaviors-in-openmp-c-cpp.md) dans OpenMP C/C++ a été ajoutée. Une implémentation est requise pour définir et documenter son comportement dans ces cas.

- Les modifications suivantes servent à clarifier ou à corriger les fonctionnalités de la précédente spécification de l’API OpenMP pour C/C++ :

  - Clarification du fait que le comportement de [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) et [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) quand retourne une valeur `omp_in_parallel` différente de zéro n’est pas défini.

  - Clarification de [la directive](2-directives.md#29-directive-nesting) en cas d’utilisation de Parallel imbriqué.

  - Les fonctions [d’initialisation](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) et de [destruction](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) de verrous peuvent être appelées dans une région parallèle.

  - De nouveaux exemples ont été ajoutés à l' [annexe A](a-examples.md).
