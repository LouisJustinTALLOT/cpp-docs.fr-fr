---
title: Cmfctoolbarcomboboxbutton, classe
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
ms.openlocfilehash: e3c124103aa95d9db5095e438a6b21d46c7cb35d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218404"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Cmfctoolbarcomboboxbutton, classe

Un bouton de barre d’outils qui contient un contrôle combo box ( [CComboBox (classe)](../../mfc/reference/ccombobox-class.md)).

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
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Ajoute un élément à la fin de la liste déroulante.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Ajoute un élément à la liste déroulante. L’ordre des éléments dans la liste est spécifié par `Compare`.|
|[CMFCToolBarComboBoxButton::Compare](#compare)|Compare deux éléments. Appelé pour trier les éléments `AddSortedItems` ajoute à la liste déroulante.|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Crée un nouveau contrôle d’édition pour le bouton de zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Supprime un élément de la liste déroulante.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Retourne l’index de l’élément qui contient une chaîne spécifiée.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Retourne un pointeur vers le bouton de zone de liste modifiable avec un ID de commande spécifiée.|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Retourne un pointeur vers le contrôle de zone de liste déroulante qui est incorporé dans le bouton de zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Retourne le nombre d’éléments dans la liste déroulante de la zone de liste.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Recherche la liste déroulante bouton de zone qui a un ID de commande spécifié. Retourne le nombre d’éléments dans la liste déroulante zone de liste de ce bouton.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Retourne l’index de l’élément sélectionné dans la liste déroulante de la zone de liste.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Recherche la liste déroulante de bouton de zone qui possède un ID de commande spécifié et retourne l’index de l’élément sélectionné dans la liste déroulante zone de liste de ce bouton.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Retourne un pointeur vers le contrôle d’édition qui est incorporé dans le bouton de zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Retourne la chaîne qui est associée à un index spécifié dans la liste déroulante de la zone de liste.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Recherche la liste déroulante de bouton de zone qui possède un ID de commande spécifié et retourne la chaîne qui est associée à un index dans la zone de liste modifiable de ce bouton.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Retourne la valeur de 32 bits qui est associée à un index spécifié dans la liste déroulante de la zone de liste.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Recherche la liste déroulante de bouton de zone qui possède un ID de commande spécifié et retourne la valeur de 32 bits qui est associée à un index dans la zone de liste modifiable de ce bouton.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Recherche la liste déroulante bouton de zone qui a un ID de commande spécifié. Récupère la valeur de 32 bits qui est associé à un index dans la zone de liste modifiable de ce bouton et renvoie la valeur de 32 bits en tant que pointeur.|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Retourne le texte à partir du contrôle d’édition de la zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Recherche la liste déroulante de bouton de zone qui a un ID de commande spécifié et retourne le texte de contrôle d’édition de ce bouton.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Détermine si les boutons de zone de liste déroulante dans l’application sont centrés ou alignés avec le haut de la barre d’outils.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Détermine si les boutons de zone de liste déroulante dans l’application ont une apparence à deux dimensions.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Supprime tous les éléments de la liste de zone et de modifier le contrôle de zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Sélectionne un élément dans la zone de liste déroulante en fonction de son index, une valeur 32 bits ou une chaîne et en avertit le contrôle de zone de liste déroulante sur la sélection.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Recherche la liste déroulante bouton de zone qui a un ID de commande spécifié. Appels `SelectItem` pour sélectionner un élément dans la zone de liste modifiable de ce bouton en fonction de sa chaîne, un index ou une valeur 32 bits.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Spécifie si les boutons de zone de liste déroulante dans l’application sont centrés verticalement ou alignés avec le haut de la barre d’outils.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Définit la hauteur de la zone de liste déroulante.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Spécifie si les boutons de zone de liste déroulante dans l’application ont une apparence à deux dimensions.|

## <a name="remarks"></a>Notes

Pour ajouter un bouton de zone de liste déroulante à une barre d’outils, procédez comme suit :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Construire un `CMFCToolBarComboBoxButton` objet.

3. Dans le Gestionnaire de messages qui traite le message AFX_WM_RESETTOOLBAR, remplacez le bouton fictif avec le nouveau bouton de zone de liste déroulante à l’aide de [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations, consultez [Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md). Pour obtenir un exemple d’un bouton de barre d’outils de zone de liste déroulante, consultez l’exemple de projet VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCToolBarComboBoxButton` . L’exemple montre comment activer les cases à modifier et de la liste déroulante, définissez des cases à la position verticale de la zone de liste déroulante dans l’application, définir la hauteur de la zone de liste lorsqu’il est déplacé vers le bas, définir l’apparence de style à deux dimensions de boutons de zone de liste modifiable dans l’application et définir le texte dans la zone d’édition de la liste déroulante bouton de zone. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtoolbarcomboboxbutton.h

##  <a name="additem"></a>  CMFCToolBarComboBoxButton::AddItem

Ajoute un élément unique à la zone de liste.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*lpszItem*<br/>
[in] Le texte de l’élément à ajouter à la zone de liste.

*dwData*<br/>
[in] Les données associées à l’élément à ajouter à la zone de liste.

### <a name="return-value"></a>Valeur de retour

L’index du dernier élément dans la zone de liste.

### <a name="remarks"></a>Notes

N’utilisez pas cette méthode lorsque le style de zone de liste est trié.

Si le texte de l’élément est déjà dans la zone de liste, les nouvelles données sont stockées avec l’élément existant. La recherche de l’élément respecte la casse.

##  <a name="addsorteditem"></a>  CMFCToolBarComboBoxButton::AddSortedItem

Ajoute un élément à la zone de liste dans l’ordre défini par le [comparer](#compare) (méthode).

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*lpszItem*<br/>
[in] Le texte de l’élément à ajouter à la zone de liste.

*dwData*<br/>
[in] Les données associées à l’élément à ajouter à la zone de liste.

### <a name="return-value"></a>Valeur de retour

Index de l’élément qui a été ajouté à la zone de liste.

### <a name="remarks"></a>Notes

Cette fonction permet d’ajouter des éléments à la zone de liste dans un ordre spécifique.

##  <a name="canbestretched"></a>  CMFCToolBarComboBoxButton::CanBeStretched

Indique si la taille de bouton de la liste déroulante peut modifier.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE.

##  <a name="cmfctoolbarcomboboxbutton"></a>  CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Construit un [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objet.

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[in] L’ID de commande du bouton Nouveau.

*iImage*<br/>
[in] L’index d’image de l’image associée au bouton Nouveau.

*dwStyle*<br/>
[in] Le style du bouton Nouveau.

*iWidth*<br/>
[in] La largeur, en pixels, du bouton Nouveau.

### <a name="remarks"></a>Notes

La largeur par défaut est 150 pixels.

Pour obtenir la liste des styles de bouton de barre d’outils, consultez [Styles de contrôle de barre d’outils](../../mfc/reference/toolbar-control-styles.md)

##  <a name="cleardata"></a>  CMFCToolBarComboBoxButton::ClearData

Supprime des données définies par l’utilisateur.

```
virtual void ClearData();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Substituez cette méthode dans une classe dérivée si vous souhaitez supprimer toutes les données définies par l’utilisateur.

##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare

Compare deux chaînes.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Paramètres

*lpszItem1*<br/>
[in] La première chaîne à comparer.

*lpszItem2*<br/>
[in] La deuxième chaîne à comparer.

### <a name="return-value"></a>Valeur de retour

Une valeur qui indique la relation lexicographique respect de la casse entre les chaînes. Le tableau suivant répertorie les valeurs possibles :

|Value|Description|
|-----------|-----------------|
|\<0|La première chaîne est inférieure à la seconde.|
|0|La première chaîne est égale à la seconde.|
|>0|La première chaîne est supérieure à la seconde.|

### <a name="remarks"></a>Notes

Substituez cette méthode pour modifier la façon dont les éléments sont triés dans la zone de liste.

La comparaison respecte la casse.

Cette méthode est appelée uniquement à partir de la [AddSortedItem](#addsorteditem) (méthode).

##  <a name="copyfrom"></a>  CMFCToolBarComboBoxButton::CopyFrom

Copie l’état de l’objet `CMFCToolBarComboBoxButton` à l’objet actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[in] La source `CMFCToolBarComboBoxButton` objet.

##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo

Crée une nouvelle zone de liste déroulante pour le bouton de zone de liste déroulante.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Pointeur vers la fenêtre parent du bouton.

*rect*<br/>
[in] Rectangle englobant de la zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la nouvelle zone de liste déroulante si la méthode a réussi ; Sinon, NULL.

##  <a name="createedit"></a>  CMFCToolBarComboBoxButton::CreateEdit

Crée une nouvelle zone d’édition pour le bouton de zone de liste déroulante.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Pointeur vers la fenêtre parent du bouton.

*rect*<br/>
[in] Rectangle englobant de la zone d’édition.

*dwEditStyle*<br/>
[in] Style de contrôle de la zone d’édition.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la nouvelle zone d’édition si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsqu’il crée une nouvelle zone d’édition pour un bouton de zone de liste déroulante. Substituez cette méthode pour modifier comment [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) est créé.

##  <a name="deleteitem"></a>  CMFCToolBarComboBoxButton::DeleteItem

Supprime un élément spécifié à partir de la zone de liste.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
  BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
[in] Index de base zéro de l’élément à supprimer.

*dwData*<br/>
[in] Les données associées à l’élément à supprimer.

*lpszText*<br/>
[in] Le texte de l’élément à supprimer. S’il existe plusieurs éléments portant le même texte, le premier élément est supprimé.

### <a name="return-value"></a>Valeur de retour

TRUE si l’élément a été trouve et a été supprimé ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData

Données définies par l’utilisateur de doublons.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Substituez cette méthode dans une classe dérivée si vous souhaitez copier toutes les données définies par l’utilisateur.

##  <a name="enablewindow"></a>  CMFCToolBarComboBoxButton::EnableWindow

Active ou désactive les zones d’édition et de la liste déroulante.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[in] TRUE pour activer les cases à modifier et de liste déroulante ; FALSE pour désactiver les cases à modifier et de la liste déroulante.

### <a name="remarks"></a>Notes

Lorsque désactivée, les contrôles ne peut pas devenir actives et ne peut pas accepter l’entrée d’utilisateur.

##  <a name="exporttomenubutton"></a>  CMFCToolBarComboBoxButton::ExportToMenuButton

Copie une chaîne à partir de la table de chaînes d’application au menu spécifié à l’aide de la commande de bouton de zone de liste déroulante ID.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Paramètres

*menuButton*<br/>
[out] Référence à un bouton de menu.

### <a name="return-value"></a>Valeur de retour

Toujours TRUE.

##  <a name="finditem"></a>  CMFCToolBarComboBoxButton::FindItem

Retourne l’index du premier élément dans la zone de liste qui contient une chaîne spécifiée.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
[in] Le texte à rechercher dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément ; ou CB_ERR si l’élément est introuvable.

### <a name="remarks"></a>Notes

##  <a name="getbycmd"></a>  CMFCToolBarComboBoxButton::GetByCmd

Obtient un pointeur vers le bouton de zone de liste déroulante qui possède un ID de commande spécifiée.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] L’ID de commande d’un bouton de zone de liste déroulante.

*bIsFocus*<br/>
[in] True permet de rechercher uniquement axée boutons ; FALSE pour rechercher tous les boutons.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un bouton de zone de liste déroulante ; ou NULL si le bouton n’est pas trouvé.

### <a name="remarks"></a>Notes

##  <a name="getcombobox"></a>  CMFCToolBarComboBoxButton::GetComboBox

Retourne un pointeur vers la zone de liste déroulante dans la liste déroulante bouton de zone.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le [CComboBox (classe)](../../mfc/reference/ccombobox-class.md) de l’objet si la méthode a réussi ; sinon, NULL.

### <a name="remarks"></a>Notes

##  <a name="getcontextmenuid"></a>  CMFCToolBarComboBoxButton::GetContextMenuID

Obtient l’ID de ressource de menu contextuel pour le bouton de zone de liste déroulante.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valeur de retour

L’ID de ressource de menu contextuel

##  <a name="getcount"></a>  CMFCToolBarComboBoxButton::GetCount

Retourne le nombre d’éléments dans la zone de liste.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la zone de liste.

### <a name="remarks"></a>Notes

##  <a name="getcountall"></a>  CMFCToolBarComboBoxButton::GetCountAll

Obtient le nombre d’éléments dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifiée.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] L’ID de commande d’un bouton de zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la zone de liste ; Sinon, CB_ERR si la liste déroulante zone de bouton est introuvable.

### <a name="remarks"></a>Notes

##  <a name="getcursel"></a>  CMFCToolBarComboBoxButton::GetCurSel

Obtient l’index de l’élément actuellement sélectionné dans la zone de liste.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

L’index de l’élément actuellement sélectionné dans la zone de liste ; ou CB_ERR si aucun élément n’est sélectionné.

### <a name="remarks"></a>Notes

L’index de zone de liste est de base zéro.

##  <a name="getcurselall"></a>  CMFCToolBarComboBoxButton::GetCurSelAll

Retourne l’index de l’élément actuellement sélectionné dans la zone de liste d’une zone de liste déroulante bouton de zone qui a un ID de commande spécifié.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] L’ID de commande d’un bouton de zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément actuellement sélectionné dans la zone de liste ; Sinon, CB_ERR si aucun élément n’est sélectionné ou un bouton de zone de liste déroulante est introuvable.

