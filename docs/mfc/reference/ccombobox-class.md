---
title: Classe CComboBox
ms.date: 11/04/2016
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
ms.openlocfilehash: dc803fb4ce137b256f4197afaec7bc3327e1e85a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754831"
---
# <a name="ccombobox-class"></a>Classe CComboBox

Fournit les fonctionnalités d'une zone de liste modifiable Windows.

## <a name="syntax"></a>Syntaxe

```
class CComboBox : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComboBox::CComboBox](#ccombobox)|Construit un objet `CComboBox`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|Ajoute une chaîne à la fin de la liste dans la boîte de liste d’une boîte combo, ou à la position triée pour les boîtes de liste avec le style CBS_SORT.|
|[CComboBox::Clair](#clear)|Supprime (efface) la sélection actuelle, le cas échéant, dans le contrôle de modification.|
|[CComboBox::CompareItem](#compareitem)|Appelé par le cadre pour déterminer la position relative d’un nouvel élément de liste dans une boîte de combo triée tirée par le propriétaire.|
|[CComboBox::Copie](#copy)|Copie la sélection actuelle, le cas échéant, sur le Clipboard en format CF_TEXT.|
|[CComboBox::Créer](#create)|Crée la boîte combo et `CComboBox` la fixe à l’objet.|
|[CComboBox::Cut](#cut)|Supprime (coupes) la sélection actuelle, le cas échéant, dans le contrôle de modification et copie le texte supprimé sur le Clipboard dans CF_TEXT format.|
|[CComboBox::DeleteItem](#deleteitem)|Appelé par le cadre quand un élément de liste est supprimé d’une boîte combo tirée par le propriétaire.|
|[CComboBox::DeleteString](#deletestring)|Supprime une chaîne de la boîte de liste d’une boîte combo.|
|[CComboBox::Dir](#dir)|Ajoute une liste de noms de fichiers à la boîte de liste d’une boîte combo.|
|[CComboBox::DrawItem](#drawitem)|Appelé par le cadre quand un aspect visuel d’une boîte combo tirée par le propriétaire change.|
|[CComboBox::FindString](#findstring)|Trouve la première chaîne qui contient le préfixe spécifié dans la boîte de liste d’une boîte combo.|
|[CComboBox::FindStringExact](#findstringexact)|Trouve la première chaîne de boîte de liste (dans une boîte de combo) qui correspond à la chaîne spécifiée.|
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Récupère des informations `CComboBox` sur l’objet.|
|[CComboBox::GetCount](#getcount)|Récupère le nombre d’éléments dans la boîte de liste d’une boîte combo.|
|[CComboBox::GetCueBanner](#getcuebanner)|Obtient le texte de repère qui est affiché pour un contrôle de boîte combo.|
|[CComboBox::GetCurSel](#getcursel)|Récupère l’index de l’élément actuellement sélectionné, le cas échéant, dans la boîte de liste d’une boîte combo.|
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Récupère les coordonnées de l’écran de la boîte de liste visible (larguée vers le bas) d’une boîte combo drop-down.|
|[CComboBox::GetDroppedState](#getdroppedstate)|Détermine si la boîte de liste d’une boîte combo drop-down est visible (tombé vers le bas).|
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Récupère la largeur minimale autorisée pour la partie de liste-boîte d’abandon d’une boîte de combo.|
|[CComboBox::GetEditSel](#geteditsel)|Obtient les positions de caractère de départ et de fin de la sélection actuelle dans le contrôle de modification d’une boîte de combo.|
|[CComboBox::GetExtendedUI](#getextendedui)|Détermine si une boîte combo a l’interface utilisateur par défaut ou l’interface utilisateur étendue.|
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Retourne la largeur en pixels que la partie liste-boîte de la boîte combo peut être défilé horizontalement.|
|[CComboBox::GetItemData](#getitemdata)|Récupère la valeur 32 bits fournie par l’application associée à l’élément combo-box spécifié.|
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Récupère le pointeur 32 bits fourni par l’application qui est associé à l’élément combo-box spécifié.|
|[CComboBox::GetItemHeight](#getitemheight)|Récupère la hauteur des éléments de liste dans une boîte combo.|
|[CComboBox::GetLBText](#getlbtext)|Obtient une chaîne de la boîte de liste d’une boîte de combo.|
|[CComboBox::GetLBTextLen](#getlbtextlen)|Obtient la longueur d’une chaîne dans la boîte de liste d’une boîte de combo.|
|[CComboBox::GetLocale](#getlocale)|Récupère l’identifiant local pour une boîte combo.|
|[CComboBox::GetMinVisible](#getminvisible)|Obtient le nombre minimum d’éléments visibles dans la liste d’abandon de la boîte combo actuelle.|
|[CComboBox::GetTopIndex](#gettopindex)|Retourne l’index du premier élément visible dans la partie liste-boîte de la boîte combo.|
|[CComboBox::InitStorage](#initstorage)|Prélocalise les blocs de mémoire pour les éléments et les chaînes dans la partie liste-boîte de la boîte combo.|
|[CComboBox::InsertString](#insertstring)|Insère une chaîne dans la zone de liste d’une zone de liste modifiable.|
|[CComboBox::LimitText](#limittext)|Limite la longueur du texte que l’utilisateur peut entrer dans le contrôle de modification d’une boîte combo.|
|[CComboBox::MeasureItem](#measureitem)|Appelé par le cadre pour déterminer les dimensions de la boîte combo lors de la création d’une boîte combo tirée par le propriétaire.|
|[CComboBox::Paste](#paste)|Insère les données du Clipboard dans le contrôle de modification à la position de curseur actuel. Les données ne sont insérées que si le Clipboard contient des données en format CF_TEXT.|
|[CComboBox::ResetContent](#resetcontent)|Supprime tous les éléments de la boîte de liste et modifie le contrôle d’une boîte combo.|
|[CComboBox::SelectString](#selectstring)|Recherche une chaîne dans la boîte de liste d’une boîte combo et, si la chaîne est trouvée, sélectionne la chaîne dans la boîte de liste et copie la chaîne au contrôle de modification.|
|[CComboBox::SetCueBanner](#setcuebanner)|Définit le texte de repère qui s’affiche pour un contrôle de boîte combo.|
|[CComboBox::SetCurSel](#setcursel)|Sélectionne une chaîne dans la boîte de liste d’une boîte combo.|
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Définit la largeur minimale autorisée pour la partie de liste-boîte d’abandon d’une boîte de combo.|
|[CComboBox::SetEditSel](#seteditsel)|Sélectionne des caractères dans le contrôle de modification d’une boîte combo.|
|[CComboBox::SetExtendedUI](#setextendedui)|Sélectionne soit l’interface utilisateur par défaut, soit l’interface utilisateur étendue pour une boîte combo dotée du CBS_DROPDOWN ou CBS_DROPDOWNLIST style.|
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Définit la largeur en pixels que la partie liste-boîte de la boîte combo peut être défilé horizontalement.|
|[CComboBox::SetItemData](#setitemdata)|Définit la valeur 32 bits associée à l’élément spécifié dans une boîte combo.|
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Définit le pointeur 32 bits associé à l’élément spécifié dans une boîte combo.|
|[CComboBox::SetItemHeight](#setitemheight)|Définit la hauteur des éléments de liste dans une boîte combo ou la hauteur de la partie de contrôle d’édition (ou de texte statique) d’une boîte combo.|
|[CComboBox::SetLocale](#setlocale)|Définit l’identifiant local pour une boîte combo.|
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Définit le nombre minimum d’éléments visibles dans la liste d’abandon de la boîte combo actuelle.|
|[CComboBox::SetTopIndex](#settopindex)|Indique la partie liste-boîte de la boîte de combo pour afficher l’élément avec l’index spécifié en haut.|
|[CComboBox::ShowDropDown](#showdropdown)|Affiche ou cache la boîte de liste d’une boîte combo qui a le style CBS_DROPDOWN ou CBS_DROPDOWNLIST.|

## <a name="remarks"></a>Notes

Une boîte combo se compose d’une boîte de liste combinée à un contrôle statique ou à un contrôle de modification. La partie de la boîte de liste du contrôle peut être affichée en tout temps ou ne peut tomber que lorsque l’utilisateur sélectionne la flèche d’abandon à côté du contrôle.

L’élément actuellement sélectionné (le cas échéant) dans la boîte de liste est affiché dans le contrôle statique ou de modification. En outre, si la boîte de combo a le style de liste de drop-down, l’utilisateur peut taper le caractère initial de l’un des éléments de la liste, et la boîte de liste, si visible, mettra en évidence l’élément suivant avec ce caractère initial.

Le tableau suivant compare les trois [styles](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)combo-box .

|Style|Quand la boîte de liste est-elle visible|Contrôle statique ou modifié|
|-----------|-------------------------------|-----------------------------|
|Simple|Toujours|Modifier|
|Drop-down|Lorsqu’il est déposé|Modifier|
|Liste déroulante|Lorsqu’il est déposé|statique|

Vous pouvez `CComboBox` créer un objet à partir d’un modèle de dialogue ou directement dans votre code. Dans les deux cas, `CComboBox` appelez d’abord le constructeur pour construire l’objet; `CComboBox` ensuite, appelez la fonction membre [Create](#create) pour `CComboBox` créer le contrôle et l’attacher à l’objet.

Si vous souhaitez traiter les messages de notification Windows envoyés par `CDialog`une boîte combo à son parent (généralement une classe dérivée), ajoutez une entrée de carte de message et une fonction de membre de gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de carte de message prend la forme suivante :

**ON\_**_Notification_ **(** _id_, _memberFxn_ **)**

où `id` spécifie l’ID de fenêtre enfant `memberFxn` du contrôle de la boîte de combo envoyant la notification et est le nom de la fonction de membre parent que vous avez écrit pour gérer la notification.

Le prototype de fonction du parent est le suivant :

afx_msg **( );** **afx_msg** `void` `memberFxn`

L’ordre dans lequel certaines notifications seront envoyées ne peut pas être prédit. En particulier, une notification CBN_SELCHANGE peut se produire avant ou après une notification CBN_CLOSEUP.

Les entrées potentielles de carte de message sont les suivantes :

- ON_CBN_CLOSEUP (Windows 3.1 et plus tard.) La boîte de liste d’une boîte combo est fermée. Ce message de notification n’est pas envoyé pour une boîte combo qui a le [style CBS_SIMPLE.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

- ON_CBN_DBLCLK L’utilisateur double-clics une chaîne dans la boîte de liste d’une boîte combo. Ce message de notification n’est envoyé que pour une boîte combo avec le style CBS_SIMPLE. Pour une boîte combo avec le [style CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) un double-clic ne peut pas se produire parce qu’un seul clic cache la case de liste.

- ON_CBN_DROPDOWN La boîte de liste d’une boîte combo est sur le point de tomber vers le bas (être rendu visible). Ce message de notification ne peut se produire que pour une boîte combo avec le style CBS_DROPDOWN ou CBS_DROPDOWNLIST.

- ON_CBN_EDITCHANGE L’utilisateur a pris une mesure qui peut avoir modifié le texte dans la partie de modification-contrôle d’une boîte combo. Contrairement au message CBN_EDITUPDATE, ce message est envoyé après windows met à jour l’écran. Il n’est pas envoyé si la boîte combo a le style CBS_DROPDOWNLIST.

- ON_CBN_EDITUPDATE La partie de contrôle d’édition d’une boîte combo est sur le point d’afficher du texte modifié. Ce message de notification est envoyé après que le contrôle a formaté le texte, mais avant qu’il n’affiche le texte. Il n’est pas envoyé si la boîte combo a le style CBS_DROPDOWNLIST.

- ON_CBN_ERRSPACE La boîte combo ne peut pas allouer assez de mémoire pour répondre à une demande spécifique.

- ON_CBN_SELENDCANCEL (Windows 3.1 et plus tard.) Indique que la sélection de l’utilisateur doit être annulée. L’utilisateur clique sur un élément, puis clique sur une autre fenêtre ou un contrôle pour masquer la boîte de liste d’une boîte combo. Ce message de notification est envoyé avant le message de notification CBN_CLOSEUP pour indiquer que la sélection de l’utilisateur doit être ignorée. Le message de notification CBN_SELENDCANCEL ou CBN_SELENDOK est envoyé même si le message de notification CBN_CLOSEUP n’est pas envoyé (comme dans le cas d’une boîte combo avec le style CBS_SIMPLE).

- ON_CBN_SELENDOK L’utilisateur sélectionne un élément, puis appuie sur la touche ENTER ou clique sur la clé DOWN ARROW pour masquer la boîte de liste d’une boîte combo. Ce message de notification est envoyé avant le CBN_CLOSEUP message pour indiquer que la sélection de l’utilisateur doit être considérée comme valide. Le message de notification CBN_SELENDCANCEL ou CBN_SELENDOK est envoyé même si le message de notification CBN_CLOSEUP n’est pas envoyé (comme dans le cas d’une boîte combo avec le style CBS_SIMPLE).

- ON_CBN_KILLFOCUS La boîte combo perd la mise au point d’entrée.

- ON_CBN_SELCHANGE La sélection dans la boîte de liste d’une boîte combo est sur le point d’être changée en raison de l’utilisateur soit en cliquant dans la boîte de liste ou en changeant la sélection en utilisant les touches de flèche. Lors du traitement de ce message, le texte dans le `GetLBText` contrôle de modification de la boîte combo ne peut être récupéré via ou une autre fonction similaire. `GetWindowText`ne peut pas être utilisé.

- ON_CBN_SETFOCUS La boîte combo reçoit la mise au point d’entrée.

Si vous `CComboBox` créez un objet dans une boîte de `CComboBox` dialogue (via une ressource de dialogue), l’objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous intégrez un `CComboBox` objet dans un autre objet de fenêtre, vous n’avez pas besoin de le détruire. Si vous `CComboBox` créez l’objet sur la pile, il est détruit automatiquement. Si vous `CComboBox` créez l’objet sur le tas en utilisant la **nouvelle** fonction, vous devez appeler **supprimer** sur l’objet pour le détruire lorsque la boîte combo Windows est détruite.

**Note** Si vous voulez gérer WM_KEYDOWN et WM_CHAR messages, vous devez sousclasser les commandes de la boîte `CEdit` de `CListBox`combo et la liste des boîtes, tirer des classes de et, et ajouter des gestionnaires pour ces messages aux classes dérivées. Pour plus d’informations, voir [CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a>CComboBox::AddString

Ajoute une chaîne à la boîte de liste d’une boîte combo.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*lpszString (lpszString)*<br/>
Points à la chaîne non terminée qui doit être ajouté.

### <a name="return-value"></a>Valeur de retour

Si la valeur de rendement est supérieure ou égale à 0, c’est l’indice à base nulle à la chaîne dans la boîte de liste. La valeur de retour est CB_ERR si une erreur se produit; la valeur de retour est CB_ERRSPACE si l’espace insuffisant est disponible pour stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Si la boîte de liste n’a pas été créée avec le style [CBS_SORT,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) la chaîne est ajoutée à la fin de la liste. Sinon, la chaîne est insérée dans la liste, et la liste est triée.

> [!NOTE]
> Cette fonction n’est `ComboBoxEx` pas prise en charge par le contrôle Windows. Pour plus d’informations sur ce contrôle, voir [les contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

Pour insérer une chaîne dans un emplacement spécifique dans la liste, utilisez la fonction membre [InsertString.](#insertstring)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a>CComboBox::CComboBox

Construit un objet `CComboBox`.

```
CComboBox();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a>CComboBox::Clair

