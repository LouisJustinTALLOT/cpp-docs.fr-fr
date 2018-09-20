---
title: 3.2.3 fonctions omp_set_lock et omp_set_nest_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 792b95baef2821bb693d9a90fc228d2b0c508e1f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420359"
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 Fonctions omp_set_lock and omp_set_nest_lock

Chacune de ces fonctions bloque le thread qui exécute la fonction jusqu'à ce que le verrou spécifié n’est disponible et qu’il définit ensuite le verrou. Un verrou simple est disponible si elle est déverrouillée. Un verrou pouvant être est disponible s’il est déverrouillé, ou si elle est déjà détenu par le thread qui exécute la fonction. Le format est le suivant :

```
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pour un verrou simple, l’argument à la `omp_set_lock` fonction doit pointer vers une variable initialisée de verrou. La propriété du verrou est accordée au thread d’exécuter la fonction.

Pour un verrou pouvant être imbriqué, l’argument à la `omp_set_nest_lock` fonction doit pointer vers une variable initialisée de verrou. Le nombre d’imbrication est incrémenté et le thread est accordé ou conserve, la propriété du verrou.