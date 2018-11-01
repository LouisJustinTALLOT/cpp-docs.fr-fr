---
title: 2.2 Compilation conditionnelle
ms.date: 11/04/2016
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
ms.openlocfilehash: 9dc107ee9e5328df205d4b6f826f71c23abfb3ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658547"
---
# <a name="22-conditional-compilation"></a>2.2 Compilation conditionnelle

Le _**OPENMP** nom de la macro est définie par les implémentations conformes OpenMP en tant que constante décimale *yyyymm*, qui sera l’année et le mois de la spécification approuvée. Cette macro ne doit pas faire l’objet d’un **#define** ou un **#undef** directive de prétraitement.

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Si les fournisseurs définissent les extensions de OpenMP, ils peuvent spécifier supplémentaires macros prédéfinies.