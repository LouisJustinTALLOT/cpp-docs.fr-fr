---
title: RECT, structure
ms.date: 11/04/2016
f1_keywords:
- LPRECT
- RECT
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
ms.openlocfilehash: 1cb997fc0f1ec89eabf5e4d2c2c5ccb15e3bafec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549008"
---
# <a name="rect-structure"></a>RECT, structure

Le `RECT` structure définit les coordonnées des angles supérieur gauche et inférieur droit d’un rectangle.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagRECT {
    LONG left;
    LONG top;
    LONG right;
    LONG bottom;
} RECT;
```

## <a name="members"></a>Membres

`left`<br/>
Spécifie la coordonnée x du coin supérieur gauche d’un rectangle.

`top`<br/>
Spécifie la coordonnée y du coin supérieur gauche d’un rectangle.

`right`<br/>
Spécifie la coordonnée x du coin inférieur droit d’un rectangle.

`bottom`<br/>
Spécifie la coordonnée y du coin inférieur droit d’un rectangle.

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** windef.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRect, classe](../../atl-mfc-shared/reference/crect-class.md)
