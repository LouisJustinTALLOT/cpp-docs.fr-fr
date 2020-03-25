---
title: Avertissement NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: d59b5656d76025fa56bfc76bad800659f25acf53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193197"
---
# <a name="nmake-warning-u4004"></a>Avertissement NMAKE U4004

règles trop nombreuses pour la cible’TargetName'

Plusieurs blocs de description ont été spécifiés pour la cible donnée à l’aide de deux-points ( **:** ) comme séparateurs. NMAKE a exécuté les commandes dans le premier bloc de description et a ignoré les blocs ultérieurs.

Pour spécifier la même cible dans plusieurs dépendances, utilisez le double deux-points (`::`) comme séparateur dans chaque ligne de dépendance.
