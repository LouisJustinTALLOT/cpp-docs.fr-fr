---
title: 'Temps écoulé : Les Classes à usage général | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54c3061ac0d081d04834ba4a8b7336732d854199
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055864"
---
# <a name="elapsed-time-general-purpose-classes"></a>Temps écoulé : Les Classes à usage général

La procédure suivante montre comment calculer la différence entre deux `CTime` objets et obtenez un `CTimeSpan` résultat. Utilisez le `CTime` et `CTimeSpan` objets pour calculer le temps écoulé, comme suit :

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

Une fois que vous avez calculé `elapsedTime`, vous pouvez utiliser les fonctions membres de `CTimeSpan` pour extraire les composants de la valeur de temps écoulé.

