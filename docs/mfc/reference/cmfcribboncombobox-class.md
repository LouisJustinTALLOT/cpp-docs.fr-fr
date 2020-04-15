---
title: CMFCRibbonComboBox, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: 5846b1c5590a756f0a0820583af3d0b159968ea2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375225"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox, classe

La `CMFCRibbonComboBox` classe implémente un contrôle de boîte combo que vous pouvez ajouter à une barre de ruban, un panneau de ruban, ou un menu popup ruban.

## <a name="syntax"></a>Syntaxe

```cpp
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Construit un objet CMFCRibbonComboBox.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonComboBox::AddItem](#additem)|Annexe un élément unique à la boîte de liste.|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Supprime un élément spécifié de la boîte de liste.|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Précise si la boîte de liste peut changer de taille lorsqu’elle tombe.|
|[CMFCRibbonComboBox::FindItem](#finditem)|Retourne l’index du premier élément dans la boîte de liste qui correspond à une chaîne spécifiée.|
|[CMFCRibbonComboBox::GetCount](#getcount)|Retourne le nombre d’éléments dans la boîte de liste.|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Obtient l’index de l’élément actuellement sélectionné dans la boîte de liste.|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Obtient la hauteur de la boîte de liste lorsque la boîte de liste est tombée vers le bas.|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Retourne la taille de la boîte combo telle qu’elle est affichée en mode intermédiaire.|
|[CMFCRibbonComboBox::GetItem](#getitem)|Retourne la chaîne associée à un élément à un index spécifié dans la boîte de liste.|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Retourne les données associées à un élément à un index spécifié dans la boîte de liste.|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Indique si le contrôle contient une boîte de modification.|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Indique si la boîte de liste peut être resized ou non.|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Appelé par le cadre lorsque l’utilisateur sélectionne un élément dans la boîte de liste.|
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Supprime tous les éléments de la boîte de liste et efface la boîte de modification.|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Sélectionne un élément dans la boîte de liste.|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Définit la hauteur de la boîte de liste lorsqu’elle est tombée.|

## <a name="remarks"></a>Notes

La boîte combo ruban se compose d’une boîte de liste combinée avec une étiquette statique ou une étiquette qui peut être éditée par l’utilisateur. Vous devez spécifier le type que vous voulez lorsque vous créez votre boîte combo ruban.

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCRibbonComboBox` un objet de la classe, ajouter un élément à la boîte combo, sélectionner un élément dans la boîte combo, et ajouter une boîte combo à un panneau.

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribboncombobox.h

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a>CMFCRibbonComboBox::AddItem

Annexe un élément unique à la boîte de liste.

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*lpszItem (en)*<br/>
[dans] La chaîne de l’élément à ajouter.

*dwData dwData*<br/>
[dans] Les données associées à l’élément à ajouter.

### <a name="return-value"></a>Valeur de retour

L’indice zéro de l’élément appendice.

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a>CMFCRibbonComboBox::CMFCRibbonComboBox

Construit un objet `CMFCRibbonComboBox`.

```cpp
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[dans] L’ID de la boîte combo.

*bHasEditBox (en anglais seulement)*<br/>
[dans] VRAI si vous voulez une boîte de modification dans le contrôle; FALSE autrement.

*nWidth (en)*<br/>
[dans] Largeur de la boîte combo en pixels; ou -1 pour la largeur par défaut.

*lpszLabel*<br/>
[dans] L’étiquette d’affichage de la boîte combo.

*nImage (en)*<br/>
[dans] Le petit index d’image de la boîte combo.

### <a name="remarks"></a>Notes

La largeur par défaut est de 108 pixels.

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a>CMFCRibbonComboBox::DeleteItem

Supprime un élément spécifié de la boîte de liste.

```cpp
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro de l’élément à supprimer.

*dwData dwData*<br/>
[dans] Les données associées à l’élément à supprimer.

*lpszText*<br/>
[dans] La chaîne de l’élément à supprimer. S’il y a plusieurs éléments avec la même chaîne, le premier élément est supprimé.

### <a name="return-value"></a>Valeur de retour

