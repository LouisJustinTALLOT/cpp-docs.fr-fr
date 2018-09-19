---
title: omp_set_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_lock OpenMP function
ms.assetid: ded839cb-ca19-403f-8622-eb52ce512d31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 390090b0f4bf5f8795373db9f61f8365257ee95b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024906"
---
# <a name="ompsetlock"></a>omp_set_lock
Blocs d’exécution de thread jusqu'à ce qu’un verrou est disponible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_lock(  
   omp_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>Paramètres
  
*lock*<br/>
Une variable de type [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) qui a été initialisée avec [fonctions omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md).  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [3.2.3 fonctions omp_set_lock et omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).  
  
## <a name="examples"></a>Exemples  
 Consultez [fonctions omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) pour obtenir un exemple d’utilisation de `omp_set_lock`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../../parallel/openmp/reference/openmp-functions.md)