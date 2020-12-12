---
description: 'En savoir plus sur : classe Cmfcribbonbuttonsgroup,'
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
ms.openlocfilehash: 0b86ce6ff21bd36daaac9d68ce511ae395141170
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293824"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup, classe

La `CMFCRibbonButtonsGroup` classe vous permet d’organiser un ensemble de boutons de ruban dans un groupe. Tous les boutons du groupe sont directement adjacents horizontalement et placés dans une bordure.

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
|[Cmfcribbonbuttonsgroup, :: AddButton](#addbutton)|Ajoute un bouton à un groupe.|
|[Cmfcribbonbuttonsgroup, :: AddButtons](#addbuttons)|Ajoute une liste de boutons à un groupe.|
|[Cmfcribbonbuttonsgroup, :: GetButton](#getbutton)|Retourne un pointeur vers le bouton situé à un index spécifié.|
|[Cmfcribbonbuttonsgroup, :: GetCount](#getcount)|Retourne le nombre de boutons dans le groupe.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Retourne la taille de l’image des images normales dans le groupe du ruban (Substitue [CMFCRibbonBaseElement :: GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Retourne la taille normale de l’élément de ruban (Substitue [CMFCRibbonBaseElement :: GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Signale si l' `CMFCRibbonButtonsGroup` objet contient des images de barre d’outils.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Dessine l’image appropriée pour un bouton spécifié, selon que le bouton est normal, mis en surbrillance ou désactivé.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Supprime tous les boutons de l' `CMFCRibbonButtonsGroup` objet.|
|[Cmfcribbonbuttonsgroup, :: SetImages](#setimages)|Attribue des images au groupe.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Définit le parent `CMFCRibbonCategory` de l' `CMFCRibbonButtonsGroup` objet et tous les boutons qu’il contient (Substitue [CMFCRibbonBaseElement :: SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Notes

Le groupe est dérivé de [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) et peut être manipulé comme une entité unique. Vous pouvez positionner le groupe dans n’importe quel panneau ou menu contextuel.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonButtonsGroup` . L’exemple montre comment construire un `CMFCRibbonButtonsGroup` objet, assigner des images au groupe de boutons du ruban et ajouter un bouton au groupe de boutons du ruban. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxribbonbuttonsgroup. h

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a> Cmfcribbonbuttonsgroup, :: AddButton

Ajoute un bouton à un groupe.

```cpp
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
dans Pointeur vers un bouton à ajouter.

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a> Cmfcribbonbuttonsgroup, :: AddButtons

Ajoute une liste de boutons à un groupe.

```cpp
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Paramètres

*lstButtons*<br/>
dans Liste de pointeurs vers les boutons que vous souhaitez ajouter.

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a> Cmfcribbonbuttonsgroup, :: Cmfcribbonbuttonsgroup,

Construit un objet `CMFCRibbonButtonsGroup`.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
dans Spécifie un bouton à ajouter à l’objet nouvellement créé `CMFCRibbonButtonsGroup` .

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a> Cmfcribbonbuttonsgroup, :: GetButton

Retourne un pointeur vers le bouton situé à un index spécifié.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Paramètres

*i*<br/>
dans Index de base zéro d’un bouton à retourner.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le bouton situé à l’index spécifié. NULL si l’index spécifié est hors limites.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a> Cmfcribbonbuttonsgroup, :: GetCount

Retourne le nombre de boutons dans le groupe.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de boutons dans le groupe.

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a> Cmfcribbonbuttonsgroup, :: GetImageSize

Récupère la taille de l’image source du `CMFCToolBarImages` membre protégé `m_Images` .

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la taille de l’image source des images de la barre d’outils, le cas échéant, ou un `CSize` de zéro dans le cas contraire.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a> Cmfcribbonbuttonsgroup, :: GetRegularSize

Récupère la taille maximale possible de l’élément de groupe de ruban.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers le contexte de périphérique (Device Context) du groupe de ruban.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a> Cmfcribbonbuttonsgroup, :: HasImages

Signale si l' `CMFCRibbonButtonsGroup` objet contient des images de barre d’outils.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le `CMFCToolBarImages` membre protégé `m_Images` contient des images, ou false dans le cas contraire.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a> Cmfcribbonbuttonsgroup, :: OnDrawImage

Dessine l’image appropriée pour un bouton spécifié, selon que le bouton est normal, mis en surbrillance ou désactivé.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers le contexte de périphérique (Device Context) de l' `CMFCRibbonButtonsGroup` objet.

*rectImage*<br/>
dans Rectangle dans lequel dessiner l’image.

*pButton*<br/>
dans Bouton pour lequel l’image doit être dessinée.

*nImageIndex*<br/>
dans Index de l’image à dessiner sur le bouton (dans l’un des trois tableaux d’images pour les boutons normaux, mis en surbrillance ou désactivés).

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a> Cmfcribbonbuttonsgroup, :: RemoveAll

Supprime tous les boutons de l' `CMFCRibbonButtonsGroup` objet.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a> Cmfcribbonbuttonsgroup, :: SetImages

Assigne des images au groupe de boutons du ruban.

```cpp
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Paramètres

*pImages*<br/>
dans Images normales.

*pHotImages*<br/>
dans Images réactives.

*pDisabledImages*<br/>
dans Images désactivées.

### <a name="remarks"></a>Notes

Appelez `SetImages` avant d’ajouter des boutons à un groupe. Le nombre d’images doit être supérieur ou égal au nombre de boutons à ajouter au groupe.

> [!NOTE]
> Les images réactives sont des images qui s’affichent lorsque l’utilisateur pointe sur le bouton. Les images désactivées sont des images qui s’affichent lorsque le bouton est désactivé.

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a> Cmfcribbonbuttonsgroup, :: SetParentCategory

Définit le parent `CMFCRibbonCategory` de l' `CMFCRibbonButtonsGroup` objet et tous les boutons qu’il contient.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Paramètres

*pCategory*<br/>
dans Pointeur vers la catégorie parente à définir (les groupes avec onglet dans les contrôles de ruban sont appelés catégories).

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
