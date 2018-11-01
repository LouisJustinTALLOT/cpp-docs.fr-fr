---
title: 'Mise en forme des valeurs de temps : Classes à usage général'
ms.date: 11/04/2016
helpviewer_keywords:
- dates, calculating intervals
- elapsed time, string representation
- time [C++], formatting
- formatting [C++], time
ms.assetid: 7fcfee24-f874-4a4d-95b3-adc19a0f2df0
ms.openlocfilehash: 48290adbc3e0e7f3cbe9a5a8e0569a5b61833e8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478661"
---
# <a name="formatting-time-values-general-purpose-classes"></a>Mise en forme des valeurs de temps : Classes à usage général

La procédure suivante montre comment formater les valeurs d’heure.

#### <a name="to-format-a-string-representation-of-a-time-or-elapsed-time"></a>Pour mettre en forme une chaîne représentant une heure ou le temps écoulé

Utilisez le `Format` fonction membre à partir d’un le [CTime](../atl-mfc-shared/reference/ctime-class.md) ou [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) classes pour créer un caractère représentation de chaîne de l’heure ou le temps écoulé, comme indiqué dans l’exemple suivant.

   [!code-cpp[NVC_ATLMFC_Utilities#175](../atl-mfc-shared/codesnippet/cpp/formatting-time-values-general-purpose-classes_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Date générale et la programmation de temps dans MFC](../atl-mfc-shared/date-and-time.md)

- [Utilisation de SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [Prise en charge de l’Automation de date et de programmation](../atl-mfc-shared/date-and-time-automation-support.md)

