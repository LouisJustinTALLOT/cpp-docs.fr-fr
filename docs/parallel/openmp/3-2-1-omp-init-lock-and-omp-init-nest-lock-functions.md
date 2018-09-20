---
title: 3.2.1 fonctions fonctions omp_init_lock et omp_init_nest_lock | Microsoft Docs
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
ms.openlocfilehash: 4303eb3ccfcb1c449022a4be32f94b9f91e6e80c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387001"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 Fonctions omp_init_lock and omp_init_nest_lock

Ces fonctions vous permettent uniquement de l’initialisation d’un verrou. Chaque fonction initialise le verrou associé au paramètre *verrou* pour une utilisation dans les appels suivants. Le format est le suivant :

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

L’état initial est déverrouillé (autrement dit, aucun thread ne possède le verrou). Pour obtenir un verrou pouvant être imbriqué, le nombre initial d’imbrication est égal à zéro. Il n’est pas conforme à appeler une de ces routines avec une variable de verrou qui a déjà été initialisé.