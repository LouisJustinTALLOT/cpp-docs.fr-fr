---
title: Cmfcribbonundobutton, classe
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
ms.openlocfilehash: cd657ac035c004e7aa9bfcd2f6dbd2f3c90da80c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776464"
---
# <a name="cmfcribbonundobutton-class"></a>Cmfcribbonundobutton, classe

Le `CMFCRibbonUndoButton` classe implémente un bouton de liste déroulante qui contient les commandes utilisateur plus récente. Les utilisateurs peuvent sélectionner un ou plusieurs des commandes plus récente dans la liste déroulante de restauration par progression ou les annuler.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Construit un nouvel `CMFCRibbonUndoButton` objet à l’aide de l’ID de commande que vous spécifiez, étiquette de texte et des images à partir de la liste d’images de l’objet parent.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Ajoute une nouvelle action à la liste d’actions.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Efface la liste d’actions, qui est la liste déroulante.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Détermine le nombre d’éléments dont un utilisateur a sélectionné dans la liste déroulante.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Indique si l’objet contient un menu.|

## <a name="remarks"></a>Notes

Le `CMFCRibbonUndoButton` classe utilise une pile pour représenter la liste déroulante.

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCRibbonUndoButton` classe et ajoutez une nouvelle action à la liste des actions. Cet extrait de code fait partie de la [exemples de Gadgets de ruban](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxribbonundobutton.h

##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction

Ajoute une nouvelle action à la liste d’actions.

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[in] L’étiquette d’action qui s’affichera dans la liste déroulante.

##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList

Efface la liste d’actions, qui est la liste déroulante.

```
void CleanUpUndoList();
```

##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton

Construit un nouvel `CMFCRibbonUndoButton` objet à l’aide de l’ID de commande que vous spécifiez, étiquette de texte et des images à partir de la liste d’images de l’objet parent.

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
[in] Spécifie l’identificateur de commande.

*lpszText*<br/>
[in] Spécifie l’étiquette de texte du bouton.

*nSmallImageIndex*<br/>
[in] Index de base zéro dans la liste d’images de l’objet parent pour l’image du bouton petit.

*nLargeImageIndex*<br/>
[in] Index de base zéro dans la liste d’images de l’objet parent pour le d’image de grande taille du bouton.

*hIcon*<br/>
[in] Un handle d’une icône que vous pouvez utiliser en tant qu’image d’un bouton.

##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber

Détermine le nombre d’éléments dont un utilisateur a sélectionné dans la liste déroulante.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments sélectionné par un utilisateur.

##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu

Indique si l’objet contient un menu.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Valeur de retour

Renvoie toujours TRUE.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Cmfcribbongallery, classe](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[Cmfcribbonbutton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
