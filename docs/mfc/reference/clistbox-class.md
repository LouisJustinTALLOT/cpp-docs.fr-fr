---
title: CListBox, classe
description: Description de la classe MFC CListBox et de ses fonctions membres.
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 5c3337641dcfc720a5f9fbccf5bb0614e97c3b54
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518424"
---
# <a name="clistbox-class"></a>CListBox, classe

Fournit les fonctionnalités d'une zone de liste Windows.

## <a name="syntax"></a>Syntaxe

```
class CListBox : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Construit un objet `CListBox`.|

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|Ajoute une chaîne à une zone de liste.|
|[CListBox::CharToItem](#chartoitem)|Substituez pour fournir une gestion de WM_CHAR personnalisée pour les zones de liste owner-draw qui n’ont pas de chaînes.|
|[CListBox::CompareItem](#compareitem)|Appelé par l’infrastructure pour déterminer la position d’un nouvel élément dans une zone de liste owner-draw triée.|
|[CListBox::Create](#create)|Crée la zone de liste Windows et l’attache à l’objet `CListBox`.|
|[CListBox::DeleteItem](#deleteitem)|Appelé par le Framework lorsque l’utilisateur supprime un élément d’une zone de liste owner-draw.|
|[CListBox::DeleteString](#deletestring)|Supprime une chaîne d’une zone de liste.|
|[CListBox::Dir](#dir)|Ajoute des noms de fichiers, des lecteurs, ou les deux, du répertoire actif à une zone de liste.|
|[CListBox::DrawItem](#drawitem)|Appelée par l’infrastructure quand un aspect visuel d’une zone de liste owner-draw change.|
|[CListBox::FindString](#findstring)|Recherche une chaîne dans une zone de liste.|
|[CListBox :: FindExactString](#findstringexact)|Recherche la première chaîne de zone de liste qui correspond à une chaîne spécifiée.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Récupère l’index de base zéro de l’élément d’ancrage actuel dans une zone de liste.|
|[CListBox::GetCaretIndex](#getcaretindex)|Détermine l’index de l’élément qui a le rectangle de focus dans une zone de liste à sélection multiple.|
|[CListBox::GetCount](#getcount)|Retourne le nombre de chaînes dans une zone de liste.|
|[CListBox::GetCurSel](#getcursel)|Retourne l’index de base zéro de la chaîne actuellement sélectionnée dans une zone de liste.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Retourne la largeur, en pixels, pendant laquelle une zone de liste peut faire défiler horizontalement.|
|[CListBox::GetItemData](#getitemdata)|Retourne une valeur associée à l’élément de zone de liste.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Retourne un pointeur désignant un élément de zone de liste.|
|[CListBox::GetItemHeight](#getitemheight)|Détermine la hauteur des éléments dans une zone de liste.|
|[CListBox::GetItemRect](#getitemrect)|Retourne le rectangle englobant de l’élément de zone de liste tel qu’il est actuellement affiché.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Récupère le nombre d’éléments par colonne.|
|[CListBox::GetLocale](#getlocale)|Récupère l’identificateur de paramètres régionaux pour une zone de liste.|
|[CListBox::GetSel](#getsel)|Retourne l’état de sélection d’un élément de zone de liste.|
|[CListBox::GetSelCount](#getselcount)|Retourne le nombre de chaînes actuellement sélectionnées dans une zone de liste à sélection multiple.|
|[CListBox::GetSelItems](#getselitems)|Retourne les index des chaînes actuellement sélectionnées dans une zone de liste.|
|[CListBox::GetText](#gettext)|Copie un élément de zone de liste dans une mémoire tampon.|
|[CListBox::GetTextLen](#gettextlen)|Retourne la longueur, en octets, d’un élément de zone de liste.|
|[CListBox::GetTopIndex](#gettopindex)|Retourne l’index de la première chaîne visible dans une zone de liste.|
|[CListBox::InitStorage](#initstorage)|Préalloue des blocs de mémoire pour les éléments de zone de liste et les chaînes.|
|[CComboBox::InsertString](#insertstring)|Insère une chaîne à un emplacement spécifique dans une zone de liste.|
|[CListBox :: ItemFromPoint](#itemfrompoint)|Retourne l’index de l’élément de zone de liste le plus proche d’un point.|
|[CListBox::MeasureItem](#measureitem)|Appelée par l’infrastructure quand une zone de liste owner-draw est créée pour déterminer les dimensions de la zone de liste.|
|[CListBox::ResetContent](#resetcontent)|Efface toutes les entrées d’une zone de liste.|
|[CListBox::SelectString](#selectstring)|Recherche et sélectionne une chaîne dans une zone de liste à sélection unique.|
|[CListBox::SelItemRange](#selitemrange)|Sélectionne ou désélectionne une plage de chaînes dans une zone de liste à sélection multiple.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Définit l’ancre dans une zone de liste à sélection multiple pour commencer une sélection étendue.|
|[CListBox::SetCaretIndex](#setcaretindex)|Définit le rectangle de focus sur l’élément à l’index spécifié dans une zone de liste à sélection multiple.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Définit la largeur de colonne d’une zone de liste multicolonne.|
|[CListBox::SetCurSel](#setcursel)|Sélectionne une chaîne de zone de liste.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Définit la largeur, en pixels, pendant laquelle une zone de liste peut faire défiler horizontalement.|
|[CListBox::SetItemData](#setitemdata)|Définit une valeur associée à l’élément de zone de liste.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Définit un pointeur vers l’élément de zone de liste.|
|[CListBox::SetItemHeight](#setitemheight)|Définit la hauteur des éléments dans une zone de liste.|
|[CListBox::SetLocale](#setlocale)|Définit l’identificateur de paramètres régionaux pour une zone de liste.|
|[CListBox::SetSel](#setsel)|Sélectionne ou désélectionne un élément de zone de liste dans une zone de liste à sélection multiple.|
|[CListBox::SetTabStops](#settabstops)|Définit les positions des taquets de tabulation dans une zone de liste.|
|[CListBox::SetTopIndex](#settopindex)|Définit l’index de base zéro de la première chaîne visible dans une zone de liste.|
|[CListBox::VKeyToItem](#vkeytoitem)|Substituez pour fournir une gestion des WM_KEYDOWN personnalisées pour les zones de liste avec le jeu de styles LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Notes

Une zone de liste affiche une liste d’éléments, tels que des noms de fichiers, que l’utilisateur peut afficher et sélectionner.

Dans une zone de liste à sélection unique, l’utilisateur ne peut sélectionner qu’un seul élément. Dans une zone de liste à sélection multiple, vous pouvez sélectionner une plage d’éléments. Lorsque l’utilisateur sélectionne un élément, il est mis en surbrillance et la zone de liste envoie un message de notification à la fenêtre parente.

Vous pouvez créer une zone de liste à partir d’un modèle de boîte de dialogue ou directement dans votre code. Pour le créer directement, construisez l’objet `CListBox`, puis appelez la fonction membre [Create](#create) pour créer le contrôle de zone de liste Windows et l’attacher à l’objet `CListBox`. Pour utiliser une zone de liste dans un modèle de boîte de dialogue, déclarez une variable de zone de liste dans votre classe de boîte de dialogue, puis utilisez `DDX_Control` dans la fonction `DoDataExchange` de la classe de boîte de dialogue pour connecter la variable membre au contrôle. (cette opération est effectuée automatiquement lorsque vous ajoutez une variable de contrôle à votre classe de boîte de dialogue.)

La construction peut être un processus en une étape dans une classe dérivée de `CListBox`. Écrivez un constructeur pour la classe dérivée et appelez `Create` à partir du constructeur.

Si vous voulez gérer les messages de notification Windows envoyés par une zone de liste à son parent (généralement une classe dérivée de [CDialog](../../mfc/reference/cdialog-class.md)), ajoutez une entrée de table des messages et une fonction membre de gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de la table des messages prend la forme suivante :

`ON_Notification( id, memberFxn )`

où `id` spécifie l’ID de fenêtre enfant du contrôle de zone de liste qui envoie la notification et `memberFxn` est le nom de la fonction membre parente que vous avez écrite pour gérer la notification.

Le prototype de fonction du parent est le suivant :

`afx_msg void memberFxn( );`

Voici une liste d’entrées de table des messages potentielle et une description des cas dans lesquels ils sont envoyés au parent :

- ON_LBN_DBLCLK l’utilisateur double-clique sur une chaîne dans une zone de liste. Seule une zone de liste avec le style [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) enverra ce message de notification.

- ON_LBN_ERRSPACE la zone de liste ne peut pas allouer suffisamment de mémoire pour répondre à la demande.

- ON_LBN_KILLFOCUS la zone de liste perd le focus d’entrée.

- ON_LBN_SELCANCEL la sélection de la zone de liste actuelle est annulée. Ce message est envoyé uniquement lorsqu’une zone de liste a le style LBS_NOTIFY.

- ON_LBN_SELCHANGE la sélection dans la zone de liste a été modifiée. Cette notification n’est pas envoyée si la sélection est modifiée par la fonction membre [CListBox :: SetCurSel](#setcursel) . Cette notification s’applique uniquement à une zone de liste avec le style LBS_NOTIFY. Le message de notification LBN_SELCHANGE est envoyé pour une zone de liste à sélection multiple chaque fois que l’utilisateur appuie sur une touche de direction, même si la sélection ne change pas.

- ON_LBN_SETFOCUS la zone de liste reçoit le focus d’entrée.

- ON_WM_CHARTOITEM une zone de liste owner-draw sans chaîne reçoit un message WM_CHAR.

- ON_WM_VKEYTOITEM une zone de liste avec le style LBS_WANTKEYBOARDINPUT reçoit un message WM_KEYDOWN.

Si vous créez un objet `CListBox` dans une boîte de dialogue (par le biais d’une ressource de boîte de dialogue), l’objet `CListBox` est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un objet `CListBox` dans une fenêtre, vous devrez peut-être détruire l’objet `CListBox`. Si vous créez l’objet `CListBox` sur la pile, il est détruit automatiquement. Si vous créez l’objet `CListBox` sur le tas à l’aide de la fonction **New** , vous devez appeler **Delete** sur l’objet pour le détruire lorsque l’utilisateur ferme la fenêtre parente.

Si vous allouez de la mémoire dans l’objet `CListBox`, substituez le destructeur `CListBox` pour supprimer l’allocation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Configuration requise pour

**En-tête :** afxwin.h

##  <a name="addstring"></a>  CListBox::AddString

Ajoute une chaîne à une zone de liste.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameters

*lpszItem*<br/>
Pointe vers la chaîne terminée par le caractère null qui doit être ajoutée.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la chaîne dans la zone de liste. La valeur de retour est LB_ERR si une erreur se produit ; la valeur de retour est LB_ERRSPACE si l’espace disponible est insuffisant pour stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Si la zone de liste n’a pas été créée avec le style [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , la chaîne est ajoutée à la fin de la liste. Dans le cas contraire, la chaîne est insérée dans la liste et la liste est triée. Si la zone de liste a été créée avec le style LBS_SORT, mais pas le style [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , l’infrastructure trie la liste en fonction d’un ou de plusieurs appels à la fonction membre `CompareItem`.

Utilisez [InsertString](#insertstring) pour insérer une chaîne à un emplacement spécifique dans la zone de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>  CListBox::CharToItem

Appelée par l’infrastructure lorsque la fenêtre parente de la zone de liste reçoit un message WM_CHARTOITEM de la zone de liste.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parameters

*nKey*<br/>
Code ANSI du caractère tapé par l’utilisateur.

*nIndex*<br/>
Position actuelle du point d’insertion de la zone de liste.

### <a name="return-value"></a>Valeur de retour

Retourne-1 ou-2 pour aucune action supplémentaire ou un nombre non négatif pour spécifier l’index d’un élément de zone de liste sur lequel exécuter l’action par défaut pour la séquence de touches. L’implémentation par défaut retourne-1.

### <a name="remarks"></a>Notes

Le message WM_CHARTOITEM est envoyé par la zone de liste lorsqu’il reçoit un message de WM_CHAR, mais uniquement si la zone de liste répond à tous ces critères :

- Est une zone de liste owner-draw.

- Le style de [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) n’est pas défini.

- A au moins un élément.

Vous ne devez jamais appeler cette fonction vous-même. Remplacez cette fonction pour fournir votre propre gestion personnalisée des messages du clavier.

Dans votre remplacement, vous devez retourner une valeur pour indiquer au Framework l’action que vous avez effectuée. Une valeur de retour de-1 ou-2 indique que vous avez géré tous les aspects de la sélection de l’élément et ne nécessite aucune action supplémentaire de la zone de liste. Avant de retourner-1 ou-2, vous pouvez définir la sélection ou déplacer le signe insertion ou les deux. Pour définir la sélection, utilisez [SetCurSel](#setcursel) ou [SetSel](#setsel). Pour déplacer le signe insertion, utilisez [SetCaretIndex](#setcaretindex).

Une valeur de retour supérieure ou égale à 0 spécifie l’index d’un élément dans la zone de liste et indique que la zone de liste doit exécuter l’action par défaut pour la frappe sur l’élément donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>  CListBox::CListBox

Construit un objet `CListBox`.

```
CListBox();
```

### <a name="remarks"></a>Notes

Vous construisez un objet `CListBox` en deux étapes. Tout d’abord, appelez le constructeur `ClistBox` puis appelez `Create`, qui initialise la zone de liste Windows et l’attache au `CListBox`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>  CListBox::CompareItem

Appelé par l’infrastructure pour déterminer la position relative d’un nouvel élément dans une zone de liste owner-draw triée.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parameters

*lpCompareItemStruct*<br/>
Pointeur long vers une structure `COMPAREITEMSTRUCT`.

### <a name="return-value"></a>Valeur de retour

Indique la position relative des deux éléments décrits dans la structure [compareitemstruct,](/windows/win32/api/winuser/ns-winuser-compareitemstruct) . Il peut s’agir de l’une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|-1|L’élément 1 est trié avant l’élément 2.|
|0|Les éléments 1 et 2 sont triés de la même façon.|
|1|L’élément 1 est trié après l’élément 2.|

Consultez [CWnd :: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) pour obtenir une description de la structure `COMPAREITEMSTRUCT`.

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Si vous créez une zone de liste owner-draw avec le style LBS_SORT, vous devez substituer cette fonction membre pour aider l’infrastructure à trier les nouveaux éléments ajoutés à la zone de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>  CListBox::Create

Crée la zone de liste Windows et l’attache à l’objet `CListBox`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameters

*dwStyle*<br/>
Spécifie le style de la zone de liste. Applique une combinaison de [styles de zone de liste](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) à la zone.

*rect*<br/>
Spécifie la taille et la position de la zone de liste. Il peut s’agir d’un objet `CRect` ou d’une structure `RECT`.

*pParentWnd*<br/>
Spécifie la fenêtre parente de la zone de liste (généralement un objet `CDialog`). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de la zone de liste.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un objet `CListBox` en deux étapes. Tout d’abord, appelez le constructeur, puis appelez `Create`, qui initialise la zone de liste Windows et l’attache à l’objet `CListBox`.

Lorsque `Create` s’exécute, Windows envoie les messages [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)et [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) au contrôle de zone de liste.

Ces messages sont gérés par défaut par les fonctions membres [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)et [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) dans la classe de base `CWnd`. Pour étendre la gestion des messages par défaut, dérivez une classe de `CListBox`, ajoutez une table des messages à la nouvelle classe et substituez les fonctions membres du gestionnaire de messages précédentes. Substituez `OnCreate`, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.

Appliquez les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle de zone de liste.

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_VSCROLL pour ajouter une barre de défilement verticale

- WS_HSCROLL pour ajouter une barre de défilement horizontale

- WS_GROUP des contrôles de groupe

- WS_TABSTOP pour autoriser la tabulation sur ce contrôle

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>  CListBox::DeleteItem

Appelé par le Framework lorsque l’utilisateur supprime un élément d’un objet `CListBox` owner-draw ou détruit la zone de liste.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parameters

*lpDeleteItemStruct*<br/>
Pointeur long vers une structure Windows [deleteitemstruct,](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) qui contient des informations sur l’élément supprimé.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour redessiner une zone de liste owner-draw si nécessaire.

Consultez [CWnd :: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) pour obtenir une description de la structure `DELETEITEMSTRUCT`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>  CListBox::DeleteString

Supprime l’élément à la position *nIndex* de la zone de liste.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de la chaîne à supprimer.

### <a name="return-value"></a>Valeur de retour

Nombre de chaînes restantes dans la liste. La valeur de retour est LB_ERR si *nIndex* spécifie un index supérieur au nombre d’éléments de la liste.

### <a name="remarks"></a>Notes

Tous les éléments suivants *nIndex* descendent d’une position. Par exemple, si une zone de liste contient deux éléments, si vous supprimez le premier élément, l’élément restant sera à présent à la première position. *nIndex*= 0 pour l’élément à la première position.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>  CListBox::Dir

Ajoute une liste de noms de fichiers, de lecteurs ou les deux à une zone de liste.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parameters

*attr*<br/>
Il peut s’agir de n’importe quelle combinaison des valeurs **enum** décrites dans `CFile::GetStatu`[s](../../mfc/reference/cfile-class.md#getstatus)ou de n’importe quelle combinaison des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|0x0000|Le fichier peut être lu ou écrit.|
|0x0001|Le fichier peut être lu à partir de laquelle il n’est pas écrit.|
|0x0002|Le fichier est masqué et n’apparaît pas dans la liste des répertoires.|
|0x0004|Le fichier est un fichier système.|
|0x0010|Le nom spécifié par *lpszWildCard* spécifie un répertoire.|
|0x0020|Le fichier a été archivé.|
|0x4000|Inclut tous les lecteurs qui correspondent au nom spécifié par *lpszWildCard*.|
|0x8000|Indicateur exclusif. Si l’indicateur exclusive est défini, seuls les fichiers du type spécifié sont répertoriés. Dans le cas contraire, les fichiers du type spécifié sont répertoriés en plus des fichiers « normaux ».|

*lpszWildCard*<br/>
Pointe vers une chaîne de spécification de fichier. La chaîne peut contenir des caractères génériques (par exemple, *.\*).

### <a name="return-value"></a>Valeur de retour

Index de base zéro du dernier nom de fichier ajouté à la liste. La valeur de retour est LB_ERR si une erreur se produit ; la valeur de retour est LB_ERRSPACE si l’espace disponible est insuffisant pour stocker les nouvelles chaînes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>  CListBox::DrawItem

Appelée par l’infrastructure quand un aspect visuel d’une zone de liste owner-draw change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameters

*lpDrawItemStruct*<br/>
Pointeur long vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Les membres `itemAction` et `itemState` de la structure `DRAWITEMSTRUCT` définissent l’action de dessin à effectuer.

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre pour implémenter le dessin pour un objet `CListBox` owner-draw. L’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction membre.

Consultez [CWnd :: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) pour obtenir une description de la structure `DRAWITEMSTRUCT`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>  CListBox::FindString

Recherche la première chaîne dans une zone de liste qui contient le préfixe spécifié sans modifier la sélection de la zone de liste.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parameters

*nStartAfter*<br/>
Contient l’index de base zéro de l’élément avant le premier élément dans lequel effectuer la recherche. Lorsque la recherche atteint le bas de la zone de liste, elle continue à partir du haut de la zone de liste jusqu’à l’élément spécifié par *nStartAfter*. Si *nStartAfter* est-1, la zone de liste entière est recherchée à partir du début.

*lpszItem*<br/>
Pointe vers la chaîne terminée par le caractère null qui contient le préfixe à rechercher. La recherche étant indépendante de la casse, cette chaîne peut contenir n’importe quelle combinaison de lettres majuscules et minuscules.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément correspondant, ou LB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Utilisez la fonction membre [SelectString](#selectstring) pour rechercher et sélectionner une chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>  CListBox::FindStringExact

Recherche la première chaîne de zone de liste qui correspond à la chaîne spécifiée dans *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parameters

*nIndexStart*<br/>
Spécifie l’index de base zéro de l’élément avant le premier élément dans lequel effectuer la recherche. Lorsque la recherche atteint le bas de la zone de liste, elle continue à partir du haut de la zone de liste jusqu’à l’élément spécifié par *nIndexStart*. Si *nIndexStart* est-1, la zone de liste entière est recherchée à partir du début.

*lpszFind*<br/>
Pointe vers la chaîne terminée par le caractère null à rechercher. Cette chaîne peut contenir un nom de fichier complet, y compris l’extension. La recherche ne respecte pas la casse. la chaîne peut donc contenir n’importe quelle combinaison de lettres majuscules et minuscules.

### <a name="return-value"></a>Valeur de retour

Index de l’élément correspondant, ou LB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Si la zone de liste a été créée avec un style owner-draw, mais sans le style [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles), la fonction membre `FindStringExact` tente de faire correspondre la valeur du mot double à la valeur de *lpszFind*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex

Récupère l’index de base zéro de l’élément d’ancrage actuel dans la zone de liste.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Index de l’élément d’ancrage actuel, en cas de réussite ; sinon LB_ERR.

### <a name="remarks"></a>Notes

Dans une zone de liste à sélection multiple, l’élément d’ancrage est le premier ou le dernier élément d’un bloc d’éléments sélectionnés contigus.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CListBox :: SetAnchorIndex](#setanchorindex).

##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex

Détermine l’index de l’élément qui a le rectangle de focus dans une zone de liste à sélection multiple.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément qui a le rectangle de focus dans une zone de liste. Si la zone de liste est une zone de liste à sélection unique, la valeur de retour est l’index de l’élément sélectionné, le cas échéant.

### <a name="remarks"></a>Notes

L’élément peut être ou non sélectionné.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CListBox :: SetCaretIndex](#setcaretindex).

##  <a name="getcount"></a>  CListBox::GetCount

Récupère le nombre d’éléments dans une zone de liste.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans la zone de liste, ou LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Le nombre retourné est supérieur à la valeur d’index du dernier élément (l’index est de base zéro).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>  CListBox::GetCurSel

Récupère l’index de base zéro de l’élément actuellement sélectionné, le cas échéant, dans une zone de liste à sélection unique.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément actuellement sélectionné s’il s’agit d’une zone de liste à sélection unique. Elle est LB_ERR si aucun élément n’est actuellement sélectionné.

Dans une zone de liste à sélection multiple, index de l’élément qui a le focus.

### <a name="remarks"></a>Notes

N’appelez pas `GetCurSel` pour une zone de liste à sélection multiple. Utilisez [CListBox :: GetSelItems](#getselitems) à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>  CListBox::GetHorizontalExtent

Récupère à partir de la zone de liste la largeur, en pixels, à laquelle il peut faire défiler horizontalement.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur de défilement de la zone de liste, en pixels.

### <a name="remarks"></a>Notes

Cela s’applique uniquement si la zone de liste comporte une barre de défilement horizontale.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>  CListBox::GetItemData

Récupère la valeur de mot double fournie par l’application associée à l’élément de zone de liste spécifié.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

Valeur associée à l’élément, ou LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

La valeur de mot double était le paramètre *dwItemData* d’un appel [SetItemData](#setitemdata) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr

Récupère la valeur 32 bits fournie par l’application associée à l’élément de zone de liste spécifié en tant que pointeur (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

Récupère un pointeur, ou-1 si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>  CListBox::GetItemHeight

Détermine la hauteur des éléments dans une zone de liste.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément dans la zone de liste. Ce paramètre est utilisé uniquement si la zone de liste a le style LBS_OWNERDRAWVARIABLE ; dans le cas contraire, la valeur doit être 0.

### <a name="return-value"></a>Valeur de retour

Hauteur, en pixels, des éléments de la zone de liste. Si la zone de liste a le style [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , la valeur de retour correspond à la hauteur de l’élément spécifié par *nIndex*. Si une erreur se produit, la valeur de retour est LB_ERR.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>  CListBox::GetItemRect

Récupère les dimensions du rectangle qui délimite un élément de zone de liste tel qu’il est actuellement affiché dans la fenêtre de zone de liste.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément.

*lpRect*<br/>
Spécifie un pointeur long vers une [structure Rect](/windows/win32/api/windef/ns-windef-rect) qui reçoit les coordonnées clientes de la zone de liste de l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>  CListBox::GetListBoxInfo

Récupère le nombre d’éléments par colonne.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments par colonne de l’objet `CListBox`.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités du message [LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo) , comme décrit dans le SDK Windows.

##  <a name="getlocale"></a>  CListBox::GetLocale

Récupère les paramètres régionaux utilisés par la zone de liste.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de l’identificateur de paramètres régionaux (LCID) pour les chaînes de la zone de liste.

### <a name="remarks"></a>Notes

Les paramètres régionaux sont utilisés, par exemple, pour déterminer l’ordre de tri des chaînes dans une zone de liste triée.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CListBox :: setlocale](#setlocale).

##  <a name="getsel"></a>  CListBox::GetSel

Récupère l’état de sélection d’un élément.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément.

### <a name="return-value"></a>Valeur de retour

Nombre positif si l’élément spécifié est sélectionné ; Sinon, la valeur est 0. La valeur de retour est LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Cette fonction membre fonctionne avec les zones de liste à sélection unique et à sélection multiple.

Pour récupérer l’index de l’élément de zone de liste actuellement sélectionné, utilisez [CListBox :: GetCurSel](#getcursel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>  CListBox::GetSelCount

Récupère le nombre total d’éléments sélectionnés dans une zone de liste à sélection multiple.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments sélectionnés dans une zone de liste. Si la zone de liste est une zone de liste à sélection unique, la valeur de retour est LB_ERR.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CListBox :: GetSelItems](#getselitems).

##  <a name="getselitems"></a>  CListBox::GetSelItems

Remplit une mémoire tampon avec un tableau d’entiers qui spécifie les numéros d’élément des éléments sélectionnés dans une zone de liste à sélection multiple.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parameters

*nMaxItems*<br/>
Spécifie le nombre maximal d’éléments sélectionnés dont les numéros d’élément doivent être placés dans la mémoire tampon.

*rgIndex*<br/>
Spécifie un pointeur vers une mémoire tampon suffisamment grande pour le nombre d’entiers spécifié par *nMaxItems*.

### <a name="return-value"></a>Valeur de retour

Nombre réel d’éléments placés dans la mémoire tampon. Si la zone de liste est une zone de liste à sélection unique, la valeur de retour est `LB_ERR`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>  CListBox::GetText

Obtient une chaîne à partir d’une zone de liste.

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de la chaîne à récupérer.

*lpszBuffer*<br/>
Pointe vers la mémoire tampon qui reçoit la chaîne. La mémoire tampon doit avoir suffisamment d’espace pour la chaîne et un caractère null de fin. La taille de la chaîne peut être déterminée à l’avance en appelant la fonction membre `GetTextLen`.

*rString*<br/>
Référence à un objet `CString`.

### <a name="return-value"></a>Valeur de retour

Longueur (en octets) de la chaîne, à l’exclusion du caractère null de fin. Si *nIndex* ne spécifie pas d’index valide, la valeur de retour est LB_ERR.

### <a name="remarks"></a>Notes

La deuxième forme de cette fonction membre remplit un objet `CString` avec le texte de chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>  CListBox::GetTextLen

Obtient la longueur d’une chaîne dans un élément de zone de liste.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de la chaîne.

### <a name="return-value"></a>Valeur de retour

Longueur de la chaîne en caractères, à l’exclusion du caractère null de fin. Si *nIndex* ne spécifie pas d’index valide, la valeur de retour est LB_ERR.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CListBox :: gettext](#gettext).

##  <a name="gettopindex"></a>  CListBox::GetTopIndex

Récupère l’index de base zéro du premier élément visible dans une zone de liste.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro du premier élément visible dans une zone de liste en cas de réussite, LB_ERR sinon.

### <a name="remarks"></a>Notes

Initialement, l’élément 0 se trouve en haut de la zone de liste, mais si vous faites défiler la zone de liste, un autre élément peut se trouver en haut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>  CListBox::InitStorage

Alloue de la mémoire pour le stockage des éléments de la zone de liste.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parameters

*nItems*<br/>
Spécifie le nombre d’éléments à ajouter.

*nBytes*<br/>
Spécifie la quantité de mémoire, en octets, à allouer pour les chaînes d’élément.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, le nombre maximal d’éléments que la zone de liste peut stocker avant qu’une réallocation de mémoire soit nécessaire, sinon LB_ERRSPACE, ce qui signifie que la mémoire disponible est insuffisante.

### <a name="remarks"></a>Notes

Appelez cette fonction avant d’ajouter un grand nombre d’éléments à un `CListBox`.

Cette fonction permet d’accélérer l’initialisation des zones de liste qui comportent un grand nombre d’éléments (plus de 100). Elle Préalloue la quantité de mémoire spécifiée afin que les fonctions [AddString](#addstring), [InsertString](#insertstring)et [dir](#dir) suivantes prennent le plus de temps possible. Vous pouvez utiliser des estimations pour les paramètres. Si vous surestime, une partie de la mémoire supplémentaire est allouée. Si vous sous-estimez, l’allocation normale est utilisée pour les éléments qui dépassent le montant préalloué.

Windows 95/98 uniquement : le paramètre *nItems* est limité aux valeurs 16 bits. Cela signifie que les zones de liste ne peuvent pas contenir plus de 32 767 éléments. Bien que le nombre d’éléments soit limité, la taille totale des éléments d’une zone de liste n’est limitée que par la mémoire disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>  CListBox::InsertString

Insère une chaîne dans la zone de liste.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de la position où insérer la chaîne. Si ce paramètre a la valeur-1, la chaîne est ajoutée à la fin de la liste.

*lpszItem*<br/>
Pointe vers la chaîne terminée par le caractère null qui doit être insérée.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la position à laquelle la chaîne a été insérée. La valeur de retour est LB_ERR si une erreur se produit ; la valeur de retour est LB_ERRSPACE si l’espace disponible est insuffisant pour stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Contrairement à la fonction membre [AddString](#addstring), `InsertString` n’entraîne pas le tri d’une liste avec le style [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint

Détermine l’élément de zone de liste le plus proche du point spécifié dans *PT*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parameters

*pt*<br/>
Point pour lequel Rechercher l’élément le plus proche, spécifié par rapport à l’angle supérieur gauche de la zone cliente de la zone de liste.

*bOutside*<br/>
Référence à une variable BOOL qui aura la valeur TRUE si *PT* est en dehors de la zone cliente de la zone de liste, false si *PT* est à l’intérieur de la zone cliente de la zone de liste.

### <a name="return-value"></a>Valeur de retour

Index de l’élément le plus proche jusqu’au point spécifié dans *PT*.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction pour déterminer à quel élément de zone de liste se déplace le curseur de la souris.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CListBox :: SetAnchorIndex](#setanchorindex).

##  <a name="measureitem"></a>  CListBox::MeasureItem

Appelé par le Framework lorsqu’une zone de liste avec un style owner-draw est créée.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parameters

*lpMeasureItemStruct*<br/>
Pointeur long vers une structure [measureitemstruct,](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre et remplissez la structure `MEASUREITEMSTRUCT` pour informer les fenêtres des dimensions de la zone de liste. Si la zone de liste est créée avec le style [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , l’infrastructure appelle cette fonction membre pour chaque élément de la zone de liste. Dans le cas contraire, ce membre n’est appelé qu’une seule fois.

Pour plus d’informations sur l’utilisation du style de [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) dans une zone de liste owner-draw créée avec la fonction membre `SubclassDlgItem` de `CWnd`, consultez la discussion dans [Technical note 14](../../mfc/tn014-custom-controls.md).

Consultez [CWnd :: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pour obtenir une description de la structure `MEASUREITEMSTRUCT`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>  CListBox::ResetContent

Supprime tous les éléments d’une zone de liste.

```
void ResetContent();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>  CListBox::SelectString

