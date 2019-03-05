---
title: Cmfcimagepaintarea, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: 37d975ace4d144cc6274b49a3406382f0fb300ee
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290741"
---
# <a name="cmfcimagepaintarea-class"></a>Cmfcimagepaintarea, classe

Fournit la zone d’image que vous utilisez pour modifier une image dans une image de boîte de dialogue Éditeur.

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
|[CMFCImagePaintArea::SetColor](#setcolor)|Définit la couleur de dessin actuelle.|
|[CMFCImagePaintArea::SetMode](#setmode)|Définit le mode de dessin en cours.|

### <a name="remarks"></a>Notes

Cette classe n’est pas destinée à être utilisée directement à partir de votre code.

Le framework utilise cette classe pour afficher la zone d’image dans une image de boîte de dialogue Éditeur. Pour plus d’informations sur l’image de boîte de dialogue Éditeur, consultez [CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCImagePaintArea` classe, définissez des cours couleur de dessin, de définir le mode de dessin en cours et de définir l’image bitmap de la zone d’image.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afximagepaintarea.h

##  <a name="cmfcimagepaintarea"></a>  CMFCImagePaintArea::CMFCImagePaintArea

Construit un objet `CMFCImagePaintArea`.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pParentDlg*|[in] Pointeur vers la boîte de dialogue qui est le parent de l’éditeur d’images.|

##  <a name="getmode"></a>  CMFCImagePaintArea::GetMode

Récupère le mode de dessin en cours.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Valeur de retour

Un [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) valeur qui spécifie le mode de dessin en cours.

##  <a name="setbitmap"></a>  CMFCImagePaintArea::SetBitmap

Définit l’image bitmap de la zone d’image.

```
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pBitmap*|[in] La nouvelle image bitmap à afficher.|

### <a name="remarks"></a>Notes

Si *pBitmap* est NULL, cette méthode définit la taille de la zone modifiable de peinture à zéro. Sinon, il définit la taille de la zone modifiable de peinture à la taille de l’image bitmap fournis.

##  <a name="setcolor"></a>  CMFCImagePaintArea::SetColor

Définit la couleur de dessin actuelle.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*color*|[in] La nouvelle couleur de dessin.|

### <a name="remarks"></a>Notes

Lorsque vous sélectionnez une couleur dans la barre de palette éditeur image ou un sélecteur de couleurs, l’infrastructure appelle cette méthode pour mettre à jour de la couleur de dessin actuelle. La couleur de dessin initiale est noire (valeur COLORREF 0).

La couleur de dessin est utilisée par la boîte de dialogue Éditeur image pour tous les modes dessins à l’exception de IMAGE_EDIT_MODE_COLOR. Pour plus d’informations sur les modes de dessin, consultez [cmfcimagepaintarea::image_edit_mode, énumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md).

##  <a name="setmode"></a>  CMFCImagePaintArea::SetMode

Définit le mode de dessin en cours.

```
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*mode*|[in] Un [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) valeur qui spécifie le mode de dessin en cours.|

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md)
