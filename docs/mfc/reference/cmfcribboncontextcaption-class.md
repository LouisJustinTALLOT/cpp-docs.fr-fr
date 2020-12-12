---
description: 'En savoir plus sur : classe CMFCRibbonContextCaption'
title: CMFCRibbonContextCaption, classe
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
ms.openlocfilehash: fa4134b89055274e4f44bef1150518207e06143e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293623"
---
# <a name="cmfcribboncontextcaption-class"></a>CMFCRibbonContextCaption, classe

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
|`CMFCRibbonContextCaption::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|

## <a name="remarks"></a>Notes

Cette classe ne peut pas être instanciée directement. La classe de [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) utilise cette classe en interne pour ajouter de la couleur aux catégories du ruban.

Pour définir la couleur des catégories de ruban, appelez [CMFCRibbonCategory :: SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Pour définir la couleur des catégories de contexte, appelez [CMFCRibbonBar :: AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxRibbonBar. h

## <a name="cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a> CMFCRibbonContextCaption :: GetColor

Retourne la couleur d’arrière-plan de la légende.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

La valeur retournée peut être l’une des valeurs énumérées suivantes :

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>Notes

La couleur de la légende peut être définie en appelant [CMFCRibbonCategory :: SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) ou [CMFCRibbonBar :: AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a> CMFCRibbonContextCaption::GetRightTabX

Récupère la position du bord droit de l’onglet de ruban de la catégorie.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur X de droite du rectangle englobant de l’onglet de ruban de l' `CMFCRibbonCategory` objet, ou la valeur-1 si l’onglet est tronqué.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory, classe](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)
