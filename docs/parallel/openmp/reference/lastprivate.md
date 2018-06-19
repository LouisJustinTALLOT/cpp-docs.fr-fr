---
title: lastprivate | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aaf80e3061877c42154ab9ee5ccd30f47f17135
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696225"
---
# <a name="lastprivate"></a>lastprivate
Spécifie que la version du contexte englobant de la variable est définie égale à la version privée du thread exécute la dernière itération (construction de la boucle for) ou la dernière section (sections #pragma).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
lastprivate(var)  
```  
  
## <a name="remarks"></a>Notes  
 où,  
  
 `var`  
 La variable est égale à la version privée du thread exécute la dernière itération (construction de la boucle for) ou la dernière section (sections #pragma).  
  
## <a name="remarks"></a>Notes  
 `lastprivate` s’applique aux directives suivantes :  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Pour plus d’informations, consultez [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## <a name="example"></a>Exemple  
 Consultez [planification](../../../parallel/openmp/reference/schedule.md) pour obtenir un exemple d’utilisation de `lastprivate` clause.  
  
## <a name="see-also"></a>Voir aussi  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)