### <a name="remarks"></a>Notes

L’index de zone de liste est de base zéro.

##  <a name="geteditctrl"></a>  CMFCToolBarComboBoxButton::GetEditCtrl

Retourne un pointeur vers la zone d’édition dans la liste déroulante bouton de zone.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la zone d’édition si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

##  <a name="gethwnd"></a>  CMFCToolBarComboBoxButton::GetHwnd

Retourne le handle de fenêtre pour la zone de liste déroulante.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valeur de retour

Le handle de fenêtre, ou NULL si la zone de liste déroulante n’est pas associée à un objet de fenêtre.

##  <a name="getitem"></a>  CMFCToolBarComboBoxButton::GetItem

Retourne la chaîne associée à un élément à l’index spécifié dans la zone de liste.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
[in] Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la chaîne qui est associé à l’élément ; Sinon, valeur NULL si le paramètre d’index n’est pas valide, ou si le paramètre d’index est -1 et il n’existe aucun élément sélectionné dans la zone de liste déroulante.

### <a name="remarks"></a>Notes

Un paramètre d’index de -1 retourne la chaîne de l’élément actuellement sélectionné.

##  <a name="getitemall"></a>  CMFCToolBarComboBoxButton::GetItemAll

Retourne la chaîne associée à un élément à l’index spécifié dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifiée.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] L’ID de commande d’un bouton de zone de liste déroulante.

