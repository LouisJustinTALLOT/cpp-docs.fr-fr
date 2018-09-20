---
title: Directives OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 983a71920e9e7ce390ab8c64e81886db0d459450
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389445"
---
# <a name="openmp-directives"></a>Directives OpenMP

Fournit des liens vers les directives utilisées dans l’API OpenMP.

Visual C++ prend en charge les directives OpenMP suivantes :

|Directive|Description|
|---------------|-----------------|
|[atomic](../../../parallel/openmp/reference/atomic.md)|Spécifie qu’un emplacement de mémoire qui sera mis à jour atomiquement.|
|[barrier](../../../parallel/openmp/reference/barrier.md)|Synchronise tous les threads dans une équipe. tous les threads suspendre à la barrière, jusqu'à ce que tous les threads exécuteront le cloisonnement.|
|[critical](../../../parallel/openmp/reference/critical.md)|Spécifie que code est exécuté uniquement sur un seul thread à la fois.|
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|Spécifie que tous les threads ont la même vue de mémoire pour tous les objets partagés.|
|[for](../../../parallel/openmp/reference/for-openmp.md)|Provoque le travail effectué dans une boucle à l’intérieur d’une région parallèle doit être divisé entre threads.|
|[master](../../../parallel/openmp/reference/master.md)|Spécifie qu’uniquement le maître threadshould exécuter une section du programme.|
|[Commandée](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Spécifie que le code sous une parallélisée pour la boucle doit être exécutée comme une boucle séquentielle.|
|[parallel](../../../parallel/openmp/reference/parallel.md)|Définit une région parallèle, ce qui est le code qui sera exécuté par plusieurs threads en parallèle.|
|[sections](../../../parallel/openmp/reference/sections-openmp.md)|Identifie les sections de code pour être réparti entre tous les threads.|
|[single](../../../parallel/openmp/reference/single.md)|Vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, mais pas nécessairement le thread principal.|
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Spécifie qu’une variable est privée pour un thread.|

## <a name="see-also"></a>Voir aussi

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[Clauses](../../../parallel/openmp/reference/openmp-clauses.md)