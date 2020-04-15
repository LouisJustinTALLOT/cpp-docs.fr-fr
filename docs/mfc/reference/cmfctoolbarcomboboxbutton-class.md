---
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
ms.openlocfilehash: 0d003bdacf13403ad8dc4be4ec7e6f71ea57d156
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372187"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton, classe

Un bouton de barre d’outils qui contient un contrôle de boîte combo ( [Classe CComboBox](../../mfc/reference/ccombobox-class.md)).

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
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Ajoute un élément à la fin de la liste de la boîte combo.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Ajoute un élément à la liste des boîtes combo. L’ordre des éléments de `Compare`la liste est spécifié par .|
|[CMFCToolBarComboBoxButton::Comparez](#compare)|Compare deux éléments. Appelé pour trier `AddSortedItems` les éléments qui ajoute à la liste de boîte combo.|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Crée un nouveau contrôle de modification pour le bouton de la boîte combo.|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Supprime un élément de la liste des boîtes combo.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Retourne l’index de l’élément qui contient une chaîne spécifiée.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Retourne un pointeur sur le bouton de la boîte combo avec un IDENTIFIANT de commande spécifié.|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Retourne un pointeur au contrôle de la boîte combo qui est intégré dans le bouton de la boîte combo.|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Retourne le nombre d’éléments dans la liste des boîtes combo.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Trouve le bouton de la boîte combo qui a un ID de commande spécifié. Retourne le nombre d’éléments dans la liste de boîte combo de ce bouton.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Retourne l’index de l’élément sélectionné dans la liste des boîtes combo.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Trouve le bouton de boîte combo qui a un ID de commande spécifié, et renvoie l’index de l’élément sélectionné dans la liste de boîte combo de ce bouton.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Retourne un pointeur au contrôle de modification qui est intégré dans le bouton de la boîte combo.|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Retourne la chaîne associée à un index spécifié dans la liste des boîtes combo.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Trouve le bouton de boîte combo qui a un ID de commande spécifié, et renvoie la chaîne qui est associée à un index dans la liste de boîte combo de ce bouton.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Retourne la valeur 32 bits associée à un index spécifié dans la liste des boîtes combo.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Trouve le bouton de boîte combo qui a un ID de commande spécifié, et renvoie la valeur 32 bits qui est associée à un index dans la liste de boîte combo de ce bouton.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Trouve le bouton de la boîte combo qui a un ID de commande spécifié. Récupère la valeur 32 bits qui est associée à un index dans la liste de boîte combo de ce bouton, et retourne la valeur 32 bits comme pointeur.|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Retourne le texte du contrôle de modification de la boîte combo.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Trouve le bouton de boîte combo qui a un ID de commande spécifié, et renvoie le texte du contrôle de modification de ce bouton.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Détermine si les boutons de la boîte combo dans l’application sont centrés ou alignés avec le haut de la barre d’outils.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Détermine si les boutons de boîte combo dans l’application ont une apparence plate.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Supprime tous les éléments de la boîte de liste et modifie le contrôle de la boîte combo.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Sélectionne un élément dans la boîte combo en fonction de son index, de sa valeur 32 bits ou de sa chaîne, et informe le contrôle de la boîte combo sur la sélection.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Trouve le bouton de la boîte combo qui a un ID de commande spécifié. Appels `SelectItem` pour sélectionner un élément dans la boîte combo de ce bouton en fonction de sa valeur de chaîne, d’index ou de 32 bits.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Précise si les boutons de boîte combo dans l’application sont centrés verticalement ou alignés avec le haut de la barre d’outils.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Définit la hauteur de la case de liste d’abandon.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Précise si les boutons de boîte combo dans l’application ont une apparence plate.|

## <a name="remarks"></a>Notes

Pour ajouter un bouton de boîte combo à une barre d’outils, suivez ces étapes :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Construire `CMFCToolBarComboBoxButton` un objet.

3. Dans le gestionnaire de message qui traite le message AFX_WM_RESETTOOLBAR, remplacez le bouton factice par le nouveau bouton de boîte combo en utilisant [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations, voir [Procédure pas à pas: Mettre des contrôles sur les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md). Pour un exemple d’un bouton de barre d’outils de boîte combo, voir l’exemple projet VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCToolBarComboBoxButton` . L’exemple montre comment activer les boîtes de montage et de combo, définir la position verticale des boutons de boîte combo dans l’application, définir la hauteur de la boîte de liste quand il est tombé vers le bas, définir l’apparence de style plat des boutons de boîte combo dans l’application, et mettre le texte dans la boîte de modification du bouton boîte combo. Cet extrait de code fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtoolbarcomboboxbutton.h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a>CMFCToolBarComboBoxButton::AddItem

Annexe un élément unique à la boîte de liste.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*lpszItem (en)*<br/>
[dans] Le texte de l’élément à ajouter à la case de liste.

*dwData dwData*<br/>
[dans] Les données associées à l’élément à ajouter à la boîte de liste.

### <a name="return-value"></a>Valeur de retour

L’index du dernier élément dans la boîte de liste.

### <a name="remarks"></a>Notes

N’utilisez pas cette méthode lorsque le style de la boîte de liste est trié.

Si le texte de l’élément est déjà dans la boîte de liste, les nouvelles données sont stockées avec l’élément existant. La recherche de l’élément est sensible au cas.

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

Ajoute un élément à la boîte de liste dans l’ordre qui est défini par la méthode [Compare.](#compare)

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*lpszItem (en)*<br/>
[dans] Le texte de l’élément à ajouter à la case de liste.

*dwData dwData*<br/>
[dans] Les données associées à l’élément à ajouter à la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Index de l’élément qui a été ajouté à la boîte de liste.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour ajouter des éléments à la boîte de liste dans un ordre spécifique.

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched

Indique si la taille du bouton de boîte combo peut changer.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI.

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Construit un objet [CMFCToolBarComboBoxButton.](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[dans] L’ID de commande du nouveau bouton.

*iImage (en)*<br/>
[dans] L’index d’image de l’image associé au nouveau bouton.

*dwStyle (en)*<br/>
[dans] Le style du nouveau bouton.

*iWidth (en)*<br/>
[dans] La largeur, en pixels, du nouveau bouton.

### <a name="remarks"></a>Notes

La largeur par défaut est de 150 pixels.

Pour une liste de styles de boutons de barre d’outils voir [Styles de contrôle ToolBar](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData

Supprime les données définies par l’utilisateur.

```
virtual void ClearData();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Remplacer cette méthode dans une classe dérivée si vous souhaitez supprimer des données définies par l’utilisateur.

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a>CMFCToolBarComboBoxButton::Comparez

Compare deux chaînes.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Paramètres

*lpszItem1 (en)*<br/>
[dans] La première chaîne à comparer.

*lpszItem2*<br/>
[dans] La deuxième chaîne à comparer.

### <a name="return-value"></a>Valeur de retour

Une valeur qui indique la relation lexicographique sensible au cas entre les cordes. Le tableau suivant répertorie les valeurs de sortie possibles :

|Valeur|Description|
|-----------|-----------------|
|\<0|La première chaîne est inférieure à la seconde.|
|0|La première corde est égale à la seconde.|
|>0|La première chaîne est supérieure à la seconde.|

### <a name="remarks"></a>Notes

Remplacez cette méthode pour modifier la façon dont les éléments sont triés dans la boîte de liste.

La comparaison est sensible aux cas.

Cette méthode est appelée uniquement à partir de la méthode [AddSortedItem.](#addsorteditem)

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyDe

Copie l’état `CMFCToolBarComboBoxButton` du spécifié à l’objet actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[dans] L’objet source. `CMFCToolBarComboBoxButton`

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo

Crée une nouvelle boîte combo pour le bouton de la boîte combo.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Un pointeur à la fenêtre parente du bouton.

*Rect*<br/>
[dans] Rectangle de délimitation de la boîte de combo.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la nouvelle boîte de combo si la méthode a été réussie; autrement, NULL.

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit

Crée une nouvelle boîte de modification pour le bouton boîte combo.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Un pointeur à la fenêtre parente du bouton.

*Rect*<br/>
[dans] Rectangle de délimitation de la nouvelle boîte d’édition.

*dwEditStyle (en)*<br/>
[dans] Style de contrôle de la nouvelle boîte d’édition.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la nouvelle boîte de modification si la méthode a été réussie; autrement, NULL.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsqu’elle crée une nouvelle boîte de modification pour un bouton de boîte combo. Remplacez cette méthode pour modifier la création [de CMFCToolBarComboBoxEdit.](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem

Supprime un élément spécifié de la boîte de liste.

```
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
[dans] Le texte de l’élément à supprimer. S’il y a plusieurs éléments avec le même texte, le premier élément est supprimé.

### <a name="return-value"></a>Valeur de retour

VRAI si l’élément a été localisé et supprimé avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData

Doublons les données définies par l’utilisateur.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Remplacer cette méthode dans une classe dérivée si vous souhaitez copier des données définies par l’utilisateur.

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

Permet ou désactive les boîtes de modification et de combo.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour activer les boîtes de montage et de combo; FALSE pour désactiver les boîtes de modification et de combo.

### <a name="remarks"></a>Notes

Lorsqu’ils sont désactivés, les contrôles ne peuvent pas devenir actifs et ne peuvent pas accepter l’entrée de l’utilisateur.

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

Copie une chaîne de la table de chaîne d’application au menu spécifié à l’aide de l’ID de commande de bouton de boîte combo.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Paramètres

*menuButton*<br/>
[out] Référence à un bouton de menu.

### <a name="return-value"></a>Valeur de retour

Toujours TRUE.

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

Retourne l’index du premier élément dans la boîte de liste qui contient une chaîne spécifiée.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
[dans] Le texte pour lequel rechercher dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément; ou CB_ERR si l’article n’est pas trouvé.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

Obtient un pointeur sur le bouton de la boîte combo qui a une carte d’identité de commande spécifiée.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande d’un bouton de boîte combo.

*bIsFocus (en)*<br/>
[dans] VRAI pour rechercher uniquement des boutons ciblés; FALSE pour rechercher tous les boutons.

### <a name="return-value"></a>Valeur de retour

Un pointeur à un bouton boîte combo; ou NULL si le bouton n’est pas trouvé.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox

Retourne un pointeur à la boîte combo dans le bouton boîte combo.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’objet [de classe CComboBox](../../mfc/reference/ccombobox-class.md) si la méthode a été réussie; autrement NULL.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID

Obtient l’ID de ressource de menu raccourci pour le bouton boîte combo.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valeur de retour

L’ID de ressources de menu raccourci.

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount

Retourne le nombre d’éléments dans la boîte de liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la boîte de liste.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

Obtient le nombre d’éléments dans la boîte de liste d’un bouton de boîte combo qui a un ID de commande spécifié.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande d’un bouton de boîte combo.

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la boîte de liste; autrement, CB_ERR si le bouton de boîte combo n’est pas trouvé.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel

Obtient l’index de l’élément actuellement sélectionné dans la boîte de liste.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

L’index de l’élément actuellement sélectionné dans la boîte de liste; ou CB_ERR si aucun élément n’est sélectionné.

### <a name="remarks"></a>Notes

L’indice de la boîte de liste est basé sur zéro.

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll

Retourne l’index de l’élément actuellement sélectionné dans la boîte de liste d’un bouton de boîte combo qui a un ID de commande spécifié.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande d’un bouton de boîte combo.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément actuellement sélectionné dans la boîte de liste; autrement, CB_ERR si aucun élément n’est sélectionné ou un bouton de boîte combo n’est pas trouvé.

### <a name="remarks"></a>Notes

L’indice de la boîte de liste est basé sur zéro.

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

Retourne un pointeur à la boîte de modification dans le bouton de la boîte combo.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la boîte de modification si la méthode a été réussie; autrement, NULL.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd

Retourne la poignée de fenêtre pour la boîte combo.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valeur de retour

La poignée de fenêtre, ou NULL si la boîte combo n’est pas associée à un objet de fenêtre.

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem

Retourne la chaîne associée à un élément à un index spécifié dans la boîte de liste.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] Index basé à zéro d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la chaîne qui est associée à l’élément; autrement, NULL si le paramètre de l’index est invalide, ou si le paramètre de l’index est de -1 et il n’y a pas d’élément sélectionné dans la boîte combo.

### <a name="remarks"></a>Notes

Un paramètre d’index de -1 renvoie la chaîne de l’élément qui est actuellement sélectionné.

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

Retourne la chaîne associée à un élément à un index spécifié dans la boîte de liste d’un bouton de boîte combo qui a un ID de commande spécifié.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande d’un bouton de boîte combo.

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la chaîne de l’élément si la méthode a été réussie; autrement, NULL si l’index est invalide, un bouton boîte combo n’est pas trouvé, ou si l’index est de -1 et il n’y a pas d’élément sélectionné dans la boîte combo.

### <a name="remarks"></a>Notes

Une valeur d’indice de -1 renvoie la chaîne de l’élément qui est actuellement sélectionné.

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData

Retourne les données associées à un élément à un index spécifique dans la boîte de liste.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Les données associées à l’élément; ou 0 si l’article n’existe pas.

### <a name="remarks"></a>Notes

Un paramètre d’index de -1 renvoie les données associées à l’élément actuellement sélectionné.

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll

Retourne les données associées à un élément à un index spécifique dans la boîte de liste d’un bouton de boîte combo qui a un ID de commande spécifique.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande d’un bouton de boîte combo.

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Les données associées à l’élément si la méthode a été couronnée de succès; autrement, 0 si l’index spécifié n’est pas valide, ou CB_ERR si le bouton de boîte combo n’est pas trouvé.

### <a name="remarks"></a>Notes

Un paramètre d’index de -1 renvoie les données associées à l’élément actuellement sélectionné.

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

Retourne les données associées à un élément à un index spécifique dans la boîte de liste d’un bouton de boîte combo qui a un ID de commande spécifique. Ces données sont retournées comme pointeur.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande du bouton de la boîte combo.

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Un pointeur associé à l’élément si la méthode a été réussie; autrement, -1 si une erreur se produit, ou NULL si le bouton boîte combo n’est pas trouvé.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt

Retourne la chaîne rapide pour le bouton de la boîte combo.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Valeur de retour

La chaîne rapide.

### <a name="remarks"></a>Notes

Cette méthode n’est actuellement pas mise en œuvre.

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a>CMFCToolBarComboBoxButton::GetText

Obtient le texte dans la boîte de modification.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Valeur de retour

Le texte dans la boîte de modification.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

Obtient le texte dans la boîte de modification d’un bouton de boîte combo qui a un ID de commande spécifié.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande d’un bouton de boîte combo spécifique.

### <a name="return-value"></a>Valeur de retour

Le texte dans la boîte de modification si la méthode a été réussie; autrement, NULL.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus

Indique si la boîte combo a actuellement la mise au point.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la boîte combo a actuellement la mise au point; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode renvoie également VRAI si n’importe quelle fenêtre d’enfant de la boîte de combo a actuellement la mise au point.

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

Retourne la position verticale des boutons de boîte combo dans l’application.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Valeur de retour

VRAI si les boutons sont centrés; FALSE si les boutons sont alignés en haut.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode

Retourne l’apparence de style plat des boutons de boîte combo dans l’application.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Valeur de retour

VRAI si les boutons ont un style plat; autrement, FALSE.

### <a name="remarks"></a>Notes

Le style plat par défaut pour les boutons de boîte combo est FALSE.

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf

Indique si la poignée spécifiée est associée au bouton de la boîte combo, ou à l’un de ses enfants.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Paramètres

*Hwnd*<br/>
[dans] Une poignée de fenêtre.

### <a name="return-value"></a>Valeur de retour

VRAI si le manche est assocated avec le bouton de boîte combo, ou l’un de ses enfants; autrement, FALSE.

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

Indique si le bouton de la boîte combo réside sur un panneau ruban.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Valeur de retour

Toujours FALSE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode renvoie toujours FALSE, ce qui signifie que le bouton de la boîte combo n’est jamais affiché sur un panneau ruban.

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

Retourne l’état de visibilité du bouton de la boîte combo.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Valeur de retour

L’état de visibilité du bouton de la boîte combo.

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand

Indique si le bouton de la boîte combo traite le message.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Paramètres

*iNotifyCode (en)*<br/>
[dans] Le message de notification associé à la commande.

### <a name="return-value"></a>Valeur de retour

Que le bouton de la boîte combo traite le message.

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage

Appelé par le cadre lorsque le bouton est ajouté à la boîte de dialogue **Customize.**

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize

Appelé par le cadre pour calculer la taille du bouton.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton boîte combo.

*tailleDefault*<br/>
[dans] La taille par défaut du bouton de la boîte combo.

*bHorz (en)*<br/>
[dans] L’état de quai de la barre d’outils parent. VRAI lorsque la barre d’outils est amarré horizontalement et FALSE lorsque la barre d’outils est amarré verticalement.

### <a name="return-value"></a>Valeur de retour

Une `SIZE` structure qui contient les dimensions du bouton de la boîte combo, en pixels.

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

Appelé par le cadre lorsque le bouton boîte combo est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Pointeur vers la nouvelle barre d’outils parent.

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick

Appelé par le cadre lorsque l’utilisateur clique sur le bouton de la boîte combo.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[dans] Pointeur vers la fenêtre parente du bouton de la boîte combo.

*bDelay (en)*<br/>
[dans] Réservé pour une utilisation dans une classe dérivée.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode gère l’événement; autrement, FALSE.

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor

Appelé par le cadre lorsque l’utilisateur change la couleur de la barre d’outils parent pour définir la couleur du bouton boîte combo.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton boîte combo.

*nCtlColor (en anglais)*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur de retour

Manipuler à la brosse que le cadre utilise pour peindre l’arrière-plan du bouton boîte combo.

### <a name="remarks"></a>Notes

Cette méthode définit également la couleur du texte de bouton de boîte de combo.

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw

Appelé par le cadre pour dessiner le bouton boîte combo en utilisant les styles spécifiés et les options.

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

*Pdc*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton.

*Rect*<br/>
[dans] Le rectangle de délimitation du bouton.

*pImages (en)*<br/>
[dans] La collection d’images qui est associée au bouton.

*bHorz (en)*<br/>
[dans] L’état de quai de la barre d’outils parent. VRAI lorsque la barre d’outils est amarré horizontalement et FALSE lorsque la barre d’outils est amarré verticalement.

*bCustomizeMode*<br/>
[dans] Si l’application est en mode personnalisation.

*bHighlight (en)*<br/>
[dans] Que ce soit pour dessiner le bouton boîte combo mis en surbrillance.

*bDrawBorder (en anglais seulement)*<br/>
[dans] Que ce soit pour dessiner le bouton boîte combo avec une bordure.

*bGrayDisabledButtons*<br/>
[dans] VRAI pour dessiner des boutons handicapés ombragés; FALSE pour utiliser la collection d’images désactivées.

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Appelé par le cadre pour dessiner le bouton de la boîte combo dans le volet **Commandes** de la boîte de dialogue **Customize.**

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton boîte combo.

*Rect*<br/>
[dans] Le rectangle de délimitation du bouton de la boîte combo.

*bSélectré*<br/>
[dans] VRAI si le bouton de la boîte combo est sélectionné; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

La largeur, en pixels, du bouton de la boîte combo.

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Appelé par le cadre pour définir la police de bouton boîte combo lorsque la police d’application change.

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove

Appelé par le cadre pour changer l’emplacement du bouton boîte combo lorsque la barre d’outils parent se déplace.

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow

Appelé par le cadre lorsque le bouton de la boîte combo est caché ou affiché.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
[dans] Que ce soit pour cacher ou afficher le bouton de la boîte combo.

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize

Appelé par le cadre pour changer la taille du bouton boîte combo lorsque la barre d’outils parent change de taille.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Paramètres

*iSize (en)*<br/>
[dans] La nouvelle largeur du bouton de la boîte combo.

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip

Appelé par le cadre lorsque l’utilisateur modifie la pointe de l’outil pour le bouton boîte combo.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Pointeur vers la fenêtre parente pour le bouton boîte combo.

*iButtonIndex*<br/>
[dans] ID du bouton de la boîte combo.

*wndToolTip*<br/>
[dans] La pointe de l’outil à associer avec le bouton boîte combo.

*Str*<br/>
[dans] Le texte de pointe d’outil.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode gère l’événement; autrement, FALSE.

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems

Supprime tous les éléments de la liste et modifie les cases.

```
void RemoveAllItems();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments de la boîte de liste et modifie le contrôle d’une boîte combo.

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem

Sélectionne un élément dans la boîte de liste.

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément dans la boîte de liste.

*bNotifier*<br/>
[dans] VRAI pour notifier le bouton de la boîte combo de la sélection; autrement FALSE.

*dwData dwData*<br/>
[dans] Les données associées à un élément dans la boîte de liste.

*lpszText*<br/>
[dans] Le texte d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll

Sélectionne un élément dans la boîte de liste d’un bouton de boîte combo qui a un ID de commande spécifié.

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

*uiCmd uiCmd*<br/>
[dans] L’ID de commande du bouton de la boîte combo qui contient la boîte de liste.

*iIndex (en)*<br/>
[dans] L’index zéro de l’élément dans la boîte de liste. Une valeur de -1 supprime toute sélection actuelle dans la boîte de liste et efface la boîte de modification.

*dwData dwData*<br/>
[dans] Les données d’un élément dans la boîte de liste.

*lpszText*<br/>
[dans] Le texte d’un élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize

Lit cet objet à partir d’une archive ou l’écrit à une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
[dans, dehors] L’objet `CArchive` de sérialisation.

### <a name="remarks"></a>Notes

Les paramètres `CArchive` de l’objet déterminent si cette méthode se lit ou écrit à l’archive.

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData

Remplit l’objet spécifié `CAccessibilityData` en utilisant les données d’accessibilité à partir du bouton de la boîte combo.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
[dans] La fenêtre parente du bouton de la boîte combo.

*data*<br/>
[out] Un `CAccessibilityData` objet qui reçoit les données d’accessibilité du bouton de la boîte combo.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

Définit la position verticale des boutons de boîte combo dans l’application.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Paramètres

*bCenterVert (en)*<br/>
[dans] VRAI pour centrer le bouton de boîte combo dans la barre d’outils; FALSE pour aligner le bouton de la boîte combo en haut de la barre d’outils.

### <a name="remarks"></a>Notes

Par défaut, les boutons de la boîte combo sont alignés en haut.

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID

Définit l’ID de ressource de menu raccourci pour le bouton de boîte de combo.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Paramètres

*uiResID*<br/>
[dans] L’ID de ressources de menu raccourci.

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

Définit la hauteur de la boîte de liste lorsqu’elle est tombée.

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Paramètres

*nHeight (en)*<br/>
[dans] La hauteur, en pixels, de la boîte de liste.

### <a name="remarks"></a>Notes

La hauteur par défaut est de 150 pixels.

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

Définit l’apparence de style plat des boutons de boîte combo dans l’application.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Paramètres

*bFlat (en)*<br/>
[dans] VRAI pour une apparence de style plat; autrement FALSE.

### <a name="remarks"></a>Notes

Le style plat par défaut pour les boutons de boîte combo est FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle

Définit le style spécifié pour le bouton de la boîte combo et redessiner le contrôle s’il n’est pas désactivé.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
[dans] Une combinaison bitwise (OU) de styles de barre d’outils.

### <a name="remarks"></a>Notes

Pour une liste de styles de boutons de barre d’outils voir [Styles de contrôle ToolBar](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a>CMFCToolBarComboBoxButton::SetText

Définit le texte dans la boîte de modification du bouton de la boîte combo.

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
[dans] Pointeur vers une chaîne qui contient le texte pour la boîte de modification.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Classe CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::RemplacerButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : placement de contrôles dans les barres d'outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
