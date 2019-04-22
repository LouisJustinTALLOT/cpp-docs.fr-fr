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
ms.openlocfilehash: 39979d48eb7b0f7aba9dbe7bd42c2f91845af968
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781989"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup, classe

Le `CMFCRibbonButtonsGroup` classe vous permet d’organiser un ensemble de boutons de ruban dans un groupe. Tous les boutons du groupe sont directement adjacents horizontalement et placés dans une bordure.

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
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Retourne un pointeur vers le bouton qui se trouve à l’index spécifié.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Retourne le nombre de boutons dans le groupe.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Retourne la taille de l’image des images normales dans le groupe de ruban (remplace [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Retourne la taille normale de l’élément Ruban (remplace [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Rapports si le `CMFCRibbonButtonsGroup` objet contient des images de barre d’outils.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Dessine l’image appropriée pour un bouton spécifié, selon que le bouton est normal, en surbrillance ou désactivé.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Supprime tous les boutons de la `CMFCRibbonButtonsGroup` objet.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Assigne des images au groupe.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Définit le parent `CMFCRibbonCategory` de la `CMFCRibbonButtonsGroup` objet et tous les boutons qu’il contient (remplace [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Notes

Le groupe est dérivé de [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) et peuvent être manipulées comme une seule entité. Vous pouvez placer le groupe sur n’importe quel panneau ou un menu contextuel.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonButtonsGroup` . L’exemple montre comment construire un `CMFCRibbonButtonsGroup` de l’objet, assigner des images au groupe de boutons de ruban et ajoutez un bouton au groupe de boutons de ruban. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxribbonbuttonsgroup.h

##  <a name="addbutton"></a>  CMFCRibbonButtonsGroup::AddButton

Ajoute un bouton à un groupe.

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
[in] Pointeur vers un bouton Ajouter.

##  <a name="addbuttons"></a>  CMFCRibbonButtonsGroup::AddButtons

Ajoute une liste de boutons à un groupe.

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Paramètres

*lstButtons*<br/>
[in] Une liste de pointeurs vers les boutons que vous souhaitez ajouter.

##  <a name="cmfcribbonbuttonsgroup"></a>  CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Construit un objet `CMFCRibbonButtonsGroup`.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
[in] Spécifie un bouton pour ajouter à la nouvelle `CMFCRibbonButtonsGroup` objet.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getbutton"></a>  CMFCRibbonButtonsGroup::GetButton

Retourne un pointeur vers le bouton qui se trouve à l’index spécifié.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Paramètres

*i*<br/>
[in] Index de base zéro d’un bouton à retourner.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le bouton qui se trouve à l’index spécifié. NULL si l’index spécifié est hors limites.

### <a name="remarks"></a>Notes

##  <a name="getcount"></a>  CMFCRibbonButtonsGroup::GetCount

Retourne le nombre de boutons dans le groupe.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de boutons dans le groupe.

##  <a name="getimagesize"></a>  CMFCRibbonButtonsGroup::GetImageSize

Récupère la taille de l’image source de l’élément protégé `CMFCToolBarImages` membre `m_Images`.

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la taille de l’image source des images de barre d’outils, le cas échéant, ou un `CSize` égale à zéro dans le cas contraire.

### <a name="remarks"></a>Notes

##  <a name="getregularsize"></a>  CMFCRibbonButtonsGroup::GetRegularSize

Récupère la taille maximale possible de l’élément de groupe de ruban.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers le contexte de périphérique du groupe de ruban.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="hasimages"></a>  CMFCRibbonButtonsGroup::HasImages

Rapports si le `CMFCRibbonButtonsGroup` objet contient des images de barre d’outils.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément protégé `CMFCToolBarImages` membre `m_Images` contient des images, ou FALSE si pas.

### <a name="remarks"></a>Notes

##  <a name="ondrawimage"></a>  CMFCRibbonButtonsGroup::OnDrawImage

Dessine l’image appropriée pour un bouton spécifié, selon que le bouton est normal, en surbrillance ou désactivé.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers le contexte de périphérique de le `CMFCRibbonButtonsGroup` objet.

*rectImage*<br/>
[in] Le rectangle dans lequel dessiner l’image.

*pButton*<br/>
[in] Le bouton pour lequel dessiner l’image.

*nImageIndex*<br/>
[in] Index de l’image à dessiner sur le bouton (dans un des tableaux de trois images pour les boutons normales, en surbrillance ou désactivés).

### <a name="remarks"></a>Notes

##  <a name="removeall"></a>  CMFCRibbonButtonsGroup::RemoveAll

Supprime tous les boutons de la `CMFCRibbonButtonsGroup` objet.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

##  <a name="setimages"></a>  CMFCRibbonButtonsGroup::SetImages

Assigne des images au groupe de boutons de ruban.

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Paramètres

*pImages*<br/>
[in] Les images.

*pHotImages*<br/>
[in] Images interactives.

*pDisabledImages*<br/>
[in] Images désactivés.

### <a name="remarks"></a>Notes

Appelez `SetImages` avant d’ajouter des boutons à un groupe. Le nombre d’images doit être supérieur ou égal au nombre de boutons à ajouter au groupe.

> [!NOTE]
>  Images interactives sont des images qui sont affichent lorsque l’utilisateur pointe sur le bouton. Images désactivés sont des images qui sont affichent lorsque le bouton est désactivé.

##  <a name="setparentcategory"></a>  CMFCRibbonButtonsGroup::SetParentCategory

Définit le parent `CMFCRibbonCategory` de la `CMFCRibbonButtonsGroup` objet et tous les boutons qu’il contient.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Paramètres

*pCategory*<br/>
[in] Pointeur vers la catégorie parente à définir (les groupes à onglets dans les contrôles de ruban sont appelés des catégories).

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