*iIndex*<br/>
[in] Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la chaîne de l’élément si la méthode a réussi ; Sinon, NULL si l’index n’est pas valide, un bouton de zone de liste déroulante est introuvable, ou si l’index est -1 et il n’existe aucun élément sélectionné dans la zone de liste déroulante.

### <a name="remarks"></a>Notes

Une valeur d’index de -1 retourne la chaîne de l’élément actuellement sélectionné.

##  <a name="getitemdata"></a>  CMFCToolBarComboBoxButton::GetItemData

Retourne les données associées à un élément à un index spécifique dans la zone de liste.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
[in] Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

Les données associées à l’élément ; ou 0 si l’élément n’existe pas.

### <a name="remarks"></a>Notes

Un paramètre d’index de -1 retourne les données associées à l’élément actuellement sélectionné.

##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll

Retourne les données associées à un élément à un index spécifique dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifique.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] L’ID de commande d’un bouton de zone de liste déroulante.

*iIndex*<br/>
[in] Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

Les données associées à l’élément si la méthode a réussi ; Sinon, 0 si l’index spécifié n’est pas valide, ou CB_ERR si la liste déroulante zone de bouton est introuvable.

### <a name="remarks"></a>Notes

Un paramètre d’index de -1 retourne les données associées à l’élément actuellement sélectionné.

