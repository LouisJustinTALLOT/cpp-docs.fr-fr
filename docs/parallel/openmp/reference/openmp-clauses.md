---
title: Clauses OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afd0a8f66f9b0d027671629998597955b3aa69e9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378324"
---
# <a name="openmp-clauses"></a>Clauses OpenMP

Fournit des liens vers les clauses utilisées dans l’API OpenMP.

Visual C++ prend en charge les clauses OpenMP suivantes :

|Clause|Description|
|------------|-----------------|
|[copyin](../../../parallel/openmp/reference/copyin.md)|Permet aux threads d’accéder à valeur du thread principal, pour un [threadprivate](../../../parallel/openmp/reference/threadprivate.md) variable.|
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|Spécifie qu’une ou plusieurs variables doivent être partagés entre tous les threads.|
|[default](../../../parallel/openmp/reference/default-openmp.md)|Spécifie le comportement de variables non délimitées dans une région parallèle.|
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Spécifie que chaque thread doit avoir sa propre instance d’une variable, et que la variable doit être initialisée avec la valeur de la variable, car il existe avant la construction parallèle.|
|[if](../../../parallel/openmp/reference/if-openmp.md)|Spécifie si une boucle doit être exécutée en parallèle ou en série.|
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Spécifie que la version du contexte englobant de la variable est définie égale à la version privée du thread quelconque qui exécute la dernière itération (construction de boucle for) ou la dernière section (sections #pragma).|
|[nowait](../../../parallel/openmp/reference/nowait.md)|Remplace la barrière implicite dans une directive.|
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|Définit le nombre de threads dans une équipe de thread.|
|[Commandée](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Requis sur un parallèle [pour](../../../parallel/openmp/reference/for-openmp.md) instruction si un [classés](../../../parallel/openmp/reference/ordered-openmp-directives.md) directive doit être utilisé dans la boucle.|
|[private](../../../parallel/openmp/reference/private-openmp.md)|Spécifie que chaque thread doit avoir sa propre instance d’une variable.|
|[reduction](../../../parallel/openmp/reference/reduction.md)|Spécifie qu’une ou plusieurs variables qui sont spécifiques à chaque thread font l’objet d’une opération de réduction à la fin de la région parallèle.|
|[schedule](../../../parallel/openmp/reference/schedule.md)|S’applique à la [pour](../../../parallel/openmp/reference/for-openmp.md) la directive.|
|[Partagé](../../../parallel/openmp/reference/shared-openmp.md)|Spécifie qu’une ou plusieurs variables doivent être partagés entre tous les threads.|

## <a name="see-also"></a>Voir aussi

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[Directives](../../../parallel/openmp/reference/openmp-directives.md)