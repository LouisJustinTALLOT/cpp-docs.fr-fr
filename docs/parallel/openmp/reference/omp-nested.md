---
title: OMP_NESTED | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 363a125cb7f9858b1ef4105234344d2a8d35b707
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="ompnested"></a>OMP_NESTED
Spécifie si parallélisme imbriquée est activée, sauf si le parallélisme imbriquée est activée ou désactivée avec `omp_set_nested`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Notes  
 Le `OMP_NESTED` variable d’environnement peut être remplacée par la [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) (fonction).  
  
 La valeur par défaut dans l’implémentation Visual C++ de la norme OpenMP est `OMP_DYNAMIC=FALSE`.  
  
 Pour plus d’informations, consultez [OMP_NESTED 4,4](../../../parallel/openmp/4-4-omp-nested.md).  
  
## <a name="example"></a>Exemple  
 La commande suivante définit le `OMP_NESTED` variable d’environnement pour la valeur TRUE :  
  
```  
set OMP_NESTED=TRUE  
```  
  
 La commande suivante affiche le paramètre actuel de la `OMP_NESTED` variable d’environnement :  
  
```  
set OMP_NESTED  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’environnement](../../../parallel/openmp/reference/openmp-environment-variables.md)