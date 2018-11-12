---
title: 3.2.1 Fonctions omp_init_lock and omp_init_nest_lock
ms.date: 11/04/2016
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
ms.openlocfilehash: 2d15aacb5e6743d18150fb45bea85b7ca22a401f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472774"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 Fonctions omp_init_lock and omp_init_nest_lock

Ces fonctions vous permettent uniquement de l’initialisation d’un verrou. Chaque fonction initialise le verrou associé au paramètre *verrou* pour une utilisation dans les appels suivants. Le format est le suivant :

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

L’état initial est déverrouillé (autrement dit, aucun thread ne possède le verrou). Pour obtenir un verrou pouvant être imbriqué, le nombre initial d’imbrication est égal à zéro. Il n’est pas conforme à appeler une de ces routines avec une variable de verrou qui a déjà été initialisé.