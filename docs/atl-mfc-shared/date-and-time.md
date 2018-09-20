---
title: Date et heure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90317405f09695c57c907e94306623d5b3e2386d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419958"
---
# <a name="date-and-time"></a>Date et heure

MFC prend en charge plusieurs façons de travailler avec des dates et heures. Elles incluent notamment :

- Classes de temps à usage général. Le [CTime](../atl-mfc-shared/reference/ctime-class.md) et [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) classes encapsulent la plupart des fonctionnalités associées à la bibliothèque de temps à la norme ANSI, qui est déclarée dans le temps. H.

- Prise en charge de l’horloge système. Avec MFC version 3.0, la prise en charge a été ajoutée à `CTime` pour Win32 `SYSTEMTIME` et `FILETIME` des types de données.

- Prise en charge de l’automatisation [type de données DATE](../atl-mfc-shared/date-type.md). Date de prise en charge DATE et d’heure des valeurs de date/heure. Le [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) et [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) classes encapsulent cette fonctionnalité. Elles fonctionnent avec le [COleVariant](../mfc/reference/colevariant-class.md) classe à l’aide de la prise en charge Automation.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Date et heure : prise en charge de SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [Date et heure : prise en charge d’Automation](../atl-mfc-shared/date-and-time-automation-support.md)

- [Date et heure : prise en charge de base de données](../atl-mfc-shared/date-and-time-database-support.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)

