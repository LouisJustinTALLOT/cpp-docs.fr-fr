---
title: Avertissement NMAKE U4004 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a89bb8abf212c8a0ffa9fb40fe5d3ea43307a08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016648"
---
# <a name="nmake-warning-u4004"></a>Avertissement NMAKE U4004

règles trop nombreuses pour la cible 'targetname'

Plusieurs blocs de description a été spécifiée pour la cible spécifiée à l’aide de signes deux-points uniques (**:**) comme séparateurs. NMAKE exécuté les commandes dans le premier bloc de description et ignoré les blocs.

Pour spécifier la même cible dans plusieurs dépendances, utilisez des signes deux-points doubles (`::`) comme séparateur dans chaque ligne de dépendance.