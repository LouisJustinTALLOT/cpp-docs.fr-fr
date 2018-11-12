---
title: 3.2 Fonctions de verrouillage
ms.date: 11/04/2016
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
ms.openlocfilehash: c189ba5b1f0bb365b387b4b4b887cfdb74d1bf2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573067"
---
# <a name="32-lock-functions"></a>3.2 Fonctions de verrouillage

Les fonctions décrites dans cette section manipulent des verrous utilisés pour la synchronisation.

Pour les fonctions suivantes, la variable de verrou doit avoir le type **omp_lock_t**. Cette variable doit uniquement être accessible via ces fonctions. Toutes les fonctions de verrouillage nécessitent un argument qui a un pointeur vers **omp_lock_t** type.

- Le `omp_init_lock` fonction initialise un verrou simple.

- Le `omp_destroy_lock` fonction supprime un verrou simple.

- Le `omp_set_lock` fonction attend un verrou simple est disponible.

- Le `omp_unset_lock` fonction libère un verrou simple.

- Le `omp_test_lock` fonction teste un verrou simple.

Pour les fonctions suivantes, la variable de verrou doit avoir le type **imbriqué omp_nest_lock_t**.  Cette variable doit uniquement être accessible via ces fonctions. Toutes les fonctions de verrou pouvant être nécessitent un argument qui a un pointeur vers **imbriqué omp_nest_lock_t** type.

- Le `omp_init_nest_lock` fonction initialise un verrou pouvant être imbriqué.

- Le `omp_destroy_nest_lock` fonction supprime un verrou pouvant être imbriqué.

- Le `omp_set_nest_lock` fonction attend un verrou pouvant être disponible.

- Le `omp_unset_nest_lock` fonction libère un verrou pouvant être imbriqué.

- Le `omp_test_nest_lock` fonction teste un verrou pouvant être imbriqué.

Les fonctions de verrouillage OpenMP accéder à la variable de verrou de sorte qu’ils toujours lire et mettre à jour la valeur la plus récente de la variable de verrou. Par conséquent, il n’est pas nécessaire pour un programme OpenMP inclure explicite **vider** directives pour vous assurer que la valeur de la variable de verrou est cohérente parmi différents threads. (Il peut être nécessaire pour **vider** directives pour rendre les valeurs des autres variables cohérents.)