---
title: 2.5.2 construction de sections parallèles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6f7a84e322cb273733c6a724ee2563928df8362
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689478"
---
# <a name="252-parallel-sections-construct"></a>2.5.2 Construction de sections parallèles
Le **de sections parallèles** directive fournit un formulaire contextuel pour spécifier un **parallèles** région contenant un seul **sections** directive. La sémantique est identique à spécifier explicitement un **parallèles** directive immédiatement suivie d’un **sections** directive. La syntaxe de la **de sections parallèles** la directive est la suivante :  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block  ]  
   ...  
}  
```  
  
 Le *clause* peut prendre l’une clauses de l’acceptation par la **parallèles** et **sections** directives, sauf le **nowait** clause.  
  
## <a name="cross-references"></a>Références externes :  
  
-   **parallèle** directive, voir [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.  
  
-   **sections** directive, voir [Section 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) page 14.