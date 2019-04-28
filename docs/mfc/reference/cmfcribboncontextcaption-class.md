---
title: Cmfcribboncontextcaption, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
ms.openlocfilehash: 26cc509db55bc95688123a7c6e673dcfc87c975b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237308"
---
# <a name="cmfcribboncontextcaption-class"></a>Cmfcribboncontextcaption, classe

Implémente une légende colorée qui apparaît en haut d'une catégorie de ruban ou d'une catégorie de contexte.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Retourne la couleur de la légende.|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|

## <a name="remarks"></a>Notes

Cette classe ne peut pas être instanciée directement. Le [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) utilise cette classe en interne pour ajouter une couleur aux catégories de ruban.

Pour définir la couleur des catégories de ruban, appelez [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Pour définir la couleur des catégories de contexte, appelez [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxRibbonBar.h

##  <a name="getcolor"></a>  CMFCRibbonContextCaption::GetColor

Retourne la couleur d’arrière-plan de la légende.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur retournée peut être une des valeurs énumérées suivantes :

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>Notes

La couleur de la légende peut être définie en appelant [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) ou [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

##  <a name="getrighttabx"></a>  CMFCRibbonContextCaption::GetRightTabX

Récupère la position du bord droit de l’onglet du ruban de la catégorie.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de X droite du rectangle englobant de la `CMFCRibbonCategory` onglet de ruban de l’objet ou la valeur -1 si l’onglet est tronqué.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory, classe](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)
