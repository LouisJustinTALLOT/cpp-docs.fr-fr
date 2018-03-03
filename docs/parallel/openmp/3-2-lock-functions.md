---
title: 3.2 fonctions de verrouillage | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 151c809a7bd28a2e4384371f5cec3bd192eed9d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="32-lock-functions"></a>3.2 Fonctions de verrouillage
Les fonctions décrites dans cette section manipulent des verrous utilisés pour la synchronisation.  
  
 Pour les fonctions suivantes, la variable de verrou doit avoir le type **omp_lock_t**. Cette variable doit être accessible uniquement au moyen de ces fonctions. Toutes les fonctions de verrouillage nécessitent un argument qui a un pointeur vers **omp_lock_t** type.  
  
-   Le `omp_init_lock` fonction initialise un verrou simple.  
  
-   Le `omp_destroy_lock` fonction supprime un verrou simple.  
  
-   Le `omp_set_lock` fonction attend un verrou simple n’est disponible.  
  
-   Le `omp_unset_lock` fonction libère un verrou simple.  
  
-   Le `omp_test_lock` fonction teste un verrou simple.  
  
 Pour les fonctions suivantes, la variable de verrou doit avoir le type **omp_nest_lock_t**.  Cette variable doit être accessible uniquement au moyen de ces fonctions. Toutes les fonctions de verrou pouvant nécessitent un argument qui a un pointeur vers **omp_nest_lock_t** type.  
  
-   Le `omp_init_nest_lock` fonction initialise un verrou pouvant.  
  
-   Le `omp_destroy_nest_lock` fonction supprime un verrou pouvant.  
  
-   Le `omp_set_nest_lock` fonction attend un verrou pouvant est disponible.  
  
-   Le `omp_unset_nest_lock` fonction libère un verrou pouvant.  
  
-   Le `omp_test_nest_lock` fonction teste un verrou pouvant.  
  
 Les fonctions de verrouillage OpenMP accéder à la variable de verrou de sorte qu’ils toujours lire et mettre à jour la valeur la plus récente de la variable de verrou. Par conséquent, il n’est pas nécessaire pour inclure explicite d’un programme OpenMP **vider** directives pour vous assurer que la valeur de la variable de verrou est cohérente parmi différents threads. (Il peut être nécessaire de **vider** directives pour rendre les valeurs des autres variables cohérente.)