##  <a name="getitemdataptrall"></a>  CMFCToolBarComboBoxButton::GetItemDataPtrAll

Retourne les données associées à un élément à un index spécifique dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifique. Ces données sont retournées en tant que pointeur.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] ID de commande du bouton de zone de liste déroulante.

*iIndex*<br/>
[in] Index de base zéro d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

Un pointeur associé à l’élément si la méthode a réussi ; Sinon,-1 si une erreur se produit, ou NULL si la liste déroulante zone de bouton est introuvable.

### <a name="remarks"></a>Notes

##  <a name="getprompt"></a>  CMFCToolBarComboBoxButton::GetPrompt

Retourne la chaîne d’invite pour la liste déroulante de bouton de zone.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Valeur de retour

La chaîne d’invite.

### <a name="remarks"></a>Notes

Cette méthode n’est actuellement pas implémentée.

##  <a name="gettext"></a>  CMFCToolBarComboBoxButton::GetText

Obtient le texte dans la zone d’édition.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Valeur de retour

Le texte dans la zone d’édition.

### <a name="remarks"></a>Notes

##  <a name="gettextall"></a>  CMFCToolBarComboBoxButton::GetTextAll

Obtient le texte dans la zone d’édition d’un bouton de zone de liste déroulante qui possède un ID de commande spécifiée.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] L’ID de commande d’un bouton de zone de liste déroulante spécifique.

