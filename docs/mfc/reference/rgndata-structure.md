---
title: RgnData, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- RGNDATA
dev_langs:
- C++
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d40cd86cff4c3e58e88f9d17a551dc789bd1db4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398209"
---
# <a name="rgndata-structure"></a>RGNDATA, structure

Le `RGNDATA` structure contient un en-tête et un tableau de rectangles qui composent une région. Ces rectangles, trié de haut en bas à gauche à droite, ne se chevauchent pas.

## <a name="syntax"></a>Syntaxe

```
typedef struct _RGNDATA { /* rgnd */
    RGNDATAHEADER rdh;
    char Buffer[1];
} RGNDATA;
```

#### <a name="parameters"></a>Paramètres

*RDH*<br/>
Spécifie un [RGNDATAHEADER](/windows/desktop/api/wingdi/ns-wingdi-_rgndataheader) structure. (Pour plus d’informations sur cette structure, consultez le Kit de développement Windows.) Les membres de cette structure de spécifient le type de région (il s’agisse rectangulaire ou trapézoïdal), le nombre de rectangles qui composent la région, la taille de la mémoire tampon qui contient les structures de rectangle, et ainsi de suite.

*mémoire tampon*<br/>
Spécifie un tampon de taille arbitraire qui contient le [RECT](../../mfc/reference/rect-structure1.md) structures qui composent la région.

## <a name="requirements"></a>Configuration requise

**En-tête :** wingdi.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)<br/>
[CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

