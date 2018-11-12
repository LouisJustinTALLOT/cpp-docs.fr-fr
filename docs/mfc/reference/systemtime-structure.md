---
title: SYSTEMTIME, structure
ms.date: 11/04/2016
f1_keywords:
- SYSTEMTIME
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
ms.openlocfilehash: b46482a9f4eb0165b72d74cb7d69e96e2a15e953
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559046"
---
# <a name="systemtime-structure"></a>SYSTEMTIME, structure

Le `SYSTEMTIME` structure représente une date et heure à l’aide des membres individuels pour le mois, jour, année, jour de la semaine, heure, minute, seconde et milliseconde.

## <a name="syntax"></a>Syntaxe

```
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME;
```

#### <a name="parameters"></a>Paramètres

*wYear*<br/>
L’année en cours.

*wMonth*<br/>
Le mois en cours ; Janvier est 1.

*wDayOfWeek*<br/>
Le jour actuel de la semaine. Dimanche est 0, lundi est 1 et ainsi de suite.

*wDay*<br/>
Le jour du mois actuel.

*wHour*<br/>
L’heure actuelle.

*wMinute*<br/>
La minute actuelle.

*wSecond*<br/>
La seconde actuelle.

*wMilliseconds*<br/>
Milliseconde en cours.

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** winbase.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

