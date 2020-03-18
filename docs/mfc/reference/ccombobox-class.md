---
title: CComboBox (classe)
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
ms.openlocfilehash: b54a1913073ca0b23aeb17a57b16f589a074637b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418817"
---
# <a name="ccombobox-class"></a>CComboBox (classe)

Fournit les fonctionnalités d'une zone de liste modifiable Windows.

## <a name="syntax"></a>Syntaxe

```
class CComboBox : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CComboBox :: CComboBox](#ccombobox)|Construit un objet `CComboBox`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|Ajoute une chaîne à la fin de la liste dans la zone de liste d’une zone de liste déroulante, ou à la position triée pour les zones de liste avec le style CBS_SORT.|
|[CComboBox :: Clear](#clear)|Supprime (efface) la sélection actuelle, le cas échéant, dans le contrôle d’édition.|
|[CComboBox :: CompareItem](#compareitem)|Appelé par l’infrastructure pour déterminer la position relative d’un nouvel élément de liste dans une zone de liste déroulante owner-drawn triée.|
|[CComboBox :: Copy](#copy)|Copie la sélection actuelle, le cas échéant, dans le presse-papiers au format CF_TEXT.|
|[CComboBox :: Create](#create)|Crée la zone de liste déroulante et l’attache à l’objet `CComboBox`.|
|[CComboBox :: Cut](#cut)|Supprime (coupe) la sélection actuelle, le cas échéant, dans le contrôle d’édition et copie le texte supprimé dans le presse-papiers au format CF_TEXT.|
|[CComboBox ::D eleteItem](#deleteitem)|Appelé par le Framework lorsqu’un élément de liste est supprimé d’une zone de liste déroulante owner-drawn.|
|[CComboBox ::D eleteString](#deletestring)|Supprime une chaîne de la zone de liste d’une zone de liste déroulante.|
|[CComboBox ::D IR](#dir)|Ajoute une liste de noms de fichiers à la zone de liste d’une zone de liste déroulante.|
|[CComboBox ::D rawItem](#drawitem)|Appelée par l’infrastructure quand un aspect visuel d’une zone de liste déroulante owner-drawn change.|
|[CComboBox :: FindString](#findstring)|Recherche la première chaîne qui contient le préfixe spécifié dans la zone de liste d’une zone de liste déroulante.|
|[CComboBox :: FindExactString](#findstringexact)|Recherche la première chaîne de zone de liste (dans une zone de liste déroulante) qui correspond à la chaîne spécifiée.|
|[CComboBox :: GetComboBoxInfo](#getcomboboxinfo)|Récupère des informations sur l’objet `CComboBox`.|
|[CComboBox :: GetCount](#getcount)|Récupère le nombre d’éléments dans la zone de liste d’une zone de liste déroulante.|
|[CComboBox :: GetCueBanner](#getcuebanner)|Obtient le texte de la pile qui est affiché pour un contrôle de zone de liste déroulante.|
|[CComboBox :: GetCurSel](#getcursel)|Récupère l’index de l’élément actuellement sélectionné, le cas échéant, dans la zone de liste d’une zone de liste déroulante.|
|[CComboBox :: GetDroppedControlRect](#getdroppedcontrolrect)|Récupère les coordonnées d’écran de la zone de liste déroulante visible (déroulée) d’une zone de liste déroulante.|
|[CComboBox :: GetDroppedState](#getdroppedstate)|Détermine si la zone de liste d’une zone de liste déroulante de liste déroulante est visible (déroulée).|
|[CComboBox :: GetDroppedWidth](#getdroppedwidth)|Récupère la largeur minimale autorisée pour la partie de zone de liste déroulante d’une zone de liste déroulante.|
|[CComboBox :: GetEditSel](#geteditsel)|Obtient les positions des caractères de début et de fin de la sélection actuelle dans le contrôle d’édition d’une zone de liste déroulante.|
|[CComboBox :: GetExtendedUI](#getextendedui)|Détermine si une zone de liste déroulante possède l’interface utilisateur par défaut ou l’interface utilisateur étendue.|
|[CComboBox :: GetHorizontalExtent](#gethorizontalextent)|Retourne la largeur, en pixels, que la partie de la zone de liste de la zone de liste déroulante peut faire défiler horizontalement.|
|[CComboBox :: GetItemData](#getitemdata)|Récupère la valeur 32 bits fournie par l’application associée à l’élément de zone de liste déroulante spécifié.|
|[CComboBox :: GetItemDataPtr](#getitemdataptr)|Récupère le pointeur 32 bits fourni par l’application qui est associé à l’élément de zone de liste déroulante spécifié.|
|[CComboBox :: GetItemHeight](#getitemheight)|Récupère la hauteur des éléments de liste dans une zone de liste déroulante.|
|[CComboBox :: GetLBText](#getlbtext)|Obtient une chaîne à partir de la zone de liste d’une zone de liste déroulante.|
|[CComboBox :: GetLBTextLen](#getlbtextlen)|Obtient la longueur d’une chaîne dans la zone de liste d’une zone de liste déroulante.|
|[CComboBox :: GetLocale](#getlocale)|Récupère l’identificateur de paramètres régionaux pour une zone de liste déroulante.|
|[CComboBox :: GetMinVisible](#getminvisible)|Obtient le nombre minimal d’éléments visibles dans la liste déroulante de la zone de liste déroulante actuelle.|
|[CComboBox :: GetTopIndex](#gettopindex)|Retourne l’index du premier élément visible dans la partie de la zone de liste de la zone de liste déroulante.|
|[CComboBox :: InitStorage](#initstorage)|Préalloue des blocs de mémoire pour les éléments et les chaînes dans la partie de la zone de liste de la zone de liste déroulante.|
|[CComboBox::InsertString](#insertstring)|Insère une chaîne dans la zone de liste d’une zone de liste modifiable.|
|[CComboBox :: LimitText](#limittext)|Limite la longueur du texte que l’utilisateur peut entrer dans le contrôle d’édition d’une zone de liste déroulante.|
|[CComboBox :: MeasureItem](#measureitem)|Appelé par l’infrastructure pour déterminer les dimensions de zone de liste déroulante lorsqu’une zone de liste déroulante owner-drawn est créée.|
|[CComboBox ::P Oller](#paste)|Insère les données du presse-papiers dans le contrôle d’édition à la position actuelle du curseur. Les données sont insérées uniquement si le presse-papiers contient des données au format CF_TEXT.|
|[CComboBox :: ResetContent](#resetcontent)|Supprime tous les éléments de la zone de liste et le contrôle d’édition d’une zone de liste déroulante.|
|[CComboBox :: SelectString](#selectstring)|Recherche une chaîne dans la zone de liste d’une zone de liste déroulante et, si la chaîne est trouvée, sélectionne la chaîne dans la zone de liste et copie la chaîne dans le contrôle d’édition.|
|[CComboBox :: SetCueBanner](#setcuebanner)|Définit le texte de la pile qui est affiché pour un contrôle zone de liste déroulante.|
|[CComboBox :: SetCurSel](#setcursel)|Sélectionne une chaîne dans la zone de liste d’une zone de liste déroulante.|
|[CComboBox :: SetDroppedWidth](#setdroppedwidth)|Définit la largeur minimale autorisée pour la partie de zone de liste déroulante d’une zone de liste déroulante.|
|[CComboBox :: SetEditSel](#seteditsel)|Sélectionne des caractères dans le contrôle d’édition d’une zone de liste déroulante.|
|[CComboBox :: SetExtendedUI](#setextendedui)|Sélectionne l’interface utilisateur par défaut ou l’interface utilisateur étendue pour une zone de liste déroulante avec le style CBS_DROPDOWN ou CBS_DROPDOWNLIST.|
|[CComboBox :: SetHorizontalExtent](#sethorizontalextent)|Définit la largeur, en pixels, que la partie de la zone de liste de la zone de liste déroulante peut faire défiler horizontalement.|
|[CComboBox :: SetItemData](#setitemdata)|Définit la valeur 32 bits associée à l’élément spécifié dans une zone de liste déroulante.|
|[CComboBox :: SetItemDataPtr](#setitemdataptr)|Définit le pointeur 32 bits associé à l’élément spécifié dans une zone de liste déroulante.|
|[CComboBox :: SetItemHeight](#setitemheight)|Définit la hauteur des éléments de liste dans une zone de liste déroulante ou la hauteur de la partie de contrôle de modification (ou de texte statique) d’une zone de liste déroulante.|
|[CComboBox :: SetLocale](#setlocale)|Définit l’identificateur de paramètres régionaux pour une zone de liste déroulante.|
|[CComboBox :: SetMinVisibleItems](#setminvisibleitems)|Définit le nombre minimal d’éléments visibles dans la liste déroulante de la zone de liste déroulante actuelle.|
|[CComboBox :: SetTopIndex](#settopindex)|Indique à la partie de zone de liste de la zone de liste déroulante d’afficher l’élément avec l’index spécifié en haut.|
|[CComboBox :: ShowDropDown](#showdropdown)|Affiche ou masque la zone de liste d’une zone de liste déroulante qui a le style CBS_DROPDOWN ou CBS_DROPDOWNLIST.|

## <a name="remarks"></a>Notes

Une zone de liste déroulante se compose d’une zone de liste associée à un contrôle statique ou à un contrôle d’édition. La partie de la zone de liste du contrôle peut être affichée à tout moment ou ne peut être déroulante que lorsque l’utilisateur sélectionne la flèche déroulante à côté du contrôle.

L’élément actuellement sélectionné (le cas échéant) dans la zone de liste est affiché dans le contrôle statique ou d’édition. En outre, si la zone de liste déroulante a le style liste déroulante, l’utilisateur peut taper le caractère initial de l’un des éléments de la liste, et la zone de liste, si elle est visible, met en surbrillance l’élément suivant avec ce caractère initial.

Le tableau suivant compare les trois [styles](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)de zone de liste déroulante.

|Style|Quand la zone de liste est visible|Contrôle statique ou d’édition|
|-----------|-------------------------------|-----------------------------|
|Simple|Toujours|Modifier|
|Drop-down|En cas de déverrouillage|Modifier|
|Liste déroulante|En cas de déverrouillage|statique|

Vous pouvez créer un objet `CComboBox` à partir d’un modèle de boîte de dialogue ou directement dans votre code. Dans les deux cas, appelez d’abord le constructeur `CComboBox` pour construire l’objet `CComboBox` ; Appelez ensuite la fonction membre [Create](#create) pour créer le contrôle et l’attacher à l’objet `CComboBox`.

Si vous voulez gérer les messages de notification Windows envoyés par une zone de liste déroulante à son parent (généralement une classe dérivée de `CDialog`), ajoutez une entrée de la table des messages et une fonction membre du gestionnaire de messages à la classe parente pour chaque message.

Chaque entrée de la table des messages prend la forme suivante :

**Sur\_** _notification_ **(** _ID_, _memberFxn_ **)**

où `id` spécifie l’ID de fenêtre enfant du contrôle de zone de liste déroulante qui envoie la notification et `memberFxn` est le nom de la fonction membre parente que vous avez écrite pour gérer la notification.

Le prototype de fonction du parent est le suivant :

**afx_msg** `void` `memberFxn` **();**

L’ordre dans lequel certaines notifications seront envoyées ne peut pas être prédit. En particulier, une notification CBN_SELCHANGE peut se produire avant ou après une notification CBN_CLOSEUP.

Les entrées de table des messages potentielles sont les suivantes :

- ON_CBN_CLOSEUP (Windows 3,1 et versions ultérieures.) La zone de liste d’une zone de liste déroulante a été fermée. Ce message de notification n’est pas envoyé pour une zone de liste modifiable avec le style [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

- ON_CBN_DBLCLK l’utilisateur double-clique sur une chaîne dans la zone de liste d’une zone de liste déroulante. Ce message de notification est uniquement envoyé pour une zone de liste modifiable avec le style CBS_SIMPLE. Pour une zone de liste modifiable avec le style [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , un double-clic ne peut pas se produire parce qu’un seul clic masque la zone de liste.

- ON_CBN_DROPDOWN la zone de liste d’une zone de liste déroulante est sur le point de se dérouler (rendue visible). Ce message de notification peut se produire uniquement pour une zone de liste modifiable avec le style CBS_DROPDOWN ou CBS_DROPDOWNLIST.

- ON_CBN_EDITCHANGE l’utilisateur a pris une action qui a peut-être modifié le texte de la partie modifier le contrôle d’une zone de liste déroulante. Contrairement au message CBN_EDITUPDATE, ce message est envoyé une fois que Windows a mis à jour l’écran. Elle n’est pas envoyée si la zone de liste déroulante a le style CBS_DROPDOWNLIST.

- ON_CBN_EDITUPDATE la partie de contrôle de modification d’une zone de liste déroulante est sur le présent d’afficher le texte modifié. Ce message de notification est envoyé une fois que le contrôle a mis en forme le texte, mais avant d’afficher le texte. Elle n’est pas envoyée si la zone de liste déroulante a le style CBS_DROPDOWNLIST.

- ON_CBN_ERRSPACE la zone de liste déroulante ne peut pas allouer suffisamment de mémoire pour répondre à une demande spécifique.

- ON_CBN_SELENDCANCEL (Windows 3,1 et versions ultérieures.) Indique que la sélection de l’utilisateur doit être annulée. L’utilisateur clique sur un élément, puis sur une autre fenêtre ou contrôle pour masquer la zone de liste d’une zone de liste déroulante. Ce message de notification est envoyé avant l’CBN_CLOSEUP message de notification pour indiquer que la sélection de l’utilisateur doit être ignorée. Le message de notification CBN_SELENDCANCEL ou CBN_SELENDOK est envoyé même si le message de notification CBN_CLOSEUP n’est pas envoyé (comme dans le cas d’une zone de liste déroulante avec le style CBS_SIMPLE).

- ON_CBN_SELENDOK l’utilisateur sélectionne un élément, appuie sur la touche entrée ou clique sur la flèche bas pour masquer la zone de liste d’une zone de liste déroulante. Ce message de notification est envoyé avant le message d’CBN_CLOSEUP pour indiquer que la sélection de l’utilisateur doit être considérée comme valide. Le message de notification CBN_SELENDCANCEL ou CBN_SELENDOK est envoyé même si le message de notification CBN_CLOSEUP n’est pas envoyé (comme dans le cas d’une zone de liste déroulante avec le style CBS_SIMPLE).

- ON_CBN_KILLFOCUS la zone de liste déroulante perd le focus d’entrée.

- ON_CBN_SELCHANGE la sélection dans la zone de liste d’une zone de liste déroulante est sur le point d’être modifiée lorsque l’utilisateur clique sur la zone de liste ou change la sélection à l’aide des touches de direction. Lors du traitement de ce message, le texte du contrôle d’édition de la zone de liste déroulante peut uniquement être récupéré via `GetLBText` ou une autre fonction similaire. `GetWindowText` ne peut pas être utilisé.

- ON_CBN_SETFOCUS la zone de liste déroulante reçoit le focus d’entrée.

Si vous créez un objet `CComboBox` dans une boîte de dialogue (par le biais d’une ressource de boîte de dialogue), l’objet `CComboBox` est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous incorporez un objet `CComboBox` dans un autre objet Window, vous n’avez pas besoin de le détruire. Si vous créez l’objet `CComboBox` sur la pile, il est détruit automatiquement. Si vous créez l’objet `CComboBox` sur le segment de mémoire à l’aide de la fonction **New** , vous devez appeler **Delete** sur l’objet pour le détruire lorsque la zone de liste déroulante Windows est détruite.

**Remarque** Si vous souhaitez gérer des messages WM_KEYDOWN et WM_CHAR, vous devez sous-classer les contrôles de zone de liste et de modification de la zone de liste déroulante, dériver des classes de `CEdit` et `CListBox`, et ajouter des gestionnaires pour ces messages aux classes dérivées. Pour plus d’informations, consultez [CWnd :: SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="addstring"></a>CComboBox :: AddString

Ajoute une chaîne à la zone de liste d’une zone de liste déroulante.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*lpszString*<br/>
Pointe vers la chaîne terminée par le caractère null qui doit être ajoutée.

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est supérieure ou égale à 0, il s’agit de l’index de base zéro de la chaîne dans la zone de liste. La valeur de retour est CB_ERR si une erreur se produit ; la valeur de retour est CB_ERRSPACE si l’espace disponible est insuffisant pour stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Si la zone de liste n’a pas été créée avec le style [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , la chaîne est ajoutée à la fin de la liste. Dans le cas contraire, la chaîne est insérée dans la liste et la liste est triée.

> [!NOTE]
>  Cette fonction n’est pas prise en charge par le contrôle Windows `ComboBoxEx`. Pour plus d’informations sur ce contrôle, consultez [contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

Pour insérer une chaîne à un emplacement spécifique de la liste, utilisez la fonction membre [InsertString](#insertstring) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

##  <a name="ccombobox"></a>CComboBox :: CComboBox

Construit un objet `CComboBox`.

```
CComboBox();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

