---
title: RgnData, Structure | Documents Microsoft
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
ms.openlocfilehash: 591c2dd65fdb9dde00f0ac1373c39affbe82da85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373506"
---
# <a name="rgndata-structure"></a>RGNDATA, structure
Le `RGNDATA` structure contient un en-tête et un tableau de rectangles qui composent une région. Ces rectangles, triées de haut en bas à gauche à droite, ne se chevauchent pas.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _RGNDATA { /* rgnd */  
    RGNDATAHEADER rdh;  
    char Buffer[1];  
} RGNDATA;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *RDH*  
 Spécifie un [RGNDATAHEADER](http://msdn.microsoft.com/library/windows/desktop/dd162941) structure. (Pour plus d’informations sur cette structure, consultez le Kit de développement Windows.) Les membres de cette structure, spécifient le type de région (qu’il soit rectangulaire ou trapézoïdal), le nombre de rectangles qui composent la région, la taille de la mémoire tampon qui contient les structures du rectangle, et ainsi de suite.  
  
 `Buffer`  
 Spécifie un tampon de taille arbitraire qui contient la [RECT](../../mfc/reference/rect-structure1.md) structures qui composent la région.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

