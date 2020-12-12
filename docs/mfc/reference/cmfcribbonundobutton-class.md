---
description: 'En savoir plus sur : classe CMFCRibbonUndoButton'
title: CMFCRibbonUndoButton, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: 8bfc02b61160a5f11a6913736c5dc784c4d00ce4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264932"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton, classe

La `CMFCRibbonUndoButton` classe implémente un bouton de liste déroulante qui contient les commandes utilisateur les plus récentes. Les utilisateurs peuvent sélectionner une ou plusieurs des commandes les plus récentes dans la liste déroulante pour les rétablir ou les annuler.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Construit un nouvel objet à l' `CMFCRibbonUndoButton` aide de l’ID de commande que vous spécifiez, de l’étiquette de texte et des images à partir de la liste d’images de l’objet parent.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Ajoute une nouvelle action à la liste d’actions.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Efface la liste d’actions, qui est la liste déroulante.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Détermine le nombre d’éléments qu’un utilisateur a sélectionnés dans la liste déroulante.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Indique si l’objet contient un menu.|

## <a name="remarks"></a>Notes

La `CMFCRibbonUndoButton` classe utilise une pile pour représenter la liste déroulante.

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCRibbonUndoButton` classe et ajouter une nouvelle action à la liste d’actions. Cet extrait de code fait partie de l' [exemple de gadgets de ruban](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxribbonundobutton. h

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a> CMFCRibbonUndoButton::AddUndoAction

Ajoute une nouvelle action à la liste d’actions.

```cpp
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Étiquette d’action qui s’affichera dans la liste déroulante.

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a> CMFCRibbonUndoButton::CleanUpUndoList

Efface la liste d’actions, qui est la liste déroulante.

```cpp
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a> CMFCRibbonUndoButton::CMFCRibbonUndoButton

Construit un nouvel objet à l' `CMFCRibbonUndoButton` aide de l’ID de commande que vous spécifiez, de l’étiquette de texte et des images à partir de la liste d’images de l’objet parent.

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
dans Spécifie l’identificateur de commande.

*lpszText*<br/>
dans Spécifie l’étiquette de texte du bouton.

*nSmallImageIndex*<br/>
dans Index de base zéro dans la liste d’images de l’objet parent pour la petite image du bouton.

*nLargeImageIndex*<br/>
dans Index de base zéro dans la liste d’images de l’objet parent pour l’image de grande taille du bouton.

*hIcon*<br/>
dans Handle vers une icône que vous pouvez utiliser comme image d’un bouton.

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a> CMFCRibbonUndoButton::GetActionNumber

Détermine le nombre d’éléments qu’un utilisateur a sélectionnés dans la liste déroulante.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments sélectionnés par un utilisateur.

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a> CMFCRibbonUndoButton::HasMenu

Indique si l’objet contient un menu.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Cmfcribbongallery,, classe](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