Recherche un élément de zone de liste qui correspond à la chaîne spécifiée et, si un élément correspondant est trouvé, il sélectionne l’élément.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parameters

*nStartAfter*<br/>
Contient l’index de base zéro de l’élément avant le premier élément dans lequel effectuer la recherche. Lorsque la recherche atteint le bas de la zone de liste, elle continue à partir du haut de la zone de liste jusqu’à l’élément spécifié par *nStartAfter*. Si *nStartAfter* est-1, la zone de liste entière est recherchée à partir du début.

*lpszItem*<br/>
Pointe vers la chaîne terminée par le caractère null qui contient le préfixe à rechercher. La recherche étant indépendante de la casse, cette chaîne peut contenir n’importe quelle combinaison de lettres majuscules et minuscules.

### <a name="return-value"></a>Valeur de retour

Index de l’élément sélectionné si la recherche a réussi. En cas d’échec de la recherche, la valeur de retour est LB_ERR et la sélection actuelle n’est pas modifiée.

### <a name="remarks"></a>Notes

La zone de liste défile, si nécessaire, pour afficher l’élément sélectionné.

Cette fonction membre ne peut pas être utilisée avec une zone de liste qui a le style [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

Un élément est sélectionné uniquement si ses caractères initiaux (à partir du point de départ) correspondent aux caractères de la chaîne spécifiée par *lpszItem*.

Utilisez la fonction membre `FindString` pour rechercher une chaîne sans sélectionner l’élément.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>  CListBox::SelItemRange

Sélectionne plusieurs éléments consécutifs dans une zone de liste à sélection multiple.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parameters

*bSelect*<br/>
Spécifie comment définir la sélection. Si *bSelect* a la valeur true, la chaîne est sélectionnée et mise en surbrillance ; Si la valeur est FALSe, la mise en surbrillance est supprimée et la chaîne n’est plus sélectionnée.

*nFirstItem*<br/>
Spécifie l’index de base zéro du premier élément à définir.

*nLastItem*<br/>
Spécifie l’index de base zéro du dernier élément à définir.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement avec des zones de liste à sélection multiple. Si vous ne devez sélectionner qu’un seul élément dans une zone de liste à sélection multiple, autrement dit, si *nFirstItem* est égal à *nLastItem* , appelez la fonction membre [SetSel](#setsel) à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex

Définit l’ancre dans une zone de liste à sélection multiple pour commencer une sélection étendue.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément de zone de liste qui sera l’ancre.

### <a name="remarks"></a>Notes

Dans une zone de liste à sélection multiple, l’élément d’ancrage est le premier ou le dernier élément d’un bloc d’éléments sélectionnés contigus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex

Définit le rectangle de focus sur l’élément à l’index spécifié dans une zone de liste à sélection multiple.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément qui recevra le rectangle de focus dans la zone de liste.

*bScroll*<br/>
Si cette valeur est 0, l’élément fait l’objet d’un défilement jusqu’à ce qu’il soit entièrement visible. Si cette valeur n’est pas 0, l’élément fait l’objet d’un défilement jusqu’à ce qu’il soit au moins partiellement visible.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Si l’élément n’est pas visible, il fait l’objet d’un défilement dans la vue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>  CListBox::SetColumnWidth

Définit la largeur en pixels de toutes les colonnes dans une zone de liste multicolonne (créée avec le style [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ).

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parameters

*cxWidth*<br/>
Spécifie la largeur en pixels de toutes les colonnes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>  CListBox::SetCurSel

Sélectionne une chaîne et la fait défiler en vue, si nécessaire.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parameters

*nSelect*<br/>
Spécifie l’index de base zéro de la chaîne à sélectionner. Si *nsélectionner* a la valeur-1, la zone de liste est définie sur ne pas sélectionner.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Lorsque la nouvelle chaîne est sélectionnée, la zone de liste supprime la mise en surbrillance de la chaîne précédemment sélectionnée.

Utilisez cette fonction membre uniquement avec les zones de liste à sélection unique.

Pour définir ou supprimer une sélection dans une zone de liste à sélection multiple, utilisez [CListBox :: SetSel](#setsel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>  CListBox::SetHorizontalExtent

Définit la largeur, en pixels, à laquelle une zone de liste peut faire défiler horizontalement.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parameters

*cxExtent*<br/>
Spécifie le nombre de pixels par lesquels la zone de liste peut faire défiler horizontalement.

### <a name="remarks"></a>Notes

Si la taille de la zone de liste est inférieure à cette valeur, la barre de défilement horizontale défile horizontalement les éléments de la zone de liste. Si la taille de la zone de liste est supérieure ou égale à cette valeur, la barre de défilement horizontale est masquée.

Pour répondre à un appel à `SetHorizontalExtent`, la zone de liste doit avoir été définie avec le style [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) .

Cette fonction membre n’est pas utile pour les zones de liste multicolonnes. Pour les zones de liste multicolonnes, appelez la fonction membre `SetColumnWidth`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>  CListBox::SetItemData

Définit une valeur associée à l’élément spécifié dans une zone de liste.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément.

*dwItemData*<br/>
Spécifie la valeur à associer à l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>  CListBox::SetItemDataPtr

Définit la valeur 32 bits associée à l’élément spécifié dans une zone de liste pour qu’elle soit le pointeur spécifié ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément.

*pData*<br/>
Spécifie le pointeur à associer à l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Ce pointeur reste valide pendant toute la durée de vie de la zone de liste, même si la position relative de l’élément dans la zone de liste peut changer à mesure que des éléments sont ajoutés ou supprimés. Par conséquent, l’index de l’élément dans la zone peut changer, mais le pointeur reste fiable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>  CListBox::SetItemHeight

Définit la hauteur des éléments dans une zone de liste.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément dans la zone de liste. Ce paramètre est utilisé uniquement si la zone de liste a le style LBS_OWNERDRAWVARIABLE ; dans le cas contraire, la valeur doit être 0.

*cyItemHeight*<br/>
Spécifie la hauteur, en pixels, de l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR si l’index ou la hauteur n’est pas valide.

### <a name="remarks"></a>Notes

Si la zone de liste a le style [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , cette fonction définit la hauteur de l’élément spécifié par *nIndex*. Dans le cas contraire, cette fonction définit la hauteur de tous les éléments de la zone de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>  CListBox::SetLocale

Définit l’identificateur de paramètres régionaux pour cette zone de liste.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parameters

*nNewLocale*<br/>
Nouvelle valeur de l’identificateur de paramètres régionaux (LCID) à définir pour la zone de liste.

### <a name="return-value"></a>Valeur de retour

Valeur précédente de l’identificateur de paramètres régionaux (LCID) pour cette zone de liste.

### <a name="remarks"></a>Notes

Si `SetLocale` n’est pas appelé, les paramètres régionaux par défaut sont obtenus à partir du système. Les paramètres régionaux par défaut du système peuvent être modifiés à l’aide de l’application régionale (ou internationale) du panneau de configuration.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>  CListBox::SetSel

Sélectionne une chaîne dans une zone de liste à sélection multiple.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Contient l’index de base zéro de la chaîne à définir. Si la valeur est-1, la sélection est ajoutée ou supprimée dans toutes les chaînes, selon la valeur de *bSelect*.

*bSelect*<br/>
Spécifie comment définir la sélection. Si *bSelect* a la valeur true, la chaîne est sélectionnée et mise en surbrillance ; Si la valeur est FALSe, la mise en surbrillance est supprimée et la chaîne n’est plus sélectionnée. La chaîne spécifiée est sélectionnée et mise en surbrillance par défaut.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement avec des zones de liste à sélection multiple.

Pour sélectionner un élément dans une zone de liste à sélection unique, utilisez [CListBox :: SetCurSel](#setcursel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>  CListBox::SetTabStops

Définit les positions des taquets de tabulation dans une zone de liste.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parameters

*cxEachStop*<br/>
Les taquets de tabulation sont définis à chaque unité de boîte de dialogue *cxEachStop* . Pour obtenir une description d’une unité de boîte de dialogue, consultez *rgTabStops* .

*nTabStops*<br/>
Spécifie le nombre d’arrêts de tabulation dans la zone de liste.

*rgTabStops*<br/>
Pointe vers le premier membre d’un tableau d’entiers contenant les positions des taquets de tabulation dans les unités de la boîte de dialogue. Une unité de boîte de dialogue est une distance horizontale ou verticale. Une unité de boîte de dialogue horizontale est égale à un quart de l’unité de largeur de base de la boîte de dialogue active, et une unité de boîte de dialogue verticale est égale à un huitième de l’unité de hauteur de base de la boîte de dialogue actuelle. Les unités de dialogue sont calculées en fonction de la hauteur et de la largeur de la police système actuelle. La fonction Windows `GetDialogBaseUnits` retourne les unités de base de la boîte de dialogue en pixels. Les taquets de tabulation doivent être triés par ordre de tri ; les onglets arrière ne sont pas autorisés.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si tous les onglets ont été définis ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour définir des taquets de tabulation sur la taille par défaut de 2 unités de boîte de dialogue, appelez la version sans paramètre de cette fonction membre. Pour définir des taquets de tabulation d’une taille autre que 2, appelez la version avec l’argument *cxEachStop* .

Pour définir des taquets de tabulation sur un tableau de tailles, utilisez la version avec les arguments *rgTabStops* et *nTabStops* . Un taquet de tabulation sera défini pour chaque valeur dans *rgTabStops*, jusqu’au nombre spécifié par *nTabStops*.

Pour répondre à un appel à la fonction membre `SetTabStops`, la zone de liste doit avoir été créée avec le style [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>  CListBox::SetTopIndex

Garantit qu’un élément de zone de liste spécifique est visible.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parameters

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément de zone de liste.

### <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, ou LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Le système fait défiler la zone de liste jusqu’à ce que l’élément spécifié par *nIndex* apparaisse en haut de la zone de liste ou que la plage de défilement maximale ait été atteinte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>  CListBox::VKeyToItem

Appelée par l’infrastructure lorsque la fenêtre parente de la zone de liste reçoit un message WM_VKEYTOITEM de la zone de liste.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parameters

*nKey*<br/>
Code de la touche virtuelle de la touche sur laquelle l’utilisateur a appuyé. Pour obtenir la liste des codes de touches virtuelles standard, consultez Winuser. h

*nIndex*<br/>
Position actuelle du point d’insertion de la zone de liste.

### <a name="return-value"></a>Valeur de retour

Retourne-2 pour aucune action supplémentaire,-1 pour l’action par défaut ou un nombre non négatif pour spécifier l’index d’un élément de zone de liste sur lequel exécuter l’action par défaut pour la séquence de touches.

### <a name="remarks"></a>Notes

Le message WM_VKEYTOITEM est envoyé par la zone de liste lorsqu’il reçoit un message de WM_KEYDOWN, mais uniquement si la zone de liste remplit les deux conditions suivantes :

- A le style de [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) défini.

- A au moins un élément.

Vous ne devez jamais appeler cette fonction vous-même. Remplacez cette fonction pour fournir votre propre gestion personnalisée des messages du clavier.

Vous devez retourner une valeur pour indiquer à l’infrastructure quelle action votre remplacement a effectué. Une valeur de retour de-2 indique que l’application a géré tous les aspects de la sélection de l’élément et ne nécessite aucune action supplémentaire de la zone de liste. Avant de retourner-2, vous pouvez définir la sélection ou déplacer le signe insertion ou les deux. Pour définir la sélection, utilisez [SetCurSel](#setcursel) ou [SetSel](#setsel). Pour déplacer le signe insertion, utilisez [SetCaretIndex](#setcaretindex).

Une valeur de retour de-1 indique que la zone de liste doit exécuter l’action par défaut en réponse à la séquence de touches. L’implémentation par défaut retourne-1.

Une valeur de retour supérieure ou égale à 0 spécifie l’index d’un élément dans la zone de liste et indique que la zone de liste doit exécuter l’action par défaut pour la frappe sur l’élément donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic, classe](../../mfc/reference/cstatic-class.md)
