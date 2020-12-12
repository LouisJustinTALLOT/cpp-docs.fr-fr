---
description: 'En savoir plus sur : classe CMFCToolBarComboBoxButton'
title: CMFCToolBarComboBoxButton, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
ms.openlocfilehash: aa28d1b125a5e1baf56a9e6e10812e7e6e56312f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163910"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton, classe

Un bouton de barre d’outils qui contient un contrôle de zone de liste déroulante ( [classe CComboBox](../../mfc/reference/ccombobox-class.md)).

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Construit un objet `CMFCToolBarComboBoxButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarComboBoxButton :: AddItem](#additem)|Ajoute un élément à la fin de la liste de la zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Ajoute un élément à la liste de la zone de liste déroulante. L’ordre des éléments dans la liste est spécifié par `Compare` .|
|[CMFCToolBarComboBoxButton :: compare](#compare)|Compare deux éléments. Appelé pour trier les éléments qui s' `AddSortedItems` ajoutent à la liste de la zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Crée un nouveau contrôle d’édition pour le bouton de zone de liste déroulante.|
|[CMFCToolBarComboBoxButton ::D eleteItem](#deleteitem)|Supprime un élément de la liste de la zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Retourne l’index de l’élément qui contient une chaîne spécifiée.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Retourne un pointeur vers le bouton de zone de liste déroulante avec un ID de commande spécifié.|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Retourne un pointeur vers le contrôle de zone de liste déroulante incorporé dans le bouton de zone de liste déroulante.|
|[CMFCToolBarComboBoxButton :: GetCount](#getcount)|Retourne le nombre d’éléments dans la liste de zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Recherche le bouton de zone de liste déroulante qui a un ID de commande spécifié. Retourne le nombre d’éléments dans la liste de zones de liste déroulante de ce bouton.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Retourne l’index de l’élément sélectionné dans la liste déroulante.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Recherche le bouton de zone de liste déroulante qui a un ID de commande spécifié et retourne l’index de l’élément sélectionné dans la liste de zone de liste déroulante de ce bouton.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Retourne un pointeur vers le contrôle d’édition qui est incorporé dans le bouton de zone de liste déroulante.|
|[CMFCToolBarComboBoxButton :: GetItem](#getitem)|Retourne la chaîne associée à un index spécifié dans la liste de zones de liste déroulante.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Recherche le bouton de zone de liste déroulante qui a un ID de commande spécifié et retourne la chaîne associée à un index dans la liste de zone de liste déroulante de ce bouton.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Retourne la valeur 32 bits qui est associée à un index spécifié dans la liste de zones de liste déroulante.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Recherche le bouton de zone de liste déroulante qui a un ID de commande spécifié et retourne la valeur 32 bits associée à un index dans la liste de zones de liste déroulante de ce bouton.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Recherche le bouton de zone de liste déroulante qui a un ID de commande spécifié. Récupère la valeur 32 bits qui est associée à un index dans la liste de la zone de liste déroulante de ce bouton et retourne la valeur 32 bits sous la forme d’un pointeur.|
|[CMFCToolBarComboBoxButton :: GetText](#gettext)|Retourne le texte du contrôle d’édition de la zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Recherche le bouton de zone de liste déroulante qui a un ID de commande spécifié et retourne le texte du contrôle d’édition de ce bouton.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Détermine si les boutons de zone de liste déroulante de l’application sont centrés ou alignés sur le haut de la barre d’outils.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Détermine si les boutons de zone de liste déroulante de l’application ont une apparence plate.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Supprime tous les éléments de la zone de liste et le contrôle d’édition de la zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Sélectionne un élément dans la zone de liste déroulante en fonction de son index, de sa valeur 32 bits ou de sa chaîne, et notifie le contrôle de zone de liste déroulante de la sélection.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Recherche le bouton de zone de liste déroulante qui a un ID de commande spécifié. Appelle `SelectItem` pour sélectionner un élément dans la zone de liste déroulante de ce bouton en fonction de sa valeur de chaîne, d’index ou de 32 bits.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Spécifie si les boutons de zone de liste déroulante de l’application sont centrés verticalement ou alignés sur le haut de la barre d’outils.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Définit la hauteur de la zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Spécifie si les boutons de zone de liste déroulante dans l’application ont une apparence à deux dimensions.|

## <a name="remarks"></a>Notes

Pour ajouter un bouton de zone de liste déroulante à une barre d’outils, procédez comme suit :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Construisez un `CMFCToolBarComboBoxButton` objet.

3. Dans le gestionnaire de messages qui traite le message AFX_WM_RESETTOOLBAR, remplacez le bouton factice par le nouveau bouton de zone de liste déroulante à l’aide de [CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations, consultez [procédure pas à pas : ajout de contrôles aux barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md). Pour obtenir un exemple de bouton de barre d’outils de zone de liste déroulante, consultez l’exemple de projet VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCToolBarComboBoxButton` . L’exemple montre comment activer les zones de modification et de liste déroulante, définir la position verticale des boutons de zone de liste déroulante dans l’application, définir la hauteur de la zone de liste lorsqu’elle est déroulée, définir l’apparence à deux dimensions (Flat) des boutons de zone de liste déroulante dans l’application et définir le texte dans la zone d’édition du bouton Cet extrait de code fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxtoolbarcomboboxbutton. h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a> CMFCToolBarComboBoxButton :: AddItem

