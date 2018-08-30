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
ms.openlocfilehash: 2c539feaac9cac5bca3a41868cc03379a63bf6bb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204357"
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
 *RDH*  
 Spécifie un [RGNDATAHEADER](/windows/desktop/api/wingdi/ns-wingdi-_rgndataheader) structure. (Pour plus d’informations sur cette structure, consultez le Kit de développement Windows.) Les membres de cette structure de spécifient le type de région (il s’agisse rectangulaire ou trapézoïdal), le nombre de rectangles qui composent la région, la taille de la mémoire tampon qui contient les structures de rectangle, et ainsi de suite.  
  
 *mémoire tampon*  
 Spécifie un tampon de taille arbitraire qui contient le [RECT](../../mfc/reference/rect-structure1.md) structures qui composent la région.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

