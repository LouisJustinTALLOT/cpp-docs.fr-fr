---
title: A.6   Utilisation de la clause lastprivate
ms.date: 11/04/2016
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
ms.openlocfilehash: 7d5ba1413827590b7fb3afa0847b9aa1da3c41e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579802"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Utilisation de la clause lastprivate

Exécution correcte parfois dépend de la valeur de la dernière itération d’une boucle assigne à une variable. Ces programmes doivent répertorier toutes les variables de ce type en tant qu’arguments à un `lastprivate` clause ([Section 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) page 27) afin que les valeurs des variables sont les mêmes que lorsque la boucle est exécutée de manière séquentielle.

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

Dans l’exemple précédent, la valeur de `i` à la fin de la région parallèle est égal à `n-1`, comme dans le cas séquentiel.