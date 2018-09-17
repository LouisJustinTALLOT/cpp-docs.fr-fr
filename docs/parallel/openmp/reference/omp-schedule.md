---
title: OMP_SCHEDULE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d873d29d5ac6de1073c1ba3f3065dd015cde1f5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720445"
---
# <a name="ompschedule"></a>OMP_SCHEDULE
Modifie le comportement de la [planification](../../../parallel/openmp/reference/schedule.md) clause lorsque `schedule(runtime)` est spécifié dans un `for` ou `parallel for` directive.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## <a name="arguments"></a>Arguments

*size*<br/>
(Facultatif) Spécifie la taille d’itérations. `size` Doit être un entier positif. La valeur par défaut est 1, sauf quand `type` est statique. Non valide quand `type` est `runtime`.  
  
 `type`  
 Le type de planification :  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## <a name="remarks"></a>Notes  
 La valeur par défaut dans l’implémentation Visual C++ de la norme OpenMP est `OMP_SCHEDULE=static,0`.  
  
 Pour plus d’informations, consultez [OMP_SCHEDULE 4.1](../../../parallel/openmp/4-1-omp-schedule.md).  
  
## <a name="example"></a>Exemple  
 La commande suivante définit le **OMP_SCHEDULE** variable d’environnement :  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 La commande suivante affiche le paramètre actuel de la **OMP_SCHEDULE** variable d’environnement :  
  
```  
set OMP_SCHEDULE  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’environnement](../../../parallel/openmp/reference/openmp-environment-variables.md)