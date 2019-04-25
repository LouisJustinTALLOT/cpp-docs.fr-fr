---
title: Avertissement NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 882f6c98b31d23d283f5e8b32b46a46c543b1a76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298150"
---
# <a name="nmake-warning-u4004"></a>Avertissement NMAKE U4004

règles trop nombreuses pour la cible 'targetname'

Plusieurs blocs de description a été spécifiée pour la cible spécifiée à l’aide de signes deux-points uniques (**:**) comme séparateurs. NMAKE exécuté les commandes dans le premier bloc de description et ignoré les blocs.

Pour spécifier la même cible dans plusieurs dépendances, utilisez des signes deux-points doubles (`::`) comme séparateur dans chaque ligne de dépendance.