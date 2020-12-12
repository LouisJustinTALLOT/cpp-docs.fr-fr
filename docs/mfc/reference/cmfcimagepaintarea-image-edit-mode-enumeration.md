---
description: 'En savoir plus sur : énumération de CMFCImagePaintArea :: IMAGE_EDIT_MODE'
title: CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration
ms.date: 11/04/2016
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
ms.openlocfilehash: f28880d108be8fb4f2b14ede1a3cbd3c7dac9f2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265322"
---
# <a name="cmfcimagepaintareaimage_edit_mode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration

Spécifie un mode dessin que vous utilisez pour modifier une image dans une boîte de dialogue de l’éditeur d’images.

## <a name="syntax"></a>Syntaxe

```
enum IMAGE_EDIT_MODE
{
    IMAGE_EDIT_MODE_PEN = 0,
    IMAGE_EDIT_MODE_FILL,
    IMAGE_EDIT_MODE_LINE,
    IMAGE_EDIT_MODE_RECT,
    IMAGE_EDIT_MODE_ELLIPSE,
    IMAGE_EDIT_MODE_COLOR
};
```

## <a name="members"></a>Membres

|Nom|Description|
|-|-|
|IMAGE_EDIT_MODE_PEN|Utilisé pour dessiner des pixels individuels.|
|IMAGE_EDIT_MODE_FILL|Utilisé pour remplir toutes les zones adjacentes contenant la couleur à l’emplacement actuel du curseur.|
|IMAGE_EDIT_MODE_LINE|Utilisé pour dessiner une ligne.|
|IMAGE_EDIT_MODE_RECT|Utilisé pour dessiner un rectangle.|
|IMAGE_EDIT_MODE_ELLIPSE|Utilisé pour dessiner une ellipse.|
|IMAGE_EDIT_MODE_COLOR|Utilisé pour définir la couleur actuelle à la couleur à l’emplacement actuel du curseur.|

### <a name="remarks"></a>Notes

Les `CMFCImagePaintArea` `CMFCImageEditorDialog` classes et utilisent cette énumération pour définir le mode de dessin actuel. Le mode dessin et la couleur actuelle sont utilisés pour modifier la zone d’image dans une boîte de dialogue de l’éditeur d’images. Pour plus d’informations sur `CMFCImagePaintArea` et `CMFCImageEditorDialog` , consultez la classe [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md) et la [classe CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md).

Lorsque vous sélectionnez une couleur à partir d’une image à l’aide du mode de dessin IMAGE_EDIT_MODE_COLOR, l’infrastructure définit le mode de dessin actuel sur IMAGE_EDIT_MODE_PEN.

## <a name="requirements"></a>Spécifications

**En-tête :** afximagepaintarea. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImagePaintArea, classe](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md)
