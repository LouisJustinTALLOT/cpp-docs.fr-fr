---
title: omp_unset_nest_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_nest_lock OpenMP function
ms.assetid: 1721d061-3f9c-45d7-b479-a665cd0a121d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ddc3605bfef5c96a8882872aafbe1a15dda3e4cf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115968"
---
# <a name="ompunsetnestlock"></a>omp_unset_nest_lock
Libère un verrou pouvant être imbriqué.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_unset_nest_lock(   
   omp_nest_lock_t *lock   
);  
```  
  
### <a name="parameters"></a>Paramètres
  
*lock*<br/>
Une variable de type [imbriqué omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) qui a été initialisée avec [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md), détenu par le thread et en cours d’exécution dans la fonction.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [3.2.4 fonctions omp_unset_lock et omp_unset_nest_lock fonctions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## <a name="example"></a>Exemple  
 Consultez [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) pour obtenir un exemple d’utilisation de `omp_unset_nest_lock`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../../parallel/openmp/reference/openmp-functions.md)