Supprime (efface) la sélection actuelle, le cas échéant, dans le contrôle de modification de la boîte combo.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

Pour supprimer la sélection actuelle et placer le contenu supprimé sur le Clipboard, utilisez la fonction [membre Cut.](#cut)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a>CComboBox::CompareItem

Appelé par le cadre pour déterminer la position relative d’un nouvel élément dans la partie liste-boîte d’une boîte de combo de propriétaire trié.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpCompareItemStruct*<br/>
Un long pointeur vers une structure [COMPAREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-compareitemstruct)

### <a name="return-value"></a>Valeur de retour

Indique la position relative des deux `COMPAREITEMSTRUCT` éléments décrits dans la structure. Il peut s’agir de l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|- 1|L’article 1 trie avant l’article 2.|
|0|L’article 1 et l’article 2 trient de la même façon.|
|1|L’article 1 trie après l’article 2.|

Voir [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) pour `COMPAREITEMSTRUCT`une description de .

### <a name="remarks"></a>Notes

Par défaut, cette fonction de membre ne fait rien. Si vous créez une boîte combo de propriétaire-tirage avec le style LBS_SORT, vous devez remplacer cette fonction de membre pour aider le cadre dans le tri des nouveaux éléments ajoutés à la boîte de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a>CComboBox::Copie

Copie la sélection actuelle, le cas échéant, dans le contrôle de modification de la boîte combo sur le Clipboard en format CF_TEXT.

```cpp
void Copy();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a>CComboBox::Créer

Crée la boîte combo et `CComboBox` la fixe à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style de la boîte combo. Appliquez n’importe quelle combinaison de [styles de combo-box](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) à la boîte.

*Rect*<br/>
Points à la position et la taille de la boîte combo. Peut être une structure `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) ou un objet.

