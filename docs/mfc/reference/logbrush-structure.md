---
title: LOGBRUSH (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGBRUSH
dev_langs:
- C++
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e02c156619e4ca36d268870c70ba783c41a352d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375208"
---
# <a name="logbrush-structure"></a>LOGBRUSH, structure
Le `LOGBRUSH` structure définit le style, la couleur et le modèle d’un pinceau physique. Il est utilisé par Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) et [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) fonctions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tag LOGBRUSH { /* lb */  
    UINT lbStyle;  
    COLORREF lbColor;  
    LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `lbStyle`  
 Spécifie le style de pinceau. Le `lbStyle` membre doit être un des styles suivants :  
  
- **BS_DIBPATTERN** un pinceau de modèle défini par une spécification le bitmap indépendante du périphérique (DIB). Si `lbStyle` est **BS_DIBPATTERN**, le **lbHatch** membre contient un handle vers un fichier DIB compressé.  
  
- **BS_DIBPATTERNPT** un pinceau de modèle défini par une spécification le bitmap indépendante du périphérique (DIB). Si `lbStyle` est **BS_DIBPATTERNPT**, le **lbHatch** membre contient un pointeur vers un fichier DIB compressé.  
  
- **BS_HATCHED** issus du pinceau.  
  
- **BS_HOLLOW** creuse pinceau.  
  
- **BS_NULL** identique **BS_HOLLOW**.  
  
- **BS_PATTERN** pinceau défini par une image bitmap de mémoire de modèle.  
  
- **BS_SOLID** pinceau plein.  
  
 `lbColor`  
 Spécifie la couleur dans laquelle le pinceau doit être dessiné. Si `lbStyle` est la **BS_HOLLOW** ou **BS_PATTERN** style, **lbColor** est ignoré. Si `lbStyle` est **BS_DIBPATTERN** ou **BS_DIBPATTERNBT**, le mot de poids faible de **lbColor** Spécifie si le **bmiColors**membres de la [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) structure contiennent explicite rouge, vert, bleu () ou les valeurs RVB index dans la palette logique actuellement réalisée. Le **lbColor** membre doit être une des valeurs suivantes :  
  
- **DIB_PAL_COLORS** la table des couleurs se compose d’un tableau d’index 16 bits dans la palette logique actuellement réalisée.  
  
- **DIB_RGB_COLORS** la table des couleurs contient des valeurs RVB littérales.  
  
 *lbHatch*  
 Spécifie un style de hachurage. La signification varie selon le style de pinceau défini par `lbStyle`. Si `lbStyle` est **BS_DIBPATTERN**, le **lbHatch** membre contient un handle vers un fichier DIB compressé. Si `lbStyle` est **BS_DIBPATTERNPT**, le **lbHatch** membre contient un pointeur vers un fichier DIB compressé. Si `lbStyle` est **BS_HATCHED**, le **lbHatch** membre spécifie l’orientation des lignes utilisées pour créer le hachurage. Il peut prendre l’une des valeurs suivantes :  
  
- `HS_BDIAGONAL` Un hachurage de 45 degrés vers le haut, de gauche à droite  
  
- `HS_CROSS` Hachurage horizontal et vertical  
  
- `HS_DIAGCROSS` hachurage de 45 degrés  
  
- `HS_FDIAGONAL` Un hachurage de 45 degrés vers le bas, de gauche à droite  
  
- `HS_HORIZONTAL` Hachurage horizontal  
  
- `HS_VERTICAL` Hachage vertical  
  
 Si `lbStyle` est **BS_PATTERN**, **lbHatch** est un handle de la bitmap qui définit le modèle. Si `lbStyle` est **BS_SOLID** ou **BS_HOLLOW**, **lbHatch** est ignoré.  
  
## <a name="remarks"></a>Notes  
 Bien que **lbColor** contrôle la couleur de premier plan d’un pinceau de hachurage, le [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) et [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) fonctions contrôlent la couleur d’arrière-plan.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** wingdi.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

