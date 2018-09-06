---
title: 'Date et heure : prise en charge Automation | Microsoft Docs'
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
- formatting [Visual Studio], dates
- dates, Automation support
- elapsed time, calculating in Automation
- COleDateTime class, Automation date/time support
- COleDateTimeSpan class, Automation date/time support
- Automation, date and time support
- formatting [Visual Studio], time
- calculations, date and time
- time [Visual Studio], Automation support
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38933847065544f97d60dfc109436f059a025f7a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763852"
---
# <a name="date-and-time-automation-support"></a>Date et heure : prise en charge Automation

Cet article décrit comment tirer parti des services de bibliothèque de classe liés à la gestion de date et d’heure. Décrit les procédures :

- [Obtenir l’heure actuelle](../atl-mfc-shared/current-time-automation-classes.md)

- [Calcul du temps écoulé](../atl-mfc-shared/elapsed-time-automation-classes.md)

- [Mise en forme d’une chaîne représentant une date/heure](../atl-mfc-shared/formatting-time-automation-classes.md)

Le [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) classe fournit un moyen pour représenter les informations de date / heure. Il fournit une granularité plus fine et une plage supérieure à la [CTime](../atl-mfc-shared/reference/ctime-class.md) classe. Le [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) classe représente le temps écoulé, telles que la différence entre deux `COleDateTime` objets.

Le `COleDateTime` et `COleDateTimeSpan` classes sont conçues pour être utilisé avec la `COleVariant` classe utilisée dans Automation. `COleDateTime` et `COleDateTimeSpan` sont également utiles en programmation de base de données MFC, mais ils peuvent être utilisés chaque fois que vous souhaitez manipuler les valeurs de date et d’heure. Bien que le `COleDateTime` classe a une plage de valeurs et de granularité plus fine que la `CTime` (classe), elle nécessite plus de stockage par objet à `CTime`. Il existe également des considérations particulières lorsque vous travaillez avec le type sous-jacent de la DATE. Consultez [le Type de DATE](../atl-mfc-shared/date-type.md) pour plus d’informations sur l’implémentation de DATE.

`COleDateTime` objets peuvent être utilisés pour représenter des dates comprises entre le 1er janvier 100 et le 31 décembre 9999. `COleDateTime` les objets sont valeurs à virgule flottante, dont la résolution de 1 milliseconde. `COleDateTime` est basé sur le type de données DATE, défini dans la documentation MFC sous [rubrique COleDateTime::opérateur DATE](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). L’implémentation réelle de DATE s’étend au-delà de ces limites. Le `COleDateTime` implémentation impose ces limites pour faciliter l’utilisation de la classe.

`COleDateTime` ne prend pas en charge les dates juliennes. Le calendrier grégorien est supposé remonter jusqu’au 1er janvier 100.

`COleDateTime` ignore l’heure d’été (DST). L’exemple de code suivant compare les deux méthodes de calcul d’un intervalle de temps qui dépasse la date de basculement de l’heure d’été : un à l’aide de la bibliothèque CRT et l’autre à l’aide `COleDateTime`. Heure d’été bascule, dans la plupart des pays, dans la deuxième semaine d’avril et le troisième en octobre.

La première méthode définit deux `CTime` objets, *time1* et *time2*, au 5 avril et le 6 avril respectivement, à l’aide des structures de type C standards `tm` et `time_t`. Le code affiche *time1* et *time2* et l’intervalle de temps entre eux.

La seconde méthode crée deux `COleDateTime` objets, `oletime1` et `oletime2`et leur affecte les mêmes dates en tant que *time1* et *time2*. Il affiche `oletime1` et `oletime2` et l’intervalle de temps entre eux.

La bibliothèque CRT calcule correctement une différence de 23 heures. `COleDateTimeSpan` calcule une différence de 24 heures.

Notez qu’une solution de contournement est utilisée à la fin de l’exemple pour afficher la date correctement à l’aide `COleDateTime::Format`. Consultez l’article de la Base de connaissances « bogue : plus échoue pour `COleDateTime` et `COleDateTimeSpan`» (Q167338).

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Date et heure](../atl-mfc-shared/date-and-time.md)