*pParentWnd*<br/>
Spécifie la fenêtre parente `CDialog`de la boîte combo (généralement un ). Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de la boîte combo.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CComboBox` objet en deux étapes. Tout d’abord, appelez `Create`le constructeur, puis appelez , ce `CComboBox` qui crée la boîte combo Windows et le fixe à l’objet.

Lors `Create` de l’exécution, Windows envoie le [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), et [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) messages à la boîte combo.

Ces messages sont traités par défaut par le [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize) `CWnd` , et les fonctions des membres [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) dans la classe de base. Pour étendre la manipulation par défaut `CComboBox`du message, extraire une classe, ajouter une carte de message à la nouvelle classe et remplacer les fonctions précédentes des membres de gestionnaire de message. `OnCreate`Remplacer, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.

Appliquez les styles de [fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle de combo-box. :

- WS_CHILD toujours

- WS_VISIBLE Habituellement

- WS_DISABLED Rarement

- WS_VSCROLL Pour ajouter le défilement vertical pour la boîte de liste dans la boîte de combo

- WS_HSCROLL Pour ajouter le défilement horizontal pour la boîte de liste dans la boîte de combo

- WS_GROUP Pour les contrôles de groupe

- WS_TABSTOP Inclure la boîte de combo dans l’ordre de tabbing

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a>CComboBox::Cut

Supprime (coupes) la sélection actuelle, le cas échéant, dans le contrôle de modification de la boîte combo et copie le texte supprimé sur le Clipboard dans CF_TEXT format.

```cpp
void Cut();
```

### <a name="remarks"></a>Notes

Pour supprimer la sélection actuelle sans placer le texte supprimé sur le Clipboard, appelez la fonction [membre Clear.](#clear)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a>CComboBox::DeleteItem

Appelé par le cadre lorsque l’utilisateur supprime `CComboBox` un élément d’un objet de dessin du propriétaire ou détruit la boîte combo.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDeleteItemStruct*<br/>
Un long pointeur vers une structure Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) qui contient des informations sur l’élément supprimé. Voir [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) pour une description de cette structure.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacer cette fonction pour redessiner la boîte combo au besoin.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a>CComboBox::DeleteString

Supprime l’élément en position *nIndex* de la boîte combo.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index à la chaîne qui doit être supprimée.

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est supérieure ou égale à 0, alors c’est un compte des chaînes restantes dans la liste. La valeur de rendement est CB_ERR si *nIndex* spécifie un indice supérieur au nombre d’éléments de la liste.

### <a name="remarks"></a>Notes

Tous les éléments suivant *nIndex* se déplacent maintenant vers le bas d’une position. Par exemple, si une boîte combo contient deux éléments, la suppression du premier élément fera en sorte que l’élément restant sera maintenant en première position. *nIndex*0 pour l’article en première position.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a>CComboBox::Dir

Ajoute une liste de noms de fichiers ou de lecteurs à la boîte de liste d’une boîte combo.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Paramètres

*Attr*<br/>
Peut être n’importe quelle combinaison des valeurs **enum** décrites dans [CFile : : GetStatus](../../mfc/reference/cfile-class.md#getstatus) ou n’importe quelle combinaison des valeurs suivantes :

- DDL_READWRITE Fichier peut être lu ou écrit à.

- DDL_READONLY Fichier peut être lu à partir, mais pas écrit à.

- DDL_HIDDEN File est caché et n’apparaît pas dans une liste d’annuaires.

- DDL_SYSTEM File est un fichier système.

- DDL_DIRECTORY Le nom spécifié par *lpszWildCard* spécifie un répertoire.

- DDL_ARCHIVE File a été archivé.

- DDL_DRIVES Inclure tous les lecteurs qui correspondent au nom spécifié par *lpszWildCard*.

- DDL_EXCLUSIVE drapeau exclusif. Si le drapeau exclusif est défini, seuls les fichiers du type spécifié sont répertoriés. Dans le cas contraire, les fichiers du type spécifié sont répertoriés en plus des fichiers « normaux ».

*lpszWildCard (en)*<br/>
Indique une chaîne de spécification de fichier. La chaîne peut contenir des wildcards\*(par exemple, . . ).

### <a name="return-value"></a>Valeur de retour

Si la valeur de rendement est supérieure ou égale à 0, c’est l’indice zéro du dernier nom de fichier ajouté à la liste. La valeur de retour est CB_ERR si une erreur se produit; la valeur de retour est CB_ERRSPACE si un espace insuffisant est disponible pour stocker les nouvelles chaînes.

### <a name="remarks"></a>Notes

Cette fonction n’est `ComboBoxEx` pas prise en charge par le contrôle Windows. Pour plus d’informations sur ce contrôle, voir [les contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a>CComboBox::DrawItem

Appelé par le cadre quand un aspect visuel d’une boîte combo propriétaire-tirage change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur vers une structure [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` membre `DRAWITEMSTRUCT` de la structure définit l’action de dessin qui doit être effectuée. Voir [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) pour une description de cette structure.

