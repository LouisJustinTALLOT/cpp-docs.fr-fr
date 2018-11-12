---
title: 2.1 Format des directives
ms.date: 11/04/2016
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
ms.openlocfilehash: 6ee977005d421a59e71f852be3d78a2caad9b45b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629487"
---
# <a name="21-directive-format"></a>2.1 Format des directives

La syntaxe d’une directive OpenMP est formellement spécifiée par la grammaire dans [annexe C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)et de manière informelle comme suit :

```
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Chaque directive commence par **#pragma omp**afin de réduire le risque potentiel de conflit avec d’autres directives de pragma (non OpenMP ou fournisseur extensions OpenMP) portant le même nom. Le reste de la directive suit les conventions des normes pour les directives de compilateur C et C++. En particulier, un espace blanc peut être utilisé avant et après le **#**, et parfois un espace blanc doit être utilisé pour séparer les mots dans une directive. Prétraitement des jetons après la **#pragma omp** subissent un remplacement de macro.

Directives respectent la casse. L’ordre dans lequel les clauses apparaissent dans les directives n’est pas significatif. Clauses sur les directives peuvent être répétées en fonction des besoins, soumis aux restrictions répertoriées dans la description de chaque clause. Si *variable-list* s’affiche dans une clause, il doit spécifier uniquement les variables. Seul *nom de la directive* peut être spécifiée par la directive.  Par exemple, la directive suivante n’est pas autorisée :

```
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Une directive OpenMP s’applique au plus une réussie instruction, qui doit être un bloc structuré.