---
title: 'Heure actuelle : Classes Automation | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, setting current
- current time, COleDateTime object
- procedures, getting current time
- Automation classes, current time
- time, getting current
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ead35da3c20630e93757787f54755dd383264d2
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860613"
---
# <a name="current-time-automation-classes"></a>Heure actuelle : Classes Automation

La procédure suivante montre comment créer un `COleDateTime` de l’objet et l’initialiser avec l’heure actuelle.

## <a name="to-get-the-current-time"></a>Pour obtenir l’heure actuelle

1. Créez un objet `COleDateTime`.

1. Appelez `GetCurrentTime`.

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Date et heure : prise en charge d’Automation](../atl-mfc-shared/date-and-time-automation-support.md)
