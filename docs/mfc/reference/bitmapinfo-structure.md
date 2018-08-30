---
title: Bitmapinfo, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAPINFO
dev_langs:
- C++
helpviewer_keywords:
- BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bc5adbb62e70a012d9dff4f9a390a46476aaa36
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200254"
---
# <a name="bitmapinfo-structure"></a>BITMAPINFO, structure
Le `BITMAPINFO` structure définit les dimensions et les informations de couleur d’une bitmap indépendante du périphérique de Windows (DIB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bmiHeader*  
 Spécifie un [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) structure qui contient des informations sur les dimensions et le format de couleur d’une bitmap indépendante du périphérique.  
  
 *bmiColors*  
 Spécifie un tableau de [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) ou les types de données de valeur DWORD qui définissent les couleurs dans l’image bitmap.  
  
## <a name="remarks"></a>Notes  
 Une bitmap indépendante du périphérique se compose de deux parties distinctes : une `BITMAPINFO` structure qui décrit les dimensions et les couleurs de l’image bitmap et un tableau d’octets qui spécifient les pixels dans l’image bitmap. Les bits contenus dans le tableau sont regroupées, mais chaque ligne de numérisation doit être rempli de zéros de fin sur une **LONG** limite. Si la hauteur est un nombre positive, l’origine de l’image bitmap est l’angle inférieur gauche. Si la hauteur est négative, l’origine est l’angle supérieur gauche.  
  
 Un *bitmap compressé* est un bitmap où le tableau d’octets suit immédiatement la `BITMAPINFO` structure. Bitmaps compressés sont référencés par un pointeur unique.  
  
 Pour plus d’informations sur la `BITMAPINFO` structure et les valeurs appropriées pour les membres de la `BITMAPINFOHEADER` et `RGBQUAD` structures, consultez les rubriques suivantes dans la documentation du SDK Windows.  
  
- [Bitmapinfo, structure](/windows/desktop/api/wingdi/ns-wingdi-tagbitmapinfo)  
  
- [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) structure  
  
- [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) structure  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)

