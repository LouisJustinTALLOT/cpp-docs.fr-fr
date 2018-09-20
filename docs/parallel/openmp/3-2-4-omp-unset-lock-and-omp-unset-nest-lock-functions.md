---
title: 3.2.4 fonctions fonctions omp_unset_lock et omp_unset_nest_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426ac0a5ff974e486f70eed2965fdc27d5acc941
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419104"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 Fonctions omp_unset_lock and omp_unset_nest_lock

Ces fonctions vous permettent de libérer la possession d’un verrou. Le format est le suivant :

```
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

L’argument de chacune de ces fonctions doit pointer vers une variable initialisée verrou détenue par le thread qui exécute la fonction. Le comportement est indéfini si le thread ne possède pas ce verrou.

Pour obtenir un verrou simple, le `omp_unset_lock` fonction libère le thread de l’exécution de la fonction à partir de la propriété du verrou.

Pour obtenir un verrou pouvant être imbriqué, le `omp_unset_nest_lock` fonction décrémente le nombre d’imbrication et les versions le thread qui exécute la fonction à partir de la propriété du verrou si le nombre résultant est égal à zéro.