Par défaut, cette fonction de membre ne fait rien. Remplacer cette fonction de membre pour implémenter le dessin d’un objet de dessin du `CComboBox` propriétaire. Avant la fin de cette fonction de membre, l’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a>CComboBox::FindString

Trouve, mais ne sélectionne pas, la première chaîne qui contient le préfixe spécifié dans la boîte de liste d’une boîte combo.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Paramètres

*nStartAprès*<br/>
Contient l’index zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la boîte de liste, elle se poursuit du haut de la boîte de liste jusqu’à l’élément spécifié par *nStartAfter*. Si -1, la boîte de liste entière est recherchée depuis le début.

*lpszString (lpszString)*<br/>
Indique la chaîne non terminée qui contient le préfixe à rechercher. La recherche est indépendante de cas, de sorte que cette chaîne peut contenir n’importe quelle combinaison de majuscules et de lettres minuscules.

### <a name="return-value"></a>Valeur de retour

Si la valeur de rendement est supérieure ou égale à 0, c’est l’indice zéro de l’élément correspondant. Il est CB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Cette fonction n’est `ComboBoxEx` pas prise en charge par le contrôle Windows. Pour plus d’informations sur ce contrôle, voir [les contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a>CComboBox::FindStringExact

Appelez `FindStringExact` la fonction membre pour trouver la première chaîne de boîte de liste (dans une boîte combo) qui correspond à la chaîne spécifiée dans *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Paramètres

*nIndexStart*<br/>
Spécifie l’index zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la boîte de liste, elle se poursuit du haut de la boîte de liste jusqu’à l’élément spécifié par *nIndexStart*. Si *nIndexStart* est de -1, la boîte de liste entière est recherchée depuis le début.

*lpszFind*<br/>
Indique la corde non terminée à rechercher. Cette chaîne peut contenir un nom de fichier complet, y compris l’extension. La recherche n’est pas sensible aux cas, de sorte que cette chaîne peut contenir n’importe quelle combinaison de majuscules et de lettres minuscules.

### <a name="return-value"></a>Valeur de retour

L’index à base nulle de l’élément correspondant, ou CB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Si la boîte combo a été créé avec un style propriétaire-tirage, mais sans le style [CBS_HASSTRINGS,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) `FindStringExact` tente de faire correspondre la valeur double mot contre la valeur de *lpszFind*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo

Récupère les informations `CComboBox` pour l’objet.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Paramètres

*pcbi pcbi*<br/>
Un pointeur à la structure [COMBOBOXINFO.](/windows/win32/api/winuser/ns-winuser-comboboxinfo)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du [message CB_GETCOMBOBOXINFO,](/windows/win32/Controls/cb-getcomboboxinfo) tel que décrit dans le SDK Windows.

## <a name="ccomboboxgetcount"></a><a name="getcount"></a>CComboBox::GetCount

Appelez cette fonction de membre pour récupérer le numéro d’éléments dans la partie liste-boîte d’une boîte de combo.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments. Le nombre retourné est supérieur à la valeur indicative du dernier élément (l’indice est basé à zéro). Il est CB_ERR si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a>CComboBox::GetCueBanner

Obtient le texte de repère qui est affiché pour un contrôle de boîte combo.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszText*|[out] Pointeur vers un tampon qui reçoit le texte de la bannière de repère.|
|*cchText*|[dans] Taille du tampon que le paramètre *lpszText* indique.|

### <a name="return-value"></a>Valeur de retour

Dans la première surcharge, un objet [CString](../../atl-mfc-shared/using-cstring.md) qui contient le texte de la bannière de repère s’il existe; autrement, `CString` un objet qui a zéro longueur.

-ou-

Dans la deuxième surcharge, VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Le texte De cue est une invite qui s’affiche dans la zone d’entrée du contrôle de la boîte combo. Le texte de repère est affiché jusqu’à ce que l’utilisateur fournisse l’entrée.

Cette méthode envoie le [message CB_GETCUEBANNER,](/windows/win32/Controls/cb-getcuebanner) qui est décrit dans le SDK Windows.

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a>CComboBox::GetCurSel

Appelez cette fonction de membre pour déterminer quel élément de la boîte combo est sélectionné.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

L’index à base zéro de l’élément actuellement sélectionné dans la boîte de liste d’une boîte combo, ou CB_ERR si aucun élément n’est sélectionné.

### <a name="remarks"></a>Notes

`GetCurSel`retourne un index dans la liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect

Appelez `GetDroppedControlRect` la fonction du membre pour récupérer les coordonnées de l’écran de la boîte de liste visible (larguée) d’une boîte combo d’abandon.

```cpp
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Paramètres

*lprect*<br/>
Points à la [structure RECT](/windows/win32/api/windef/ns-windef-rect) qui doit recevoir les coordonnées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a>CComboBox::GetDroppedState

Appelez `GetDroppedState` la fonction membre pour déterminer si la boîte de liste d’une boîte combo drop-down est visible (tombé vers le bas).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la boîte de liste est visible; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth

Appelez cette fonction pour récupérer la largeur minimale autorisée, en pixels, de la boîte de liste d’une boîte combo.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, la largeur minimale autorisée, en pixels; autrement, CB_ERR.

### <a name="remarks"></a>Notes

Cette fonction ne s’applique qu’aux boîtes combo avec le [style CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

Par défaut, la largeur minimale autorisée de la case de liste de décrochage est de 0. La largeur minimale autorisée peut être définie en appelant [SetDroppedWidth](#setdroppedwidth). Lorsque la partie liste-boîte de la boîte combo est affichée, sa largeur est la plus grande de la largeur minimale autorisée ou la largeur de la boîte combo.

### <a name="example"></a>Exemple

  Voir l’exemple pour [SetDroppedWidth](#setdroppedwidth).

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a>CComboBox::GetEditSel

Obtient les positions de caractère de départ et de fin de la sélection actuelle dans le contrôle de modification d’une boîte de combo.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur 32 bits qui contient la position de départ dans le mot de faible ordre et la position du premier personnage non sélectionné après la fin de la sélection dans le mot de haute commande. Si cette fonction est utilisée sur une boîte combo sans contrôle de modification, CB_ERR est retournée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a>CComboBox::GetExtendedUI

Appelez `GetExtendedUI` la fonction membre pour déterminer si une boîte combo a l’interface utilisateur par défaut ou l’interface utilisateur étendue.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la boîte combo a l’interface utilisateur étendue; sinon 0.

### <a name="remarks"></a>Notes

L’interface utilisateur étendue peut être identifiée de la manière suivante :

- En cliquant sur le contrôle statique affiche la boîte de liste uniquement pour les boîtes combo avec le style [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

- Appuyer sur la clé DOWN ARROW affiche la boîte de liste (F4 est désactivé).

Le défilement dans le contrôle statique est désactivé lorsque la liste d’éléments n’est pas visible (les touches fléchées sont désactivées).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent

Récupère à partir de la boîte combo la largeur en pixels par lequel la partie liste-boîte de la boîte combo peut être défilé horizontalement.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur défilement de la partie liste-boîte de la boîte combo, en pixels.

### <a name="remarks"></a>Notes

Ceci n’est applicable que si la partie liste-boîte de la boîte de combo a une barre de défilement horizontal.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a>CComboBox::GetItemData

Récupère la valeur 32 bits fournie par l’application associée à l’élément combo-box spécifié.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index zéro d’un élément dans la boîte de liste de la boîte de combo.

### <a name="return-value"></a>Valeur de retour

La valeur 32 bits associée à l’élément, ou CB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

La valeur 32 bits peut être définie avec le paramètre *dwItemData* d’un appel de fonction membre [SetItemData.](#setitemdata) Utilisez `GetItemDataPtr` la fonction membre si la valeur 32 bits à récupérer est un pointeur **(vide** <strong>\*</strong>).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a>CComboBox::GetItemDataPtr

Récupère la valeur 32 bits fournie par l’application associée à l’élément combo-box spécifié comme pointeur **(vide** <strong>\*</strong>).

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index zéro d’un élément dans la boîte de liste de la boîte de combo.

### <a name="return-value"></a>Valeur de retour

Récupère un pointeur, ou -1 si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a>CComboBox::GetItemHeight

Appelez `GetItemHeight` la fonction membre pour récupérer la hauteur des éléments de liste dans une boîte combo.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie le composant de la boîte combo dont la hauteur doit être récupérée. Si le paramètre *nIndex* est de -1, la hauteur de la partie de contrôle de modification (ou de texte statique) de la boîte combo est récupérée. Si la boîte combo a le style [CBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) *nIndex* spécifie l’index zéro de l’élément de liste dont la hauteur doit être récupérée. Dans le cas contraire, *nIndex* devrait être réglé à 0.

### <a name="return-value"></a>Valeur de retour

La hauteur, en pixels, de l’élément spécifié dans une boîte combo. La valeur de retour est CB_ERR si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a>CComboBox::GetLBText

Obtient une chaîne de la boîte de liste d’une boîte de combo.

```
int GetLBText(
    int nIndex,
    LPTSTR lpszText) const;

void GetLBText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index zéro de la chaîne de boîte de liste à copier.

*lpszText*<br/>
Points à un tampon qui est de recevoir la chaîne. Le tampon doit avoir suffisamment d’espace pour la chaîne et un caractère nul de fin.

*rString (en)*<br/>
Référence à un `CString`.

### <a name="return-value"></a>Valeur de retour

La longueur (dans les octets) de la chaîne, à l’exclusion du caractère nul de fin. Si *nIndex* ne spécifie pas un indice valide, la valeur de rendement est CB_ERR.

### <a name="remarks"></a>Notes

La deuxième forme de cette `CString` fonction membre remplit un objet avec le texte de l’élément.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a>CComboBox::GetLBTextLen

Obtient la longueur d’une chaîne dans la boîte de liste d’une boîte de combo.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index zéro de la chaîne de boîte de liste.

### <a name="return-value"></a>Valeur de retour

La longueur de la chaîne dans les octets, à l’exclusion du caractère nul de fin. Si *nIndex* ne spécifie pas un indice valide, la valeur de rendement est CB_ERR.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CComboBox:GetLBText](#getlbtext).

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a>CComboBox::GetLocale

Récupère le lieu utilisé par la boîte combo.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de l’identifiant local (LCID) pour les cordes de la boîte combo.

### <a name="remarks"></a>Notes

Le lieu est utilisé, par exemple, pour déterminer le tri d’ordre des cordes dans une boîte combo triée.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CComboBox:SetLocale](#setlocale).

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a>CComboBox::GetMinVisible

Obtient le nombre minimum d’éléments visibles dans la liste d’abandon du contrôle actuel de la boîte combo.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre minimum d’éléments visibles dans la liste d’abandon actuelle.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message CB_GETMINVISIBLE,](/windows/win32/Controls/cb-setminvisible) qui est décrit dans le SDK Windows.

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a>CComboBox::GetTopIndex

