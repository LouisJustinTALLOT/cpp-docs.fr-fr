---
title: CMFCRibbonButtonsGroup, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: af5919ff2a72fc2aa1eeeb95fc93afbe9e743582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375286"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup, classe

La `CMFCRibbonButtonsGroup` classe vous permet d’organiser un ensemble de boutons ruban dans un groupe. Tous les boutons du groupe sont directement adjacents horizontalement et placés dans une bordure.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Construit un objet `CMFCRibbonButtonsGroup`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Ajoute un bouton à un groupe.|
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Ajoute une liste de boutons à un groupe.|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Retourne un pointeur sur le bouton qui se trouve à un index spécifié.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Retourne le nombre de boutons dans le groupe.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Retourne la taille de l’image des images normales dans le groupe de ruban (remplace [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Retourne la taille régulière de l’élément ruban (remplace [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Indique si `CMFCRibbonButtonsGroup` l’objet contient des images de barre d’outils.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Dessine l’image appropriée pour un bouton spécifié, selon que le bouton est normal, surligné ou désactivé.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Supprime tous les boutons `CMFCRibbonButtonsGroup` de l’objet.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Assigne des images au groupe.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Définit le `CMFCRibbonCategory` parent `CMFCRibbonButtonsGroup` de l’objet et tous les boutons à l’intérieur (remplace [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Notes

Le groupe est dérivé de [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) et peut être manipulé en tant qu’entité unique. Vous pouvez positionner le groupe sur n’importe quel panneau ou menu popup.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonButtonsGroup` . L’exemple montre comment `CMFCRibbonButtonsGroup` construire un objet, attribuer des images au groupe de boutons ruban, et ajouter un bouton au groupe de boutons ruban. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribbonbuttonsgroup.h

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFCRibbonButtonsGroup::AddButton

Ajoute un bouton à un groupe.

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
[dans] Un pointeur à un bouton à ajouter.

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFCRibbonButtonsGroup::AddButtons

Ajoute une liste de boutons à un groupe.

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Paramètres

*lstButtons*<br/>
[dans] Une liste de pointeurs sur les boutons que vous souhaitez ajouter.

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Construit un objet `CMFCRibbonButtonsGroup`.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
[dans] Spécifie un bouton à `CMFCRibbonButtonsGroup` ajouter à l’objet nouvellement créé.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFCRibbonButtonsGroup::GetButton

Retourne un pointeur sur le bouton qui se trouve à un index spécifié.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Paramètres

*Ⅰ*<br/>
[dans] Un index à base nulle d’un bouton à retourner.

### <a name="return-value"></a>Valeur de retour

Un pointeur sur le bouton qui se trouve à l’index spécifié. NULL si l’indice spécifié est hors de portée.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFCRibbonButtonsGroup::GetCount

Retourne le nombre de boutons dans le groupe.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de boutons dans le groupe.

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFCRibbonButtonsGroup::GetImageSize

Récupère la taille de l’image source du membre `CMFCToolBarImages` `m_Images`protégé .

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la taille de l’image source des images `CSize` de la barre d’outils, le cas échéant, ou un de zéro sinon.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonButtonsGroup::GetRegularSize

Récupère la taille maximale possible de l’élément du groupe de ruban.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur sur le contexte de l’appareil du groupe de ruban.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFCRibbonButtonsGroup::HasImages

Indique si `CMFCRibbonButtonsGroup` l’objet contient des images de barre d’outils.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si `CMFCToolBarImages` `m_Images` le membre protégé contient des images, ou FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFCRibbonButtonsGroup::OnDrawImage

Dessine l’image appropriée pour un bouton spécifié, selon que le bouton est normal, surligné ou désactivé.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur sur le `CMFCRibbonButtonsGroup` contexte de l’appareil de l’objet.

*rectImage*<br/>
[dans] Le rectangle dans lequel dessiner l’image.

*pButton*<br/>
[dans] Le bouton pour lequel dessiner l’image.

*nImageIndex*<br/>
[dans] L’index de l’image pour dessiner sur le bouton (dans l’un des trois tableaux d’images pour les boutons normaux, surlignés ou désactivés).

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFCRibbonButtonsGroup::RemoveAll

Supprime tous les boutons `CMFCRibbonButtonsGroup` de l’objet.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFCRibbonButtonsGroup::SetImages

Attribue des images au groupe de boutons ruban.

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Paramètres

*pImages (en)*<br/>
[dans] Images régulières.

*pHotImages (en)*<br/>
[dans] Images chaudes.

*pDisabledImages*<br/>
[dans] Images désactivées.

### <a name="remarks"></a>Notes

Appelez `SetImages` avant d’ajouter des boutons à un groupe. Le nombre d’images doit être plus ou égal au nombre de boutons à ajouter au groupe.

> [!NOTE]
> Les images chaudes sont des images qui s’affichent lorsque l’utilisateur plane sur le bouton. Les images désactivées sont des images qui s’affichent lorsque le bouton est désactivé.

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonButtonsGroup::SetParentCategory

Définit le `CMFCRibbonCategory` parent `CMFCRibbonButtonsGroup` de l’objet et tous les boutons à l’intérieur.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Paramètres

*pCatégory*<br/>
[dans] Pointeur vers la catégorie des parents à définir (les groupes tabbed dans les contrôles de ruban sont appelés catégories).

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
