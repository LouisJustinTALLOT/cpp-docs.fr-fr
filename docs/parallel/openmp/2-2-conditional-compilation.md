---
title: 2.2 Compilation conditionnelle | Documents Microsoft
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
ms.openlocfilehash: b3d8c7073548c015d9982b721387176a0ca658c2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685903"
---
# <a name="22-conditional-compilation"></a>2.2 Compilation conditionnelle
La _**OPENMP** nom de la macro est définie par les implémentations OpenMP conforme en tant que constante décimale *yyyymm*, qui sera l’année et le mois de la spécification approuvée. Cette macro ne doit pas faire l’objet d’un **#define** ou un **#undef** directive de prétraitement.  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 Si fournisseurs définissent les extensions de OpenMP, ils peuvent spécifier macros prédéfinies supplémentaires.