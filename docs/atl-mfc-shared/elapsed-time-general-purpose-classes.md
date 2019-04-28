---
title: 'Temps écoulé : Classes à usage général'
ms.date: 11/04/2016
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
ms.openlocfilehash: 5990f6f5db0270c8d24ff35b5c9bbea5b24e6ed7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236272"
---
# <a name="elapsed-time-general-purpose-classes"></a>Temps écoulé : Classes à usage général

La procédure suivante montre comment calculer la différence entre deux `CTime` objets et obtenez un `CTimeSpan` résultat. Utilisez le `CTime` et `CTimeSpan` objets pour calculer le temps écoulé, comme suit :

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

Une fois que vous avez calculé `elapsedTime`, vous pouvez utiliser les fonctions membres de `CTimeSpan` pour extraire les composants de la valeur de temps écoulé.
