---
title: A.21   Portée des variables avec la clause private
ms.date: 11/04/2016
ms.assetid: 7cdb4a7f-af24-44ac-9d33-e43840bc8f3d
ms.openlocfilehash: 4217bcc3911ded88b9385695c8c0ac851fceae9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616125"
---
# <a name="a21---scoping-variables-with-the-private-clause"></a>A.21   Portée des variables avec la clause private

Les valeurs de `i` et `j` dans l’exemple suivant ne sont pas définies à la sortie à partir de la région parallèle :

```
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

Pour plus d’informations sur la `private` clause, consultez [Section 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) page 25.