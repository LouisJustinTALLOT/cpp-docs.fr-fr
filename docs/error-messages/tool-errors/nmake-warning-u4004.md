---
title: Avertissement NMAKE U4004 | Documents Microsoft
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
ms.openlocfilehash: 532abf2f62616d6e748c9a4e34f5c983f0853276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317178"
---
# <a name="nmake-warning-u4004"></a>Avertissement NMAKE U4004
règles trop nombreuses pour la cible 'targetname'  
  
 Plusieurs blocs de description a été spécifiée pour la cible de donnée unique comprenant les signes deux-points (**:**) comme séparateurs. NMAKE exécuté les commandes dans le premier bloc de description et ignoré les blocs.  
  
 Pour spécifier la même cible dans plusieurs dépendances, utilisez des signes deux-points doubles (`::`) comme séparateur dans chaque ligne de dépendance.