### <a name="return-value"></a>Valeur de retour

Le texte dans la zone d’édition si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

##  <a name="hasfocus"></a>  CMFCToolBarComboBoxButton::HasFocus

Indique si la zone de liste déroulante possède actuellement le focus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la zone de liste modifiable a actuellement le focus ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode retourne également la valeur TRUE si n’importe quelle fenêtre enfant de la zone de liste modifiable a actuellement le focus.

##  <a name="iscentervert"></a>  CMFCToolBarComboBoxButton::IsCenterVert

Retourne la position verticale de boutons de zone de liste modifiable dans l’application.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Valeur de retour

TRUE si les boutons sont centrées ; FALSE si les boutons sont alignés en haut.

### <a name="remarks"></a>Notes

##  <a name="isflatmode"></a>  CMFCToolBarComboBoxButton::IsFlatMode

Retourne l’apparence de style à deux dimensions de boutons de zone de liste modifiable dans l’application.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Valeur de retour

TRUE si les boutons ont un style à deux dimensions ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Le style à deux dimensions par défaut pour les boutons de zone de liste déroulante est FALSE.

##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf

Indique si le handle spécifié est associé avec le bouton de zone de liste déroulante, ou l’un de ses enfants.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Paramètres

*hwnd*<br/>
[in] Un handle de fenêtre.

### <a name="return-value"></a>Valeur de retour

TRUE si le handle est associé le bouton de zone de liste déroulante, ou l’un de ses enfants ; Sinon, FALSE.

##  <a name="isribbonbutton"></a>  CMFCToolBarComboBoxButton::IsRibbonButton

Indique si le bouton de zone de liste déroulante réside sur un panneau de ruban.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Valeur de retour

Toujours la valeur FALSE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode retourne toujours FALSE, ce qui signifie que le bouton de zone de liste déroulante n’est jamais affiché dans un panneau de ruban.

##  <a name="iswindowvisible"></a>  CMFCToolBarComboBoxButton::IsWindowVisible

Retourne l’état de visibilité de la liste déroulante de bouton de zone.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Valeur de retour

L’état de visibilité du bouton de zone de liste déroulante.

##  <a name="notifycommand"></a>  CMFCToolBarComboBoxButton::NotifyCommand

Indique si le bouton de zone de liste déroulante traite le message.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Paramètres

*iNotifyCode*<br/>
[in] Le message de notification qui est associé à la commande.

### <a name="return-value"></a>Valeur de retour

Indique si le bouton de zone de liste déroulante traite le message.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarComboBoxButton::OnAddToCustomizePage

Appelé par le framework lorsque le bouton est ajouté à la **personnaliser** boîte de dialogue.

```
virtual void OnAddToCustomizePage();
```

##  <a name="oncalculatesize"></a>  CMFCToolBarComboBoxButton::OnCalculateSize

Appelé par l’infrastructure pour calculer la taille du bouton.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Le contexte de périphérique qui affiche le bouton de zone de liste déroulante.

*sizeDefault*<br/>
[in] La taille par défaut, la liste déroulante du bouton de zone.

*bHorz*<br/>
[in] L’état d’ancrage de la barre d’outils parent. TRUE si la barre d’outils est ancrée horizontalement et FALSE lorsque la barre d’outils est ancrée verticalement.

### <a name="return-value"></a>Valeur de retour

Un `SIZE` structure qui contient les dimensions du bouton de zone de liste déroulante, en pixels.

##  <a name="onchangeparentwnd"></a>  CMFCToolBarComboBoxButton::OnChangeParentWnd

