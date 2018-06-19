---
title: OMP_NESTED | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6b51df88ae700f81cf84250cc06ae24c9131fec
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691220"
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