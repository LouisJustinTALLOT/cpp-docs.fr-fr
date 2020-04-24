---
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
ms.openlocfilehash: 15cf93d39057f0e235779d47cf24d920d80a807d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753495"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton, classe

La `CMFCRibbonUndoButton` classe implémente un bouton de liste d’abandon qui contient les commandes utilisateur les plus récentes. Les utilisateurs peuvent sélectionner une ou plusieurs des commandes les plus récentes de la liste d’abandon pour les refaire ou les défaire.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Construit un `CMFCRibbonUndoButton` nouvel objet en utilisant l’ID de commande que vous spécifiez, l’étiquette de texte et les images de la liste d’images de l’objet parent.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Ajoute une nouvelle action à la liste des actions.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Efface la liste d’action, qui est la liste d’abandon.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Détermine le nombre d’éléments qu’un utilisateur a sélectionnés dans la liste d’abandon.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Indique si l’objet contient un menu.|

## <a name="remarks"></a>Notes

La `CMFCRibbonUndoButton` classe utilise une pile pour représenter la liste des dépôts.

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCRibbonUndoButton` un objet de la classe, et ajouter une nouvelle action à la liste des actions. Cet extrait de code fait partie de [l’échantillon De gadgets ruban](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribbonundobutton.h

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction

Ajoute une nouvelle action à la liste des actions.

```cpp
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] L’étiquette d’action qui sera affichée dans la liste d’abandon.

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList

Efface la liste d’action, qui est la liste d’abandon.

```cpp
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton

Construit un `CMFCRibbonUndoButton` nouvel objet en utilisant l’ID de commande que vous spécifiez, l’étiquette de texte et les images de la liste d’images de l’objet parent.

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
[dans] Spécifie l’identifiant de commande.

*lpszText*<br/>
[dans] Spécifie l’étiquette de texte du bouton.

*nSmallImageIndex*<br/>
[dans] Index basé sur zéro dans la liste d’images de l’objet parent pour la petite image du bouton.

*nLargeImageIndex*<br/>
[dans] Index basé sur zéro dans la liste d’images de l’objet parent pour la grande image du bouton.

*hIcon (en)*<br/>
[dans] Une poignée à une icône que vous pouvez utiliser comme image d’un bouton.

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber

Détermine le nombre d’éléments qu’un utilisateur a sélectionnés dans la liste d’abandon.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments sélectionnés par un utilisateur.

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu

Indique si l’objet contient un menu.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours VRAI.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
