---
title: A.5 Utilisation de la Directive critical | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f9ab513ae1df5a7e1e62cfefcefe404637c063
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444565"
---
# <a name="a5---using-the-critical-directive"></a>A.5   Utilisation de la directive critical

L’exemple suivant inclut plusieurs `critical` directives ([Section 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) à la page 18). L’exemple illustre un modèle de file d’attente dans laquelle une tâche est dépilée et a travaillé sur. Pour vous protéger contre plusieurs threads du retrait de la même tâche, l’opération de retrait doit être dans un `critical` section. Étant donné que les deux files d’attente dans cet exemple sont indépendants, ils sont protégés par `critical` directives avec des noms différents, *xaxis* et *yaxis*.

```
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```