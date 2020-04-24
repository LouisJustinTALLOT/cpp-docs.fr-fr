---
title: Classe CMFCImagePaintArea
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
ms.openlocfilehash: cd74d2418bb874553fbbafa637f527a7b84b73bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754279"
---
# <a name="cmfcimagepaintarea-class"></a>Classe CMFCImagePaintArea

Fournit la zone d’image que vous utilisez pour modifier une image dans une boîte de dialogue d’éditeur d’images.

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
|[CMFCImagePaintArea::GetMode](#getmode)|Récupère le mode de dessin actuel.|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Définit l’image de bitmap pour la zone d’image.|
|[CMFCImagePaintArea::SetColor](#setcolor)|Définit la couleur de dessin actuelle.|
|[CMFCImagePaintArea::SetMode](#setmode)|Définit le mode de dessin actuel.|

### <a name="remarks"></a>Notes

Cette classe n'est pas destinée à être utilisée directement à partir de votre code.

Le cadre utilise cette classe pour afficher la zone d’image dans une boîte de dialogue d’éditeur d’images. Pour plus d’informations sur la boîte de dialogue de l’éditeur d’images, voir [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCImagePaintArea` un objet de la classe, définir la couleur de dessin actuelle, définir le mode de dessin actuel, et définir l’image de bitmap pour la zone d’image.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afximagepaintarea.h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea

Construit un objet `CMFCImagePaintArea`.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pParentDlg*|[dans] Un pointeur à la boîte de dialogue qui est le parent de l’éditeur d’image.|

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a>CMFCImagePaintArea::GetMode

Récupère le mode de dessin actuel.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) qui spécifie le mode de dessin actuel.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap

Définit l’image de bitmap pour la zone d’image.

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pBitmap (en)*|[dans] La nouvelle image de bitmap à afficher.|

### <a name="remarks"></a>Notes

Si *pBitmap* est NULL, cette méthode définit la taille de la zone de peinture modifiable à zéro. Dans le cas contraire, il définit la taille de la zone de peinture modifiable à la taille de l’image de bitmap fournie.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a>CMFCImagePaintArea::SetColor

Définit la couleur de dessin actuelle.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*color*|[dans] La nouvelle couleur de dessin.|

### <a name="remarks"></a>Notes

Lorsque vous sélectionnez une couleur à partir de la barre de palette de l’éditeur d’images ou de la palette de couleur, le cadre appelle cette méthode pour mettre à jour la couleur de dessin actuelle. La couleur de dessin initiale est noire (une valeur COLORREF de 0).

La couleur de dessin est utilisée par la boîte de dialogue de l’éditeur d’images pour tous les modes de dessin, sauf pour IMAGE_EDIT_MODE_COLOR. Pour plus d’informations sur les modes de dessin, voir [CMFCImagePaintArea:IMAGE_EDIT_MODE Enumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md).

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a>CMFCImagePaintArea::SetMode

Définit le mode de dessin actuel.

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*Mode*|[dans] Une valeur [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) qui spécifie le mode de dessin actuel.|

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
