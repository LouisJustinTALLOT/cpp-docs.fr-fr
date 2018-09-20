---
title: A.23 exemples de Directive ordered | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec609a77e9bdc7cbdbb0822dfde0a88110ce0244
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405968"
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   Exemples de directive ordered

Il est possible d’avoir plusieurs sections ordonnées avec un `for` spécifié avec le `ordered` clause. Le premier exemple n’est pas conforme, car l’API spécifie les éléments suivants :

« Une itération d’une boucle avec une `for` construction ne doit pas exécuter le même `ordered` directive plus qu’une seule fois et il ne doivent pas exécuter plusieurs `ordered` directive. » (Consultez [Section 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) à la page 22)

Dans cet exemple non conforme, toutes les itérations exécutent classés par 2 section :

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

L’exemple conforme suivant un `for` avec plus d’une section classée :

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```