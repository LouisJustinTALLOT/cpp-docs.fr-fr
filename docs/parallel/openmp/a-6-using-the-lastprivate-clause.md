---
title: A.6 utilisation de la Clause lastprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03d18d3aaf5c5d1cbe03282710ae4f4e2bb613f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390576"
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