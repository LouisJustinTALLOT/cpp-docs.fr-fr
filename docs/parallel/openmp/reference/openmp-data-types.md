---
title: Types de données OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b41eaf7012c1d119071281f98177e4a4d841890b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410069"
---
# <a name="openmp-data-types"></a>Types de données OpenMP

Fournit des liens vers les types de données utilisés dans l’API OpenMP.

L’implémentation Visual C++ de l’OpenMP standard inclut les types de données suivants.

|Type de données|Description|
|---------------|-----------------|
|[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md)|Un type qui contient l’état d’un verrou, si le verrou est disponible ou si un thread détient un verrou.|
|[omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)|Un type qui conserve l’un des éléments suivants d’informations sur un verrou : si le verrou est disponible et que l’identité du thread qui détient le verrou et un nombre d’imbrication.|

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque](../../../parallel/openmp/reference/openmp-library-reference.md)