Récupère l’index zéro du premier élément visible dans la partie liste-boîte de la boîte de combo.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valeur de retour

L’index zéro de la première élément visible dans la partie liste-boîte de la boîte de combo en cas de succès, CB_ERR autrement.

### <a name="remarks"></a>Notes

Initialement, l’élément 0 est en haut de la case de liste, mais si la boîte de liste est défilé, un autre élément peut être en haut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a>CComboBox::InitStorage

Alloue la mémoire pour stocker les articles de la boîte de liste dans la partie liste-boîte de la boîte combo.

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

En cas de succès, le nombre maximum d’éléments que la partie liste-boîte de la boîte combo peut stocker avant qu’une réaffectation de mémoire soit nécessaire, sinon CB_ERRSPACE, ce qui signifie pas assez de mémoire est disponible.

### <a name="remarks"></a>Notes

Appelez cette fonction avant d’ajouter un grand nombre `CComboBox`d’éléments à la partie liste-boîte de la .

Windows 95/98 seulement: Le paramètre *wParam* est limité à des valeurs 16 bits. Cela signifie que les boîtes de liste ne peuvent pas contenir plus de 32 767 articles. Bien que le nombre d’éléments soit limité, la taille totale des éléments dans une boîte de liste n’est limitée que par la mémoire disponible.

