---
description: 'En savoir plus sur : classe CMFCImagePaintArea'
title: CMFCImagePaintArea, classe
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
ms.openlocfilehash: c12a85c05686dcde24560b5ecc69cc68de07aa48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265348"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea, classe

Fournit la zone d’image que vous utilisez pour modifier une image dans une boîte de dialogue de l’éditeur d’images.

## <a name="syntax"></a>Syntaxe

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Construit un objet `CMFCImagePaintArea`.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[CMFCImagePaintArea::GetMode](#getmode)|Récupère le mode de dessin actuel.|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Définit l’image bitmap pour la zone d’image.|
|[CMFCImagePaintArea :: SetColor](#setcolor)|Définit la couleur de dessin actuelle.|
|[CMFCImagePaintArea::SetMode](#setmode)|Définit le mode de dessin actuel.|

### <a name="remarks"></a>Notes

Cette classe n'est pas destinée à être utilisée directement à partir de votre code.

L’infrastructure utilise cette classe pour afficher la zone d’image dans une boîte de dialogue de l’éditeur d’images. Pour plus d’informations sur la boîte de dialogue Éditeur d’images, consultez [CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCImagePaintArea` classe, définir la couleur de dessin actuelle, définir le mode de dessin actuel et définir l’image bitmap pour la zone d’image.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afximagepaintarea. h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a> CMFCImagePaintArea::CMFCImagePaintArea

Construit un objet `CMFCImagePaintArea`.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Paramètres

*pParentDlg*\
dans Pointeur vers la boîte de dialogue qui est le parent de l’éditeur d’images.

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a> CMFCImagePaintArea::GetMode

Récupère le mode de dessin actuel.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) qui spécifie le mode de dessin actuel.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a> CMFCImagePaintArea::SetBitmap

Définit l’image bitmap pour la zone d’image.

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

*pBitmap*\
dans Nouvelle image bitmap à afficher.

### <a name="remarks"></a>Notes

Si *pBitmap* a la valeur null, cette méthode définit la taille de la zone de peinture modifiable sur zéro. Dans le cas contraire, elle définit la taille de la zone de peinture modifiable sur la taille de l’image bitmap fournie.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a> CMFCImagePaintArea :: SetColor

Définit la couleur de dessin actuelle.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*\
dans Nouvelle couleur de dessin.

### <a name="remarks"></a>Notes

Lorsque vous sélectionnez une couleur à partir de la barre de palette ou du sélecteur de couleurs de l’éditeur d’images, l’infrastructure appelle cette méthode pour mettre à jour la couleur de dessin actuelle. La couleur de dessin initiale est le noir (valeur COLORREF égale à 0).

La couleur de dessin est utilisée par la boîte de dialogue Éditeur d’images pour tous les modes de dessin, à l’exception de IMAGE_EDIT_MODE_COLOR. Pour plus d’informations sur les modes de dessin, consultez l' [énumération CMFCImagePaintArea :: IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md).

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a> CMFCImagePaintArea::SetMode

Définit le mode de dessin actuel.

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Paramètres

*mode*\
dans Valeur [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) qui spécifie le mode de dessin actuel.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md)
