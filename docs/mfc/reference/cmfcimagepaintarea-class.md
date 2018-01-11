---
title: Classe de CMFCImagePaintArea | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
dev_langs: C++
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f4af09ad1da91e3d59f82736ae9b240812069eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcimagepaintarea-class"></a>Classe de CMFCImagePaintArea
Fournit la zone d’image qui vous permet de modifier une image dans une boîte de dialogue Éditeur image.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Construit un objet `CMFCImagePaintArea`.|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCImagePaintArea::GetMode](#getmode)|Récupère le mode de dessin en cours.|  
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Définit l’image bitmap de la zone d’image.|  
|[CMFCImagePaintArea::SetColor](#setcolor)|Définit la couleur de dessin en cours.|  
|[CMFCImagePaintArea::SetMode](#setmode)|Définit le mode de dessin en cours.|  
  
### <a name="remarks"></a>Notes  
 Cette classe n’est pas destinée à être utilisée directement depuis votre code.  
  
 Le framework utilise cette classe pour afficher la zone d’image dans une boîte de dialogue Éditeur image. Pour plus d’informations sur la boîte de dialogue Éditeur image, consultez [CMFCImageEditorDialog classe](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCImagePaintArea` de classe, définissez actuel couleur de dessin, de définir le mode de dessin en cours et définir l’image bitmap de la zone d’image.  
  
 [!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afximagepaintarea.h  
  
##  <a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea  
 Construit un objet `CMFCImagePaintArea`.  
  
```  
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `pParentDlg`|Pointeur vers la boîte de dialogue qui est le parent de l’éditeur d’images.|  
  
##  <a name="getmode"></a>CMFCImagePaintArea::GetMode  
 Récupère le mode de dessin en cours.  
  
```  
IMAGE_EDIT_MODE GetMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) valeur qui spécifie le mode de dessin en cours.  
  
##  <a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap  
 Définit l’image bitmap de la zone d’image.  
  
```  
void SetBitmap(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `pBitmap`|La nouvelle image bitmap à afficher.|  
  
### <a name="remarks"></a>Notes  
 Si `pBitmap` est `NULL`, cette méthode définit la taille de la zone de peinture modifiable à zéro. Dans le cas contraire, il définit la taille de la zone modifiable de peinture à la taille de l’image bitmap fournis.  
  
##  <a name="setcolor"></a>CMFCImagePaintArea::SetColor  
 Définit la couleur de dessin en cours.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `color`|La nouvelle couleur de dessin.|  
  
### <a name="remarks"></a>Notes  
 Lorsque vous sélectionnez une couleur dans la barre d’outils image éditeur palette ou sélecteur de couleurs, l’infrastructure appelle cette méthode pour mettre à jour la couleur de dessin en cours. La couleur de dessin initiale est noire (un `COLORREF` la valeur 0).  
  
 La couleur de dessin est utilisée par la boîte de dialogue Éditeur image pour tous les modes de dessin à l’exception de `IMAGE_EDIT_MODE_COLOR`. Pour plus d’informations sur les modes de dessin, consultez [CMFCImagePaintArea::IMAGE_EDIT_MODE énumération](cmfcimagepaintarea-image-edit-mode-enumeration.md).  
  
##  <a name="setmode"></a>CMFCImagePaintArea::SetMode  
 Définit le mode de dessin en cours.  
  
```  
void SetMode(IMAGE_EDIT_MODE mode);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `mode`|Un [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) valeur qui spécifie le mode de dessin en cours.|  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md)
