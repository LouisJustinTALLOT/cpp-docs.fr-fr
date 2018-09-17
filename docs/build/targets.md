---
title: Cibles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: edb75258c548526c68ed33f7f8037656750f6855
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713795"
---
# <a name="targets"></a>Cibles

Dans une ligne de dépendance, spécifiez une ou plusieurs cibles, à l’aide de n’importe quel nom de fichier valide, le nom de répertoire, ou [pseudocible](../build/pseudotargets.md). Séparez plusieurs cibles par un ou plusieurs espaces ou des tabulations. Cibles ne respectent pas la casse. Chemins d’accès sont autorisées avec les noms de fichiers. Une cible ne peut pas dépasser 256 caractères. Si la cible qui précède le signe deux-points est un caractère unique, utilisez un espace de séparation ; Sinon, NMAKE interprète la combinaison lettre-signe deux-points comme un spécificateur de lecteur.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Pseudocibles](../build/pseudotargets.md)

[Plusieurs cibles](../build/multiple-targets.md)

[Dépendances cumulatives](../build/cumulative-dependencies.md)

[Cibles dans des blocs de description multiples](../build/targets-in-multiple-description-blocks.md)

[Effets secondaires des dépendances](../build/dependency-side-effects.md)

## <a name="see-also"></a>Voir aussi

[Blocs de description](../build/description-blocks.md)