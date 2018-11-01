---
title: FILETIME, structure
ms.date: 11/04/2016
f1_keywords:
- FILETIME
helpviewer_keywords:
- FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
ms.openlocfilehash: f70792b83637018e707b6ee48d1b169f28d46d71
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514931"
---
# <a name="filetime-structure"></a>FILETIME, structure

Le `FILETIME` structure est une valeur 64 bits représentant le nombre d’intervalles de 100 nanosecondes depuis le 1er janvier 1601.

## <a name="syntax"></a>Syntaxe

```
typedef struct _FILETIME {
    DWORD dwLowDateTime;   /* low 32 bits */
    DWORD dwHighDateTime;  /* high 32 bits */
} FILETIME, *PFILETIME, *LPFILETIME;
```

#### <a name="parameters"></a>Paramètres

*dwLowDateTime*<br/>
Spécifie le faible 32 bits de l’heure du fichier.

*FILETIME*<br/>
Spécifie la haute 32 bits de l’heure du fichier.

## <a name="requirements"></a>Configuration requise

**En-tête :** windef.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

