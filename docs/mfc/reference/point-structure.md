---
title: POINT, structure
ms.date: 10/12/2018
f1_keywords:
- POINT
- LPPOINT
helpviewer_keywords:
- LPPOINT structure [MFC]
- POINT structure [MFC]
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
ms.openlocfilehash: c53f250b714c66e74a12432b879cbc4bcc1fd88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646899"
---
# <a name="point-structure"></a>POINT, structure

Le `POINT` structure définit le x*-* coordonnées d’un point.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagPOINT {
    LONG x;
    LONG y;
} POINT;
```

#### <a name="parameters"></a>Paramètres

*x*<br/>
Spécifie la coordonnée x d’un point.

*y*<br/>
Spécifie la coordonnée y d’un point.

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#37](../../mfc/codesnippet/cpp/point-structure1_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** windef.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPoint, classe](../../atl-mfc-shared/reference/cpoint-class.md)
