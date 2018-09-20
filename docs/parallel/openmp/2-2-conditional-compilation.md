---
title: 2.2 Compilation conditionnelle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25b52ce624777efe85e27b8ce5e7941bc2f5dcba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440379"
---
# <a name="22-conditional-compilation"></a>2.2 Compilation conditionnelle

Le _**OPENMP** nom de la macro est définie par les implémentations conformes OpenMP en tant que constante décimale *yyyymm*, qui sera l’année et le mois de la spécification approuvée. Cette macro ne doit pas faire l’objet d’un **#define** ou un **#undef** directive de prétraitement.

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Si les fournisseurs définissent les extensions de OpenMP, ils peuvent spécifier supplémentaires macros prédéfinies.