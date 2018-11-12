---
title: A.30   Utilisation de la reprivatisation
ms.date: 11/04/2016
ms.assetid: 26529090-6c39-40f2-b806-e12374d6b5f8
ms.openlocfilehash: dc1d142a282fe6bb55c9cc512e6a6e8155b286e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437321"
---
# <a name="a30---use-of-reprivatization"></a>A.30   Utilisation de la reprivatisation

L’exemple suivant montre la reprivatisation des variables. Variables privées peuvent être marqués `private` dans une directive imbriquée. Ils n’ont pas à être partagées dans la région parallèle englobante.

```
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```