Ajoute un élément unique à la zone de liste.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*lpszItem*<br/>
dans Texte de l’élément à ajouter à la zone de liste.

*dwData*<br/>
dans Données associées à l’élément à ajouter à la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Index du dernier élément de la zone de liste.

### <a name="remarks"></a>Notes

N’utilisez pas cette méthode lorsque le style de zone de liste est trié.

Si le texte de l’élément figure déjà dans la zone de liste, les nouvelles données sont stockées avec l’élément existant. La recherche de l’élément respecte la casse.

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a> CMFCToolBarComboBoxButton::AddSortedItem

Ajoute un élément à la zone de liste dans l’ordre défini par la méthode [compare](#compare) .

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*lpszItem*<br/>
dans Texte de l’élément à ajouter à la zone de liste.

*dwData*<br/>
dans Données associées à l’élément à ajouter à la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Index de l’élément qui a été ajouté à la zone de liste.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour ajouter des éléments à la zone de liste dans un ordre spécifique.

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a> CMFCToolBarComboBoxButton::CanBeStretched

Indique si la taille du bouton de zone de liste déroulante peut être modifiée.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE.

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a> CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Construit un objet [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) .

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
dans ID de commande du bouton nouveau.

*iImage*<br/>
dans Index d’image de l’image associée au bouton nouveau.

*dwStyle*<br/>
dans Style du nouveau bouton.

*iWidth*<br/>
dans Largeur, en pixels, du bouton nouveau.

### <a name="remarks"></a>Notes

La largeur par défaut est de 150 pixels.

Pour obtenir la liste des styles de boutons de barre d’outils, consultez [styles de contrôle ToolBar](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a> CMFCToolBarComboBoxButton::ClearData

Supprime les données définies par l’utilisateur.

```
virtual void ClearData();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Substituez cette méthode dans une classe dérivée si vous souhaitez supprimer toutes les données définies par l’utilisateur.

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a> CMFCToolBarComboBoxButton :: compare

Compare deux chaînes.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Paramètres

*lpszItem1*<br/>
dans Première chaîne à comparer.

*lpszItem2*<br/>
dans Deuxième chaîne à comparer.

### <a name="return-value"></a>Valeur renvoyée

Valeur qui indique la relation lexicographique qui respecte la casse entre les chaînes. Le tableau suivant répertorie les valeurs de sortie possibles :

|Valeur|Description|
|-----------|-----------------|
|\<0|La première chaîne est inférieure à la seconde.|
|0|La première chaîne est égale à la seconde.|
|>0|La première chaîne est supérieure à la seconde.|

### <a name="remarks"></a>Notes

Substituez cette méthode pour modifier la façon dont les éléments sont triés dans la zone de liste.

La comparaison respecte la casse.

Cette méthode est appelée uniquement à partir de la méthode [AddSortedItem](#addsorteditem) .

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a> CMFCToolBarComboBoxButton :: CopyFrom

Copie l’état du spécifié `CMFCToolBarComboBoxButton` vers l’objet actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
dans Objet source `CMFCToolBarComboBoxButton` .

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a> CMFCToolBarComboBoxButton::CreateCombo

Crée une zone de liste déroulante pour le bouton de zone de liste déroulante.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la fenêtre parente du bouton.

*rectangulaire*<br/>
dans Rectangle englobant de la zone de liste déroulante.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la nouvelle zone de liste déroulante si la méthode a réussi ; Sinon, NULL.

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a> CMFCToolBarComboBoxButton::CreateEdit

Crée une nouvelle zone d’édition pour le bouton de zone de liste déroulante.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la fenêtre parente du bouton.

*rectangulaire*<br/>
dans Rectangle englobant de la nouvelle zone d’édition.

*dwEditStyle*<br/>
dans Style de contrôle de la nouvelle zone d’édition.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la nouvelle zone d’édition si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsqu’elle crée une nouvelle zone d’édition pour un bouton de zone de liste déroulante. Substituez cette méthode pour modifier le mode de création de [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) .

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a> CMFCToolBarComboBoxButton ::D eleteItem

Supprime un élément spécifié de la zone de liste.

```
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
dans Texte de l’élément à supprimer. S’il y a plusieurs éléments avec le même texte, le premier élément est supprimé.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’élément a été trouvé et supprimé avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a> CMFCToolBarComboBoxButton ::D uplicateData

Duplique les données définies par l’utilisateur.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Substituez cette méthode dans une classe dérivée si vous souhaitez copier toutes les données définies par l’utilisateur.

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a> CMFCToolBarComboBoxButton::EnableWindow

Active ou désactive les zones de modification et de liste déroulante.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour activer les zones de modification et de liste déroulante ; FALSe pour désactiver les zones de modification et de liste modifiable.

### <a name="remarks"></a>Notes

Lorsqu’ils sont désactivés, les contrôles ne peuvent pas devenir actifs et ne peuvent pas accepter les entrées utilisateur.

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a> CMFCToolBarComboBoxButton::ExportToMenuButton

Copie une chaîne de la table de la chaîne d’application dans le menu spécifié à l’aide de l’ID de commande du bouton de zone de liste déroulante.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Paramètres

*menuButton*<br/>
à Référence à un bouton de menu.

### <a name="return-value"></a>Valeur renvoyée

Toujours TRUE.

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a> CMFCToolBarComboBoxButton::FindItem

Retourne l’index du premier élément de la zone de liste qui contient une chaîne spécifiée.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
dans Texte à rechercher dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Index de l’élément ; ou CB_ERR si l’élément est introuvable.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a> CMFCToolBarComboBoxButton::GetByCmd

Obtient un pointeur vers le bouton de zone de liste déroulante qui a un ID de commande spécifié.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande d’un bouton de zone de liste déroulante.

*bIsFocus*<br/>
dans TRUE pour rechercher uniquement les boutons ciblés ; FALSe pour rechercher tous les boutons.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un bouton de zone de liste déroulante ; ou NULL si le bouton est introuvable.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a> CMFCToolBarComboBoxButton::GetComboBox

Retourne un pointeur vers la zone de liste déroulante dans le bouton de zone de liste déroulante.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet de [classe CComboBox](../../mfc/reference/ccombobox-class.md) si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a> CMFCToolBarComboBoxButton::GetContextMenuID

Obtient l’ID de ressource du menu contextuel pour le bouton de zone de liste déroulante.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valeur renvoyée

ID de ressource du menu contextuel.

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a> CMFCToolBarComboBoxButton :: GetCount

Retourne le nombre d’éléments dans la zone de liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans la zone de liste.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a> CMFCToolBarComboBoxButton::GetCountAll

Obtient le nombre d’éléments dans la zone de liste d’un bouton de zone de liste déroulante qui a un ID de commande spécifié.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande d’un bouton de zone de liste déroulante.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans la zone de liste ; Sinon, CB_ERR si le bouton de zone de liste déroulante est introuvable.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a> CMFCToolBarComboBoxButton::GetCurSel

Obtient l’index de l’élément actuellement sélectionné dans la zone de liste.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur renvoyée

Index de l’élément actuellement sélectionné dans la zone de liste ; ou CB_ERR si aucun élément n’est sélectionné.

### <a name="remarks"></a>Notes

L’index de la zone de liste est de base zéro.

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a> CMFCToolBarComboBoxButton::GetCurSelAll

Retourne l’index de l’élément actuellement sélectionné dans la zone de liste d’un bouton de zone de liste déroulante qui a un ID de commande spécifié.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande d’un bouton de zone de liste déroulante.

### <a name="return-value"></a>Valeur renvoyée

Index de l’élément actuellement sélectionné dans la zone de liste ; Sinon, CB_ERR si aucun élément n’est sélectionné ou si aucun bouton de zone de liste déroulante n’est trouvé.

### <a name="remarks"></a>Notes

L’index de la zone de liste est de base zéro.

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a> CMFCToolBarComboBoxButton::GetEditCtrl

Retourne un pointeur vers la zone d’édition dans le bouton de zone de liste déroulante.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la zone d’édition si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a> CMFCToolBarComboBoxButton::GetHwnd

Retourne le handle de fenêtre pour la zone de liste déroulante.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valeur renvoyée

Handle de fenêtre, ou NULL si la zone de liste déroulante n’est pas associée à un objet Window.

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a> CMFCToolBarComboBoxButton :: GetItem

Retourne la chaîne associée à un élément à un index spécifié dans la zone de liste.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la chaîne associée à l’élément ; Sinon, NULL si le paramètre d’index n’est pas valide ou si le paramètre d’index est-1 et qu’il n’y a pas d’élément sélectionné dans la zone de liste déroulante.

### <a name="remarks"></a>Notes

Un paramètre d’index de-1 retourne la chaîne de l’élément actuellement sélectionné.

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a> CMFCToolBarComboBoxButton::GetItemAll

Retourne la chaîne associée à un élément à un index spécifié dans la zone de liste d’un bouton de zone de liste déroulante qui a un ID de commande spécifié.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande d’un bouton de zone de liste déroulante.

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la chaîne de l’élément si la méthode a réussi ; Sinon, NULL si l’index n’est pas valide, si un bouton de zone de liste déroulante est introuvable ou si index a la valeur-1 et qu’il n’y a pas d’élément sélectionné dans la zone de liste déroulante.

### <a name="remarks"></a>Notes

Une valeur d’index de-1 retourne la chaîne de l’élément actuellement sélectionné.

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a> CMFCToolBarComboBoxButton::GetItemData

Retourne les données associées à un élément à un index spécifique dans la zone de liste.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Données associées à l’élément ; ou 0 si l’élément n’existe pas.

### <a name="remarks"></a>Notes

Un paramètre d’index de-1 retourne les données associées à l’élément actuellement sélectionné.

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a> CMFCToolBarComboBoxButton::GetItemDataAll

Retourne les données associées à un élément à un index spécifique dans la zone de liste d’un bouton de zone de liste déroulante qui a un ID de commande spécifique.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande d’un bouton de zone de liste déroulante.

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Données associées à l’élément si la méthode a réussi ; dans le cas contraire, 0 si l’index spécifié n’est pas valide ou CB_ERR si le bouton de zone de liste déroulante est introuvable.

### <a name="remarks"></a>Notes

Un paramètre d’index de-1 retourne les données associées à l’élément actuellement sélectionné.

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a> CMFCToolBarComboBoxButton::GetItemDataPtrAll

Retourne les données associées à un élément à un index spécifique dans la zone de liste d’un bouton de zone de liste déroulante qui a un ID de commande spécifique. Ces données sont retournées sous la forme d’un pointeur.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande du bouton de zone de liste déroulante.

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

Pointeur associé à l’élément si la méthode a réussi ; Sinon,-1 si une erreur se produit, ou NULL si le bouton de zone de liste déroulante est introuvable.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a> CMFCToolBarComboBoxButton::GetPrompt

Retourne la chaîne d’invite pour le bouton de zone de liste déroulante.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Valeur renvoyée

Chaîne d’invite.

### <a name="remarks"></a>Notes

Cette méthode n’est pas implémentée pour le moment.

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a> CMFCToolBarComboBoxButton :: GetText

Obtient le texte dans la zone d’édition.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Valeur renvoyée

Texte dans la zone d’édition.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a> CMFCToolBarComboBoxButton::GetTextAll

Obtient le texte de la zone d’édition d’un bouton de zone de liste déroulante qui a un ID de commande spécifié.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande d’un bouton de zone de liste déroulante spécifique.

### <a name="return-value"></a>Valeur renvoyée

Texte dans la zone d’édition si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a> CMFCToolBarComboBoxButton :: HasFocus

Indique si la zone de liste déroulante a actuellement le focus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la zone de liste déroulante a actuellement le focus ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode retourne également TRUE si une fenêtre enfant de la zone de liste déroulante a actuellement le focus.

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a> CMFCToolBarComboBoxButton::IsCenterVert

Retourne la position verticale des boutons de zone de liste déroulante dans l’application.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si les boutons sont centrés ; FALSe si les boutons sont alignés en haut.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a> CMFCToolBarComboBoxButton::IsFlatMode

Retourne l’apparence à deux dimensions (Flat) des boutons de zone de liste déroulante dans l’application.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si les boutons ont un style à deux dimensions ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le style à deux dimensions par défaut des boutons de zone de liste déroulante est FALSe.

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a> CMFCToolBarComboBoxButton::IsOwnerOf

Indique si le handle spécifié est associé au bouton de zone de liste déroulante ou à l’un de ses enfants.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Paramètres

*HWND*<br/>
dans Handle de fenêtre.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le handle est afin avec le bouton de zone de liste déroulante ou l’un de ses enfants ; Sinon, FALSe.

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a> CMFCToolBarComboBoxButton::IsRibbonButton

Indique si le bouton de zone de liste déroulante réside sur un panneau du ruban.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Valeur renvoyée

Toujours FALSE.

### <a name="remarks"></a>Remarques

Par défaut, cette méthode retourne toujours la valeur FALSe, ce qui signifie que le bouton de zone de liste déroulante n’est jamais affiché sur un panneau de ruban.

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a> CMFCToolBarComboBoxButton::IsWindowVisible

Retourne l’état de visibilité du bouton de zone de liste déroulante.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Valeur renvoyée

État de visibilité du bouton de zone de liste déroulante.

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a> CMFCToolBarComboBoxButton::NotifyCommand

Indique si le bouton de zone de liste déroulante traite le message.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Paramètres

*iNotifyCode*<br/>
dans Message de notification associé à la commande.

### <a name="return-value"></a>Valeur renvoyée

Indique si le bouton de zone de liste déroulante traite le message.

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a> CMFCToolBarComboBoxButton::OnAddToCustomizePage

Appelée par l’infrastructure quand le bouton est ajouté à la boîte de dialogue **personnaliser** .

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a> CMFCToolBarComboBoxButton::OnCalculateSize

Appelé par l’infrastructure pour calculer la taille du bouton.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Contexte de périphérique qui affiche le bouton de zone de liste déroulante.

*sizeDefault*<br/>
dans Taille par défaut du bouton de zone de liste déroulante.

*bHorz*<br/>
dans État d’ancrage de la barre d’outils parente. TRUE lorsque la barre d’outils est ancrée horizontalement et FALSe lorsque la barre d’outils est ancrée verticalement.

### <a name="return-value"></a>Valeur renvoyée

`SIZE`Structure qui contient les dimensions du bouton de zone de liste déroulante, en pixels.

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a> CMFCToolBarComboBoxButton::OnChangeParentWnd

Appelé par le Framework lorsque le bouton de zone de liste déroulante est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la nouvelle barre d’outils parente.

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a> CMFCToolBarComboBoxButton :: OnClick

Appelée par l’infrastructure quand l’utilisateur clique sur le bouton de zone de liste déroulante.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Pointeur vers la fenêtre parente du bouton de zone de liste déroulante.

*bDelay*<br/>
dans Réservé à une utilisation dans une classe dérivée.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode gère l’événement ; Sinon, FALSe.

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a> CMFCToolBarComboBoxButton::OnCtlColor

Appelé par le Framework lorsque l’utilisateur modifie la couleur de la barre d’outils parent pour définir la couleur du bouton de zone de liste déroulante.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Contexte de périphérique qui affiche le bouton de zone de liste déroulante.

*nCtlColor*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur renvoyée

Handle du pinceau utilisé par l’infrastructure pour peindre l’arrière-plan du bouton de zone de liste déroulante.

### <a name="remarks"></a>Notes

Cette méthode définit également la couleur du texte du bouton de zone de liste déroulante.

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a> CMFCToolBarComboBoxButton :: OnDraw

Appelé par l’infrastructure pour dessiner le bouton de zone de liste déroulante en utilisant les styles et les options spécifiés.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Contexte de périphérique qui affiche le bouton.

*rectangulaire*<br/>
dans Rectangle englobant du bouton.

*pImages*<br/>
dans Collection d’images qui est associée au bouton.

*bHorz*<br/>
dans État d’ancrage de la barre d’outils parente. TRUE lorsque la barre d’outils est ancrée horizontalement et FALSe lorsque la barre d’outils est ancrée verticalement.

*bCustomizeMode*<br/>
dans Indique si l’application est en mode de personnalisation.

*bHighlight*<br/>
dans Indique si le bouton de zone de liste déroulante doit être mis en surbrillance.

*bDrawBorder*<br/>
dans Indique s’il faut dessiner le bouton de zone de liste déroulante avec une bordure.

*bGrayDisabledButtons*<br/>
dans TRUE pour dessiner les boutons désactivés ombrés ; FALSe pour utiliser la collection d’images désactivées.

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a> CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Appelé par l’infrastructure pour dessiner le bouton de zone de liste déroulante dans le volet **commandes** de la boîte de dialogue **personnaliser** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Contexte de périphérique qui affiche le bouton de zone de liste déroulante.

*rectangulaire*<br/>
dans Rectangle englobant du bouton de zone de liste déroulante.

*bSelected*<br/>
dans TRUE si le bouton de zone de liste déroulante est sélectionné ; Sinon, FALSe.

### <a name="return-value"></a>Valeur renvoyée

Largeur, en pixels, du bouton de zone de liste déroulante.

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a> CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Appelé par l’infrastructure pour définir la police du bouton de zone de liste déroulante lorsque la police de l’application est modifiée.

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a> CMFCToolBarComboBoxButton::OnMove

Appelé par l’infrastructure pour modifier l’emplacement du bouton de zone de liste déroulante lorsque la barre d’outils parente se déplace.

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a> CMFCToolBarComboBoxButton :: OnShow

Appelé par le Framework lorsque le bouton de zone de liste déroulante est masqué ou affiché.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
dans Indique s’il faut masquer ou afficher le bouton de zone de liste déroulante.

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a> CMFCToolBarComboBoxButton :: OnSize

Appelé par l’infrastructure pour modifier la taille du bouton de zone de liste déroulante lorsque la taille de la barre d’outils parente change.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Paramètres

*iSize*<br/>
dans Nouvelle largeur du bouton de zone de liste déroulante.

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a> CMFCToolBarComboBoxButton::OnUpdateToolTip

Appelée par l’infrastructure quand l’utilisateur modifie l’info-bulle pour le bouton de zone de liste déroulante.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la fenêtre parente pour le bouton de zone de liste déroulante.

*iButtonIndex*<br/>
dans ID du bouton de zone de liste déroulante.

*wndToolTip*<br/>
dans Info-bulle à associer au bouton de zone de liste déroulante.

*str*<br/>
dans Texte d’info-bulle.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode gère l’événement ; Sinon, FALSe.

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a> CMFCToolBarComboBoxButton::RemoveAllItems

Supprime tous les éléments de la liste et les zones d’édition.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments de la zone de liste et le contrôle d’édition d’une zone de liste déroulante.

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a> CMFCToolBarComboBoxButton::SelectItem

Sélectionne un élément dans la zone de liste.

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément dans la zone de liste.

*bNotify*<br/>
dans TRUE pour notifier le bouton de zone de liste déroulante de la sélection ; Sinon, FALSe.

*dwData*<br/>
dans Données associées à un élément dans la zone de liste.

*lpszText*<br/>
dans Texte d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a> CMFCToolBarComboBoxButton::SelectItemAll

Sélectionne un élément dans la zone de liste d’un bouton de zone de liste déroulante qui a un ID de commande spécifié.

```
static BOOL SelectItemAll(
    UINT uiCmd,
    int iIndex);

static BOOL SelectItemAll(
    UINT uiCmd,
    DWORD_PTR dwData);

static BOOL SelectItemAll(
    UINT uiCmd,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande du bouton de zone de liste déroulante qui contient la zone de liste.

*iIndex*<br/>
dans Index de base zéro de l’élément dans la zone de liste. La valeur-1 supprime toute sélection en cours dans la zone de liste et efface la zone d’édition.

*dwData*<br/>
dans Données d’un élément dans la zone de liste.

*lpszText*<br/>
dans Texte d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a> CMFCToolBarComboBoxButton :: Serialize

Lit cet objet à partir d’une archive ou l’écrit dans une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
[in, out] `CArchive` Objet à sérialiser.

### <a name="remarks"></a>Notes

Les paramètres de l' `CArchive` objet déterminent si cette méthode lit ou écrit dans l’archive.

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a> CMFCToolBarComboBoxButton :: SetACCData

Remplit l’objet spécifié à `CAccessibilityData` l’aide des données d’accessibilité du bouton de zone de liste déroulante.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
dans Fenêtre parente du bouton de zone de liste déroulante.

*data*<br/>
à `CAccessibilityData` Objet qui reçoit les données d’accessibilité à partir du bouton de zone de liste déroulante.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode a réussi ; Sinon, FALSe.

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a> CMFCToolBarComboBoxButton::SetCenterVert

Définit la position verticale des boutons de zone de liste déroulante dans l’application.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Paramètres

*bCenterVert*<br/>
dans TRUE pour centrer le bouton de zone de liste déroulante dans la barre d’outils ; FALSe pour aligner le bouton de zone de liste déroulante en haut de la barre d’outils.

### <a name="remarks"></a>Notes

Par défaut, les boutons de zone de liste déroulante sont alignés en haut.

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a> CMFCToolBarComboBoxButton::SetContextMenuID

Définit l’ID de ressource du menu contextuel pour le bouton de zone de liste déroulante.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Paramètres

*uiResID*<br/>
dans ID de ressource du menu contextuel.

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a> CMFCToolBarComboBoxButton::SetDropDownHeight

Définit la hauteur de la zone de liste lorsqu’elle est déroulée.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Paramètres

*nHeight*<br/>
dans Hauteur, en pixels, de la zone de liste.

### <a name="remarks"></a>Notes

La hauteur par défaut est de 150 pixels.

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a> CMFCToolBarComboBoxButton::SetFlatMode

Définit l’apparence à deux dimensions (Flat) des boutons de zone de liste déroulante dans l’application.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Paramètres

*bFlat*<br/>
dans TRUE pour une apparence à deux dimensions ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le style à deux dimensions par défaut des boutons de zone de liste déroulante est FALSe.

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a> CMFCToolBarComboBoxButton :: SetStyle

Définit le style spécifié pour le bouton de zone de liste déroulante et redessine le contrôle s’il n’est pas désactivé.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
dans Combinaison d’opérations de bits de styles de barre d’outils.

### <a name="remarks"></a>Notes

Pour obtenir la liste des styles de boutons de barre d’outils, consultez [styles de contrôle ToolBar](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a> CMFCToolBarComboBoxButton :: SetText

Définit le texte dans la zone d’édition du bouton de zone de liste déroulante.

```cpp
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
dans Pointeur vers une chaîne qui contient le texte de la zone d’édition.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox (classe)](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : ajout de contrôles aux barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
