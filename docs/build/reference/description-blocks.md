---
title: Blocs de description
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: da9265d6b0026bb47496d3aa58847824b5d634d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293808"
---
# <a name="description-blocks"></a>Blocs de description

Un bloc de description est une ligne de dépendance suivie éventuellement d’un bloc de commandes :

```
targets... : dependents...
    commands...
```

Une ligne de dépendance spécifie une ou plusieurs cibles et zéro ou plusieurs dépendants. Une cible doit être au début de la ligne. Séparez les cibles des dépendants par un signe deux-points ( :)) ; des espaces ou des tabulations sont autorisées. Pour fractionner la ligne, utilisez une barre oblique inverse (\) après une cible ou un dépendant. Si une cible n’existe pas, a un horodatage antérieur à celui d’une dépendance ou est un [pseudocible](pseudotargets.md), NMAKE exécute les commandes. Si une dépendance est une cible ailleurs et n’existe pas ou est obsolète par rapport à ses propres dépendants, NMAKE met à jour du dépendant avant la mise à jour de la dépendance actuelle.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Cibles](targets.md)

[Dépendants](dependents.md)

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](nmake-reference.md)