##  <a name="clear"></a>CComboBox :: Clear

Supprime (efface) la sélection actuelle, le cas échéant, dans le contrôle d’édition de la zone de liste déroulante.

```
void Clear();
```

### <a name="remarks"></a>Notes

Pour supprimer la sélection actuelle et placer le contenu supprimé dans le presse-papiers, utilisez la fonction membre [Cut](#cut) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

##  <a name="compareitem"></a>CComboBox :: CompareItem

Appelée par l’infrastructure pour déterminer la position relative d’un nouvel élément dans la partie de la zone de liste d’une zone de liste déroulante owner-draw triée.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpCompareItemStruct*<br/>
Pointeur long vers une structure [compareitemstruct,](/windows/win32/api/winuser/ns-winuser-compareitemstruct) .

### <a name="return-value"></a>Valeur de retour

Indique la position relative des deux éléments décrits dans la structure `COMPAREITEMSTRUCT`. Il peut s’agir de l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|- 1|L’élément 1 est trié avant l’élément 2.|
|0|Les éléments 1 et 2 sont triés de la même façon.|
|1|L’élément 1 est trié après l’élément 2.|

Consultez [CWnd :: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) pour obtenir une description de `COMPAREITEMSTRUCT`.

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Si vous créez une zone de liste déroulante owner-draw avec le style LBS_SORT, vous devez substituer cette fonction membre pour aider l’infrastructure à trier les nouveaux éléments ajoutés à la zone de liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

##  <a name="copy"></a>CComboBox :: Copy

Copie la sélection actuelle, le cas échéant, dans le contrôle d’édition de la zone de liste déroulante dans le presse-papiers au format CF_TEXT.

```
void Copy();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

##  <a name="create"></a>CComboBox :: Create

Crée la zone de liste déroulante et l’attache à l’objet `CComboBox`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style de la zone de liste déroulante. Applique une combinaison de [styles de zone de liste déroulante](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) à la zone.

*rectangulaire*<br/>
Pointe vers la position et la taille de la zone de liste déroulante. Peut être une [structure Rect](/windows/win32/api/windef/ns-windef-rect) ou un objet `CRect`.

*pParentWnd*<br/>
Spécifie la fenêtre parente de la zone de liste déroulante (généralement un `CDialog`). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de la zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un objet `CComboBox` en deux étapes. Tout d’abord, appelez le constructeur, puis appelez `Create`, qui crée la zone de liste déroulante Windows et l’attache à l’objet `CComboBox`.

Lorsque `Create` s’exécute, Windows envoie les messages [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)et [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) à la zone de liste déroulante.

Ces messages sont gérés par défaut par les fonctions membres [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)et [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) dans la classe de base `CWnd`. Pour étendre la gestion des messages par défaut, dérivez une classe de `CComboBox`, ajoutez une table des messages à la nouvelle classe et substituez les fonctions membres du gestionnaire de messages précédentes. Substituez `OnCreate`, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.

Appliquez les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle de zone de liste déroulante. :

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_VSCROLL pour ajouter le défilement vertical pour la zone de liste dans la zone de liste déroulante

- WS_HSCROLL pour ajouter le défilement horizontal pour la zone de liste dans la zone de liste déroulante

- WS_GROUP des contrôles de groupe

- WS_TABSTOP d’inclure la zone de liste déroulante dans l’ordre de tabulation

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

##  <a name="cut"></a>CComboBox :: Cut

Supprime (coupe) la sélection actuelle, le cas échéant, dans le contrôle d’édition de zone de liste déroulante, et copie le texte supprimé dans le presse-papiers au format CF_TEXT.

```
void Cut();
```

### <a name="remarks"></a>Notes

Pour supprimer la sélection actuelle sans placer le texte supprimé dans le presse-papiers, appelez la fonction membre [Clear](#clear) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

##  <a name="deleteitem"></a>CComboBox ::D eleteItem

Appelé par le Framework lorsque l’utilisateur supprime un élément d’un objet `CComboBox` owner-draw ou détruit la zone de liste déroulante.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDeleteItemStruct*<br/>
Pointeur long vers une structure Windows [deleteitemstruct,](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) qui contient des informations sur l’élément supprimé. Consultez [CWnd :: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) pour obtenir une description de cette structure.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Substituez cette fonction pour redessiner la zone de liste déroulante en fonction des besoins.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

##  <a name="deletestring"></a>CComboBox ::D eleteString

Supprime l’élément à la position *nIndex* de la zone de liste déroulante.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de la chaîne à supprimer.

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est supérieure ou égale à 0, il s’agit du nombre de chaînes restantes dans la liste. La valeur de retour est CB_ERR si *nIndex* spécifie un index supérieur au nombre d’éléments de la liste.

### <a name="remarks"></a>Notes

Tous les éléments suivants *nIndex* descendent d’une position. Par exemple, si une zone de liste déroulante contient deux éléments, le fait de supprimer le premier élément entraînera l’élément restant dans la première position. *nIndex*= 0 pour l’élément à la première position.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

##  <a name="dir"></a>CComboBox ::D IR

Ajoute une liste de noms de fichiers ou de lecteurs à la zone de liste d’une zone de liste déroulante.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Paramètres

*AVERTISSEMENT*<br/>
Il peut s’agir de n’importe quelle combinaison des valeurs **enum** décrites dans [CFile :: GetStatus](../../mfc/reference/cfile-class.md#getstatus) ou de n’importe quelle combinaison des valeurs suivantes :

- DDL_READWRITE fichier peut être lu ou écrit.

- DDL_READONLY fichier peut être lu à partir de laquelle il n’est pas écrit.

- DDL_HIDDEN fichier est masqué et n’apparaît pas dans la liste des répertoires.

- DDL_SYSTEM fichier est un fichier système.

- DDL_DIRECTORY le nom spécifié par *lpszWildCard* spécifie un répertoire.

- DDL_ARCHIVE fichier a été archivé.

- DDL_DRIVES inclure tous les lecteurs qui correspondent au nom spécifié par *lpszWildCard*.

- DDL_EXCLUSIVE l’indicateur exclusif. Si l’indicateur exclusive est défini, seuls les fichiers du type spécifié sont répertoriés. Dans le cas contraire, les fichiers du type spécifié sont répertoriés en plus des fichiers « normaux ».

*lpszWildCard*<br/>
Pointe vers une chaîne de spécification de fichier. La chaîne peut contenir des caractères génériques (par exemple, *.\*).

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est supérieure ou égale à 0, il s’agit de l’index de base zéro du dernier nom de fichier ajouté à la liste. La valeur de retour est CB_ERR si une erreur se produit ; la valeur de retour est CB_ERRSPACE si l’espace disponible est insuffisant pour stocker les nouvelles chaînes.

### <a name="remarks"></a>Notes

Cette fonction n’est pas prise en charge par le contrôle Windows `ComboBoxEx`. Pour plus d’informations sur ce contrôle, consultez [contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

##  <a name="drawitem"></a>CComboBox ::D rawItem

Appelée par l’infrastructure quand un aspect visuel d’une zone de liste déroulante owner-draw change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le membre `itemAction` de la structure `DRAWITEMSTRUCT` définit l’action de dessin à effectuer. Consultez [CWnd :: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) pour obtenir une description de cette structure.

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre pour implémenter le dessin pour un objet `CComboBox` owner-draw. Avant que cette fonction membre ne se termine, l’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

##  <a name="findstring"></a>CComboBox :: FindString

Recherche, mais ne sélectionne pas, la première chaîne qui contient le préfixe spécifié dans la zone de liste d’une zone de liste déroulante.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Paramètres

*nStartAfter*<br/>
Contient l’index de base zéro de l’élément avant le premier élément dans lequel effectuer la recherche. Lorsque la recherche atteint le bas de la zone de liste, elle continue à partir du haut de la zone de liste jusqu’à l’élément spécifié par *nStartAfter*. Si-1, la zone de liste entière est recherchée à partir du début.

*lpszString*<br/>
Pointe vers la chaîne terminée par le caractère null qui contient le préfixe à rechercher. La recherche étant indépendante de la casse, cette chaîne peut contenir n’importe quelle combinaison de lettres majuscules et minuscules.

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est supérieure ou égale à 0, il s’agit de l’index de base zéro de l’élément correspondant. Elle est CB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Cette fonction n’est pas prise en charge par le contrôle Windows `ComboBoxEx`. Pour plus d’informations sur ce contrôle, consultez [contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

##  <a name="findstringexact"></a>CComboBox :: FindExactString

Appelez la fonction membre `FindStringExact` pour rechercher la première chaîne de zone de liste (dans une zone de liste déroulante) qui correspond à la chaîne spécifiée dans *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Paramètres

*nIndexStart*<br/>
Spécifie l’index de base zéro de l’élément avant le premier élément dans lequel effectuer la recherche. Lorsque la recherche atteint le bas de la zone de liste, elle continue à partir du haut de la zone de liste jusqu’à l’élément spécifié par *nIndexStart*. Si *nIndexStart* est-1, la zone de liste entière est recherchée à partir du début.

*lpszFind*<br/>
Pointe vers la chaîne terminée par le caractère null à rechercher. Cette chaîne peut contenir un nom de fichier complet, y compris l’extension. La recherche ne respecte pas la casse, par conséquent, cette chaîne peut contenir n’importe quelle combinaison de lettres majuscules et minuscules.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément correspondant, ou CB_ERR si la recherche a échoué.

### <a name="remarks"></a>Notes

Si la zone de liste déroulante a été créée avec un style owner-draw, mais sans le style [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , `FindStringExact` tente de faire correspondre la valeur du mot double à la valeur de *lpszFind*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

##  <a name="getcomboboxinfo"></a>CComboBox :: GetComboBoxInfo

Récupère des informations pour l’objet `CComboBox`.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Paramètres

*pcbi*<br/>
Pointeur vers la structure [COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo) .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités du message [CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo) , comme décrit dans le SDK Windows.

##  <a name="getcount"></a>CComboBox :: GetCount

Appelez cette fonction membre pour récupérer le nombre d’éléments dans la partie de la zone de liste d’une zone de liste déroulante.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments. Le nombre retourné est supérieur à la valeur d’index du dernier élément (l’index est de base zéro). Elle est CB_ERR si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

##  <a name="getcuebanner"></a>CComboBox :: GetCueBanner

Obtient le texte de la pile qui est affiché pour un contrôle de zone de liste déroulante.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszText*|à Pointeur vers une mémoire tampon qui reçoit le texte de la bannière de signal.|
|*cchText*|dans Taille de la mémoire tampon vers laquelle pointe le paramètre *lpszText* .|

### <a name="return-value"></a>Valeur de retour

Dans la première surcharge, objet [CString](../../atl-mfc-shared/using-cstring.md) qui contient le texte de la bannière de signal, le cas échéant ; Sinon, un objet `CString` qui a une longueur égale à zéro.

-ou-

Dans la deuxième surcharge, TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le texte de la pile est une invite qui s’affiche dans la zone d’entrée du contrôle de zone de liste déroulante. Le texte de la file d’attente s’affiche jusqu’à ce que l’utilisateur fournisse une entrée.

Cette méthode envoie le message [CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner) , qui est décrit dans le SDK Windows.

##  <a name="getcursel"></a>CComboBox :: GetCurSel

Appelez cette fonction membre pour déterminer quel élément de la zone de liste déroulante est sélectionné.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément actuellement sélectionné dans la zone de liste d’une zone de liste déroulante, ou CB_ERR si aucun élément n’est sélectionné.

### <a name="remarks"></a>Notes

`GetCurSel` retourne un index dans la liste.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

##  <a name="getdroppedcontrolrect"></a>CComboBox :: GetDroppedControlRect

Appelez la fonction membre `GetDroppedControlRect` pour récupérer les coordonnées d’écran de la zone de liste déroulante visible d’une zone de liste déroulante.

```
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Paramètres

*lprect*<br/>
Pointe vers la [structure Rect](/windows/win32/api/windef/ns-windef-rect) qui doit recevoir les coordonnées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

##  <a name="getdroppedstate"></a>CComboBox :: GetDroppedState

Appelez la fonction membre `GetDroppedState` pour déterminer si la zone de liste d’une zone de liste déroulante de liste déroulante est visible (déroulée).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la zone de liste est visible ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

##  <a name="getdroppedwidth"></a>CComboBox :: GetDroppedWidth

Appelez cette fonction pour récupérer la largeur minimale autorisée, en pixels, de la zone de liste d’une zone de liste déroulante.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, largeur minimale autorisée, en pixels ; Sinon, CB_ERR.

### <a name="remarks"></a>Notes

Cette fonction s’applique uniquement aux zones de liste modifiable avec le style [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

Par défaut, la largeur minimale autorisée de la zone de liste déroulante est 0. La largeur minimale autorisée peut être définie en appelant [SetDroppedWidth](#setdroppedwidth). Lorsque la partie zone de liste de la zone de liste déroulante est affichée, sa largeur est supérieure à la largeur minimale autorisée ou à la largeur de la zone de liste déroulante.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [SetDroppedWidth](#setdroppedwidth).

##  <a name="geteditsel"></a>CComboBox :: GetEditSel

Obtient les positions des caractères de début et de fin de la sélection actuelle dans le contrôle d’édition d’une zone de liste déroulante.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur 32 bits qui contient la position de début dans le mot de poids faible et la position du premier caractère non sélectionné après la fin de la sélection dans le mot de poids fort. Si cette fonction est utilisée sur une zone de liste déroulante sans contrôle d’édition, CB_ERR est retourné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

##  <a name="getextendedui"></a>CComboBox :: GetExtendedUI

Appelez la fonction membre `GetExtendedUI` pour déterminer si une zone de liste déroulante possède l’interface utilisateur par défaut ou l’interface utilisateur étendue.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la zone de liste déroulante possède l’interface utilisateur étendue ; Sinon, 0.

### <a name="remarks"></a>Notes

L’interface utilisateur étendue peut être identifiée des façons suivantes :

- Cliquer sur le contrôle statique affiche la zone de liste uniquement pour les zones de liste déroulante avec le style [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

- Appuyez sur la touche bas pour afficher la zone de liste (F4 est désactivé).

Le défilement dans le contrôle statique est désactivé lorsque la liste d’éléments n’est pas visible (les touches de direction sont désactivées).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

##  <a name="gethorizontalextent"></a>CComboBox :: GetHorizontalExtent

Récupère à partir de la zone de liste déroulante la largeur, en pixels, à laquelle la partie de zone de liste de la zone de liste déroulante peut faire défiler horizontalement.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur de défilement de la partie de zone de liste de la zone de liste déroulante, en pixels.

### <a name="remarks"></a>Notes

Cela s’applique uniquement si la partie de la zone de liste de la zone de liste déroulante comporte une barre de défilement horizontale.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

##  <a name="getitemdata"></a>CComboBox :: GetItemData

Récupère la valeur 32 bits fournie par l’application associée à l’élément de zone de liste déroulante spécifié.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index de base zéro d’un élément dans la zone de liste de la zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

Valeur 32 bits associée à l’élément, ou CB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

La valeur 32 bits peut être définie avec le paramètre *dwItemData* d’un appel de fonction membre [SetItemData](#setitemdata) . Utilisez la fonction membre `GetItemDataPtr` si la valeur 32 bits à récupérer est un pointeur (**void** <strong>\*</strong>).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

##  <a name="getitemdataptr"></a>CComboBox :: GetItemDataPtr

Récupère la valeur 32 bits fournie par l’application associée à l’élément de zone de liste déroulante spécifié sous la forme d’un pointeur (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index de base zéro d’un élément dans la zone de liste de la zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

Récupère un pointeur, ou-1 si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

##  <a name="getitemheight"></a>CComboBox :: GetItemHeight

Appelez la fonction membre `GetItemHeight` pour récupérer la hauteur des éléments de liste dans une zone de liste déroulante.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie le composant de la zone de liste déroulante dont la hauteur doit être récupérée. Si le paramètre *nIndex* est défini sur-1, la hauteur de la partie de contrôle Edit-Control (ou texte statique) de la zone de liste déroulante est récupérée. Si la zone de liste déroulante a le style [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , *nIndex* spécifie l’index de base zéro de l’élément de liste dont la hauteur doit être récupérée. Sinon, *nIndex* doit avoir la valeur 0.

### <a name="return-value"></a>Valeur de retour

Hauteur, en pixels, de l’élément spécifié dans une zone de liste déroulante. La valeur de retour est CB_ERR si une erreur se produit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

##  <a name="getlbtext"></a>CComboBox :: GetLBText

Obtient une chaîne à partir de la zone de liste d’une zone de liste déroulante.

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
Contient l’index de base zéro de la chaîne de zone de liste à copier.

*lpszText*<br/>
Pointe vers une mémoire tampon qui doit recevoir la chaîne. La mémoire tampon doit avoir suffisamment d’espace pour la chaîne et un caractère null de fin.

*rString*<br/>
Référence à un `CString`.

### <a name="return-value"></a>Valeur de retour

Longueur (en octets) de la chaîne, à l’exclusion du caractère null de fin. Si *nIndex* ne spécifie pas d’index valide, la valeur de retour est CB_ERR.

### <a name="remarks"></a>Notes

La deuxième forme de cette fonction membre remplit un objet `CString` avec le texte de l’élément.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

##  <a name="getlbtextlen"></a>CComboBox :: GetLBTextLen

Obtient la longueur d’une chaîne dans la zone de liste d’une zone de liste déroulante.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index de base zéro de la chaîne de zone de liste.

### <a name="return-value"></a>Valeur de retour

Longueur de la chaîne en octets, à l’exclusion du caractère null de fin. Si *nIndex* ne spécifie pas d’index valide, la valeur de retour est CB_ERR.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CComboBox :: GetLBText](#getlbtext).

##  <a name="getlocale"></a>CComboBox :: GetLocale

Récupère les paramètres régionaux utilisés par la zone de liste déroulante.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de l’identificateur de paramètres régionaux (LCID) pour les chaînes de la zone de liste déroulante.

### <a name="remarks"></a>Notes

Les paramètres régionaux sont utilisés, par exemple, pour déterminer l’ordre de tri des chaînes dans une zone de liste déroulante triée.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CComboBox :: setlocale](#setlocale).

##  <a name="getminvisible"></a>CComboBox :: GetMinVisible

Obtient le nombre minimal d’éléments visibles dans la liste déroulante du contrôle de zone de liste déroulante actuelle.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre minimal d’éléments visibles dans la liste déroulante actuelle.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) , qui est décrit dans le SDK Windows.

##  <a name="gettopindex"></a>CComboBox :: GetTopIndex

Récupère l’index de base zéro du premier élément visible dans la partie de la zone de liste de la zone de liste déroulante.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro du premier élément visible dans la partie de zone de liste de la zone de liste déroulante en cas de réussite, CB_ERR sinon.

### <a name="remarks"></a>Notes

Initialement, l’élément 0 se trouve en haut de la zone de liste, mais si vous faites défiler la zone de liste, un autre élément peut se trouver en haut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

##  <a name="initstorage"></a>CComboBox :: InitStorage

Alloue de la mémoire pour le stockage des éléments de zone de liste dans la partie de zone de liste de la zone de liste déroulante.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Paramètres

*nItems*<br/>
Spécifie le nombre d’éléments à ajouter.

*nBytes*<br/>
Spécifie la quantité de mémoire, en octets, à allouer pour les chaînes d’élément.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, le nombre maximal d’éléments que la partie de la zone de liste de la zone de liste déroulante peut stocker avant qu’une réallocation de mémoire soit nécessaire, sinon CB_ERRSPACE, ce qui signifie que la mémoire disponible est insuffisante.

### <a name="remarks"></a>Notes

Appelez cette fonction avant d’ajouter un grand nombre d’éléments à la partie de la zone de liste de la `CComboBox`.

Windows 95/98 uniquement : le paramètre *wParam* est limité aux valeurs 16 bits. Cela signifie que les zones de liste ne peuvent pas contenir plus de 32 767 éléments. Bien que le nombre d’éléments soit limité, la taille totale des éléments d’une zone de liste n’est limitée que par la mémoire disponible.

Cette fonction permet d’accélérer l’initialisation des zones de liste qui comportent un grand nombre d’éléments (plus de 100). Elle Préalloue la quantité de mémoire spécifiée afin que les fonctions [AddString](#addstring), [InsertString](#insertstring)et [dir](#dir) suivantes prennent le plus de temps possible. Vous pouvez utiliser des estimations pour les paramètres. Si vous surestime, une partie de la mémoire supplémentaire est allouée. Si vous sous-estimez, l’allocation normale est utilisée pour les éléments qui dépassent le montant préalloué.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

##  <a name="insertstring"></a>CComboBox :: InsertString

Insère une chaîne dans la zone de liste d’une zone de liste modifiable.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient l’index de base zéro de la position dans la zone de liste qui doit recevoir la chaîne. Si ce paramètre a la valeur-1, la chaîne est ajoutée à la fin de la liste.

*lpszString*<br/>
Pointe vers la chaîne terminée par le caractère null qui doit être insérée.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la position à laquelle la chaîne a été insérée. La valeur de retour est CB_ERR si une erreur se produit. La valeur de retour est CB_ERRSPACE si l’espace disponible est insuffisant pour stocker la nouvelle chaîne.

### <a name="remarks"></a>Notes

Contrairement à la fonction membre [AddString](#addstring) , la fonction membre `InsertString` n’entraîne pas le tri d’une liste associée au style [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

> [!NOTE]
>  Cette fonction n’est pas prise en charge par le contrôle Windows `ComboBoxEx`. Pour plus d’informations sur ce contrôle, consultez [contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

##  <a name="limittext"></a>CComboBox :: LimitText

Limite la longueur en octets du texte que l’utilisateur peut entrer dans le contrôle d’édition d’une zone de liste déroulante.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Paramètres

*nMaxChars*<br/>
Spécifie la longueur (en octets) du texte que l’utilisateur peut entrer. Si ce paramètre a la valeur 0, la longueur du texte est définie sur 65 535 octets.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite. Si elle est appelée pour une zone de liste déroulante avec le style [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou pour une zone de liste déroulante sans contrôle d’édition, la valeur de retour est CB_ERR.

### <a name="remarks"></a>Notes

Si la zone de liste déroulante n’a pas le style [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles), la définition de la limite du texte sur une valeur supérieure à la taille du contrôle d’édition n’aura aucun effet.

`LimitText` limite uniquement le texte que l’utilisateur peut entrer. Elle n’a aucun effet sur le texte déjà présent dans le contrôle d’édition lorsque le message est envoyé, ni sur la longueur du texte copié dans le contrôle d’édition lorsqu’une chaîne de la zone de liste est sélectionnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

##  <a name="measureitem"></a>CComboBox :: MeasureItem

Appelé par le Framework lorsqu’une zone de liste déroulante avec un style owner-draw est créée.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Pointeur long vers une structure [measureitemstruct,](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre et remplissez la structure `MEASUREITEMSTRUCT` pour informer les fenêtres des dimensions de la zone de liste de la zone de liste déroulante. Si la zone de liste déroulante est créée avec le style [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , l’infrastructure appelle cette fonction membre pour chaque élément de la zone de liste. Dans le cas contraire, ce membre n’est appelé qu’une seule fois.

L’utilisation du style CBS_OWNERDRAWFIXED dans une zone de liste déroulante owner-draw créée à l’aide de la fonction membre [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) de `CWnd` implique des considérations de programmation supplémentaires. Consultez la section [Technical note 14](../../mfc/tn014-custom-controls.md).

Consultez [CWnd :: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pour obtenir une description de la structure `MEASUREITEMSTRUCT`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

##  <a name="paste"></a>CComboBox ::P Oller

Insère les données du presse-papiers dans le contrôle d’édition de la zone de liste déroulante à la position actuelle du curseur.

```
void Paste();
```

### <a name="remarks"></a>Notes

Les données sont insérées uniquement si le presse-papiers contient des données au format CF_TEXT.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

##  <a name="resetcontent"></a>CComboBox :: ResetContent

Supprime tous les éléments de la zone de liste et le contrôle d’édition d’une zone de liste déroulante.

```
void ResetContent();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

##  <a name="selectstring"></a>CComboBox :: SelectString

Recherche une chaîne dans la zone de liste d’une zone de liste déroulante, et si la chaîne est trouvée, sélectionne la chaîne dans la zone de liste et la copie dans le contrôle d’édition.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Paramètres

*nStartAfter*<br/>
Contient l’index de base zéro de l’élément avant le premier élément dans lequel effectuer la recherche. Lorsque la recherche atteint le bas de la zone de liste, elle continue à partir du haut de la zone de liste jusqu’à l’élément spécifié par *nStartAfter*. Si-1, la zone de liste entière est recherchée à partir du début.

*lpszString*<br/>
Pointe vers la chaîne terminée par le caractère null qui contient le préfixe à rechercher. La recherche étant indépendante de la casse, cette chaîne peut contenir n’importe quelle combinaison de lettres majuscules et minuscules.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément sélectionné si la chaîne a été trouvée. En cas d’échec de la recherche, la valeur de retour est CB_ERR et la sélection actuelle n’est pas modifiée.

### <a name="remarks"></a>Notes

Une chaîne est sélectionnée uniquement si ses caractères initiaux (à partir du point de départ) correspondent aux caractères de la chaîne de préfixe.

Notez que les fonctions membres `SelectString` et `FindString` recherchent une chaîne, mais la fonction membre `SelectString` sélectionne également la chaîne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

##  <a name="setcuebanner"></a>CComboBox :: SetCueBanner

Définit le texte de la pile qui est affiché pour un contrôle zone de liste déroulante.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpszText*|dans Pointeur vers une mémoire tampon se terminant par un caractère null qui contient le texte de la file d’attente.|

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le texte de la pile est une invite qui s’affiche dans la zone d’entrée du contrôle de zone de liste déroulante. Le texte de la file d’attente s’affiche jusqu’à ce que l’utilisateur fournisse une entrée.

Cette méthode envoie le message [CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_combobox*, qui est utilisée pour accéder par programmation au contrôle de zone de liste déroulante. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit la bannière de signal pour le contrôle de zone de liste déroulante.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="setcursel"></a>CComboBox :: SetCurSel

Sélectionne une chaîne dans la zone de liste d’une zone de liste déroulante.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Paramètres

*Nsélectionner*<br/>
Spécifie l’index de base zéro de la chaîne à sélectionner. Si-1, toute sélection en cours dans la zone de liste est supprimée et le contrôle d’édition est effacé.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’élément sélectionné si le message a réussi. La valeur de retour est CB_ERR si *nsélectionner* est supérieur au nombre d’éléments dans la liste ou si *nsélectionner* est défini sur-1, ce qui efface la sélection.

### <a name="remarks"></a>Notes

Si nécessaire, la zone de liste fait défiler la chaîne dans la vue (si la zone de liste est visible). Le texte du contrôle d’édition de la zone de liste déroulante est modifié afin de refléter la nouvelle sélection. Toute sélection précédente dans la zone de liste est supprimée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

##  <a name="setdroppedwidth"></a>CComboBox :: SetDroppedWidth

Appelez cette fonction pour définir la largeur minimale autorisée, en pixels, de la zone de liste d’une zone de liste déroulante.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
Largeur minimale autorisée de la partie de zone de liste de la zone de liste déroulante, en pixels.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, nouvelle largeur de la zone de liste, sinon CB_ERR.

### <a name="remarks"></a>Notes

Cette fonction s’applique uniquement aux zones de liste modifiable avec le style [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

Par défaut, la largeur minimale autorisée de la zone de liste déroulante est 0. Lorsque la partie zone de liste de la zone de liste déroulante est affichée, sa largeur est supérieure à la largeur minimale autorisée ou à la largeur de la zone de liste déroulante.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

##  <a name="seteditsel"></a>CComboBox :: SetEditSel

Sélectionne des caractères dans le contrôle d’édition d’une zone de liste déroulante.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Paramètres

*nStartChar*<br/>
Spécifie la position de départ. Si la position de départ est égale à-1, toute sélection existante est supprimée.

*nEndChar*<br/>
Spécifie la position de fin. Si la position de fin a la valeur-1, tout le texte de la position de départ jusqu’au dernier caractère dans le contrôle d’édition est sélectionné.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction membre est réussie ; Sinon, 0. Elle est CB_ERR si `CComboBox` a le style de [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou n’a pas de zone de liste.

### <a name="remarks"></a>Notes

Les positions sont de base zéro. Pour sélectionner le premier caractère du contrôle d’édition, vous spécifiez une position de départ de 0. La position de fin correspond au caractère situé juste après le dernier caractère à sélectionner. Par exemple, pour sélectionner les quatre premiers caractères du contrôle d’édition, vous devez utiliser une position de départ de 0 et une position de fin de 4.

> [!NOTE]
>  Cette fonction n’est pas prise en charge par le contrôle Windows `ComboBoxEx`. Pour plus d’informations sur ce contrôle, consultez [contrôles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CComboBox :: GetEditSel](#geteditsel).

##  <a name="setextendedui"></a>CComboBox :: SetExtendedUI

Appelez la fonction membre `SetExtendedUI` pour sélectionner l’interface utilisateur par défaut ou l’interface utilisateur étendue pour une zone de liste déroulante avec le style [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Paramètres

*bla*<br/>
Spécifie si la zone de liste déroulante doit utiliser l’interface utilisateur étendue ou l’interface utilisateur par défaut. La valeur TRUE sélectionne l’interface utilisateur étendue. la valeur FALSe sélectionne l’interface utilisateur standard.

### <a name="return-value"></a>Valeur de retour

CB_OKAY si l’opération réussit, ou CB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

L’interface utilisateur étendue peut être identifiée des façons suivantes :

- Cliquer sur le contrôle statique affiche la zone de liste uniquement pour les zones de liste déroulante avec le style CBS_DROPDOWNLIST.

- Appuyez sur la touche bas pour afficher la zone de liste (F4 est désactivé).

Le défilement dans le contrôle statique est désactivé lorsque la liste d’éléments n’est pas visible (les touches de direction sont désactivées).

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CComboBox :: GetExtendedUI](#getextendedui).

##  <a name="sethorizontalextent"></a>CComboBox :: SetHorizontalExtent

Définit la largeur, en pixels, par laquelle la partie de la zone de liste de la zone de liste déroulante peut faire défiler horizontalement.

```
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Paramètres

*nExtent*<br/>
Spécifie le nombre de pixels par lequel la partie de la zone de liste de la zone de liste déroulante peut faire défiler horizontalement.

### <a name="remarks"></a>Notes

Si la largeur de la zone de liste est inférieure à cette valeur, la barre de défilement horizontale défile horizontalement les éléments de la zone de liste. Si la largeur de la zone de liste est supérieure ou égale à cette valeur, la barre de défilement horizontale est masquée ou, si la zone de liste déroulante a le style [CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , elle est désactivée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

##  <a name="setitemdata"></a>CComboBox :: SetItemData

Définit la valeur 32 bits associée à l’élément spécifié dans une zone de liste déroulante.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient un index de base zéro de l’élément à définir.

*dwItemData*<br/>
Contient la nouvelle valeur à associer à l’élément.

### <a name="return-value"></a>Valeur de retour

CB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Utilisez la fonction membre `SetItemDataPtr` si l’élément 32 bits doit être un pointeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

##  <a name="setitemdataptr"></a>CComboBox :: SetItemDataPtr

Définit la valeur 32 bits associée à l’élément spécifié dans une zone de liste déroulante comme pointeur spécifié (**void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Contient un index de base zéro de l’élément.

*pData*<br/>
Contient le pointeur à associer à l’élément.

### <a name="return-value"></a>Valeur de retour

CB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Ce pointeur reste valide pour la durée de vie de la zone de liste déroulante, même si la position relative de l’élément dans la zone de liste déroulante peut changer à mesure que des éléments sont ajoutés ou supprimés. Par conséquent, l’index de l’élément dans la zone peut changer, mais le pointeur reste fiable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

##  <a name="setitemheight"></a>CComboBox :: SetItemHeight

Appelez la fonction membre `SetItemHeight` pour définir la hauteur des éléments de liste dans une zone de liste déroulante ou la hauteur de la partie de contrôle de modification (ou de texte statique) d’une zone de liste déroulante.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie si la hauteur des éléments de liste ou la hauteur de la partie de contrôle Edit-Control (ou de texte statique) de la zone de liste déroulante est définie.

Si la zone de liste déroulante a le style [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , *nIndex* spécifie l’index de base zéro de l’élément de liste dont la hauteur doit être définie. Sinon, *nIndex* doit avoir la valeur 0 et la hauteur de tous les éléments de la liste est définie.

Si *nIndex* a la valeur-1, la hauteur de la partie de contrôle Edit-Control ou Static-Text de la zone de liste déroulante doit être définie.

*cyItemHeight*<br/>
Spécifie la hauteur, en pixels, du composant de zone de liste déroulante identifié par *nIndex*.

### <a name="return-value"></a>Valeur de retour

CB_ERR si l’index ou la hauteur n’est pas valide ; Sinon, 0.

### <a name="remarks"></a>Notes

La hauteur de la partie de contrôle d’édition (ou de texte statique) de la zone de liste déroulante est définie indépendamment de la hauteur des éléments de liste. Une application doit s’assurer que la hauteur de la partie de contrôle de modification (ou de texte statique) n’est pas inférieure à la hauteur d’un élément de zone de liste particulier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

##  <a name="setlocale"></a>CComboBox :: SetLocale

Définit l’identificateur de paramètres régionaux pour cette zone de liste déroulante.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Paramètres

*nNewLocale*<br/>
Nouvelle valeur de l’identificateur de paramètres régionaux (LCID) à définir pour la zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

Valeur précédente de l’identificateur de paramètres régionaux (LCID) pour cette zone de liste déroulante.

### <a name="remarks"></a>Notes

Si `SetLocale` n’est pas appelé, les paramètres régionaux par défaut sont obtenus à partir du système. Les paramètres régionaux par défaut du système peuvent être modifiés à l’aide de l’application régionale (ou internationale) du panneau de configuration.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

##  <a name="setminvisibleitems"></a>CComboBox :: SetMinVisibleItems

Définit le nombre minimal d’éléments visibles dans la liste déroulante du contrôle de zone de liste déroulante actuelle.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*invisible*|dans Spécifie le nombre minimal d’éléments visibles.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_combobox*, qui est utilisée pour accéder par programmation au contrôle de zone de liste déroulante. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant insère 20 éléments dans la liste déroulante d’un contrôle zone de liste déroulante. Ensuite, il spécifie qu’un minimum de 10 éléments s’affiche lorsqu’un utilisateur appuie sur la flèche déroulante.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="settopindex"></a>CComboBox :: SetTopIndex

Garantit qu’un élément particulier est visible dans la partie de la zone de liste de la zone de liste déroulante.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Spécifie l’index de base zéro de l’élément de zone de liste.

### <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, ou CB_ERR si une erreur se produit.

### <a name="remarks"></a>Notes

Le système fait défiler la zone de liste jusqu’à ce que l’élément spécifié par *nIndex* apparaisse en haut de la zone de liste ou que la plage de défilement maximale ait été atteinte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

##  <a name="showdropdown"></a>CComboBox :: ShowDropDown

Affiche ou masque la zone de liste d’une zone de liste déroulante qui a le style [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ou [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

```
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Paramètres

*bShowIt*<br/>
Spécifie si la zone de liste déroulante doit être affichée ou masquée. La valeur TRUE affiche la zone de liste. La valeur FALSe masque la zone de liste.

### <a name="remarks"></a>Notes

Par défaut, une zone de liste déroulante de ce style affiche la zone de liste.

Cette fonction membre n’a aucun effet sur une zone de liste déroulante créée avec le style [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CComboBox :: GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic, classe](../../mfc/reference/cstatic-class.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)
