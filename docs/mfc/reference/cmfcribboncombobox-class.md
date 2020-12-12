---
description: 'En savoir plus sur : classe CMFCRibbonComboBox'
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
ms.openlocfilehash: be4078145817d06fafddb76f2cefbd0df0083503
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293663"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox, classe

La `CMFCRibbonComboBox` classe implémente un contrôle de zone de liste déroulante que vous pouvez ajouter à une barre de ruban, un panneau de ruban ou un menu contextuel de ruban.

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
|[CMFCRibbonComboBox :: AddItem](#additem)|Ajoute un élément unique à la zone de liste.|
|[CMFCRibbonComboBox ::D eleteItem](#deleteitem)|Supprime un élément spécifié de la zone de liste.|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Spécifie si la zone de liste peut changer de taille lorsqu’elle descend.|
|[CMFCRibbonComboBox::FindItem](#finditem)|Retourne l’index du premier élément de la zone de liste qui correspond à une chaîne spécifiée.|
|[CMFCRibbonComboBox :: GetCount](#getcount)|Retourne le nombre d’éléments dans la zone de liste.|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Obtient l’index de l’élément actuellement sélectionné dans la zone de liste.|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Obtient la hauteur de la zone de liste lorsque la zone de liste est déroulée.|
|[CMFCRibbonComboBox :: GetIntermediateSize](#getintermediatesize)|Retourne la taille de la zone de liste déroulante telle qu’elle est affichée en mode intermédiaire.|
|[CMFCRibbonComboBox :: GetItem](#getitem)|Retourne la chaîne associée à un élément à un index spécifié dans la zone de liste.|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Retourne les données associées à un élément à un index spécifié dans la zone de liste.|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Indique si le contrôle contient une zone d’édition.|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Indique si la zone de liste peut être redimensionnée.|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Appelé par le Framework lorsque l’utilisateur sélectionne un élément dans la zone de liste.|
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Supprime tous les éléments de la zone de liste et efface la zone d’édition.|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Sélectionne un élément dans la zone de liste.|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Définit la hauteur de la zone de liste lorsqu’elle est déroulée.|

## <a name="remarks"></a>Notes

La zone de liste déroulante du ruban se compose d’une zone de liste associée à une étiquette ou étiquette statique qui peut être modifiée par l’utilisateur. Vous devez spécifier le type que vous souhaitez lorsque vous créez votre zone de liste déroulante du ruban.

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCRibbonComboBox` classe, ajouter un élément à la zone de liste déroulante, sélectionner un élément dans la zone de liste déroulante et ajouter une zone de liste déroulante à un panneau.

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxribboncombobox. h

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a> CMFCRibbonComboBox :: AddItem

Ajoute un élément unique à la zone de liste.

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*lpszItem*<br/>
dans Chaîne de l’élément à ajouter.

*dwData*<br/>
dans Données associées à l’élément à ajouter.

### <a name="return-value"></a>Valeur renvoyée

Index de base zéro de l’élément ajouté.

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a> CMFCRibbonComboBox::CMFCRibbonComboBox

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
dans ID de la zone de liste déroulante.

*bHasEditBox*<br/>
dans TRUE si vous souhaitez une zone d’édition dans le contrôle ; FALSe dans le cas contraire.

*nWidth*<br/>
dans Largeur de la zone de liste déroulante en pixels ; ou-1 pour la largeur par défaut.

*lpszLabel*<br/>
dans Étiquette d’affichage de la zone de liste déroulante.

*nImage*<br/>
dans Index d’image de petite taille de la zone de liste déroulante.

### <a name="remarks"></a>Notes

La largeur par défaut est de 108 pixels.

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a> CMFCRibbonComboBox ::D eleteItem

Supprime un élément spécifié de la zone de liste.

```cpp
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro de l’élément à supprimer.

*dwData*<br/>
dans Données associées à l’élément à supprimer.

*lpszText*<br/>
dans Chaîne de l’élément à supprimer. S’il y a plusieurs éléments avec la même chaîne, le premier élément est supprimé.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’élément spécifié a été supprimé ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a> CMFCRibbonComboBox::EnableDropDownListResize

Spécifie si la zone de liste peut changer de taille lorsqu’elle descend.

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour activer le redimensionnement ; FALSe pour désactiver le redimensionnement.

### <a name="remarks"></a>Notes

Lorsque le redimensionnement est activé, la zone de liste change de taille en fonction des éléments qu’elle affiche.

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a> CMFCRibbonComboBox::FindItem

Retourne l’index du premier élément de la zone de liste qui correspond à une chaîne spécifiée.

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
dans Chaîne d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Index de base zéro de l’élément ; ou-1 si l’élément est introuvable.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a> CMFCRibbonComboBox :: GetCount

Retourne le nombre d’éléments dans la zone de liste.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans la zone de liste, ou 0 si la zone de liste ne contient aucun élément.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a> CMFCRibbonComboBox::GetCurSel

Obtient l’index de l’élément actuellement sélectionné dans la zone de liste.

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur renvoyée

Index de base zéro de l’élément actuellement sélectionné dans la zone de liste ; ou-1 si aucun élément n’est sélectionné.

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a> CMFCRibbonComboBox::GetDropDownHeight

Obtient la hauteur de la zone de liste lorsque la zone de liste est déroulée.

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>Valeur renvoyée

Hauteur, en pixels, de la zone de liste.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a> CMFCRibbonComboBox :: GetIntermediateSize

Retourne la taille de la zone de liste déroulante telle qu’elle est affichée en mode intermédiaire.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique pour la zone de liste déroulante.

### <a name="return-value"></a>Valeur renvoyée

Taille de la zone de liste déroulante.

### <a name="remarks"></a>Notes

La taille retournée est basée sur la taille de la zone de liste déroulante lorsqu’elle affiche de petites images.

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a> CMFCRibbonComboBox :: GetItem

Retourne la chaîne associée à un élément à un index spécifié dans la zone de liste.

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la chaîne associée à l’élément ; Sinon, NULL si le paramètre d’index n’est pas valide ou si le paramètre d’index est-1 et qu’aucun élément n’est sélectionné dans la zone de liste déroulante.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a> CMFCRibbonComboBox::GetItemData

Retourne les données associées à un élément à un index spécifié dans la zone de liste.

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Données associées à l’élément ; ou 0 si l’élément n’existe pas, ou si le paramètre d’index est-1 et qu’il n’y a aucun élément sélectionné dans la zone de liste.

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a> CMFCRibbonComboBox::HasEditBox

Indique si le contrôle contient une zone d’édition.

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le contrôle contient une zone d’édition ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a> CMFCRibbonComboBox::IsResizeDropDownList

Indique si la zone de liste peut être redimensionnée.

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la zone de liste peut être redimensionnée ; Sinon, FALSe. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>Notes

Vous pouvez activer le redimensionnement de zone de liste à l’aide de la méthode [CMFCRibbonComboBox :: EnableDropDownListResize](#enabledropdownlistresize) .

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a> CMFCRibbonComboBox::OnSelectItem

Appelé par le Framework quand un utilisateur sélectionne un élément dans la zone de liste.

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
dans Index de l’élément sélectionné.

### <a name="remarks"></a>Notes

Substituez cette méthode si vous souhaitez traiter une sélection d’entrée d’utilisateur.

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a> CMFCRibbonComboBox::RemoveAllItems

Supprime tous les éléments de la zone de liste et efface la zone d’édition.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a> CMFCRibbonComboBox::SelectItem

Sélectionne un élément dans la zone de liste.

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

*dwData*<br/>
dans Données associées à un élément dans la zone de liste.

*lpszText*<br/>
dans Chaîne d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a> CMFCRibbonComboBox::SetDropDownHeight

Définit la hauteur de la zone de liste lorsqu’elle est déroulée.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Paramètres

*nHeight*<br/>
dans Hauteur, en pixels, de la zone de liste.

### <a name="remarks"></a>Notes

La hauteur par défaut est de 150 pixels.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit, classe](../../mfc/reference/cmfcribbonedit-class.md)