Appelé par le framework lorsque le bouton de zone de liste déroulante est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Pointeur vers la nouvelle barre d’outils parent.

##  <a name="onclick"></a>  CMFCToolBarComboBoxButton::OnClick

Appelé par le framework lorsque l’utilisateur clique sur le bouton de zone de liste déroulante.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] Pointeur vers la fenêtre parente de la liste déroulante du bouton de zone.

*bDelay*<br/>
[in] Réservé pour une utilisation dans une classe dérivée.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode gère l’événement ; Sinon, FALSE.

##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor

Appelé par le framework lorsque l’utilisateur modifie la couleur de la barre d’outils parent pour définir la liste déroulante couleur de bouton de zone.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Le contexte de périphérique qui affiche le bouton de zone de liste déroulante.

*nCtlColor*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur de retour

Handle vers le pinceau de l’infrastructure utilise pour peindre l’arrière-plan du bouton de zone de liste déroulante.

### <a name="remarks"></a>Notes

Cette méthode définit également la couleur de texte de zone de liste déroulante bouton.

##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw

Appelé par l’infrastructure pour dessiner le bouton de zone de liste déroulante en utilisant les options et les styles spécifiés.

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
[in] Le contexte de périphérique qui affiche le bouton.

*rect*<br/>
[in] Le rectangle englobant du bouton.

*pImages*<br/>
[in] Collection d’images associée au bouton.

*bHorz*<br/>
[in] L’état d’ancrage de la barre d’outils parent. TRUE si la barre d’outils est ancrée horizontalement et FALSE lorsque la barre d’outils est ancrée verticalement.

*bCustomizeMode*<br/>
[in] Indique si l’application est en mode de personnalisation.

*bHighlight*<br/>
[in] Si vous souhaitez dessiner le bouton de zone de liste déroulante en surbrillance.

*bDrawBorder*<br/>
[in] Si vous souhaitez dessiner le bouton de zone de liste modifiable avec une bordure.

*bGrayDisabledButtons*<br/>
[in] True pour dessiner un ombrage les boutons désactivés ; FALSE pour utiliser la collection d’images désactivé.

##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Appelé par l’infrastructure pour dessiner le bouton de zone de liste déroulante dans le **commandes** volet de la **personnaliser** boîte de dialogue.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Le contexte de périphérique qui affiche le bouton de zone de liste déroulante.

*rect*<br/>
[in] Le rectangle englobant la zone de liste déroulante du bouton de zone.

*bSelected*<br/>
[in] TRUE si le bouton de zone de liste déroulante est sélectionné ; Sinon, FALSE.

### <a name="return-value"></a>Valeur de retour

La largeur, en pixels, du bouton de zone de liste déroulante.

##  <a name="onglobalfontschanged"></a>  CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Appelé par l’infrastructure pour définir la liste déroulante Police de bouton de zone lors de la modification de la police de l’application.

```
virtual void OnGlobalFontsChanged();
```

##  <a name="onmove"></a>  CMFCToolBarComboBoxButton::OnMove

Appelé par l’infrastructure pour modifier l’emplacement du bouton de zone de liste déroulante lorsque la barre d’outils parent se déplace.

```
virtual void OnMove();
```

##  <a name="onshow"></a>  CMFCToolBarComboBoxButton::OnShow

Appelé par le framework lorsque le bouton de zone de liste déroulante est masqué ou affiché.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
[in] Il faut masquer ou afficher le bouton de zone de liste déroulante.

##  <a name="onsize"></a>  CMFCToolBarComboBoxButton::OnSize

Appelé par l’infrastructure pour modifier la taille du bouton de zone de liste déroulante lorsque la barre d’outils parent change de taille.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Paramètres

*iSize*<br/>
[in] La nouvelle largeur du bouton de zone de liste déroulante.

##  <a name="onupdatetooltip"></a>  CMFCToolBarComboBoxButton::OnUpdateToolTip

Appelé par le framework lorsque l’utilisateur modifie l’info-bulle pour le bouton de zone de liste déroulante.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Pointeur vers la fenêtre parente pour le bouton de zone de liste déroulante.

*iButtonIndex*<br/>
[in] ID de la liste déroulante du bouton de zone.

*wndToolTip*<br/>
[in] L’info-bulle à associer avec le bouton de zone de liste déroulante.

