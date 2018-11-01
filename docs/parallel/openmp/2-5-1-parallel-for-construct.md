---
title: 2.5.1 Construction for parallèle
ms.date: 11/04/2016
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
ms.openlocfilehash: e74fa958a70fb10aadd39ccc6b4e56670bc072b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590331"
---
# <a name="251-parallel-for-construct"></a>2.5.1 Construction for parallèle

Le **parallèles pour** directive est un raccourci pour un **parallèles** région qui contient une seule **pour** la directive. La syntaxe de la **parallèles pour** directive se présente comme suit :

```
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Cette directive permet toutes les clauses de la **parallèles** directive et le **pour** directive, sauf le `nowait` clause, avec une signification identique et des restrictions. La sémantique est identique à spécifier explicitement un **parallèles** directive immédiatement suivie d’un **pour** la directive.

## <a name="cross-references"></a>Références externes :

- **parallèle** directive, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.

- **pour** directive, consultez [Section 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) à la page 11.

- Les clauses d’attributs de données, consultez [2.7.2 Clauses d’attributs de partage de données](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.