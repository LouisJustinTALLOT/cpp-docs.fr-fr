---
title: 3.2.5 fonctions fonctions omp_test_lock et omp_test_nest_lock | Microsoft Docs
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
ms.openlocfilehash: 5349134bf92f407d4b65df9b92e3eebe87c097c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426144"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 Fonctions omp_test_lock and omp_test_nest_lock

Ces fonctions tentent de définition d’un verrou, mais ils ne bloquent pas l’exécution du thread. Le format est le suivant :

```
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

L’argument doit pointer vers une variable initialisée de verrou. Ces fonctions essayez de définir un verrou de la même manière que `omp_set_lock` et `omp_set_nest_lock`, sauf qu’ils ne bloquent pas l’exécution du thread.

Pour obtenir un verrou simple, le `omp_test_lock` fonction retourne une valeur différente de zéro si le verrou est défini correctement ; sinon, elle retourne zéro.

Pour obtenir un verrou pouvant être imbriqué, le `omp_test_nest_lock` fonction retourne le nouveau nombre d’imbrication si le verrou est défini correctement ; sinon, elle retourne zéro.