Cette fonction permet d’accélérer l’initialisation des boîtes de liste qui ont un grand nombre d’éléments (plus de 100). Il préalloce la quantité spécifiée de mémoire de sorte que les fonctions [suivantes AddString](#addstring), [InsertString](#insertstring), et [Dir](#dir) prennent le temps le plus court possible. Vous pouvez utiliser des estimations pour les paramètres. Si vous surestimez, une certaine mémoire supplémentaire est allouée; si vous sous-estimez, l’allocation normale est utilisée pour les articles qui dépassent le montant préaffecté.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a>CComboBox::InsertString

Insère une chaîne dans la zone de liste d’une zone de liste modifiable.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index de base zéro de la position dans la zone de liste qui doit recevoir la chaîne. Si ce paramètre est de -1, la chaîne est ajoutée à la fin de la liste.

*lpszString (lpszString)*<br/>
Pointe vers la chaîne terminée par le caractère null qui doit être insérée.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la position à laquelle la chaîne a été insérée. La valeur de retour est CB_ERR si une erreur se produit. La valeur de retour est CB_ERRSPACE si l’espace disponible est insuffisant pour stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Contrairement à la fonction membre [AddString](#addstring) , la fonction membre `InsertString` n’entraîne pas le tri d’une liste associée au style [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

> [!NOTE]
> Cette fonction n’est `ComboBoxEx` pas prise en charge par le contrôle Windows. Pour plus d’informations sur ce contrôle, voir [les contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a>CComboBox::LimitText

Limite la longueur des octets du texte que l’utilisateur peut entrer dans le contrôle de modification d’une boîte combo.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Paramètres

*nMaxChars (en)*<br/>
Spécifie la longueur (dans les octets) du texte que l’utilisateur peut entrer. Si ce paramètre est de 0, la longueur du texte est réglée à 65 535 octets.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès. Si appelé pour une boîte combo avec le style [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou pour une boîte combo sans contrôle de modification, la valeur de retour est CB_ERR.

### <a name="remarks"></a>Notes

Si la boîte combo n’a pas le style [CBS_AUTOHSCROLL,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)la fixation de la limite de texte pour être plus grande que la taille du contrôle de modification n’aura aucun effet.

`LimitText`limite uniquement le texte que l’utilisateur peut entrer. Il n’a aucun effet sur un texte déjà dans le contrôle de modification lorsque le message est envoyé, ni n’affecte la longueur du texte copié sur le contrôle de modification quand une chaîne dans la boîte de liste est sélectionnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a>CComboBox::MeasureItem

Appelé par le cadre quand une boîte combo avec un style propriétaire-tirage est créé.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Un long pointeur vers une structure [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Notes

Par défaut, cette fonction de membre ne fait rien. Remplacez cette fonction de `MEASUREITEMSTRUCT` membre et remplissez la structure pour informer Windows des dimensions de la boîte de liste dans la boîte de combo. Si la boîte combo est créée avec le style [CBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) le cadre appelle cette fonction de membre pour chaque élément de la boîte de liste. Sinon, ce membre n’est appelé qu’une seule fois.

L’utilisation du style CBS_OWNERDRAWFIXED dans une boîte combo propriétaire-tirage créé avec `CWnd` la fonction membre [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) implique d’autres considérations de programmation. Voir la discussion dans [La Note Technique 14](../../mfc/tn014-custom-controls.md).

Voir [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pour une `MEASUREITEMSTRUCT` description de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a>CComboBox::Paste

Insère les données du Clipboard dans le contrôle de modification de la boîte combo à la position de curseur actuel.

```cpp
void Paste();
```

### <a name="remarks"></a>Notes

Les données ne sont insérées que si le Clipboard contient des données en format CF_TEXT.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a>CComboBox::ResetContent

Supprime tous les éléments de la boîte de liste et modifie le contrôle d’une boîte combo.

```cpp
void ResetContent();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a>CComboBox::SelectString

Recherche une chaîne dans la boîte de liste d’une boîte combo, et si la chaîne est trouvée, sélectionne la chaîne dans la boîte de liste et l’copie au contrôle de modification.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*nStartAprès*<br/>
Contient l’index zéro de l’élément avant le premier élément à rechercher. Lorsque la recherche atteint le bas de la boîte de liste, elle se poursuit du haut de la boîte de liste jusqu’à l’élément spécifié par *nStartAfter*. Si -1, la boîte de liste entière est recherchée depuis le début.

*lpszString (lpszString)*<br/>
Indique la chaîne non terminée qui contient le préfixe à rechercher. La recherche est indépendante de cas, de sorte que cette chaîne peut contenir n’importe quelle combinaison de majuscules et de lettres minuscules.

### <a name="return-value"></a>Valeur de retour

L’index à base nulle de l’élément sélectionné si la chaîne a été trouvée. Si la recherche a échoué, la valeur de retour est CB_ERR et la sélection actuelle n’est pas modifiée.

### <a name="remarks"></a>Notes

Une chaîne n’est sélectionnée que si ses personnages initiaux (à partir du point de départ) correspondent aux personnages de la chaîne préfixe.

Notez `SelectString` que `FindString` les fonctions et les `SelectString` fonctions du membre trouvent une chaîne, mais la fonction membre sélectionne également la chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a>CComboBox::SetCueBanner

Définit le texte de repère qui s’affiche pour un contrôle de boîte combo.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszText*|[dans] Pointeur vers un tampon annulé qui contient le texte de repère.|

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Le texte De cue est une invite qui s’affiche dans la zone d’entrée du contrôle de la boîte combo. Le texte de repère est affiché jusqu’à ce que l’utilisateur fournisse l’entrée.

Cette méthode envoie le [message CB_SETCUEBANNER,](/windows/win32/Controls/cb-setcuebanner) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_combobox*, qui est utilisée pour accéder programmatiquement au contrôle de la boîte combo. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit la bannière de repère pour le contrôle de la boîte combo.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a>CComboBox::SetCurSel

Sélectionne une chaîne dans la boîte de liste d’une boîte combo.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Paramètres

*nSelect*<br/>
Spécifie l’index zéro de la chaîne à sélectionner. Si -1, toute sélection actuelle dans la boîte de liste est supprimée et le contrôle de modification est effacé.

### <a name="return-value"></a>Valeur de retour

L’index zéro de l’élément sélectionné si le message est réussi. La valeur de retour est CB_ERR si *nSelect* est supérieur au nombre d’éléments de la liste ou si *nSelect* est réglé à -1, ce qui efface la sélection.

### <a name="remarks"></a>Notes

Si nécessaire, la boîte de liste fait défiler la chaîne en vue (si la boîte de liste est visible). Le texte dans le contrôle de modification de la boîte combo est modifié pour refléter la nouvelle sélection. Toute sélection précédente dans la boîte de liste est supprimée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth

Appelez cette fonction pour définir la largeur minimale autorisée, en pixels, de la boîte de liste d’une boîte combo.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Paramètres

*nWidth (en)*<br/>
La largeur minimale autorisée de la partie liste-boîte de la boîte combo, en pixels.

### <a name="return-value"></a>Valeur de retour

En cas de succès, la nouvelle largeur de la boîte de liste, sinon CB_ERR.

### <a name="remarks"></a>Notes

Cette fonction ne s’applique qu’aux boîtes combo avec le [style CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

Par défaut, la largeur minimale autorisée de la case de liste de décrochage est de 0. Lorsque la partie liste-boîte de la boîte combo est affichée, sa largeur est la plus grande de la largeur minimale autorisée ou la largeur de la boîte combo.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a>CComboBox::SetEditSel

Sélectionne des caractères dans le contrôle de modification d’une boîte combo.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Paramètres

*nStartChar (en)*<br/>
Spécifie la position de départ. Si la position de départ est réglée à -1, alors toute sélection existante est supprimée.

*nEndChar (en)*<br/>
Spécifie la position de fin. Si la position de fin est réglée à -1, alors tout le texte de la position de départ au dernier personnage dans le contrôle de modification est sélectionné.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction de membre est réussie; sinon 0. Il est CB_ERR si `CComboBox` a le style [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou n’a pas de boîte de liste.

### <a name="remarks"></a>Notes

Les positions sont basées à zéro. Pour sélectionner le premier caractère du contrôle de modification, vous spécifiez une position de départ de 0. La position de fin est pour le personnage juste après le dernier personnage à sélectionner. Par exemple, pour sélectionner les quatre premiers caractères du contrôle de modification, vous utiliseriez une position de départ de 0 et une position de fin de 4.

> [!NOTE]
> Cette fonction n’est `ComboBoxEx` pas prise en charge par le contrôle Windows. Pour plus d’informations sur ce contrôle, voir [les contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CComboBox:GetEditSel](#geteditsel).

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a>CComboBox::SetExtendedUI

Appelez `SetExtendedUI` la fonction membre pour sélectionner l’interface utilisateur par défaut ou l’interface utilisateur étendue pour une boîte combo qui a le [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Paramètres

*bExtended*<br/>
Précise si la boîte combo doit utiliser l’interface utilisateur étendue ou l’interface utilisateur par défaut. Une valeur de TRUE sélectionne l’interface utilisateur étendue; une valeur de FALSE sélectionne l’interface utilisateur standard.

### <a name="return-value"></a>Valeur de retour

CB_OKAY si l’opération est réussie, ou CB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

L’interface utilisateur étendue peut être identifiée de la manière suivante :

- En cliquant sur le contrôle statique affiche la boîte de liste uniquement pour les boîtes combo avec le style CBS_DROPDOWNLIST.

- Appuyer sur la clé DOWN ARROW affiche la boîte de liste (F4 est désactivé).

Le défilement dans le contrôle statique est désactivé lorsque la liste d’éléments n’est pas visible (les touches fléchées sont désactivées).

### <a name="example"></a>Exemple

  Voir l’exemple pour [CComboBox:GetExtendedUI](#getextendedui).

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent

Définit la largeur, en pixels, par laquelle la partie liste-boîte de la boîte combo peut être défilé horizontalement.

```cpp
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Paramètres

*nExtent*<br/>
Spécifie le nombre de pixels par lequel la partie liste-boîte de la boîte combo peut être défilé horizontalement.

### <a name="remarks"></a>Notes

Si la largeur de la boîte de liste est plus petite que cette valeur, la barre de défilement horizontal fera défiler horizontalement les éléments dans la boîte de liste. Si la largeur de la boîte de liste est égale ou supérieure à cette valeur, la barre de défilement horizontal est cachée ou, si la boîte combo a le style [CBS_DISABLENOSCROLL,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) désactivée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a>CComboBox::SetItemData

Définit la valeur 32 bits associée à l’élément spécifié dans une boîte combo.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient un index à base nulle à l’élément à définir.

*dwItemData*<br/>
Contient la nouvelle valeur à associer à l’article.

### <a name="return-value"></a>Valeur de retour

CB_ERR en cas d’erreur.

### <a name="remarks"></a>Notes

Utilisez `SetItemDataPtr` la fonction membre si l’élément 32 bits doit être un pointeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a>CComboBox::SetItemDataPtr

Définit la valeur 32 bits associée à l’élément spécifié dans une boîte combo pour être le pointeur spécifié **(vide** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient un index à base nulle de l’élément.

*Pdata*<br/>
Contient le pointeur à associer à l’élément.

### <a name="return-value"></a>Valeur de retour

CB_ERR en cas d’erreur.

### <a name="remarks"></a>Notes

Ce pointeur reste valable pour la durée de vie de la boîte combo, même si la position relative de l’élément dans la boîte combo peut changer au fur et à mesure que les éléments sont ajoutés ou supprimés. Par conséquent, l’index de l’élément dans la boîte peut changer, mais le pointeur reste fiable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a>CComboBox::SetItemHeight

Appelez `SetItemHeight` la fonction membre pour définir la hauteur des éléments de liste dans une boîte combo ou la hauteur de la partie de contrôle de modification (ou de texte statique) d’une boîte combo.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Précise si la hauteur des éléments de liste ou la hauteur de la partie de contrôle de modification (ou de texte statique) de la boîte de combo est définie.

Si la boîte de combo a le style [CBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) *nIndex* spécifie l’index zéro de l’élément de liste dont la hauteur doit être définie; sinon, *nIndex* doit être 0 et la hauteur de tous les éléments de liste sera définie.

Si *nIndex* est de -1, la hauteur de la partie de modification-contrôle ou de texte statique de la boîte de combo doit être définie.

*cyItemHeight*<br/>
Spécifie la hauteur, en pixels, du composant combo-box identifié par *nIndex*.

### <a name="return-value"></a>Valeur de retour

CB_ERR si l’indice ou la hauteur est invalide; sinon 0.

### <a name="remarks"></a>Notes

La hauteur de la partie de contrôle d’édition (ou de texte statique) de la boîte de combo est définie indépendamment de la hauteur des éléments de liste. Une application doit s’assurer que la hauteur de la partie de contrôle de modification (ou de texte statique) n’est pas plus petite que la hauteur d’un élément particulier de boîte de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a>CComboBox::SetLocale

Définit l’identifiant local pour cette boîte combo.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Paramètres

*nNewLocale (en)*<br/>
La nouvelle valeur d’identifiant local (LCID) à définir pour la boîte combo.

### <a name="return-value"></a>Valeur de retour

La valeur précédente de l’identifiant local (LCID) pour cette boîte combo.

### <a name="remarks"></a>Notes

Si `SetLocale` ce n’est pas appelé, le lieu par défaut est obtenu à partir du système. Ce local par défaut du système peut être modifié en utilisant l’application Régionale (ou Internationale) de Control Panel.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems

Définit le nombre minimum d’éléments visibles dans la liste d’abandon du contrôle actuel de la boîte combo.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iMinVisible*|[dans] Spécifie le nombre minimum d’objets visibles.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message CB_SETMINVISIBLE,](/windows/win32/Controls/cb-setminvisible) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_combobox*, qui est utilisée pour accéder programmatiquement au contrôle de la boîte combo. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant insère 20 éléments dans la liste des gouttes d’un contrôle de boîte combo. Ensuite, il spécifie qu’un minimum de 10 éléments soient affichés lorsqu’un utilisateur appuie sur la flèche de chute.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a>CComboBox::SetTopIndex

S’assure qu’un élément particulier est visible dans la partie liste-boîte de la boîte combo.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index zéro de l’élément de la boîte de liste.

### <a name="return-value"></a>Valeur de retour

Zéro en cas de succès, ou CB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Le système fait défiler la case de liste jusqu’à ce que l’élément spécifié par *nIndex* s’affiche en haut de la case de liste ou que la plage de défilement maximum ait été atteinte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a>CComboBox::ShowDropDown

Affiche ou cache la case liste d’une boîte combo qui a le [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.

```cpp
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Paramètres

*bShowIt*<br/>
Précise si la case de liste de drop-down doit être affichée ou cachée. Une valeur de TRUE montre la boîte de liste. Une valeur de FALSE cache la boîte de liste.

### <a name="remarks"></a>Notes

Par défaut, une boîte combo de ce style affichera la boîte de liste.

Cette fonction de membre n’a aucun effet sur une boîte de combo créée avec le style [CBS_SIMPLE.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

### <a name="example"></a>Exemple

  Voir l’exemple pour [CComboBox:GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Classe CButton](../../mfc/reference/cbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[Classe CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)
