---
title: 3.2.4 fonctions fonctions omp_unset_lock and omp_unset_nest_lock | Documents Microsoft
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
ms.openlocfilehash: f480a75efff737356c1477593e182537ae73a8c8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690219"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 Fonctions omp_unset_lock and omp_unset_nest_lock
Ces fonctions vous permettent de libérer la possession d’un verrou. Le format est le suivant :  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 L’argument de chacune de ces fonctions doit pointer vers une variable initialisée verrou détenue par le thread d’exécution de la fonction. Le comportement est indéfini si le thread ne possède pas ce verrou.  
  
 Pour obtenir un verrou simple, le `omp_unset_lock` fonction libère le thread de l’exécution de la fonction à partir de la propriété du verrou.  
  
 Pour obtenir un verrou pouvant, le `omp_unset_nest_lock` fonction décrémente le nombre d’imbrication et libère le thread d’exécution de la fonction de la propriété du verrou si le nombre résultant est égal à zéro.