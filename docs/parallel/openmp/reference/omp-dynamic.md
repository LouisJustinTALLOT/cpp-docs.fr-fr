---
title: OMP_DYNAMIC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de4a81d861bf72943a67356577da37c36df63f69
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695809"
---
# <a name="ompdynamic"></a>OMP_DYNAMIC
Spécifie si la durée d’exécution de OpenMP peut ajuster le nombre de threads dans une région parallèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set OMP_DYNAMIC[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Notes  
 Le `OMP_DYNAMIC` variable d’environnement peut être remplacée par la [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) (fonction).  
  
 La valeur par défaut dans l’implémentation Visual C++ de la norme OpenMP est `OMP_DYNAMIC=FALSE`.  
  
 Pour plus d’informations, consultez [OMP_DYNAMIC 4.3](../../../parallel/openmp/4-3-omp-dynamic.md).  
  
## <a name="example"></a>Exemple  
 La commande suivante définit le `OMP_DYNAMIC` variable d’environnement pour la valeur TRUE :  
  
```  
set OMP_DYNAMIC=TRUE  
```  
  
 La commande suivante affiche le paramètre actuel de la `OMP_DYNAMIC` variable d’environnement :  
  
```  
set OMP_DYNAMIC  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’environnement](../../../parallel/openmp/reference/openmp-environment-variables.md)