*str*<br/>
[in] Le texte info-bulle.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode gère l’événement ; Sinon, FALSE.

##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems

Supprime tous les éléments dans les zones de liste et les modifier.

```
void RemoveAllItems();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments de la liste de zone et de modifier le contrôle de zone de liste déroulante.

##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem

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
[in] Index de base zéro d’un élément dans la zone de liste.

*bNotify*<br/>
[in] TRUE pour informer le bouton de zone de liste déroulante de la sélection ; Sinon, FALSE.

*dwData*<br/>
[in] Les données associées à un élément dans la zone de liste.

*lpszText*<br/>
[in] Le texte d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll

Sélectionne un élément dans la zone de liste d’un bouton de zone de liste déroulante qui possède un ID de commande spécifiée.

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
[in] ID de commande du bouton de zone de liste déroulante qui contient la zone de liste.

*iIndex*<br/>
[in] Index de base zéro de l’élément dans la zone de liste. La valeur -1 supprime la sélection actuelle dans la zone de liste et efface la zone d’édition.

*dwData*<br/>
[in] Les données d’un élément dans la zone de liste.

*lpszText*<br/>
[in] Le texte d’un élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="serialize"></a>  CMFCToolBarComboBoxButton::Serialize

Lit de cet objet à partir d’une archive ou écrit dans une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
[in, out] Le `CArchive` objet à sérialiser.

### <a name="remarks"></a>Notes

Paramètres dans le `CArchive` objet déterminer si cette méthode lit ou écrit dans l’archive.

##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData

Remplit spécifié `CAccessibilityData` objet à l’aide des données d’accessibilité à partir du bouton de zone de liste déroulante.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
[in] La fenêtre parente, la liste déroulante du bouton de zone.

*data*<br/>
[out] Un `CAccessibilityData` objet qui reçoit les données d’accessibilité à partir du bouton de zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi ; Sinon, FALSE.

##  <a name="setcentervert"></a>  CMFCToolBarComboBoxButton::SetCenterVert

Définit la position verticale de boutons de zone de liste déroulante de l’application.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Paramètres

*bCenterVert*<br/>
[in] TRUE pour centrer le bouton de zone de liste déroulante dans la barre d’outils ; FALSE pour aligner le bouton de zone de liste déroulante en haut de la barre d’outils.

### <a name="remarks"></a>Notes

Par défaut, les boutons de zone de liste déroulante sont alignés en haut.

##  <a name="setcontextmenuid"></a>  CMFCToolBarComboBoxButton::SetContextMenuID

Définit l’ID de ressource de menu contextuel pour la liste déroulante de bouton de zone.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Paramètres

*uiResID*<br/>
[in] L’ID de ressource de menu contextuel

##  <a name="setdropdownheight"></a>  CMFCToolBarComboBoxButton::SetDropDownHeight

Définit la hauteur de la zone de liste lorsqu’il est déplacé vers le bas.

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Paramètres

*nHeight*<br/>
[in] La hauteur, en pixels, de la zone de liste.

### <a name="remarks"></a>Notes

La hauteur par défaut est 150 pixels.

##  <a name="setflatmode"></a>  CMFCToolBarComboBoxButton::SetFlatMode

Définit l’apparence de style à deux dimensions de boutons de zone de liste déroulante de l’application.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Paramètres

*bFlat*<br/>
[in] TRUE pour un aspect de style à deux dimensions ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Le style à deux dimensions par défaut pour les boutons de zone de liste déroulante est FALSE.

##  <a name="setstyle"></a>  CMFCToolBarComboBoxButton::SetStyle

Définit le style spécifié pour la liste déroulante bouton de zone et redessine le contrôle s’il n’est pas désactivé.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
[in] Une combinaison (OR) au niveau du bit de styles de barre d’outils.

### <a name="remarks"></a>Notes

Pour obtenir la liste des styles de bouton de barre d’outils, consultez [Styles de contrôle de barre d’outils](../../mfc/reference/toolbar-control-styles.md)

##  <a name="settext"></a>  CMFCToolBarComboBoxButton::SetText

Définit le texte dans la zone d’édition de la liste déroulante de bouton de zone.

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
[in] Pointeur vers une chaîne qui contient le texte de la zone d’édition.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
