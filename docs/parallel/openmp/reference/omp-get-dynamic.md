---
title: omp_get_dynamic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d97cae8091f88c283412b36ef757b03c72f7580d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691265"
---
# <a name="ompgetdynamic"></a>omp_get_dynamic
Retourne une valeur qui indique si le nombre de threads disponibles dans une région parallèle suivante peut être ajusté par le temps d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int omp_get_dynamic();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si elle est différente de zéro, l’ajustement dynamique de threads est activée.  
  
## <a name="remarks"></a>Notes  
 L’ajustement dynamique de threads est spécifié avec [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) et [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md).  
  
 Pour plus d’informations, consultez [3.1.7 fonction omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## <a name="example"></a>Exemple  
 Consultez [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) pour obtenir un exemple d’utilisation de `omp_get_dynamic`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../../parallel/openmp/reference/openmp-functions.md)