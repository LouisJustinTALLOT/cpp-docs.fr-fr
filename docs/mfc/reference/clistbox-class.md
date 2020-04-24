---
title: CListBox, classe
description: Une description de la classe MFC CListBox et de ses fonctions membres.
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
ms.openlocfilehash: 171038ebaaed815aa687c200fe3210bde8000be3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753581"
---
# <a name="clistbox-class"></a>CListBox, classe

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
|[CComboBox::AddString](#addstring)|Ajoute une chaîne à une boîte de liste.|
|[CListBox::CharToItem](#chartoitem)|Remplacement pour fournir la manipulation personnalisée WM_CHAR pour les boîtes de liste propriétaire-tirage qui n’ont pas de chaînes.|
|[CListBox::CompareItem](#compareitem)|Appelé par le cadre pour déterminer la position d’un nouvel élément dans une boîte triée liste propriétaire-tirage.|
|[CListBox::Créer](#create)|Crée la boîte de liste Windows `CListBox` et la fixe à l’objet.|
|[CListBox::DeleteItem](#deleteitem)|Appelé par le cadre lorsque l’utilisateur supprime un élément d’une boîte de liste propriétaire-tirage.|
|[CListBox::DeleteString](#deletestring)|Supprime une chaîne d’une boîte de liste.|
|[CListBox::Dir](#dir)|Ajoute des noms de fichiers, des lecteurs, ou les deux de l’annuaire actuel à une boîte de liste.|
|[CListBox::DrawItem](#drawitem)|Appelé par le cadre quand un aspect visuel d’une boîte de liste propriétaire-tirage change.|
|[CListBox::FindString](#findstring)|Recherche une chaîne dans une boîte de liste.|
|[CListBox::FindStringExact](#findstringexact)|Trouve la première chaîne de boîte de liste qui correspond à une chaîne spécifiée.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Récupère l’index zéro de l’élément d’ancrage actuel dans une boîte de liste.|
|[CListBox::GetCaretIndex](#getcaretindex)|Détermine l’index de l’élément qui a le rectangle de mise au point dans une boîte de liste de sélection multiple.|
|[CListBox::GetCount](#getcount)|Retourne le nombre de chaînes dans une boîte de liste.|
|[CListBox::GetCurSel](#getcursel)|Retourne l’index zéro de la chaîne actuellement sélectionnée dans une boîte de liste.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Retourne la largeur en pixels qu’une boîte de liste peut être défichée horizontalement.|
|[CListBox::GetItemData](#getitemdata)|Retourne une valeur associée à l’élément de la boîte de liste.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Retourne un pointeur à un élément de boîte de liste.|
|[CListBox::GetItemHeight](#getitemheight)|Détermine la hauteur des éléments dans une boîte de liste.|
|[CListBox::GetItemRect](#getitemrect)|Retourne le rectangle de délimitation de l’élément de la boîte de liste tel qu’il est actuellement affiché.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Récupère le nombre d’éléments par colonne.|
|[CListBox::GetLocale](#getlocale)|Récupère l’identifiant local pour une boîte de liste.|
|[CListBox::GetSel](#getsel)|Retourne l’état de sélection d’un élément de liste-boîte.|
|[CListBox::GetSelCount](#getselcount)|Retourne le nombre de chaînes actuellement sélectionnées dans une boîte de liste de sélection multiple.|
|[CListBox::GetSelItems](#getselitems)|Retourne les indices des cordes actuellement sélectionnées dans une boîte de liste.|
|[CListBox::GetText](#gettext)|Copie d’un élément de boîte de liste dans un tampon.|
|[CListBox::GetTextLen](#gettextlen)|Retourne la longueur dans les octets d’un élément de liste-boîte.|
|[CListBox::GetTopIndex](#gettopindex)|Retourne l’index de la première chaîne visible dans une boîte de liste.|
|[CListBox::InitStorage](#initstorage)|Prélocalise les blocs de mémoire pour les articles de la boîte de liste et les chaînes.|
|[CComboBox::InsertString](#insertstring)|Insère une chaîne à un endroit précis dans une boîte de liste.|
|[CListBox::ItemDePoint](#itemfrompoint)|Retourne l’index de l’élément de la boîte de liste le plus proche d’un point.|
|[CListBox::MeasureItem](#measureitem)|Appelé par le cadre lorsqu’une boîte de liste propriétaire-tirage est créée pour déterminer les dimensions de la boîte de liste.|
|[CListBox::ResetContent](#resetcontent)|Efface toutes les entrées d’une boîte de liste.|
|[CListBox::SelectString](#selectstring)|Recherche et sélectionne une chaîne dans une boîte de liste à une seule sélection.|
|[CListBox::SelItemRange](#selitemrange)|Sélectionne ou désélectionne une gamme de chaînes dans une boîte de liste multi-sélection.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Définit l’ancre dans une boîte de liste de sélection multiple pour commencer une sélection étendue.|
|[CListBox::SetCaretIndex](#setcaretindex)|Définit le rectangle de mise au point à l’index spécifié dans une boîte de liste de sélection multiple.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Définit la largeur de colonne d’une boîte de liste multicolumn.|
|[CListBox::SetCurSel](#setcursel)|Sélectionne une chaîne de boîte de liste.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Définit la largeur en pixels qu’une boîte de liste peut être défichée horizontalement.|
|[CListBox::SetItemData](#setitemdata)|Définit une valeur associée à l’élément de liste.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Définit un pointeur à l’élément de liste-boîte.|
|[CListBox::SetItemHeight](#setitemheight)|Définit la hauteur des éléments dans une boîte de liste.|
|[CListBox::SetLocale](#setlocale)|Définit l’identifiant local pour une boîte de liste.|
|[CListBox::SetSel](#setsel)|Sélectionne ou désélectionne un élément de liste dans une boîte de liste multiple.|
|[CListBox::SetTabStops](#settabstops)|Définit les positions d’onglet-arrêt dans une boîte de liste.|
|[CListBox::SetTopIndex](#settopindex)|Définit l’index zéro de la première chaîne visible dans une boîte de liste.|
|[CListBox::VKeyToItem](#vkeytoitem)|Remplacement pour fournir la manipulation personnalisée WM_KEYDOWN pour les boîtes de liste avec l’ensemble de style LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Notes

Une boîte de liste affiche une liste d’éléments, tels que les noms de fichiers, que l’utilisateur peut afficher et sélectionner.

Dans une boîte de liste à une seule sélection, l’utilisateur ne peut sélectionner qu’un seul élément. Dans une boîte de liste de sélection multiple, une gamme d’éléments peut être sélectionnée. Lorsque l’utilisateur sélectionne un élément, il est mis en surbrillance et la boîte de liste envoie un message de notification à la fenêtre parente.

Vous pouvez créer une boîte de liste à partir d’un modèle de dialogue ou directement dans votre code. Pour le créer directement, construisez l’objet, `CListBox` appelez ensuite la fonction membre [Create](#create) pour créer le contrôle de la boîte de liste Windows et l’attacher à l’objet. `CListBox` Pour utiliser une boîte de liste dans un modèle de dialogue, déclarez `DDX_Control` une variable de boîte `DoDataExchange` de liste dans votre classe de boîte de dialogue, puis utilisez dans la fonction de votre classe de boîte de dialogue pour connecter la variable du membre au contrôle. (cela est fait pour vous automatiquement lorsque vous ajoutez une variable de contrôle à votre classe de boîte de dialogue.)

La construction peut être un processus en `CListBox`une seule étape dans une classe dérivée de . Écrivez un constructeur pour la `Create` classe dérivée et appelez à l’intérieur du constructeur.

Si vous souhaitez traiter les messages de notification Windows envoyés par une case de liste à son parent (généralement une classe dérivée de [CDialog),](../../mfc/reference/cdialog-class.md)ajoutez une entrée de carte de message et une fonction de membre de gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de carte de message prend la forme suivante :

`ON_Notification( id, memberFxn )`

où `id` spécifie l’ID de fenêtre de `memberFxn` l’enfant du contrôle de la boîte de liste envoyant la notification et est le nom de la fonction de membre parent que vous avez écrit pour gérer la notification.

Le prototype de fonction du parent est le suivant :

`afx_msg void memberFxn( );`

Voici une liste d’entrées potentielles de carte de message et une description des cas dans lesquels elles seraient envoyées au parent :

- ON_LBN_DBLCLK L’utilisateur double-clics une chaîne dans une boîte de liste. Seule une case qui a le style [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) enverra ce message de notification.

- ON_LBN_ERRSPACE La boîte de liste ne peut pas allouer suffisamment de mémoire pour répondre à la demande.

- ON_LBN_KILLFOCUS La boîte de liste perd la mise au point des entrées.

- ON_LBN_SELCANCEL La sélection actuelle de la case est annulée. Ce message n’est envoyé que lorsqu’une case a le style LBS_NOTIFY.

- ON_LBN_SELCHANGE La sélection dans la boîte de liste a changé. Cette notification n’est pas envoyée si la sélection est modifiée par la [CListBox : Fonction membre SetCurSel.](#setcursel) Cette notification ne s’applique qu’à une boîte de liste qui a le style LBS_NOTIFY. Le message de notification LBN_SELCHANGE est envoyé pour une boîte de liste de sélection multiple chaque fois que l’utilisateur appuie une clé de flèche, même si la sélection ne change pas.

- ON_LBN_SETFOCUS La boîte de liste reçoit l’accent sur les entrées.

- ON_WM_CHARTOITEM Une boîte de liste propriétaire-tirage qui n’a pas de chaînes reçoit un message WM_CHAR.

- ON_WM_VKEYTOITEM Une case box avec le style LBS_WANTKEYBOARDINPUT reçoit un message WM_KEYDOWN.

Si vous `CListBox` créez un objet dans une boîte de `CListBox` dialogue (via une ressource de dialogue), l’objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous `CListBox` créez un objet à l’intérieur `CListBox` d’une fenêtre, vous devrez peut-être détruire l’objet. Si vous `CListBox` créez l’objet sur la pile, il est détruit automatiquement. Si vous `CListBox` créez l’objet sur le tas en utilisant la **nouvelle** fonction, vous devez appeler **supprimer** sur l’objet pour le détruire lorsque l’utilisateur ferme la fenêtre parente.

Si vous allouez `CListBox` de la mémoire `CListBox` dans l’objet, remplacez le destructeur pour disposer de l’allocation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="clistboxaddstring"></a><a name="addstring"></a>CListBox::AddString

Ajoute une chaîne à une boîte de liste.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Paramètres

*lpszItem (en)*<br/>
Points à la chaîne non terminée qui doit être ajouté.

### <a name="return-value"></a>Valeur de retour

L’index à base de zéro à la chaîne dans la boîte de liste. La valeur de retour est LB_ERR si une erreur se produit; la valeur de retour est LB_ERRSPACE si un espace insuffisant est disponible pour stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Si la boîte de liste n’a pas été créée avec le style [LBS_SORT,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) la chaîne est ajoutée à la fin de la liste. Sinon, la chaîne est insérée dans la liste, et la liste est triée. Si la boîte de liste a été créée avec le style LBS_SORT mais pas le style [LBS_HASSTRINGS,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) le cadre trie la liste par un ou plusieurs appels à la `CompareItem` fonction membre.

Utilisez [InsertString](#insertstring) pour insérer une chaîne dans un emplacement spécifique dans la boîte de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

## <a name="clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::CharToItem

Appelé par le cadre lorsque la fenêtre parente de la boîte de liste reçoit un message WM_CHARTOITEM de la boîte de liste.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Paramètres

*nKey (en)*<br/>
Le code ANSI du personnage que l’utilisateur a tapé.

*nIndex*<br/>
La position actuelle de la liste-boîte caret.

### <a name="return-value"></a>Valeur de retour

Retourne - 1 ou - 2 pour aucune autre action ou un numéro non natif pour spécifier un index d’un élément de liste-boîte sur lequel effectuer l’action par défaut pour le coup de clé. La mise en œuvre par défaut revient - 1.

### <a name="remarks"></a>Notes

Le message WM_CHARTOITEM est envoyé par la case de liste lorsqu’il reçoit un message WM_CHAR, mais seulement si la case répond à tous ces critères :

- Est une boîte de liste propriétaire-tirage.

- N’a pas le [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ensemble de style.

- A au moins un élément.

Vous ne devriez jamais appeler cette fonction vous-même. Remplacez cette fonction pour fournir votre propre manipulation personnalisée des messages clavier.

Dans votre remplacement, vous devez retourner une valeur pour indiquer au cadre quelle action vous avez effectuée. Une valeur de retour de - 1 ou - 2 indique que vous avez traité tous les aspects de la sélection de l’élément et ne nécessite aucune autre action par la boîte de liste. Avant de revenir - 1 ou - 2, vous pouvez définir la sélection ou déplacer le caret ou les deux. Pour définir la sélection, utilisez [SetCurSel](#setcursel) ou [SetSel](#setsel). Pour déplacer le caret, utilisez [SetCaretIndex](#setcaretindex).

Une valeur de retour de 0 ou plus spécifie l’index d’un élément dans la boîte de liste et indique que la boîte de liste doit effectuer l’action par défaut pour la frappe sur l’élément donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

## <a name="clistboxclistbox"></a><a name="clistbox"></a>CListBox::CListBox

Construit un objet `CListBox`.

```
CListBox();
```

### <a name="remarks"></a>Notes

Vous construisez un `CListBox` objet en deux étapes. Tout d’abord, `ClistBox` appelez `Create`le constructeur, puis appelez , qui initialise `CListBox`la boîte de liste Windows et le fixe à la .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

## <a name="clistboxcompareitem"></a><a name="compareitem"></a>CListBox::CompareItem

Appelé par le cadre pour déterminer la position relative d’un nouvel élément dans une boîte de liste de propriétaire trié-tirage.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpCompareItemStruct*<br/>
Un long pointeur à une `COMPAREITEMSTRUCT` structure.

### <a name="return-value"></a>Valeur de retour

Indique la position relative des deux éléments décrits dans la structure [COMPAREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-compareitemstruct) Il peut s’agir de l’une ou l’autre des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|-1|L’article 1 trie avant l’article 2.|
|0|L’article 1 et l’article 2 trient de la même façon.|
|1|L’article 1 trie après l’article 2.|

Voir [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) pour une `COMPAREITEMSTRUCT` description de la structure.

### <a name="remarks"></a>Notes

Par défaut, cette fonction de membre ne fait rien. Si vous créez une boîte de liste propriétaire-tirage avec le style LBS_SORT, vous devez remplacer cette fonction de membre pour aider le cadre dans le tri des nouveaux éléments ajoutés à la boîte de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

## <a name="clistboxcreate"></a><a name="create"></a>CListBox::Créer

Crée la boîte de liste Windows `CListBox` et la fixe à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style de la boîte de liste. Appliquez n’importe quelle combinaison de [styles de boîte de liste](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) à la boîte.

*Rect*<br/>
Spécifie la taille et la position de la boîte de liste. Peut être `CRect` soit un `RECT` objet ou une structure.

*pParentWnd*<br/>
Spécifie la fenêtre parente `CDialog` de la boîte de liste (généralement un objet). Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CListBox` objet en deux étapes. Tout d’abord, appelez `Create`le constructeur, puis appelez , qui initialise `CListBox` la boîte de liste Windows et le fixe à l’objet.

Lors `Create` de l’exécution, Windows envoie le [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), et [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) messages au contrôle de la boîte de liste.

Ces messages sont traités par défaut par le [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize) `CWnd` , et les fonctions des membres [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) dans la classe de base. Pour étendre la manipulation par défaut `CListBox`du message, extraire une classe, ajouter une carte de message à la nouvelle classe et remplacer les fonctions précédentes des membres de gestionnaire de message. `OnCreate`Remplacer, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.

Appliquer les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle de liste-boîte.

- WS_CHILD toujours

- WS_VISIBLE Habituellement

- WS_DISABLED Rarement

- WS_VSCROLL Pour ajouter une barre de défilement verticale

- WS_HSCROLL Pour ajouter une barre de défilement horizontal

- WS_GROUP Pour les contrôles de groupe

- WS_TABSTOP pour permettre le tabbing à ce contrôle

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

## <a name="clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::DeleteItem

Appelé par le cadre lorsque l’utilisateur supprime `CListBox` un élément d’un objet de dessin du propriétaire ou détruit la boîte de liste.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDeleteItemStruct*<br/>
Un long pointeur vers une structure Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) qui contient des informations sur l’élément supprimé.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacer cette fonction pour redessiner une boîte de liste propriétaire-tirage au besoin.

Voir [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) pour une `DELETEITEMSTRUCT` description de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

## <a name="clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString

Supprime l’élément en position *nIndex* de la boîte de liste.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de la chaîne à supprimer.

### <a name="return-value"></a>Valeur de retour

Un décompte des cordes restantes dans la liste. La valeur de rendement est LB_ERR si *nIndex* spécifie un indice supérieur au nombre d’éléments de la liste.

### <a name="remarks"></a>Notes

Tous les éléments suivant *nIndex* se déplacent maintenant vers le bas d’une position. Par exemple, si une boîte de liste contient deux éléments, la suppression du premier élément entraînera l’élément restant d’être maintenant dans la première position. *nIndex*0 pour l’article en première position.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

## <a name="clistboxdir"></a><a name="dir"></a>CListBox::Dir

Ajoute une liste de noms de fichiers, lecteurs, ou les deux à une boîte de liste.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Paramètres

*Attr*<br/>
Peut être n’importe quelle combinaison `CFile::GetStatu`des valeurs **enum** décrites dans s , ou [n’importe](../../mfc/reference/cfile-class.md#getstatus)quelle combinaison des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|0x0000|Le fichier peut être lu ou écrit à.|
|0x0001|Le fichier peut être lu à partir mais pas écrit à.|
|0x0002|Le fichier est caché et n’apparaît pas dans une liste d’annuaire.|
|0x0004|Le fichier est un fichier système.|
|0x0010|Le nom spécifié par *lpszWildCard* spécifie un répertoire.|
|0x0020|Le fichier a été archivé.|
|0x4000|Inclure tous les lecteurs qui correspondent au nom spécifié par *lpszWildCard*.|
|0x8000|Drapeau exclusif. Si le drapeau exclusif est défini, seuls les fichiers du type spécifié sont répertoriés. Dans le cas contraire, les fichiers du type spécifié sont répertoriés en plus des fichiers « normaux ».|

*lpszWildCard (en)*<br/>
Indique une chaîne de spécification de fichier. La chaîne peut contenir des wildcards\*(par exemple, . . ).

### <a name="return-value"></a>Valeur de retour

L’index zéro du dernier nom de fichier ajouté à la liste. La valeur de retour est LB_ERR si une erreur se produit; la valeur de retour est LB_ERRSPACE si l’espace insuffisant est disponible pour stocker les nouvelles chaînes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

## <a name="clistboxdrawitem"></a><a name="drawitem"></a>CListBox::DrawItem

Appelé par le cadre quand un aspect visuel d’une boîte de liste propriétaire-tirage change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un long pointeur vers une structure [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` `itemState` et les `DRAWITEMSTRUCT` membres de la structure définissent l’action de dessin qui doit être effectuée.

Par défaut, cette fonction de membre ne fait rien. Remplacer cette fonction de membre pour implémenter le dessin d’un objet de dessin du `CListBox` propriétaire. L’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction de membre.

Voir [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) pour une `DRAWITEMSTRUCT` description de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

## <a name="clistboxfindstring"></a><a name="findstring"></a>CListBox::FindString

Trouve la première chaîne dans une boîte de liste qui contient le préfixe spécifié sans modifier la sélection de la boîte de liste.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Paramètres

*nStartAprès*<br/>
Contient l’index zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la boîte de liste, elle se poursuit du haut de la boîte de liste jusqu’à l’élément spécifié par *nStartAfter*. Si *nStartAfter* est de -1, la boîte de liste entière est recherchée depuis le début.

*lpszItem (en)*<br/>
Indique la chaîne non terminée qui contient le préfixe à rechercher. La recherche est indépendante de cas, de sorte que cette chaîne peut contenir n’importe quelle combinaison de majuscules et de lettres minuscules.

### <a name="return-value"></a>Valeur de retour

L’index à base nulle de l’élément correspondant, ou LB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Utilisez la fonction de membre [SelectString](#selectstring) pour trouver et sélectionner une chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

## <a name="clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::FindStringExact

Trouve la première chaîne de boîte de liste qui correspond à la chaîne spécifiée dans *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Paramètres

*nIndexStart*<br/>
Spécifie l’index zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la boîte de liste, elle se poursuit du haut de la boîte de liste jusqu’à l’élément spécifié par *nIndexStart*. Si *nIndexStart* est de -1, la boîte de liste entière est recherchée depuis le début.

*lpszFind*<br/>
Indique la corde non terminée à rechercher. Cette chaîne peut contenir un nom de fichier complet, y compris l’extension. La recherche n’est pas sensible aux cas, de sorte que la chaîne peut contenir n’importe quelle combinaison de majuscules et de lettres minuscules.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément correspondant, ou LB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Si la boîte de liste a été créée avec un style `FindStringExact` propriétaire-tirage, mais sans le style [LBS_HASSTRINGS,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) la fonction membre tente de correspondre à la valeur double mot contre la valeur de *lpszFind*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

## <a name="clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox::GetAnchorIndex

Récupère l’index zéro de l’élément d’ancrage actuel dans la boîte de liste.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Valeur de retour

L’indice de l’élément d’ancrage actuel, en cas de succès; autrement LB_ERR.

### <a name="remarks"></a>Notes

Dans une boîte de liste de sélection multiple, l’élément d’ancrage est le premier ou le dernier élément d’un bloc d’éléments contigus sélectionnés.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CListBox:SetAnchorIndex](#setanchorindex).

## <a name="clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox::GetCaretIndex

Détermine l’index de l’élément qui a le rectangle de mise au point dans une boîte de liste de sélection multiple.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Valeur de retour

L’index à base nulle de l’élément qui a le rectangle de mise au point dans une boîte de liste. Si la boîte de liste est une boîte de liste à sélection unique, la valeur de rendement est l’index de l’élément qui est sélectionné, le cas échéant.

### <a name="remarks"></a>Notes

L’article peut ou non être sélectionné.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CListBox:SetCaretIndex](#setcaretindex).

## <a name="clistboxgetcount"></a><a name="getcount"></a>CListBox::GetCount

Récupère le nombre d’éléments dans une boîte de liste.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la boîte de liste, ou LB_ERR en cas d’erreur.

### <a name="remarks"></a>Notes

Le nombre retourné est supérieur à la valeur indicative du dernier élément (l’indice est basé à zéro).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

## <a name="clistboxgetcursel"></a><a name="getcursel"></a>CListBox::GetCurSel

Récupère l’index zéro de l’élément actuellement sélectionné, le cas échéant, dans une boîte de liste à une seule sélection.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

L’index zéro de l’élément actuellement sélectionné s’il s’agit d’une boîte de liste à sélection unique. Il est LB_ERR si aucun élément n’est actuellement sélectionné.

Dans une boîte de liste à sélection multiple, l’index de l’élément qui a la mise au point.

### <a name="remarks"></a>Notes

N’appelez `GetCurSel` pas une case liste de sélection multiple. Utilisez [CListBox:GetSelItems](#getselitems) à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

## <a name="clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent

Récupère de la boîte de liste la largeur en pixels par lequel il peut être défilé horizontalement.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur défilement de la boîte de liste, en pixels.

### <a name="remarks"></a>Notes

Ceci n’est applicable que si la boîte de liste a une barre de défilement horizontale.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

## <a name="clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox::GetItemData

Récupère la valeur de double mot fournie par l’application associée à l’élément de boîte de liste spécifié.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de l’élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

La valeur associée à l’article, ou LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

La valeur de double mot était le paramètre *dwItemData* d’un appel [SetItemData.](#setitemdata)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

## <a name="clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox::GetItemDataPtr

Récupère la valeur 32 bits fournie par l’application associée à l’élément de boîte de liste spécifié comme pointeur **(vide** <strong>\*</strong>).

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de l’élément dans la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Récupère un pointeur, ou -1 si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

## <a name="clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox::GetItemHeight

Détermine la hauteur des éléments dans une boîte de liste.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de l’élément dans la boîte de liste. Ce paramètre n’est utilisé que si la boîte de liste a le style LBS_OWNERDRAWVARIABLE; autrement, il devrait être réglé à 0.

### <a name="return-value"></a>Valeur de retour

La hauteur, en pixels, des éléments de la boîte de liste. Si la boîte de liste a le style [LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) la valeur de retour est la hauteur de l’élément spécifié par *nIndex*. En cas d’erreur, la valeur de retour est LB_ERR.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

## <a name="clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox::GetItemRect

Récupère les dimensions du rectangle qui limite un élément de boîte de liste tel qu’il est actuellement affiché dans la fenêtre de la boîte de liste.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’indice zéro de l’élément.

*lpRect*<br/>
Spécifie un long pointeur d’une [structure RECT](/windows/win32/api/windef/ns-windef-rect) qui reçoit les coordonnées des clients de l’article.

### <a name="return-value"></a>Valeur de retour

LB_ERR en cas d’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

## <a name="clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox::GetListBoxInfo

Récupère le nombre d’éléments par colonne.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments par `CListBox` colonne de l’objet.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du [message LB_GETLISTBOXINFO,](/windows/win32/Controls/lb-getlistboxinfo) tel que décrit dans le SDK Windows.

## <a name="clistboxgetlocale"></a><a name="getlocale"></a>CListBox::GetLocale

Récupère le lieu utilisé par la boîte de liste.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de l’identifiant local (LCID) pour les chaînes de la boîte de liste.

### <a name="remarks"></a>Notes

Le lieu est utilisé, par exemple, pour déterminer le tri d’ordre des cordes dans une boîte de liste triée.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CListBox:SetLocale](#setlocale).

## <a name="clistboxgetsel"></a><a name="getsel"></a>CListBox::GetSel

Récupère l’état de sélection d’un élément.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’indice zéro de l’élément.

### <a name="return-value"></a>Valeur de retour

Un nombre positif si l’élément spécifié est sélectionné; sinon, c’est 0. La valeur de retour est LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Cette fonction de membre fonctionne avec des boîtes de liste de sélection unique et multiple.

Pour récupérer l’index de l’élément de la boîte de liste actuellement sélectionné, utilisez [CListBox:GetCurSel](#getcursel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

## <a name="clistboxgetselcount"></a><a name="getselcount"></a>CListBox::GetSelCount

Récupère le nombre total d’éléments sélectionnés dans une boîte de liste de sélection multiple.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments sélectionnés dans une boîte de liste. Si la boîte de liste est une boîte de liste à une seule sélection, la valeur de retour est LB_ERR.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CListBox:GetSelItems](#getselitems).

## <a name="clistboxgetselitems"></a><a name="getselitems"></a>CListBox::GetSelItems

Remplit un tampon avec une gamme d’entiers qui spécifie les numéros d’éléments sélectionnés dans une boîte de liste de sélection multiple.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Paramètres

*nMaxItems (en)*<br/>
Spécifie le nombre maximum d’éléments sélectionnés dont les numéros d’article doivent être placés dans le tampon.

*rgIndex*<br/>
Specifie un pointeur à un tampon assez grand pour le nombre d’intégrateurs spécifiés par *nMaxItems*.

### <a name="return-value"></a>Valeur de retour

Le nombre réel d’éléments placés dans le tampon. Si la boîte de liste est une boîte `LB_ERR`de liste de sélection unique, la valeur de retour est .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

## <a name="clistboxgettext"></a><a name="gettext"></a>CListBox::GetText

Obtient une chaîne d’une boîte de liste.

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
Spécifie l’index zéro de la chaîne à récupérer.

*lpszBuffer (en)*<br/>
Points vers le tampon qui reçoit la chaîne. Le tampon doit avoir suffisamment d’espace pour la chaîne et un caractère nul de fin. La taille de la chaîne peut être `GetTextLen` déterminée à l’avance en appelant la fonction membre.

*rString (en)*<br/>
Référence à un objet `CString`.

### <a name="return-value"></a>Valeur de retour

La longueur (dans les octets) de la chaîne, à l’exclusion du caractère nul de fin. Si *nIndex* ne spécifie pas un indice valide, la valeur de rendement est LB_ERR.

### <a name="remarks"></a>Notes

La deuxième forme de cette `CString` fonction de membre remplit un objet avec le texte de chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

## <a name="clistboxgettextlen"></a><a name="gettextlen"></a>CListBox::GetTextLen

Obtient la longueur d’une chaîne dans un élément de boîte de liste.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’indice zéro de la chaîne.

### <a name="return-value"></a>Valeur de retour

La longueur de la chaîne en caractères, à l’exclusion du caractère nul de fin. Si *nIndex* ne spécifie pas un indice valide, la valeur de rendement est LB_ERR.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CListBox:GetText](#gettext).

## <a name="clistboxgettopindex"></a><a name="gettopindex"></a>CListBox::GetTopIndex

Récupère l’index zéro du premier élément visible dans une boîte de liste.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valeur de retour

L’index zéro du premier élément visible dans une boîte de liste en cas de succès, LB_ERR autrement.

### <a name="remarks"></a>Notes

Initialement, l’élément 0 est en haut de la case de liste, mais si la boîte de liste est défilé, un autre élément peut être en haut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

## <a name="clistboxinitstorage"></a><a name="initstorage"></a>CListBox::InitStorage

Alloue la mémoire pour stocker les articles de liste.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Paramètres

*nItems (en)*<br/>
Spécifie le nombre d’éléments à ajouter.

*nBytes (en)*<br/>
Spécifie la quantité de mémoire, dans les octets, à allouer pour les chaînes d’objets.

### <a name="return-value"></a>Valeur de retour

En cas de succès, le nombre maximum d’articles que la boîte de liste peut stocker avant qu’une réaffectation de mémoire soit nécessaire, sinon LB_ERRSPACE, ce qui signifie qu’il n’y a pas assez de mémoire disponible.

### <a name="remarks"></a>Notes

Appelez cette fonction avant d’ajouter `CListBox`un grand nombre d’articles à un .

Cette fonction permet d’accélérer l’initialisation des boîtes de liste qui ont un grand nombre d’éléments (plus de 100). Il préalloce la quantité spécifiée de mémoire de sorte que les fonctions [suivantes AddString](#addstring), [InsertString](#insertstring), et [Dir](#dir) prennent le temps le plus court possible. Vous pouvez utiliser des estimations pour les paramètres. Si vous surestimez, une certaine mémoire supplémentaire est allouée; si vous sous-estimez, l’allocation normale est utilisée pour les articles qui dépassent le montant préaffecté.

Windows 95/98 seulement: Le paramètre *nItems* est limité à des valeurs 16 bits. Cela signifie que les boîtes de liste ne peuvent pas contenir plus de 32 767 articles. Bien que le nombre d’éléments soit limité, la taille totale des éléments dans une boîte de liste n’est limitée que par la mémoire disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

## <a name="clistboxinsertstring"></a><a name="insertstring"></a>CListBox::InsertString

Insère une chaîne dans la boîte de liste.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de la position d’insérer la chaîne. Si ce paramètre est de -1, la chaîne est ajoutée à la fin de la liste.

*lpszItem (en)*<br/>
Pointe vers la chaîne terminée par le caractère null qui doit être insérée.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la position à laquelle la chaîne a été insérée. La valeur de retour est LB_ERR si une erreur se produit; la valeur de retour est LB_ERRSPACE si un espace insuffisant est disponible pour stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Contrairement à la fonction `InsertString` membre [AddString,](#addstring) ne provoque pas une liste avec le style [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) à trier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

## <a name="clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox::ItemDePoint

Détermine l’élément de liste le plus proche du point spécifié dans *pt*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Point pour trouver l’article le plus proche, spécifié par rapport au coin supérieur gauche de la zone client de la boîte de liste.

*bOutside (en)*<br/>
Référence à une variable BOOL qui sera définie à TRUE si *pt* est en dehors de la zone client de la boîte de liste, FALSE si *pt* est à l’intérieur de la zone client de la boîte de liste.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément le plus proche au point spécifié dans *pt*.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction pour déterminer l’élément de liste-boîte du curseur de souris se déplace plus.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CListBox:SetAnchorIndex](#setanchorindex).

## <a name="clistboxmeasureitem"></a><a name="measureitem"></a>CListBox::MeasureItem

Appelé par le cadre quand une boîte de liste avec un style propriétaire-tirage est créé.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Un long pointeur vers une structure [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Notes

Par défaut, cette fonction de membre ne fait rien. Remplacez cette fonction de `MEASUREITEMSTRUCT` membre et remplissez la structure pour informer Windows des dimensions de la boîte de liste. Si la boîte de liste est créée avec le style [LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) le cadre appelle cette fonction de membre pour chaque élément de la boîte de liste. Sinon, ce membre n’est appelé qu’une seule fois.

Pour plus d’informations sur l’utilisation [du](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style LBS_OWNERDRAWFIXED dans `SubclassDlgItem` une `CWnd`boîte de liste propriétaire-tirage créé avec la fonction membre de , voir la discussion dans [La note technique 14](../../mfc/tn014-custom-controls.md).

Voir [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pour une `MEASUREITEMSTRUCT` description de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

## <a name="clistboxresetcontent"></a><a name="resetcontent"></a>CListBox::ResetContent

Supprime tous les éléments d’une boîte de liste.

```cpp
void ResetContent();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

## <a name="clistboxselectstring"></a><a name="selectstring"></a>CListBox::SelectString

Recherche un élément de boîte de liste qui correspond à la chaîne spécifiée, et si un élément correspondant est trouvé, il sélectionne l’élément.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Paramètres

*nStartAprès*<br/>
Contient l’index zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la boîte de liste, elle se poursuit du haut de la boîte de liste jusqu’à l’élément spécifié par *nStartAfter*. Si *nStartAfter* est de -1, la boîte de liste entière est recherchée depuis le début.

*lpszItem (en)*<br/>
Indique la chaîne non terminée qui contient le préfixe à rechercher. La recherche est indépendante de cas, de sorte que cette chaîne peut contenir n’importe quelle combinaison de majuscules et de lettres minuscules.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément sélectionné si la recherche a été réussie. Si la recherche a échoué, la valeur de retour est LB_ERR et la sélection actuelle n’est pas modifiée.

### <a name="remarks"></a>Notes

La boîte de liste est défichée, si nécessaire, pour mettre l’élément sélectionné en vue.

Cette fonction de membre ne peut pas être utilisée avec une boîte de liste qui a le [style LBS_MULTIPLESEL.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

Un élément n’est sélectionné que si ses personnages initiaux (à partir du point de départ) correspondent aux caractères de la chaîne spécifiée par *lpszItem*.

Utilisez `FindString` la fonction membre pour trouver une chaîne sans sélectionner l’élément.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

## <a name="clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::SelItemRange

Sélectionne plusieurs éléments consécutifs dans une boîte de liste de sélection multiple.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Paramètres

*bSelect (en)*<br/>
Précise comment définir la sélection. Si *bSelect* est VRAI, la chaîne est sélectionnée et mise en surbrillance; si FALSE, le point culminant est supprimé et la chaîne n’est plus sélectionnée.

*nFirstItem (en)*<br/>
Spécifie l’indice zéro du premier élément à définir.

*nLastItem (en)*<br/>
Spécifie l’indice zéro du dernier élément à définir.

### <a name="return-value"></a>Valeur de retour

LB_ERR en cas d’erreur.

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre uniquement avec des cases de liste de sélection multiple. Si vous avez besoin de sélectionner un seul élément dans une boîte de liste de sélection multiple - c’est-à-dire, si *nFirstItem* est égal à *nLastItem* - appelez la fonction [membre SetSel](#setsel) à la place.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

## <a name="clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::SetAnchorIndex

Définit l’ancre dans une boîte de liste de sélection multiple pour commencer une sélection étendue.

```cpp
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de l’élément de la boîte de liste qui sera l’ancre.

### <a name="remarks"></a>Notes

Dans une boîte de liste de sélection multiple, l’élément d’ancrage est le premier ou le dernier élément d’un bloc d’éléments contigus sélectionnés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

## <a name="clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::SetCaretIndex

Définit le rectangle de mise au point à l’index spécifié dans une boîte de liste de sélection multiple.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de l’élément pour recevoir le rectangle de mise au point dans la boîte de liste.

*bScroll (en)*<br/>
Si cette valeur est de 0, l’élément est défilé jusqu’à ce qu’il soit entièrement visible. Si cette valeur n’est pas 0, l’élément est défilé jusqu’à ce qu’il soit au moins partiellement visible.

### <a name="return-value"></a>Valeur de retour

LB_ERR en cas d’erreur.

### <a name="remarks"></a>Notes

Si l’élément n’est pas visible, il est défiché en vue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

## <a name="clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox::SetColumnWidth

Définit la largeur en pixels de toutes les colonnes dans une boîte de liste multicolumn (créée avec le style [LBS_MULTICOLUMN).](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

```cpp
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Paramètres

*cxWidth (en)*<br/>
Spécifie la largeur en pixels de toutes les colonnes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

## <a name="clistboxsetcursel"></a><a name="setcursel"></a>CListBox::SetCurSel

Sélectionne une chaîne et la défile en vue, si nécessaire.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Paramètres

*nSelect*<br/>
Spécifie l’index zéro de la chaîne à sélectionner. Si *nSelect* est de -1, la boîte de liste est définie pour n’avoir aucune sélection.

### <a name="return-value"></a>Valeur de retour

LB_ERR en cas d’erreur.

### <a name="remarks"></a>Notes

Lorsque la nouvelle chaîne est sélectionnée, la boîte de liste supprime le point culminant de la chaîne précédemment sélectionnée.

Utilisez cette fonction de membre uniquement avec des boîtes de liste de sélection unique.

Pour définir ou supprimer une sélection dans une boîte de liste de sélection multiple, utilisez [CListBox:SetSel](#setsel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

## <a name="clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent

Définit la largeur, en pixels, par laquelle une boîte de liste peut être défichée horizontalement.

```cpp
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Paramètres

*cxExtent*<br/>
Spécifie le nombre de pixels par lesquels la boîte de liste peut être défichée horizontalement.

### <a name="remarks"></a>Notes

Si la taille de la boîte de liste est plus petite que cette valeur, la barre de défilement horizontal fera défiler horizontalement les éléments dans la boîte de liste. Si la boîte de liste est aussi grande ou plus grande que cette valeur, la barre de défilement horizontal est cachée.

Pour répondre à `SetHorizontalExtent`un appel à , la boîte de liste doit avoir été définie avec le [style WS_HSCROLL.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

Cette fonction de membre n’est pas utile pour les boîtes de liste multicolumn. Pour les boîtes de liste `SetColumnWidth` multicolumn, appelez la fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

## <a name="clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox::SetItemData

Définit une valeur associée à l’élément spécifié dans une boîte de liste.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’indice zéro de l’élément.

*dwItemData*<br/>
Spécifie la valeur à associer à l’article.

### <a name="return-value"></a>Valeur de retour

LB_ERR en cas d’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

## <a name="clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::SetItemDataPtr

Définit la valeur 32 bits associée à l’élément spécifié dans une boîte de liste pour être le pointeur spécifié **(vide** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’indice zéro de l’élément.

*Pdata*<br/>
Spécifie le pointeur à associer à l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR en cas d’erreur.

### <a name="remarks"></a>Notes

Ce pointeur reste valable pour la durée de vie de la boîte de liste, même si la position relative de l’élément dans la boîte de liste peut changer au fur et à mesure que les éléments sont ajoutés ou supprimés. Par conséquent, l’index de l’élément dans la boîte peut changer, mais le pointeur reste fiable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

## <a name="clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox::SetItemHeight

Définit la hauteur des éléments dans une boîte de liste.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de l’élément dans la boîte de liste. Ce paramètre n’est utilisé que si la boîte de liste a le style LBS_OWNERDRAWVARIABLE; autrement, il devrait être réglé à 0.

*cyItemHeight*<br/>
Spécifie la hauteur, en pixels, de l’élément.

### <a name="return-value"></a>Valeur de retour

LB_ERR si l’indice ou la hauteur est invalide.

### <a name="remarks"></a>Notes

Si la boîte de liste a le style [LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) cette fonction définit la hauteur de l’élément spécifié par *nIndex*. Sinon, cette fonction définit la hauteur de tous les éléments dans la boîte de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

## <a name="clistboxsetlocale"></a><a name="setlocale"></a>CListBox::SetLocale

Définit l’identifiant local pour cette boîte de liste.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Paramètres

*nNewLocale (en)*<br/>
La nouvelle valeur d’identifiant local (LCID) à définir pour la boîte de liste.

### <a name="return-value"></a>Valeur de retour

La valeur précédente de l’identifiant local (LCID) pour cette boîte de liste.

### <a name="remarks"></a>Notes

Si `SetLocale` ce n’est pas appelé, le lieu par défaut est obtenu à partir du système. Ce local par défaut du système peut être modifié en utilisant l’application Régionale (ou Internationale) de Control Panel.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

## <a name="clistboxsetsel"></a><a name="setsel"></a>CListBox::SetSel

Sélectionne une chaîne dans une boîte de liste de sélection multiple.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index zéro de la chaîne à définir. Si -1, la sélection est ajoutée ou supprimée de toutes les cordes, selon la valeur de *bSelect*.

*bSelect (en)*<br/>
Précise comment définir la sélection. Si *bSelect* est VRAI, la chaîne est sélectionnée et mise en surbrillance; si FALSE, le point culminant est supprimé et la chaîne n’est plus sélectionnée. La chaîne spécifiée est sélectionnée et mise en surbrillance par défaut.

### <a name="return-value"></a>Valeur de retour

LB_ERR en cas d’erreur.

### <a name="remarks"></a>Notes

Utilisez cette fonction de membre uniquement avec des cases de liste de sélection multiple.

Pour sélectionner un élément dans une boîte de liste de sélection unique, utilisez [CListBox:SetCurSel](#setcursel).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

## <a name="clistboxsettabstops"></a><a name="settabstops"></a>CListBox::SetTabStops

Définit les positions d’onglet-arrêt dans une boîte de liste.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Paramètres

*cxEachStop*<br/>
Les arrêts d’onglet sont réglés à toutes les unités de dialogue *cxEachStop.* Voir *rgTabStops* pour une description d’une unité de dialogue.

*nTabStops (en)*<br/>
Spécifie le nombre d’arrêts d’onglets à avoir dans la boîte de liste.

*rgTabStops*<br/>
Indique le premier membre d’un tableau d’intégrants contenant les positions d’arrêt d’onglet dans les unités de dialogue. Une unité de dialogue est une distance horizontale ou verticale. Une unité de dialogue horizontale est égale à un quart de l’unité actuelle de largeur de base de dialogue, et une unité verticale de dialogue est égale à un huitième de l’unité actuelle de hauteur de base de dialogue. Les unités de dialogue sont calculées en fonction de la hauteur et de la largeur de la police système actuelle. La `GetDialogBaseUnits` fonction Windows renvoie les unités de base de dialogue actuelles en pixels. Les arrêts d’onglet doivent être triés dans l’ordre croissant; les onglets arrière ne sont pas autorisés.

### <a name="return-value"></a>Valeur de retour

Nonzero si tous les onglets ont été fixés; sinon 0.

### <a name="remarks"></a>Notes

Pour définir des arrêts d’onglet à la taille par défaut de 2 unités de dialogue, appelez la version sans paramètres de cette fonction de membre. Pour définir l’onglet s’arrête à une taille autre que 2, appelez la version avec *l’argument cxEachStop.*

Pour définir des arrêts d’onglet à un tableau de tailles, utilisez la version avec les arguments *rgTabStops* et *nTabStops.* Un arrêt d’onglet sera réglé pour chaque valeur dans *rgTabStops*, jusqu’au nombre spécifié par *nTabStops*.

Pour répondre à un `SetTabStops` appel à la fonction membre, la boîte de liste doit avoir été créée avec le [style LBS_USETABSTOPS.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

## <a name="clistboxsettopindex"></a><a name="settopindex"></a>CListBox::SetTopIndex

S’assure qu’un élément de liste particulier est visible.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de l’élément de la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Zéro en cas de succès, ou LB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Le système fait défiler la case de liste jusqu’à ce que l’élément spécifié par *nIndex* s’affiche en haut de la case de liste ou que la plage de défilement maximum ait été atteinte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

## <a name="clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::VKeyToItem

Appelé par le cadre lorsque la fenêtre parente de la boîte de liste reçoit un message WM_VKEYTOITEM de la boîte de liste.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Paramètres

*nKey (en)*<br/>
Le code clé virtuel de la clé que l’utilisateur a pressé. Pour une liste de codes clés virtuels standard, voir Winuser.h

*nIndex*<br/>
La position actuelle de la liste-boîte caret.

### <a name="return-value"></a>Valeur de retour

Retours - 2 pour aucune autre action, - 1 pour l’action par défaut, ou un numéro non natifgatif pour spécifier un index d’un élément de boîte de liste sur lequel effectuer l’action par défaut pour le coup de clé.

### <a name="remarks"></a>Notes

Le message WM_VKEYTOITEM est envoyé par la case de liste lorsqu’il reçoit un message WM_KEYDOWN, mais seulement si la case rencontre les deux suivantes :

- A l’ensemble de style [LBS_WANTKEYBOARDINPUT.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

- A au moins un élément.

Vous ne devriez jamais appeler cette fonction vous-même. Remplacez cette fonction pour fournir votre propre manipulation personnalisée des messages clavier.

Vous devez retourner une valeur pour dire au cadre quelle action votre remplacement a effectué. Une valeur de retour de - 2 indique que l’application a traité tous les aspects de la sélection de l’élément et ne nécessite aucune autre action par la boîte de liste. Avant de revenir - 2, vous pouvez définir la sélection ou déplacer le caret ou les deux. Pour définir la sélection, utilisez [SetCurSel](#setcursel) ou [SetSel](#setsel). Pour déplacer le caret, utilisez [SetCaretIndex](#setcaretindex).

Une valeur de retour de - 1 indique que la boîte de liste doit effectuer l’action par défaut en réponse à la frappe. La mise en œuvre par défaut revient - 1.

Une valeur de retour de 0 ou plus spécifie l’index d’un élément dans la boîte de liste et indique que la boîte de liste doit effectuer l’action par défaut pour la frappe sur l’élément donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Classe CButton](../../mfc/reference/cbutton-class.md)<br/>
[Classe CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[Classe CStatic](../../mfc/reference/cstatic-class.md)
