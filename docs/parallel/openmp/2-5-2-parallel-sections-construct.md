---
title: 2.5.2 construction parallel sections | Microsoft Docs
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
ms.openlocfilehash: 073d0561fe4bfbb96ed88681a077da6fc985c963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402328"
---
# <a name="252-parallel-sections-construct"></a>2.5.2 Construction de sections parallèles

Le **de sections parallèles** directive fournit un formulaire contextuel pour spécifier un **parallèles** région contenant un seul **sections** directive. La sémantique est identique à spécifier explicitement un **parallèles** directive immédiatement suivie d’un **sections** directive. La syntaxe de la **de sections parallèles** directive se présente comme suit :

```
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

Le *clause* peut prendre l’une des clauses du acceptées par le **parallèles** et **sections** directives, sauf le **nowait** clause.

## <a name="cross-references"></a>Références externes :

- **parallèle** directive, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.

- **sections** directive, consultez [Section 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) page 14.