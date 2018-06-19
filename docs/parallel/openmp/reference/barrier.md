---
title: cloisonnement | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf5b2cd9edf54e58c06e7d2a48529393cd3ced64
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690892"
---
# <a name="barrier"></a>barrier
Synchronise tous les threads dans une équipe. tous les threads suspendre au cloisonnement, jusqu'à ce que tous les threads s’exécutent le cloisonnement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp barrier  
```  
  
## <a name="remarks"></a>Notes  
 Le `barrier` directive prend en charge aucune clauses OpenMP.  
  
 Pour plus d’informations, consultez [2.6.3 Directive barrier](../../../parallel/openmp/2-6-3-barrier-directive.md).  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple montrant comment utiliser `barrier`, consultez [master](../../../parallel/openmp/reference/master.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)