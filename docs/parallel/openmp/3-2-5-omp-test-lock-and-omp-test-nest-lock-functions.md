---
title: 3.2.5 fonctions fonctions omp_test_lock and omp_test_nest_lock | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5023f0b089d76e92be886f4917905f57dda7a018
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686225"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 Fonctions omp_test_lock and omp_test_nest_lock
Ces fonctions, essayez de définir un verrou mais ne bloquent pas l’exécution du thread. Le format est le suivant :  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 L’argument doit pointer vers une variable initialisée de verrou. Ces fonctions essayez de définir un verrou de la même manière que `omp_set_lock` et `omp_set_nest_lock`, mais ils ne bloquent pas l’exécution du thread.  
  
 Pour obtenir un verrou simple, le `omp_test_lock` fonction retourne une valeur différente de zéro si le verrou est correctement défini ; sinon, elle retourne zéro.  
  
 Pour obtenir un verrou pouvant, le `omp_test_nest_lock` fonction retourne le nouveau nombre d’imbrication si le verrou est correctement défini ; sinon, elle retourne zéro.