VRAI si l’élément spécifié a été supprimé; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a>CMFCRibbonComboBox::EnableDropDownListResize

Précise si la boîte de liste peut changer de taille lorsqu’elle tombe.

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour permettre la resizing; FALSE pour désactiver la resizing.

### <a name="remarks"></a>Notes

Lorsque la resizing est activée, la boîte de liste changera de taille pour s’adapter aux éléments qu’elle affiche.

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a>CMFCRibbonComboBox::FindItem

Retourne l’index du premier élément dans la boîte de liste qui correspond à une chaîne spécifiée.

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
[dans] La chaîne d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

L’indice zéro de l’élément; ou -1 si l’article n’est pas trouvé.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a>CMFCRibbonComboBox::GetCount

Retourne le nombre d’éléments dans la boîte de liste.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la boîte de liste, ou 0 si la boîte de liste ne contient pas d’éléments.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a>CMFCRibbonComboBox::GetCurSel

Obtient l’index de l’élément actuellement sélectionné dans la boîte de liste.

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

L’index zéro de l’élément actuellement sélectionné dans la boîte de liste; ou -1 si aucun élément n’est sélectionné.

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a>CMFCRibbonComboBox::GetDropDownHeight

Obtient la hauteur de la boîte de liste lorsque la boîte de liste est tombée vers le bas.

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>Valeur de retour

La hauteur, en pixels, de la boîte de liste.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonComboBox::GetIntermediateSize

Retourne la taille de la boîte combo telle qu’elle est affichée en mode intermédiaire.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un contexte d’appareil pour la boîte combo.

### <a name="return-value"></a>Valeur de retour

La taille de la boîte combo.

### <a name="remarks"></a>Notes

La taille retournée est basée sur la taille de la boîte combo quand il affiche de petites images.

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a>CMFCRibbonComboBox::GetItem

Retourne la chaîne associée à un élément à un index spécifié dans la boîte de liste.

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la chaîne qui est associée à l’élément; autrement, NULL si le paramètre de l’index est invalide, ou si le paramètre de l’index est de -1 et il n’y a pas d’élément sélectionné dans la boîte combo.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a>CMFCRibbonComboBox::GetItemData

Retourne les données associées à un élément à un index spécifié dans la boîte de liste.

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Les données associées à l’élément; ou 0 si l’élément n’existe pas, ou si le paramètre de l’index est de -1 et il n’y a pas d’élément sélectionné dans la boîte de liste.

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a>CMFCRibbonComboBox::HasEditBox

Indique si le contrôle contient une boîte de modification.

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le contrôle contient une boîte de modification; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a>CMFCRibbonComboBox::IsResizeDropDownList

Indique si la boîte de liste peut être resized ou non.

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la boîte de liste peut être resized; autrement FALSE. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>Notes

Vous pouvez activer la resizing de la boîte de liste en utilisant la méthode [CMFCRibbonComboBox::EnableDropDownListResize.](#enabledropdownlistresize)

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a>CMFCRibbonComboBox::OnSelectItem

Appelé par le cadre quand un utilisateur sélectionne un élément dans la boîte de liste.

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
[dans] L’index de l’élément sélectionné.

### <a name="remarks"></a>Notes

Remplacez cette méthode si vous souhaitez traiter une sélection d’entrées utilisateur.

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a>CMFCRibbonComboBox::RemoveAllItems

Supprime tous les éléments de la boîte de liste et efface la boîte de modification.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a>CMFCRibbonComboBox::SelectItem

Sélectionne un élément dans la boîte de liste.

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément dans la boîte de liste.

*dwData dwData*<br/>
[dans] Les données associées à un élément dans la boîte de liste.

*lpszText*<br/>
[dans] La chaîne d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCRibbonComboBox::SetDropDownHeight

Définit la hauteur de la boîte de liste lorsqu’elle est tombée.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Paramètres

*nHeight (en)*<br/>
[dans] La hauteur, en pixels, de la boîte de liste.

### <a name="remarks"></a>Notes

La hauteur par défaut est de 150 pixels.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit, classe](../../mfc/reference/cmfcribbonedit-class.md)
