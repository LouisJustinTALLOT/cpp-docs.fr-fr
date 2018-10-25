---
title: CListBox, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5341342336b05d4fddab50a81d611e89b85573f2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068940"
---
# <a name="clistbox-class"></a>CListBox (classe)

Fournit les fonctionnalités d'une zone de liste Windows.

## <a name="syntax"></a>Syntaxe

```
class CListBox : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Construit un objet `CListBox`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|Ajoute une chaîne à une zone de liste.|
|[CListBox::CharToItem](#chartoitem)|Méthode override pour fournir WM_CHAR personnalisé gérant pour les zones de liste en mode owner-draw n’ayant pas de chaînes.|
|[CListBox::CompareItem](#compareitem)|Appelé par l’infrastructure pour déterminer la position d’un nouvel élément dans une zone de liste triée en mode owner-draw.|
|[CListBox::Create](#create)|Crée la zone de liste Windows et l’attache à la `CListBox` objet.|
|[CListBox::DeleteItem](#deleteitem)|Appelé par le framework lorsque l’utilisateur supprime un élément à partir d’une zone de liste owner-draw.|
|[CListBox::DeleteString](#deletestring)|Supprime une chaîne à partir d’une zone de liste.|
|[CListBox::Dir](#dir)|Ajoute les noms de fichiers, disques ou les deux à partir du répertoire actuel à une zone de liste.|
|[CListBox::DrawItem](#drawitem)|Appelé par l’infrastructure lorsqu’un aspect visuel d’une change de zone de liste en mode owner-draw.|
|[CListBox::FindString](#findstring)|Recherche une chaîne dans une zone de liste.|
|[CListBox::FindStringExact](#findstringexact)|Recherche la première chaîne de zone de liste qui correspond à une chaîne spécifiée.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Récupère l’index de base zéro de l’élément d’ancrage actuel dans une zone de liste.|
|[CListBox::GetCaretIndex](#getcaretindex)|Détermine l’index de l’élément qui a le rectangle de focus dans une zone de liste à sélection multiple.|
|[CListBox::GetCount](#getcount)|Retourne le nombre de chaînes dans une zone de liste.|
|[CListBox::GetCurSel](#getcursel)|Retourne l’index de base zéro de la chaîne actuellement sélectionnée dans une zone de liste.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Retourne la largeur en pixels qu’une zone de liste de défilement horizontale.|
|[CListBox::GetItemData](#getitemdata)|Retourne la valeur de 32 bits associée à l’élément de zone de liste.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Retourne un pointeur vers un élément de zone de liste.|
|[CListBox::GetItemHeight](#getitemheight)|Détermine la hauteur d’éléments dans une zone de liste.|
|[CListBox::GetItemRect](#getitemrect)|Retourne le rectangle englobant de l’élément de zone de liste tel qu’il est actuellement affiché.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Récupère le nombre d’éléments par colonne.|
|[CListBox::GetLocale](#getlocale)|Récupère l’identificateur de paramètres régionaux pour une zone de liste.|
|[CListBox::GetSel](#getsel)|Retourne l’état de sélection d’un élément de zone de liste.|
|[CListBox::GetSelCount](#getselcount)|Retourne le nombre de chaînes actuellement sélectionné dans une zone de liste à sélection multiple.|
|[CListBox::GetSelItems](#getselitems)|Retourne les index des chaînes actuellement sélectionnés dans une zone de liste.|
|[CListBox::GetText](#gettext)|Copie un élément de zone de liste dans une mémoire tampon.|
|[CListBox::GetTextLen](#gettextlen)|Retourne la longueur en octets d’un élément de zone de liste.|
|[CListBox::GetTopIndex](#gettopindex)|Retourne l’index de la première chaîne visible dans une zone de liste.|
|[CListBox::InitStorage](#initstorage)|Préalloue les blocs de mémoire pour les chaînes et les éléments de liste.|
|[CComboBox::InsertString](#insertstring)|Insère une chaîne à un emplacement spécifique dans une zone de liste.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Retourne l’index de l’élément de zone de liste le plus proche d’un point.|
|[CListBox::MeasureItem](#measureitem)|Appelé par le framework lorsqu’une zone de liste owner-draw est créée pour déterminer les dimensions de la zone de liste.|
|[CListBox::ResetContent](#resetcontent)|Efface toutes les entrées à partir d’une zone de liste.|
|[CListBox::SelectString](#selectstring)|Recherche et sélectionne une chaîne dans une zone de liste à sélection unique.|
|[CListBox::SelItemRange](#selitemrange)|Sélectionne ou désélectionne une plage de chaînes dans une zone de liste à sélection multiple.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Définit le point d’ancrage dans une zone de liste à sélection multiple pour commencer une sélection étendue.|
|[CListBox::SetCaretIndex](#setcaretindex)|Définit le rectangle de focus à l’élément à l’index spécifié dans une zone de liste à sélection multiple.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Définit la largeur de colonne d’une zone de liste multicolonne.|
|[CListBox::SetCurSel](#setcursel)|Sélectionne une chaîne de la zone de liste.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Définit la largeur en pixels qu’une zone de liste de défilement horizontale.|
|[CListBox::SetItemData](#setitemdata)|Définit la valeur de 32 bits associée à l’élément de zone de liste.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Définit un pointeur vers l’élément de zone de liste.|
|[CListBox::SetItemHeight](#setitemheight)|Définit la hauteur d’éléments dans une zone de liste.|
|[CListBox::SetLocale](#setlocale)|Définit l’identificateur de paramètres régionaux pour une zone de liste.|
|[CListBox::SetSel](#setsel)|Sélectionne ou désélectionne un élément de zone de liste dans une zone de liste à sélection multiple.|
|[CListBox::SetTabStops](#settabstops)|Définit les positions de taquet de tabulation dans une zone de liste.|
|[CListBox::SetTopIndex](#settopindex)|Définit l’index de base zéro de la première chaîne visible dans une zone de liste.|
|[CListBox::VKeyToItem](#vkeytoitem)|Méthode override pour fournir WM_KEYDOWN personnalisée de gestion des zones de liste avec le jeu de styles LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Notes

Une zone de liste affiche une liste d’éléments, tels que des noms de fichiers, l’utilisateur peut afficher et sélectionner.

Dans une zone de liste à sélection unique, l’utilisateur peut sélectionner un seul élément. Dans une zone de liste à sélection multiple, une plage d’éléments peut être sélectionnée. Lorsque l’utilisateur sélectionne un élément, il est mis en surbrillance et la zone de liste envoie un message de notification à la fenêtre parente.

Vous pouvez créer une zone de liste à partir d’un modèle de boîte de dialogue ou directement dans votre code. Pour la créer directement, vous devez construire le `CListBox` de l’objet, puis appelez le [créer](#create) fonction membre pour créer le contrôle de zone de liste Windows et l’attacher à la `CListBox` objet. Pour utiliser une zone de liste dans un modèle de boîte de dialogue, déclarez une variable de la zone de liste dans votre classe de boîte de dialogue, puis utilisez `DDX_Control` dans votre classe de boîte de dialogue `DoDataExchange` (fonction) pour se connecter de la variable membre pour le contrôle. (cela est fait pour vous automatiquement lorsque vous ajoutez une variable de contrôle à votre classe de boîte de dialogue.)

Construction peut être un processus en une étape dans une classe dérivée de `CListBox`. Écrire un constructeur pour la classe dérivée et appelez `Create` à partir de dans le constructeur.

Si vous souhaitez gérer les messages de notification Windows envoyés par une zone de liste à son parent (généralement une classe dérivée de [CDialog](../../mfc/reference/cdialog-class.md)), ajouter une fonction de membre entrée et le Gestionnaire de messages-table des messages à la classe parente pour chaque message.

Chaque entrée de table des messages prend la forme suivante :

`ON_Notification( id, memberFxn )`

où `id` Spécifie l’ID de fenêtre enfant du contrôle zone de liste envoie la notification et `memberFxn` est le nom de la fonction de membre parent que vous avez écrit pour gérer les notifications.

Prototype de fonction du parent est la suivante :

`afx_msg void memberFxn( );`

Voici une liste des entrées de table des messages potentielles et une description des cas dans lequel ils seraient envoyées au parent :

- ON_LBN_DBLCLK l’utilisateur double-clique sur une chaîne dans une zone de liste. Une zone de liste qui a le [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style va envoyer ce message de notification.

- ON_LBN_ERRSPACE la zone de liste ne peut pas allouer suffisamment de mémoire pour répondre à la demande.

- ON_LBN_KILLFOCUS la zone de liste perd le focus d’entrée.

- ON_LBN_SELCANCEL la sélection actuelle de la zone de liste est annulée. Ce message est envoyé uniquement quand une zone de liste a le style LBS_NOTIFY.

- ON_LBN_SELCHANGE la sélection dans la zone de liste a changé. Cette notification n’est pas envoyée si la sélection est modifiée par le [CListBox::SetCurSel](#setcursel) fonction membre. Cette notification s’applique uniquement à une zone de liste qui a le style LBS_NOTIFY. Le message de notification LBN_SELCHANGE est envoyé pour une zone de liste à sélection multiple chaque fois que l’utilisateur appuie sur une touche de direction, même si la sélection ne change pas.

- ON_LBN_SETFOCUS la zone de liste reçoit le focus d’entrée.

- ON_WM_CHARTOITEM une zone de liste en mode owner-draw dont aucun chaînes reçoit un message WM_CHAR.

- Zone de liste A ON_WM_VKEYTOITEM avec le style LBS_WANTKEYBOARDINPUT reçoit un message WM_KEYDOWN.

Si vous créez un `CListBox` objet au sein d’une boîte de dialogue (via une ressource de boîte de dialogue), le `CListBox` automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CListBox` objet dans une fenêtre, vous devez détruire le `CListBox` objet. Si vous créez le `CListBox` de l’objet sur la pile, il est supprimé automatiquement. Si vous créez le `CListBox` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet à détruire lorsque l’utilisateur ferme la fenêtre parente.

