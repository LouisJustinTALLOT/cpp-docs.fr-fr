---
title: Structure BITMAP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAP
dev_langs:
- C++
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ddc4868d7cc3c094ad2bb81b5d9706a2b749553d
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339345"
---
# <a name="bitmap-structure"></a>Structure BITMAP
Le **BITMAP** structure définit la hauteur, largeur, format de couleur et les valeurs de bit d’une image bitmap logique **.**  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagBITMAP {  /* bm */  
    int bmType;  
    int bmWidth;  
    int bmHeight;  
    int bmWidthBytes;  
    BYTE bmPlanes;  
    BYTE bmBitsPixel;  
    LPVOID bmBits;  
} BITMAP;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bmType*  
 Spécifie le type d’image bitmap. Pour les bitmaps de logiques, ce membre doit être 0.  
  
 *bmWidth*  
 Spécifie la largeur de l’image bitmap en pixels. La largeur doit être supérieure à 0.  
  
 *bmHeight*  
 Spécifie la hauteur de l’image bitmap en lignes raster. La hauteur doit être supérieure à 0.  
  
 *bmWidthBytes*  
 Spécifie le nombre d’octets dans chaque ligne raster. Cette valeur doit être un nombre pair, car l’interface graphique (GDI) suppose que les valeurs de bit d’une image bitmap forment un tableau d’entiers de (2 octets). En d’autres termes, *bmWidthBytes* \* 8 doit être au prochain multiple de 16 supérieure ou égale à la valeur obtenue lorsque le *bmWidth* membre est multiplié par la *bmBitsPixel*  membre.  
  
 *bmPlanes*  
 Spécifie le nombre de plans de couleur de l’image bitmap.  
  
 *bmBitsPixel*  
 Spécifie le nombre de bits de couleur adjacent sur chaque plan nécessaire à la définition d’un pixel.  
  
 *bmBits*  
 Pointe vers l’emplacement des valeurs de bit de l’image bitmap. Le *bmBits* membre doit être un pointeur long désignant un tableau de valeurs de 1 octet.  
  
## <a name="remarks"></a>Notes  
 Les formats de bitmap actuellement utilisés sont monochrome et couleur. L’image bitmap monochrome utilise un format de 1 bit, 1-plan. Chaque analyse est un multiple de 16 bits.  
  
 Les analyses sont organisées comme suit pour une image bitmap monochrome de hauteur *n*:  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 Les pixels sur un appareil monochrome sont soit noir ou blanc. Si le bit correspondant dans la bitmap est 1, le pixel est activé (blanc). Si le bit correspondant dans l’image bitmap est 0, le pixel est désactivé (noir).  
  
 Tous les périphériques prennent en charge les bitmaps qui ont le jeu RC_BITBLT bit dans l’index RASTERCAPS de la [CDC::GetDeviceCaps](../../mfc/reference/cdc-class.md#getdevicecaps) fonction membre.  
  
 Chaque périphérique possède son propre format de couleur unique. Afin de transférer une image bitmap à partir d’un périphérique vers un autre, utilisez la [GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879) et [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) des fonctions de Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
