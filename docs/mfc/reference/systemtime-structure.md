---
title: SYSTEMTIME, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6882a4e169b7efa67bef02ab5abee1276384e52f
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334537"
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