Si vous allouez de mémoire dans le `CListBox` d’objet, de remplacer le `CListBox` destructeur pour les supprimer de l’allocation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="addstring"></a>  CListBox::AddString

Ajoute une chaîne à une zone de liste.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Paramètres

*lpszItem*<br/>
Pointe vers la chaîne se terminant par null qui doit être ajouté.

### <a name="return-value"></a>Valeur de retour

Index de base zéro à la chaîne dans la zone de liste. La valeur de retour est LB_ERR si une erreur se produit ; la valeur de retour est LB_ERRSPACE si l’espace est insuffisant stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Si la zone de liste n’a pas été créée avec le [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style, la chaîne est ajoutée à la fin de la liste. Sinon, la chaîne est insérée dans la liste, et la liste est triée. Si la zone de liste a été créée avec le style LBS_SORT mais pas le [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style, le framework trie la liste par un ou plusieurs appels à la `CompareItem` fonction membre.

Utilisez [InsertString](#insertstring) pour insérer une chaîne dans un emplacement spécifique dans la zone de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>  CListBox::CharToItem

Appelé par l’infrastructure lors de la fenêtre parente de la zone de liste reçoit un message WM_CHARTOITEM à partir de la zone de liste.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Paramètres

*nKey*<br/>
Le code ANSI du caractère de l’utilisateur a tapé.

*nIndex*<br/>
La position actuelle du signe insertion de zone de liste.

### <a name="return-value"></a>Valeur de retour

Retourne - 1 ou - 2 pour aucune autre action ou un nombre non négatif pour spécifier un index d’un élément de zone de liste sur laquelle effectuer l’action par défaut pour la séquence de touches. L’implémentation par défaut retourne - 1.

### <a name="remarks"></a>Notes

Le message WM_CHARTOITEM est envoyé par la zone de liste lorsqu’il reçoit un message WM_CHAR, mais uniquement si la zone de liste répond à ces critères :

- Est une zone de liste owner-draw.

- N’a pas la [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ensemble de style.

- A au moins un élément.

Vous devez jamais appeler cette fonction vous-même. Remplacez cette fonction pour fournir votre propre gestion personnalisée des messages de clavier.

Dans la substitution, vous devez retourner une valeur pour indiquer quelle action que vous avez effectuées à l’infrastructure. Une valeur de retour de - 1 ou - 2 indique que vous géré tous les aspects de la sélection de l’élément et ne nécessite aucune action supplémentaire par la zone de liste. Avant de retourner - 1 ou - 2, vous pouvez définir la sélection ou déplacer le signe insertion ou les deux. Pour définir la sélection, utilisez [SetCurSel](#setcursel) ou [fonction membre SetSel](#setsel). Pour déplacer le signe insertion, utilisez [SetCaretIndex](#setcaretindex).

Une valeur de retour égale ou supérieure à 0 spécifie l’index d’un élément dans la zone de liste et indique que la zone de liste doit effectuer l’action par défaut pour la séquence de touches sur l’élément donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>  CListBox::CListBox

Construit un objet `CListBox`.

```
CListBox();
```

### <a name="remarks"></a>Notes

Vous construisez un `CListBox` objet en deux étapes. Tout d’abord, appelez le constructeur `ClistBox` , puis appelez `Create`, qui initialise la zone de liste Windows et l’attache à la `CListBox`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>  CListBox::CompareItem

Appelé par l’infrastructure pour déterminer la position relative d’un nouvel élément dans une zone de liste triée en mode owner-draw.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpCompareItemStruct*<br/>
Un pointeur long désignant un `COMPAREITEMSTRUCT` structure.

### <a name="return-value"></a>Valeur de retour

Indique la position relative des deux éléments décrits dans le [COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md) structure. Il peut être une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|-1|Élément 1 est trié avant l’élément 2.|
|0|Article 1 et article 2 trient les mêmes.|
|1|Élément 1 se situe après l’élément 2.|

Consultez [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) pour obtenir une description de la `COMPAREITEMSTRUCT` structure.

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Si vous créez une zone de liste owner-draw avec le style LBS_SORT, vous devez substituer cette fonction membre pour aider le framework lors du tri des nouveaux éléments ajoutés à la zone de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>  CListBox::Create

Crée la zone de liste Windows et l’attache à la `CListBox` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style de la zone de liste. Appliquer n’importe quelle combinaison de [styles de zone de liste](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) à la zone.

*Rect*<br/>
Spécifie la taille de la zone de liste et la position. Peut être un `CRect` objet ou un `RECT` structure.

*pParentWnd*<br/>
Spécifie la fenêtre parente de la zone de liste (généralement un `CDialog` objet). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de. la zone de liste

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CListBox` objet en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, qui initialise la zone de liste Windows et l’attache à la `CListBox` objet.

Lorsque `Create` s’exécute, les envois de Windows le [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), et [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) messages sur le contrôle de zone de liste.

Ces messages sont gérées par défaut par le [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), et [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) fonctions membres dans la `CWnd` classe de base. Pour étendre la gestion de message par défaut, dérivez une classe de `CListBox`, ajouter une table des messages à la nouvelle classe et substituer les fonctions membres de gestionnaire de messages précédent. Substituer `OnCreate`, par exemple, pour effectuer une initialisation nécessaire pour une nouvelle classe.

Appliquer les éléments suivants [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à un contrôle de zone de liste.

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_VSCROLL pour ajouter une barre de défilement verticale

- WS_HSCROLL pour ajouter une barre de défilement horizontale

- WS_GROUP aux contrôles de groupe

- WS_TABSTOP pour permettre la tabulation à ce contrôle

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>  CListBox::DeleteItem

Appelé par le framework lorsque l’utilisateur supprime un élément à partir d’un mode owner-draw `CListBox` détruit la zone de liste ou d’objet.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDeleteItemStruct*<br/>
Un pointeur long désignant un Windows [DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md) structure qui contient des informations sur l’élément supprimé.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour redessiner une zone de liste owner-draw en fonction des besoins.

Consultez [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) pour obtenir une description de la `DELETEITEMSTRUCT` structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>  CListBox::DeleteString

Supprime l’élément dans la position *nIndex* à partir de la zone de liste.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de la chaîne à supprimer.

### <a name="return-value"></a>Valeur de retour

Décompte des chaînes restant dans la liste. La valeur de retour est LB_ERR si *nIndex* spécifie un index supérieur au nombre d’éléments dans la liste.

### <a name="remarks"></a>Notes

Tous les éléments suivant *nIndex* maintenant déplacer vers le bas une position. Par exemple, si une zone de liste contient deux éléments, la suppression du premier élément entraîne l’élément restant maintenant se trouver dans la première position. *nIndex*= 0 pour l’élément dans la première position.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>  CListBox::Dir

Ajoute une liste de noms de fichiers, les lecteurs ou les deux dans une zone de liste.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Paramètres

*attr*<br/>
Peut être n’importe quelle combinaison de la **enum** valeurs décrites dans `CFile::GetStatu` [s](../../mfc/reference/cfile-class.md#getstatus), ou n’importe quelle combinaison des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|0x0000|Fichier permettre être lues ou écrit pour.|
|0 x 0001|Fichier puisse être lues mais ne pas écrite dans.|
|0 x 0002|Fichier est masqué et n’apparaît pas dans une liste de répertoires.|
|0 x 0004|Fichier est un fichier système.|
|0x0010|Le nom spécifié par *lpszWildCard* spécifie un répertoire.|
|0x0020|Fichier a été archivé.|
|0 x 4000|Inclure tous les lecteurs qui correspondent au nom spécifié par *lpszWildCard*.|
|0 x 8000|Indicateur exclusive. Si l’indicateur exclusif est défini, seuls les fichiers du type spécifié sont répertoriés. Sinon, les fichiers du type spécifié sont répertoriés en plus des fichiers « normales ».|

*lpszWildCard*<br/>
Pointe vers une chaîne de spécification de fichier. La chaîne peut contenir des caractères génériques (par exemple, *.\*).

### <a name="return-value"></a>Valeur de retour

Index de base zéro du dernier nom de fichier ajouté à la liste. La valeur de retour est LB_ERR si une erreur se produit ; la valeur de retour est LB_ERRSPACE si l’espace est insuffisant stocker les nouvelles chaînes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>  CListBox::DrawItem

Appelé par l’infrastructure lorsqu’un aspect visuel d’une change de zone de liste en mode owner-draw.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur long désignant un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` et `itemState` membres de la `DRAWITEMSTRUCT` structure définir l’action de dessin qui doit être effectuée.

Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre pour implémenter le dessin pour un mode owner-draw `CListBox` objet. L’application doit restaurer tous les objets interface (GDI) périphérique graphique sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant ce membre de fonction se termine.

Consultez [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) pour obtenir une description de la `DRAWITEMSTRUCT` structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>  CListBox::FindString

Recherche la première chaîne dans une zone de liste qui contient le préfixe spécifié sans modifier la sélection de zone de liste.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Paramètres

*nStartAfter*<br/>
Contient l’index de base zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la zone de liste, il continue à partir du haut de la zone de liste à l’élément spécifié par *nStartAfter*. Si *nStartAfter* est -1, la zone de liste entière est recherchée à partir du début.

*lpszItem*<br/>
Pointe vers la chaîne se terminant par null qui contient le préfixe à rechercher. La recherche respecte la casse est indifférente, donc cette chaîne peut contenir toute combinaison de lettres majuscules et les minuscules.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément correspondant, ou LB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Utilisez le [SelectString](#selectstring) fonction membre pour rechercher et sélectionner une chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>  CListBox::FindStringExact

Recherche la première chaîne de zone de liste qui correspond à la chaîne spécifiée dans *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Paramètres

*nIndexStart*<br/>
Spécifie l’index de base zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la zone de liste, il continue à partir du haut de la zone de liste à l’élément spécifié par *nIndexStart*. Si *nIndexStart* est -1, la zone de liste entière est recherchée à partir du début.

*lpszFind*<br/>
Pointe vers la chaîne se terminant par null à rechercher. Cette chaîne peut contenir un nom de fichier complet, y compris l’extension. La recherche n’est pas la casse, la chaîne peut contenir toute combinaison de lettres majuscules et les minuscules.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément correspondant, ou LB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Si la zone de liste a été créée avec un style de mode owner-draw, mais sans le [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style, le `FindStringExact` fonction membre tente de correspondre à la valeur DWORD par rapport à la valeur de *lpszFind*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex

Récupère l’index de base zéro de l’élément d’ancrage actuel dans la zone de liste.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Valeur de retour

L’index de l’élément d’ancrage actuel, en cas de réussite ; LB_ERR sinon.

### <a name="remarks"></a>Notes

Dans une zone de liste à sélection multiple, l’élément d’ancrage est le premier ou au dernier élément dans un bloc d’éléments sélectionnés contiguës.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CListBox::SetAnchorIndex](#setanchorindex).

##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex

Détermine l’index de l’élément qui a le rectangle de focus dans une zone de liste à sélection multiple.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément qui contient le rectangle de focus dans une zone de liste. Si la zone de liste est une zone de liste de sélection unique, la valeur de retour est l’index de l’élément est sélectionné, le cas échéant.

### <a name="remarks"></a>Notes

L’élément peut ou ne peut pas être sélectionné.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CListBox::SetCaretIndex](#setcaretindex).

##  <a name="getcount"></a>  CListBox::GetCount

Récupère le nombre d’éléments dans une zone de liste.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la zone de liste, ou LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Le nombre retourné est égale à celle de la valeur d’index du dernier élément (l’index est de base zéro).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>  CListBox::GetCurSel

Récupère l’index de base zéro de l’élément actuellement sélectionné, le cas échéant, dans une zone de liste de sélection unique.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément actuellement sélectionné dans le cas d’une zone de liste de sélection unique. Il est LB_ERR si aucun élément n’est actuellement sélectionné.

Dans une zone de liste à sélection multiple, l’index de l’élément qui a le focus.

### <a name="remarks"></a>Notes

N’appelez pas `GetCurSel` pour une zone de liste à sélection multiple. Utilisez [CListBox::GetSelItems](#getselitems) à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>  CListBox::GetHorizontalExtent

Récupère, à partir de la zone de liste, la largeur en pixels par lequel il peut défiler horizontalement.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de défilement de la zone de liste, en pixels.

### <a name="remarks"></a>Notes

Cela s’applique uniquement si la zone de liste a une barre de défilement horizontale.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>  CListBox::GetItemData

Récupère la valeur de DWORD fournie par l’application associée à l’élément de zone de liste spécifié.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

La valeur de 32 bits associée à l’élément, ou LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

La valeur de mot double a été le *dwItemData* paramètre d’un [SetItemData](#setitemdata) appeler.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr

Récupère la valeur de 32 bits fournie par l’application associée à l’élément de zone de liste spécifié en tant que pointeur (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément dans la zone de liste.

### <a name="return-value"></a>Valeur de retour

Récupère un pointeur, ou -1 si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>  CListBox::GetItemHeight

Détermine la hauteur d’éléments dans une zone de liste.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément dans la zone de liste. Ce paramètre est utilisé uniquement si la zone de liste a le style LBS_OWNERDRAWVARIABLE ; Sinon, elle doit être définie sur 0.

### <a name="return-value"></a>Valeur de retour

La hauteur, en pixels, des éléments dans la zone de liste. Si la zone de liste a le [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style, la valeur de retour est la hauteur de l’élément spécifié par *nIndex*. Si une erreur se produit, la valeur de retour est LB_ERR.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>  CListBox::GetItemRect

Récupère les dimensions du rectangle de cet élément de limites d’une zone de liste tel qu’il est actuellement affiché dans la fenêtre de la zone de liste.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément.

*lpRect*<br/>
Spécifie un pointeur long désignant un [structure RECT](../../mfc/reference/rect-structure1.md) qui reçoit les coordonnées clientes de zone de liste de l’élément.

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

Nombre d’éléments par colonne de la `CListBox` objet.

### <a name="remarks"></a>Notes

Cette fonction membre émule la fonctionnalité de la [LB_GETLISTBOXINFO](/windows/desktop/Controls/lb-getlistboxinfo) du message, comme décrit dans le SDK Windows.

##  <a name="getlocale"></a>  CListBox::GetLocale

Récupère les paramètres régionaux utilisés par la zone de liste.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur d’identificateur (LCID) de paramètres régionaux pour les chaînes dans la zone de liste.

### <a name="remarks"></a>Notes

Par exemple, les paramètres régionaux sont utilisé pour déterminer l’ordre de tri des chaînes dans une zone de liste triée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CListBox::SetLocale](#setlocale).

##  <a name="getsel"></a>  CListBox::GetSel

Récupère l’état de sélection d’un élément.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément.

### <a name="return-value"></a>Valeur de retour

Un nombre positif si l’élément spécifié est sélectionné ; Sinon, il est 0. La valeur de retour est LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Cette fonction membre fonctionne avec les deux zones de liste de sélection unique et multiple.

Pour récupérer l’index de l’élément de zone de liste sélectionné, utilisez [CListBox::GetCurSel](#getcursel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>  CListBox::GetSelCount

Récupère le nombre total d’éléments sélectionnés dans une zone de liste à sélection multiple.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments sélectionnés dans une zone de liste. Si la zone de liste est une zone de liste de sélection unique, la valeur de retour est LB_ERR.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CListBox::GetSelItems](#getselitems).

##  <a name="getselitems"></a>  CListBox::GetSelItems

Remplit une mémoire tampon avec un tableau d’entiers qui spécifie les numéros d’article des éléments sélectionnés dans une zone de liste à sélection multiple.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Paramètres

*nMaxItems*<br/>
Spécifie le nombre maximal d’éléments sélectionnés, dont les numéros d’élément doivent être placés dans la mémoire tampon.

*rgIndex*<br/>
Spécifie un pointeur vers une mémoire tampon assez grande pour que le nombre d’entiers spécifié par *nMaxItems*.

### <a name="return-value"></a>Valeur de retour

Le nombre réel d’éléments placés dans la mémoire tampon. Si la zone de liste est une zone de liste de sélection unique, la valeur de retour est `LB_ERR`.

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

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de la chaîne doit être récupéré.

*lpszbuffer a été*<br/>
Pointe vers la mémoire tampon qui reçoit la chaîne. La mémoire tampon doit avoir suffisamment d’espace pour la chaîne et un caractère null de fin. La taille de la chaîne peut être déterminée avance en appelant le `GetTextLen` fonction membre.

*rString*<br/>
Référence à un objet `CString`.

### <a name="return-value"></a>Valeur de retour

La longueur (en octets) de la chaîne, à l’exclusion du caractère null de fin. Si *nIndex* ne spécifie pas un index valide, la valeur de retour est LB_ERR.

### <a name="remarks"></a>Notes

La deuxième forme de ce membre de fonction remplit un `CString` objet avec le texte de la chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>  CListBox::GetTextLen

Obtient la longueur d’une chaîne dans un élément de zone de liste.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de la chaîne.

### <a name="return-value"></a>Valeur de retour

La longueur de la chaîne en caractères, à l’exclusion du caractère null de fin. Si *nIndex* ne spécifie pas un index valide, la valeur de retour est LB_ERR.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CListBox::GetText](#gettext).

##  <a name="gettopindex"></a>  CListBox::GetTopIndex

Récupère l’index de base zéro du premier élément visible dans une zone de liste.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro du premier élément visible dans une zone de liste en cas de réussite, LB_ERR sinon.

### <a name="remarks"></a>Notes

Initialement, l’élément 0 est en haut de la zone de liste, mais si le défile de la zone de liste, un autre élément peut être en haut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>  CListBox::InitStorage

Alloue de la mémoire pour stocker les éléments de la zone de liste.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Paramètres

*nItems*<br/>
Spécifie le nombre d’éléments à ajouter.

*nBytes*<br/>
Spécifie la quantité de mémoire, en octets, à allouer pour les chaînes de l’élément.

### <a name="return-value"></a>Valeur de retour

Si la réussite, le nombre maximal d’éléments que la zone de liste peut stocker avant une réallocation de mémoire est nécessaire, sinon LB_ERRSPACE, ce qui signifie que ne pas assez de mémoire est disponible.

### <a name="remarks"></a>Notes

Appelez cette fonction avant d’ajouter un grand nombre d’éléments à un `CListBox`.

Cette fonction permet d’accélérer l’initialisation de zones de liste qui ont un grand nombre d’éléments (plus de 100). Il pré-alloue la quantité spécifiée de mémoire suivante qui [AddString](#addstring), [InsertString](#insertstring), et [Dir](#dir) fonctions acceptent les plus brefs délais. Vous pouvez utiliser des estimations pour les paramètres. Si vous Surestimez, partie de la mémoire supplémentaire est alloué ; Si vous sous-estimez, l’allocation normale est utilisée pour les éléments qui dépassent le montant préalloué.

Windows 95/98 : le *nItems* paramètre est limité aux valeurs de 16 bits. Cela signifie que les zones de liste ne peut pas contenir d’éléments de plus de 32 767. Bien que le nombre d’éléments est limité, la taille totale des éléments dans une zone de liste est limitée uniquement par la mémoire disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>  CListBox::InsertString

Insère une chaîne dans la zone de liste.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de la position à laquelle insérer la chaîne. Si ce paramètre est -1, la chaîne est ajoutée à la fin de la liste.

*lpszItem*<br/>
Pointe vers la chaîne terminée par le caractère null qui doit être insérée.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la position à laquelle la chaîne a été insérée. La valeur de retour est LB_ERR si une erreur se produit ; la valeur de retour est LB_ERRSPACE si l’espace est insuffisant stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Contrairement à la [AddString](#addstring) fonction membre, `InsertString` n’entraîne pas une liste avec la [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style à trier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint

Détermine l’élément de zone de liste le plus proche du point spécifié dans *pt*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Point pour lequel rechercher l’élément le plus proche, spécifié par rapport à l’angle supérieur gauche de la zone cliente de la zone de liste.

*bOutside*<br/>
Référence à une variable de type BOOL qui sera définie sur TRUE si *pt* est en dehors de la zone cliente de l’élément de zone de liste le plus proche, FALSE si *pt* se trouve dans la zone cliente de l’élément de zone de liste le plus proche.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément le plus proche du point spécifié dans *pt*.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction pour déterminer quel élément de zone de liste le curseur de la souris passe au-dessus.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CListBox::SetAnchorIndex](#setanchorindex).

##  <a name="measureitem"></a>  CListBox::MeasureItem

Appelé par l’infrastructure lors de la création d’une zone de liste avec un style de dessin owner-drawn.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Un pointeur long désignant un [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) structure.

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre et renseignez la `MEASUREITEMSTRUCT` structure afin d’informer Windows de dimensions de la zone de liste. Si la zone de liste est créée avec le [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style, l’infrastructure appelle cette fonction membre pour chaque élément dans la zone de liste. Sinon, ce membre est appelé une seule fois.

Pour plus d’informations sur l’utilisation de la [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style dans une zone de liste owner-draw créée avec le `SubclassDlgItem` fonction membre de `CWnd`, consultez la discussion dans [14 Note technique](../../mfc/tn014-custom-controls.md).

Consultez [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pour obtenir une description de la `MEASUREITEMSTRUCT` structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>  CListBox::ResetContent

Supprime tous les éléments à partir d’une zone de liste.

```
void ResetContent();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>  CListBox::SelectString

Recherche d’un élément de zone de liste qui correspond à la chaîne spécifiée, et si un élément correspondant est trouvé, il sélectionne l’élément.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Paramètres

*nStartAfter*<br/>
Contient l’index de base zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la zone de liste, il continue à partir du haut de la zone de liste à l’élément spécifié par *nStartAfter*. Si *nStartAfter* est -1, la zone de liste entière est recherchée à partir du début.

*lpszItem*<br/>
Pointe vers la chaîne se terminant par null qui contient le préfixe à rechercher. La recherche respecte la casse est indifférente, donc cette chaîne peut contenir toute combinaison de lettres majuscules et les minuscules.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément sélectionné si la recherche a abouti. Si la recherche a échoué, la valeur de retour est LB_ERR et la sélection actuelle n’est pas modifiée.

### <a name="remarks"></a>Notes

La zone de liste défile si nécessaire, pour afficher l’élément sélectionné dans la vue.

Cette fonction membre ne peut pas être utilisée avec une zone de liste qui a le [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style.

Un élément est sélectionné uniquement si ses premiers caractères (du point de départ) correspondent aux caractères dans la chaîne spécifiée par *lpszItem*.

Utilisez le `FindString` fonction membre pour rechercher une chaîne sans sélectionner l’élément.

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

### <a name="parameters"></a>Paramètres

*zone bSélectionnez*<br/>
Spécifie la manière de définir la sélection. Si *zone bSélectionnez* a la valeur TRUE, la chaîne est sélectionnée et mis en surbrillance ; si la valeur est FALSE, la mise en surbrillance est supprimé et la chaîne n’est plus sélectionnée.

*nFirstItem*<br/>
Spécifie l’index de base zéro du premier élément à définir.

*nLastItem*<br/>
Spécifie l’index de base zéro du dernier élément à définir.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement avec les zones de liste à sélection multiple. Si vous devez sélectionner un seul élément dans une zone de liste à sélection multiple, autrement dit, si *nFirstItem* est égal à *nLastItem* : appeler le [fonction membre SetSel](#setsel) membre de fonction à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex

Définit le point d’ancrage dans une zone de liste à sélection multiple pour commencer une sélection étendue.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément de zone de liste qui sera le point d’ancrage.

### <a name="remarks"></a>Notes

Dans une zone de liste à sélection multiple, l’élément d’ancrage est le premier ou au dernier élément dans un bloc d’éléments sélectionnés contiguës.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex

Définit le rectangle de focus à l’élément à l’index spécifié dans une zone de liste à sélection multiple.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément à recevoir le rectangle de focus dans la zone de liste.

*bScroll*<br/>
Si cette valeur est 0, l’élément est l’objet d’un défilement jusqu'à ce qu’il soit entièrement visible. Si cette valeur n’est pas 0, l’élément défile jusqu'à ce qu’il soit au moins partiellement visible.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Si l’élément n’est pas visible, elle défile dans la vue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>  CListBox::SetColumnWidth

Définit la largeur en pixels de toutes les colonnes dans une zone de liste multicolonne (créé avec le [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style).

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Paramètres

*cxWidth*<br/>
Spécifie la largeur en pixels de toutes les colonnes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>  CListBox::SetCurSel

Sélectionne une chaîne et fait défiler dans la vue, si nécessaire.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Paramètres

*nSélectionnez*<br/>
Spécifie l’index de base zéro de la chaîne à être sélectionné. Si *nSélectionnez* est -1, la zone de liste est définie pour n’avoir aucune sélection.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Lorsque la nouvelle chaîne est sélectionnée, la zone de liste supprime la mise en surbrillance de la chaîne précédemment sélectionnée.

Utilisez cette fonction membre uniquement avec les zones de liste de sélection unique.

Pour définir ou supprimer une sélection dans une zone de liste à sélection multiple, utilisez [CListBox::SetSel](#setsel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>  CListBox::SetHorizontalExtent

Définit la largeur, en pixels, par lequel une zone de liste de défilement horizontale.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Paramètres

*cxExtent*<br/>
Spécifie le nombre de pixels par lequel la zone de liste de défilement horizontale.

### <a name="remarks"></a>Notes

Si la taille de la zone de liste est inférieure à cette valeur, la barre de défilement horizontale défilera horizontalement les éléments dans la zone de liste. Si la zone de liste est plus larges que cette valeur, la barre de défilement horizontale est masquée.

Pour répondre à un appel à `SetHorizontalExtent`, la zone de liste doit avoir été définie avec la [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) style.

Cette fonction membre n’est pas utile pour les zones de liste multicolonne. Pour les zones de liste multicolonne, appelez le `SetColumnWidth` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>  CListBox::SetItemData

Définit une valeur 32 bits associée à l’élément spécifié dans une zone de liste.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément.

*dwItemData*<br/>
Spécifie la valeur à associer à l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>  CListBox::SetItemDataPtr

Définit la valeur de 32 bits associée à l’élément spécifié dans une zone de liste comme étant le pointeur spécifié ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément.

*pData*<br/>
Spécifie le pointeur à associer à l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Ce pointeur reste valide pour la durée de vie de la zone de liste, même si la position relative de l’élément dans la zone de liste peut changer en fonction des éléments sont ajoutés ou supprimés. Par conséquent, l’index de l’élément dans la zone peut changer, mais le pointeur reste fiable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>  CListBox::SetItemHeight

Définit la hauteur d’éléments dans une zone de liste.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément dans la zone de liste. Ce paramètre est utilisé uniquement si la zone de liste a le style LBS_OWNERDRAWVARIABLE ; Sinon, elle doit être définie sur 0.

*cyItemHeight*<br/>
Spécifie la hauteur, en pixels, de l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR si l’index ou la hauteur n’est pas valide.

### <a name="remarks"></a>Notes

Si la zone de liste a le [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style, cette fonction définit la hauteur de l’élément spécifié par *nIndex*. Sinon, cette fonction définit la hauteur de tous les éléments dans la zone de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>  CListBox::SetLocale

Définit l’identificateur de paramètres régionaux pour cette zone de liste.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Paramètres

*nNewLocale*<br/>
La nouvelle valeur de l’identificateur (LCID) de paramètres régionaux à définir pour la zone de liste.

### <a name="return-value"></a>Valeur de retour

Valeur LCID (identificateur) de paramètres régionaux précédente pour cette zone de liste.

### <a name="remarks"></a>Notes

Si `SetLocale` n’est pas appelée, la valeur par défaut aux paramètres régionaux sont obtenu à partir du système. Ce paramètres régionaux par défaut du système peut être modifié à l’aide du panneau application régionales (ou International).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>  CListBox::SetSel

Sélectionne une chaîne dans une zone de liste à sélection multiple.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index de base zéro de la chaîne à définir. Si -1, la sélection est ajoutée ou supprimée de toutes les chaînes, selon la valeur de *zone bSélectionnez*.

*zone bSélectionnez*<br/>
Spécifie la manière de définir la sélection. Si *zone bSélectionnez* a la valeur TRUE, la chaîne est sélectionnée et mis en surbrillance ; si la valeur est FALSE, la mise en surbrillance est supprimé et la chaîne n’est plus sélectionnée. La chaîne spécifiée est sélectionnée et mis en surbrillance par défaut.

### <a name="return-value"></a>Valeur de retour

LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Utilisez cette fonction membre uniquement avec les zones de liste à sélection multiple.

Pour sélectionner un élément dans une zone de liste de sélection unique, utilisez [CListBox::SetCurSel](#setcursel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>  CListBox::SetTabStops

Définit les positions de taquet de tabulation dans une zone de liste.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Paramètres

*cxEachStop*<br/>
Taquets de tabulation sont définies à chaque *cxEachStop* unités de boîte de dialogue. Consultez *rgTabStops* pour obtenir une description d’une unité de boîte de dialogue.

*nTabStops*<br/>
Spécifie le nombre de taquets de tabulation pour avoir dans la zone de liste.

*rgTabStops*<br/>
Pointe vers le premier membre d’un tableau d’entiers qui contient les positions de taquet de tabulation dans les unités de boîte de dialogue. Une unité de boîte de dialogue est une distance horizontale ou verticale. Une unité de boîte de dialogue horizontale est égale à un quart de l’unité de base de la largeur de boîte de dialogue actuelle, et une unité de boîte de dialogue verticale est égale à un huitième de l’unité de base de hauteur de boîte de dialogue actuelle. Les unités de dialogue sont calculées en fonction de la hauteur et de la largeur de la police système actuelle. Le `GetDialogBaseUnits` (fonction) Windows retourne, unités de base, la boîte de dialogue actuelle en pixels. Les taquets de tabulation doivent être triées dans l’ordre ; croissant onglets précédent ne sont pas autorisés.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si tous les onglets ont été définies ; sinon 0.

### <a name="remarks"></a>Notes

Pour définir des taquets de tabulation à la taille par défaut de 2 unités de boîte de dialogue, appelez la version sans paramètre de cette fonction membre. Pour définir des taquets de tabulation à une taille de 2, appelez la version avec le *cxEachStop* argument.

Pour définir des taquets de tabulation à un tableau de tailles, utilisez la version avec le *rgTabStops* et *nTabStops* arguments. Un taquet de tabulation est défini pour chaque valeur dans *rgTabStops*, jusqu’au nombre spécifié par *nTabStops*.

Pour répondre à un appel à la `SetTabStops` fonction membre, la zone de liste doit avoir été créée avec le [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>  CListBox::SetTopIndex

Garantit qu’un élément particulier de zone de liste est visible.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément de zone de liste.

### <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, ou LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Le système fait défiler la liste jusqu'à ce que soit l’élément spécifié par *nIndex* s’affiche en haut de la liste de zone ou la plage de défilement maximal a été atteint.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>  CListBox::VKeyToItem

Appelé par l’infrastructure lors de la fenêtre parente de la zone de liste reçoit un message WM_VKEYTOITEM à partir de la zone de liste.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Paramètres

*nKey*<br/>
Le code de touche virtuelle de la clé de l’utilisateur a appuyé. Pour obtenir la liste de codes de touches virtuelles, consultez Winuser.h

*nIndex*<br/>
La position actuelle du signe insertion de zone de liste.

### <a name="return-value"></a>Valeur de retour

Retourne - 2 pour aucune autre action, - 1 pour l’action par défaut ou un nombre non négatif pour spécifier un index d’un élément de zone de liste sur laquelle effectuer l’action par défaut pour la séquence de touches.

### <a name="remarks"></a>Notes

Le message WM_VKEYTOITEM est envoyé par la zone de liste lorsqu’il reçoit un message WM_KEYDOWN, mais uniquement si la zone de liste répond à des opérations suivantes :

- A la [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ensemble de style.

- A au moins un élément.

Vous devez jamais appeler cette fonction vous-même. Remplacez cette fonction pour fournir votre propre gestion personnalisée des messages de clavier.

Vous devez retourner une valeur pour indiquer quelle action votre remplacement effectuée à l’infrastructure. Une valeur de retour de - 2 indique que l’application gérée de tous les aspects de la sélection de l’élément et ne nécessite aucune action supplémentaire par la zone de liste. Avant de retourner - 2, vous pouvez définir la sélection ou déplacer le signe insertion ou les deux. Pour définir la sélection, utilisez [SetCurSel](#setcursel) ou [fonction membre SetSel](#setsel). Pour déplacer le signe insertion, utilisez [SetCaretIndex](#setcaretindex).

Une valeur de retour de - 1 indique que la zone de liste doit effectuer l’action par défaut en réponse à la séquence de touches. L’implémentation par défaut retourne - 1.

Une valeur de retour égale ou supérieure à 0 spécifie l’index d’un élément dans la zone de liste et indique que la zone de liste doit effectuer l’action par défaut pour la séquence de touches sur l’élément donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Voir aussi

[CTRLTEST MFC, exemple](../../visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic, classe](../../mfc/reference/cstatic-class.md)
