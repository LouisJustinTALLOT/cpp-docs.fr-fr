---
title: Cmfcimagepaintarea::image_edit_mode, énumeration | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
dev_langs:
- C++
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 913a87383e617f331043751c4e3089acac744c7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374642"
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration

Spécifie un mode de dessin qui vous permet de modifier une image dans une image de boîte de dialogue Éditeur.

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

|||
|-|-|
|Nom|Description|
|IMAGE_EDIT_MODE_PEN|Utilisé pour dessiner les pixels individuels.|
|IMAGE_EDIT_MODE_FILL|Utilisé pour remplir toutes les zones adjacentes qui contiennent la couleur à l’emplacement du curseur.|
|IMAGE_EDIT_MODE_LINE|Utilisé pour dessiner une ligne.|
|IMAGE_EDIT_MODE_RECT|Utilisé pour dessiner un rectangle.|
|IMAGE_EDIT_MODE_ELLIPSE|Utilisé pour dessiner une ellipse.|
|IMAGE_EDIT_MODE_COLOR|Utilisé pour définir la couleur actuelle à la couleur à l’emplacement du curseur.|

### <a name="remarks"></a>Notes

Le `CMFCImagePaintArea` et `CMFCImageEditorDialog` classes utilisent cette énumération pour définir le mode de dessin en cours. Le mode de dessin et de la couleur actuelle sont utilisés pour modifier la zone d’image dans une image de boîte de dialogue Éditeur. Pour plus d’informations sur `CMFCImagePaintArea` et `CMFCImageEditorDialog`, consultez [cmfcimagepaintarea, classe](../../mfc/reference/cmfcimagepaintarea-class.md) et [CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md).

Lorsque vous sélectionnez une couleur à partir d’une image en utilisant le mode de dessin IMAGE_EDIT_MODE_COLOR, le framework définit le mode de dessin actuel à IMAGE_EDIT_MODE_PEN.

## <a name="requirements"></a>Configuration requise

**En-tête :** afximagepaintarea.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImagePaintArea, classe](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md)
