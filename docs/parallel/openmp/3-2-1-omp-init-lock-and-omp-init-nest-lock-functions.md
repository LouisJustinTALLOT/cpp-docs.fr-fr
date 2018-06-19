---
title: 3.2.1 fonctions fonctions omp_init_lock and omp_init_nest_lock | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f14e182e6c981cd5de7a4cf92d8c285a4b49c66
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695796"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 Fonctions omp_init_lock and omp_init_nest_lock
Ces fonctions vous permettent uniquement de l’initialisation d’un verrou. Chaque fonction initialise le verrou associé au paramètre *verrou* pour une utilisation dans les appels suivants. Le format est le suivant :  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 L’état initial est déverrouillé (autrement dit, aucun thread ne possède le verrou). Pour obtenir un verrou pouvant, le nombre initial d’imbrication est égale à zéro. Il n’est pas conforme à appeler une de ces routines avec une variable de verrou a déjà été initialisé.