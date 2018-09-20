---
title: POINT, Structure1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- POINT
- LPPOINT
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure [MFC]
- POINT structure [MFC]
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82955bb42ae68cb7f07fb89be94a7fcf424ee81c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416095"
---
# <a name="point-structure1"></a>POINT, Structure1

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
