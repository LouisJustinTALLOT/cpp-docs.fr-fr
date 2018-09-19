---
title: partagé (OpenMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 078d4b01d2c797fa11c3603c79a341f75e11f18c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115474"
---
# <a name="shared-openmp"></a>shared (OpenMP)
Spécifie qu’une ou plusieurs variables doivent être partagés entre tous les threads.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
shared(var)  
```  
  
### <a name="parameters"></a>Paramètres
  
*var*<br/>
Une ou plusieurs variables à partager. Si plusieurs variables est spécifié, séparez les noms de variables par une virgule.  
  
## <a name="remarks"></a>Notes  
 Une autre façon de partager des variables entre les threads est avec la [copyprivate](../../../parallel/openmp/reference/copyprivate.md) clause.  
  
 `shared` s’applique aux directives suivantes :  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Pour plus d’informations, consultez [2.7.2.4 partagé](../../../parallel/openmp/2-7-2-4-shared.md).  
  
## <a name="example"></a>Exemple  
 Consultez [privé](../../../parallel/openmp/reference/private-openmp.md) pour obtenir un exemple d’utilisation de `shared`.  
  
## <a name="see-also"></a>Voir aussi  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)