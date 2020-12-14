---
description: 'En savoir plus sur : NMAKE Warning U4004'
title: Avertissement NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 44326bfb6a69b583967163054b4510bf5c50d6bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345288"
---
# <a name="nmake-warning-u4004"></a>Avertissement NMAKE U4004

règles trop nombreuses pour la cible’TargetName'

Plusieurs blocs de description ont été spécifiés pour la cible donnée à l’aide de deux-points (**:**) comme séparateurs. NMAKE a exécuté les commandes dans le premier bloc de description et a ignoré les blocs ultérieurs.

Pour spécifier la même cible dans plusieurs dépendances, utilisez le double signe deux-points ( `::` ) comme séparateur dans chaque ligne de dépendance.
