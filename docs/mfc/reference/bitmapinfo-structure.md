---
title: BITMAPINFO (Structure) | Documents Microsoft
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
ms.openlocfilehash: e061802cbcd8926a146e5765cc9ecfd9bf917295
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348151"
---
# <a name="bitmapinfo-structure"></a>BITMAPINFO, structure
Le `BITMAPINFO` structure définit les dimensions et les informations de couleur pour une image bitmap indépendante du périphérique de Windows (DIB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bmiHeader`  
 Spécifie un [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) structure qui contient des informations sur les dimensions et le format de couleur d’une image bitmap indépendante du périphérique.  
  
 `bmiColors`  
 Spécifie un tableau de [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) ou `DWORD` des types de données qui définissent les couleurs dans l’image bitmap.  
  
## <a name="remarks"></a>Notes  
 Une image bitmap indépendante du périphérique se compose de deux parties distinctes : une `BITMAPINFO` structure qui décrit les dimensions et les couleurs de l’image bitmap et un tableau d’octets qui spécifient les pixels de la bitmap. Les bits du tableau sont regroupées, mais chaque ligne d’analyse doit être complétée par des zéros de fin une `LONG` limite. Si la hauteur est un nombre positive, l’origine de l’image bitmap est l’angle inférieur gauche. Si la hauteur est négative, l’origine sont l’angle supérieur gauche.  
  
 A *bitmap compressé* est un bitmap dans laquelle le tableau d’octets suit immédiatement la `BITMAPINFO` structure. Bitmaps compressés sont référencés par un pointeur unique.  
  
 Pour plus d’informations sur la `BITMAPINFO` de la structure et les valeurs appropriées pour les membres de la `BITMAPINFOHEADER` et `RGBQUAD` structures, consultez les rubriques suivantes dans la documentation du Kit de développement logiciel Windows.  
  
- [BITMAPINFO (structure)](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
- [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) structure  
  
- [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) structure  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)

