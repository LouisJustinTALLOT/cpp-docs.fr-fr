---
title: Blocs de description | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d83e010f690f96afa5a57eb89ca1e8f4cf444225
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699658"
---
# <a name="description-blocks"></a>Blocs de description

Un bloc de description est une ligne de dépendance suivie éventuellement d’un bloc de commandes :

```
targets... : dependents...
    commands...
```

Une ligne de dépendance spécifie une ou plusieurs cibles et zéro ou plusieurs dépendants. Une cible doit être au début de la ligne. Séparez les cibles des dépendants par un signe deux-points ( :)) ; des espaces ou des tabulations sont autorisées. Pour fractionner la ligne, utilisez une barre oblique inverse (\) après une cible ou un dépendant. Si une cible n’existe pas, a un horodatage antérieur à celui d’une dépendance ou est un [pseudocible](../build/pseudotargets.md), NMAKE exécute les commandes. Si une dépendance est une cible ailleurs et n’existe pas ou est obsolète par rapport à ses propres dépendants, NMAKE met à jour du dépendant avant la mise à jour de la dépendance actuelle.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Cibles](../build/targets.md)

[Dépendants](../build/dependents.md)

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](../build/nmake-reference.md)