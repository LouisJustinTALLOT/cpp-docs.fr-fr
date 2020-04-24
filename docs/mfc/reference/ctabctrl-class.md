---
title: CTabCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
ms.openlocfilehash: 42d4b24222b1760bc418e904881edb2bb0e5a1f4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752307"
---
# <a name="ctabctrl-class"></a>CTabCtrl, classe

Fournit les fonctionnalités du contrôle commun d'onglet Windows.

## <a name="syntax"></a>Syntaxe

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|Construit un objet `CTabCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Calcule la zone d’affichage d’un onglet donné un rectangle de fenêtre, ou calcule le rectangle de fenêtre qui correspondrait à une zone d’affichage donnée.|
|[CTabCtrl::Créer](#create)|Crée un contrôle d’onglet et le `CTabCtrl` fixe à une instance d’objet.|
|[CTabCtrl::CreateEx](#createex)|Crée un contrôle d’onglet avec les styles windows étendus spécifiés et le fixe à une instance d’un `CTabCtrl` objet.|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Supprime tous les éléments d’un contrôle d’onglet.|
|[CTabCtrl::DeleteItem](#deleteitem)|Retire un élément d’un contrôle d’onglet.|
|[CTabCtrl::DeselectAll](#deselectall)|Réinitialise les éléments dans un contrôle d’onglet, effaçant tout ce qui a été pressé.|
|[CTabCtrl::DrawItem](#drawitem)|Dessine un élément spécifié d’un contrôle d’onglet.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Récupère l’onglet avec le point actuel d’un contrôle de l’onglet.|
|[CTabCtrl::GetCurSel](#getcursel)|Détermine l’onglet actuellement sélectionné dans un contrôle d’onglet.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Récupère les styles étendus qui sont actuellement utilisés pour le contrôle de l’onglet.|
|[CTabCtrl::GetImageList](#getimagelist)|Récupère la liste d’images associée à un contrôle de l’onglet.|
|[CTabCtrl::GetItem](#getitem)|Récupère des informations sur un onglet dans un contrôle d’onglet.|
|[CTabCtrl::GetItemCount](#getitemcount)|Récupère le nombre d’onglets dans le contrôle de l’onglet.|
|[CTabCtrl::GetItemRect](#getitemrect)|Récupère le rectangle de délimitation pour un onglet dans un contrôle d’onglet.|
|[CTabCtrl::GetItemState](#getitemstate)|Récupère l’état de l’élément de commande de l’onglet indiqué.|
|[CTabCtrl::GetRowCount](#getrowcount)|Récupère le nombre actuel de rangées d’onglets dans un contrôle d’onglet.|
|[CTabCtrl::GetToolTips](#gettooltips)|Récupère la poignée du contrôle de pointe de l’outil associé à un contrôle de l’onglet.|
|[CTabCtrl::HighlightItem](#highlightitem)|Définit l’état de surbrillance d’un élément d’onglet.|
|[CTabCtrl::HitTest](#hittest)|Détermine quel onglet, le cas échéant, se trouve à une position d’écran spécifiée.|
|[CTabCtrl::InsertItem](#insertitem)|Insère un nouvel onglet dans un contrôle d’onglet.|
|[CTabCtrl::RemoveImage](#removeimage)|Supprime une image de la liste d’images d’un contrôle de l’onglet.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Définit la mise au point vers un onglet spécifié dans un contrôle d’onglet.|
|[CTabCtrl::SetCurSel](#setcursel)|Sélectionne un onglet dans un contrôle d’onglet.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Définit les styles étendus pour un contrôle de l’onglet.|
|[CTabCtrl::SetImageList](#setimagelist)|Assigne une liste d’images à un contrôle d’onglet.|
|[CTabCtrl::SetItem](#setitem)|Définit une partie ou la totalité des attributs d’un onglet.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Définit le nombre d’octets par onglet réservé aux données définies par application dans un contrôle d’onglet.|
|[CTabCtrl::SetItemSize](#setitemsize)|Définit la largeur et la hauteur d’un élément.|
|[CTabCtrl::SetItemState](#setitemstate)|Définit l’état de l’élément de commande de l’onglet indiqué.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Définit la largeur minimale des éléments dans un contrôle d’onglet.|
|[CTabCtrl::SetPadding](#setpadding)|Définit la quantité d’espace (remdding) autour de l’icône de chaque onglet et l’étiquette dans un contrôle d’onglet.|
|[CTabCtrl::SetToolTips](#settooltips)|Attribue un contrôle de pointe d’outil à un contrôle d’onglet.|

## <a name="remarks"></a>Notes

Un « contrôle de l’onglet » est analogue aux diviseurs d’un ordinateur portable ou aux étiquettes d’une classe de fichiers. En utilisant un contrôle tab, une application peut définir plusieurs pages pour la même zone d’une fenêtre ou d’une boîte de dialogue. Chaque page se compose d’un ensemble d’informations ou d’un groupe de contrôles que l’application affiche lorsque l’utilisateur sélectionne l’onglet correspondant. Un type spécial de contrôle d’onglet affiche des onglets qui ressemblent à des boutons. En cliquant sur un bouton, vous devez immédiatement effectuer une commande au lieu d’afficher une page.

Ce contrôle (et `CTabCtrl` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT version 3.51 et plus tard.

Pour plus d’informations sur l’utilisation `CTabCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation de [CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="ctabctrladjustrect"></a><a name="adjustrect"></a>CTabCtrl::AdjustRect

Calcule la zone d’affichage d’un onglet donné un rectangle de fenêtre, ou calcule le rectangle de fenêtre qui correspondrait à une zone d’affichage donnée.

```cpp
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*bLarger (en)*<br/>
Indique quelle opération effectuer. Si ce paramètre est VRAI, *lpRect* spécifie un rectangle d’affichage et reçoit le rectangle de fenêtre correspondant. Si ce paramètre est FALSE, *lpRect* spécifie un rectangle de fenêtre et reçoit le rectangle d’affichage correspondant.

*lpRect*<br/>
Pointeur vers une structure [RECT](/windows/win32/api/windef/ns-windef-rect) qui spécifie le rectangle donné et reçoit le rectangle calculé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

## <a name="ctabctrlcreate"></a><a name="create"></a>CTabCtrl::Créer

Crée un contrôle d’onglet et le `CTabCtrl` fixe à une instance d’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du contrôle de l’onglet. Appliquer toute combinaison de styles de contrôle de [l’onglet](/windows/win32/Controls/tab-control-styles), décrit dans le SDK Windows. Voir **Remarques** pour une liste de styles de fenêtre que vous pouvez également appliquer au contrôle.

*Rect*<br/>
Spécifie la taille et la position du contrôle de l’onglet. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Spécifie la fenêtre parente `CDialog`du contrôle de l’onglet, généralement un . Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de l’onglet.

### <a name="return-value"></a>Valeur de retour

VRAI si l’initialisation de l’objet a été couronnée de succès; autrement FALSE.

### <a name="remarks"></a>Notes

Vous construisez un `CTabCtrl` objet en deux étapes. Tout d’abord, appelez le `Create`constructeur, puis appelez , ce `CTabCtrl` qui crée le contrôle de l’onglet et le fixe à l’objet.

En plus des styles de contrôle de l’onglet, vous pouvez appliquer les styles de fenêtre suivants à un contrôle d’onglet :

- WS_CHILD crée une fenêtre pour enfants qui représente le contrôle de l’onglet. Impossible d’être utilisé avec le style WS_POPUP.

- WS_VISIBLE crée un contrôle de l’onglet qui est initialement visible.

- WS_DISABLED crée une fenêtre qui est initialement désactivée.

- WS_GROUP précise le premier contrôle d’un groupe de contrôles dans lequel l’utilisateur peut passer d’un contrôle à l’autre avec les touches fléchées. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le prochain contrôle avec le style WS_GROUP se termine le groupe de style et commence le groupe suivant (c’est-à-dire, un groupe se termine là où le suivant commence).

- WS_TABSTOP précise l’un des nombreux contrôles par lesquels l’utilisateur peut se déplacer en utilisant la clé TAB. La clé TAB déplace l’utilisateur vers le contrôle suivant spécifié par le style WS_TABSTOP.

Pour créer un contrôle d’onglet avec des styles de fenêtre `Create`étendus, appelez [CTabCtrl::CreateEx](#createex) au lieu de .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

## <a name="ctabctrlcreateex"></a><a name="createex"></a>CTabCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CTabCtrl` et l’associe à l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle (en anglais)*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour une liste de styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

*dwStyle (en)*<br/>
Spécifie le style du contrôle de l’onglet. Appliquer toute combinaison de styles de contrôle de [l’onglet](/windows/win32/Controls/tab-control-styles), décrit dans le SDK Windows. Voir **Remarques** dans [Créer](#create) pour une liste de styles de fenêtre que vous pouvez également appliquer au contrôle.

*Rect*<br/>
Une référence à une structure [RECT](/windows/win32/api/windef/ns-windef-rect) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Nonzero si réussi autrement 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

`CreateEx`crée le contrôle avec les styles Windows étendus spécifiés par *dwExStyle*. Définissez des styles étendus spécifiques à un contrôle à l’aide [de SetExtendedStyle](#setextendedstyle). Par exemple, `CreateEx` utilisez-le pour définir des `SetExtendedStyle` styles tels que WS_EX_CONTEXTHELP, mais utilisez-le pour définir des styles tels que TCS_EX_FLATSEPARATORS. Pour plus d’informations, voir les styles décrits dans [Tab Control Extended Styles](/windows/win32/Controls/tab-control-extended-styles) dans le SDK Windows.

## <a name="ctabctrlctabctrl"></a><a name="ctabctrl"></a>CTabCtrl::CTabCtrl

Construit un objet `CTabCtrl`.

```
CTabCtrl();
```

## <a name="ctabctrldeleteallitems"></a><a name="deleteallitems"></a>CTabCtrl::DeleteAllItems

Supprime tous les éléments d’un contrôle d’onglet.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="ctabctrldeleteitem"></a><a name="deleteitem"></a>CTabCtrl::DeleteItem

Supprime l’élément spécifié d’un contrôle d’onglet.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Valeur basée sur zéro de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

## <a name="ctabctrldeselectall"></a><a name="deselectall"></a>CTabCtrl::DeselectAll

Réinitialise les éléments dans un contrôle d’onglet, effaçant tout ce qui a été pressé.

```cpp
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Paramètres

*fExcludeFocus*<br/>
Indicateur qui spécifie la portée de l’élément désélection. Si ce paramètre est défini à FALSE, tous les boutons de l’onglet seront réinitialisés. S’il est réglé sur TRUE, alors tous les éléments de l’onglet, sauf celui actuellement sélectionné seront réinitialisés.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32, [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), tel que décrit dans le SDK Windows.

## <a name="ctabctrldrawitem"></a><a name="drawitem"></a>CTabCtrl::DrawItem

Appelé par le cadre quand un aspect visuel d’un contrôle d’onglet propriétaire-tirage change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur d’une structure [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) décrivant l’élément à peindre.

### <a name="remarks"></a>Notes

Le `itemAction` membre `DRAWITEMSTRUCT` de la structure définit l’action de dessin qui doit être effectuée.

Par défaut, cette fonction de membre ne fait rien. Remplacer cette fonction de membre pour implémenter le dessin d’un objet de dessin du `CTabCtrl` propriétaire.

L’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction de membre.

## <a name="ctabctrlgetcurfocus"></a><a name="getcurfocus"></a>CTabCtrl::GetCurFocus

Récupère l’index de l’onglet avec la mise au point actuelle.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Valeur de retour

L’indice zéro de l’onglet avec l’accent actuel.

## <a name="ctabctrlgetcursel"></a><a name="getcursel"></a>CTabCtrl::GetCurSel

Récupère l’onglet actuellement sélectionné dans un contrôle d’onglet.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

Index à base zéro de l’onglet sélectionné en cas de succès ou - 1 si aucun onglet n’est sélectionné.

## <a name="ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CTabCtrl::GetExtendedStyle

Récupère les styles étendus qui sont actuellement utilisés pour le contrôle de l’onglet.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Valeur de retour

Représente les styles étendus actuellement utilisés pour le contrôle de l’onglet. Cette valeur est une combinaison de styles étendus de contrôle de [l’onglet,](/windows/win32/Controls/tab-control-extended-styles)comme décrit dans le SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle), tel que décrit dans le SDK Windows.

## <a name="ctabctrlgetimagelist"></a><a name="getimagelist"></a>CTabCtrl::GetImageList

Récupère la liste d’images associée à un contrôle de l’onglet.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, un pointeur à la liste d’image du contrôle de l’onglet; autrement, NULL.

## <a name="ctabctrlgetitem"></a><a name="getitem"></a>CTabCtrl::GetItem

Récupère des informations sur un onglet dans un contrôle d’onglet.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Indice zéro de l’onglet.

*pTabCtrlItem (en)*<br/>
Pointeur vers une structure [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) utilisée pour spécifier les informations à récupérer. Également utilisé pour recevoir des informations sur l’onglet. Cette structure est `InsertItem`utilisée `GetItem`avec `SetItem` les fonctions , et membres.

### <a name="return-value"></a>Valeur de retour

Rendements VRAI en cas de succès; FALSE autrement.

### <a name="remarks"></a>Notes

Lorsque le message est `mask` envoyé, le membre précise quels attributs pour revenir. Si `mask` le membre précise la valeur TCIF_TEXT, `pszText` le membre doit contenir l’adresse du `cchTextMax` tampon qui reçoit le texte de l’élément et le membre doit spécifier la taille du tampon.

- `mask`

   Valeur spécifiant les membres de la `TCITEM` structure à récupérer ou à définir. Ce membre peut être nul ou une combinaison des valeurs suivantes :

  - TCIF_TEXT Le `pszText` membre est valide.

  - TCIF_IMAGE Le `iImage` membre est valide.

  - TCIF_PARAM Le `lParam` membre est valide.

  - TCIF_RTLREADING Le texte est `pszText` affiché à l’aide de l’ordre de lecture de droite à gauche sur les systèmes hébreu ou arabe.

  - TCIF_STATE Le `dwState` membre est valide.

- `pszText`

   Pointeur vers une chaîne non terminée contenant le texte de l’onglet si la structure contient des informations sur un onglet. Si la structure reçoit des informations, ce membre précise l’adresse du tampon qui reçoit le texte de l’onglet.

- `cchTextMax`

   Taille de la mémoire `pszText`tampon pointée par . Ce membre est ignoré si la structure ne reçoit pas d’information.

- `iImage`Indexez dans la liste d’image du contrôle de l’onglet, ou - 1 s’il n’y a pas d’image pour l’onglet.

- `lParam`

   Données définies par l’application associées à l’onglet. S’il y a plus de quatre octets de données définies par onglet, `TCITEM` une application doit définir une structure et l’utiliser au lieu de la structure. Le premier membre de la structure définie par l’application doit être une structure [TCITEMHEADER.](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw) La `TCITEMHEADER` structure est `TCITEM` identique à la `lParam` structure, mais sans le membre. La différence entre la taille de votre `TCITEMHEADER` structure et la taille de la structure devrait égaler le nombre d’octets supplémentaires par onglet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

## <a name="ctabctrlgetitemcount"></a><a name="getitemcount"></a>CTabCtrl::GetItemCount

Récupère le nombre d’onglets dans le contrôle de l’onglet.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le contrôle de l’onglet.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertySheet:GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemrect"></a><a name="getitemrect"></a>CTabCtrl::GetItemRect

Récupère le rectangle de délimitation pour l’onglet spécifié dans un contrôle d’onglet.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Indice à base zéro de l’élément de l’onglet.

*lpRect*<br/>
Pointeur vers une structure [RECT](/windows/win32/api/windef/ns-windef-rect) qui reçoit le rectangle de délimitation de l’onglet. Ces coordonnées utilisent le mode de cartographie actuel du viewport.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertySheet:GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemstate"></a><a name="getitemstate"></a>CTabCtrl::GetItemState

Récupère l’état de l’élément de contrôle de l’onglet identifié par *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Le numéro d’index à base nulle de l’élément pour lequel récupérer les informations d’état.

*dwMask*<br/>
Masque spécifiant lequel des drapeaux d’état de l’article à retourner. Pour une liste de valeurs, voir le membre masque de la structure [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) tel que décrit dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Une référence à une valeur DWORD recevant les informations de l’État. Il peut s'agir de l'une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|L’élément de commande de l’onglet est sélectionné.|
|TCIS_HIGHLIGHTED|L’élément de commande de l’onglet est mis en surbrillance, et l’onglet et le texte sont dessinés à l’aide de la couleur actuelle de mise en évidence. Lors de l’utilisation de la couleur de surbrillance, ce sera une véritable interpolation, pas une couleur tergiversée.|

### <a name="remarks"></a>Notes

L’état d’un élément `dwState` est `TCITEM` spécifié par le membre de la structure.

## <a name="ctabctrlgetrowcount"></a><a name="getrowcount"></a>CTabCtrl::GetRowCount

Récupère le nombre actuel de lignes dans un contrôle d’onglet.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de rangées d’onglets dans le contrôle de l’onglet.

### <a name="remarks"></a>Notes

Seuls les commandes d’onglets qui ont le style TCS_MULTILINE peuvent avoir plusieurs rangées d’onglets.

## <a name="ctabctrlgettooltips"></a><a name="gettooltips"></a>CTabCtrl::GetToolTips

Récupère la poignée du contrôle de pointe de l’outil associé à un contrôle de l’onglet.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valeur de retour

Poignée du contrôle de l’extrémité d’outil en cas de succès ; autrement NULL.

### <a name="remarks"></a>Notes

Un contrôle d’onglet crée un contrôle de pointe d’outil s’il a le style TCS_TOOLTIPS. Vous pouvez également affecter un contrôle de pointe `SetToolTips` d’outil à un contrôle d’onglet en utilisant la fonction membre.

## <a name="ctabctrlhighlightitem"></a><a name="highlightitem"></a>CTabCtrl::HighlightItem

Définit l’état de surbrillance d’un élément d’onglet.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Paramètres

*idItem (en)*<br/>
Index à base zéro d’un élément de contrôle de l’onglet.

*fHighlight*<br/>
Valeur spécifiant l’état de mise en évidence à définir. Si cette valeur est VRAIE, l’onglet est mis en surbrillance; si FALSE, l’onglet est réglé à son état par défaut.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le message Win32 [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem), tel que décrit dans le SDK Windows.

## <a name="ctabctrlhittest"></a><a name="hittest"></a>CTabCtrl::HitTest

Détermine quel onglet, le cas échéant, se trouve à la position d’écran spécifiée.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Paramètres

*pHitTestInfo (en anglais)*<br/>
Pointeur vers une structure [TCHITTESTINFO,](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) tel que décrit dans le SDK Windows, qui spécifie la position de l’écran à tester.

### <a name="return-value"></a>Valeur de retour

Retourne l’index à base zéro de l’onglet ou - 1 si aucun onglet n’est à la position spécifiée.

## <a name="ctabctrlinsertitem"></a><a name="insertitem"></a>CTabCtrl::InsertItem

Insère un nouvel onglet dans un contrôle d’onglet existant.

```
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam,
    DWORD dwState,
    DWORD dwStateMask);
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Indice zéro du nouvel onglet.

*pTabCtrlItem (en)*<br/>
Pointeur vers une structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) qui spécifie les attributs de l’onglet.

*lpszItem (en)*<br/>
Adresse d’une chaîne non terminée qui contient le texte de l’onglet.

*nImage (en)*<br/>
L’index zéro d’une image à insérer à partir d’une liste d’images.

*nMask (nMask)*<br/>
Précise quelle `TCITEM` structure attribue à définir. Peut être nul ou une combinaison des valeurs suivantes :

- TCIF_TEXT Le `pszText` membre est valide.

- TCIF_IMAGE Le `iImage` membre est valide.

- TCIF_PARAM Le membre *lParam* est valide.

- TCIF_RTLREADING Le texte est `pszText` affiché à l’aide de l’ordre de lecture de droite à gauche sur les systèmes hébreu ou arabe.

- TCIF_STATE Le membre *dwState* est valide.

*lParam*<br/>
Données définies par l’application associées à l’onglet.

*dwState (en)*<br/>
Spécifie les valeurs des états de l’article. Pour plus d’informations, voir [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) dans windows SDK.

*dwStateMask*<br/>
Précise quels états doivent être définis. Pour plus d’informations, voir [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) dans windows SDK.

### <a name="return-value"></a>Valeur de retour

Indice zéro du nouvel onglet en cas de succès; autrement - 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

## <a name="ctabctrlremoveimage"></a><a name="removeimage"></a>CTabCtrl::RemoveImage

Supprime l’image spécifiée de la liste d’images d’un contrôle de l’onglet.

```cpp
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Paramètres

*nImage (en)*<br/>
Index zéro de l’image à supprimer.

### <a name="remarks"></a>Notes

Le contrôle de l’onglet met à jour l’index d’image de chaque onglet afin que chaque onglet reste associé à la même image.

## <a name="ctabctrlsetcurfocus"></a><a name="setcurfocus"></a>CTabCtrl::SetCurFocus

Définit la mise au point vers un onglet spécifié dans un contrôle d’onglet.

```cpp
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Spécifie l’index de l’onglet qui obtient la mise au point.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus), tel que décrit dans le SDK Windows.

## <a name="ctabctrlsetcursel"></a><a name="setcursel"></a>CTabCtrl::SetCurSel

Sélectionne un onglet dans un contrôle d’onglet.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
L’index zéro de l’élément à sélectionner.

### <a name="return-value"></a>Valeur de retour

Indice zéro de l’onglet précédemment sélectionné en cas de succès, autrement - 1.

### <a name="remarks"></a>Notes

Un contrôle d’onglet n’envoie pas de message de notification TCN_SELCHANGING ou TCN_SELCHANGE lorsqu’un onglet est sélectionné à l’aide de cette fonction. Ces notifications sont envoyées, à l’aide de WM_NOTIFY, lorsque l’utilisateur clique ou utilise le clavier pour changer les onglets.

## <a name="ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CTabCtrl::SetExtendedStyle

Définit les styles étendus pour un contrôle de l’onglet.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Paramètres

*dwNewStyle (en)*<br/>
Valeur spécifiant une combinaison de styles étendus de contrôle de l’onglet.

*dwExMask (en anglais)*<br/>
Une valeur DWORD qui indique quels styles dans *dwNewStyle* doivent être affectés. Seuls les styles étendus dans *dwExMask* seront changés. Tous les autres styles seront maintenus tels qu’ils sont. Si ce paramètre est nul, alors tous les styles de *dwNewStyle* seront affectés.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui contient les styles étendus de contrôle de [l’onglet](/windows/win32/Controls/tab-control-extended-styles)précédent, comme décrit dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Cette fonction de membre implémente le comportement du message Win32 [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle), tel que décrit dans le SDK Windows.

## <a name="ctabctrlsetimagelist"></a><a name="setimagelist"></a>CTabCtrl::SetImageList

Assigne une liste d’images à un contrôle d’onglet.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList (en)*<br/>
Pointeur vers la liste d’images à attribuer au contrôle de l’onglet.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la liste d’images précédente ou NULL s’il n’y a pas de liste d’images précédente.

## <a name="ctabctrlsetitem"></a><a name="setitem"></a>CTabCtrl::SetItem

Définit une partie ou la totalité des attributs d’un onglet.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Indice zéro de l’élément.

*pTabCtrlItem (en)*<br/>
Pointeur vers une structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) qui contient les attributs du nouvel élément. Le `mask` membre précise quels attributs à définir. Si `mask` le membre précise la valeur TCIF_TEXT, le `pszText` membre est l’adresse `cchTextMax` d’une chaîne non résiliée et le membre est ignoré.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [GetItem](#getitem).

## <a name="ctabctrlsetitemextra"></a><a name="setitemextra"></a>CTabCtrl::SetItemExtra

Définit le nombre d’octets par onglet réservé aux données définies par application dans un contrôle d’onglet.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
Le nombre d’octets supplémentaires à définir.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra), tel que décrit dans le SDK Windows.

## <a name="ctabctrlsetitemsize"></a><a name="setitemsize"></a>CTabCtrl::SetItemSize

Définit la largeur et la hauteur des éléments du contrôle des tabulations.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Nouvelles largeur et hauteur, en pixels, des éléments du contrôle des tabulations.

### <a name="return-value"></a>Valeur de retour

Retourne les anciennes largeur et hauteur des éléments du contrôle des tabulations.

## <a name="ctabctrlsetitemstate"></a><a name="setitemstate"></a>CTabCtrl::SetItemState

Définit l’état de l’élément de contrôle de l’onglet identifié par *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
Le numéro d’index zéro de l’élément pour lequel définir les informations d’état.

*dwMask*<br/>
Masque spécifiant lequel des drapeaux d’état de l’élément à définir. Pour une liste de valeurs, voir le membre masque de la structure [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) tel que décrit dans le SDK Windows.

*dwState (en)*<br/>
Une référence à une valeur DWORD contenant les informations de l’État. Il peut s'agir de l'une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|L’élément de commande de l’onglet est sélectionné.|
|TCIS_HIGHLIGHTED|L’élément de commande de l’onglet est mis en surbrillance, et l’onglet et le texte sont dessinés à l’aide de la couleur actuelle de mise en évidence. Lors de l’utilisation de la couleur de surbrillance, ce sera une véritable interpolation, pas une couleur tergiversée.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a>CTabCtrl::SetMinTabWidth

Définit la largeur minimale des éléments dans un contrôle d’onglet.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Paramètres

*Cx*<br/>
Largeur minimale à régler pour un élément de commande de l’onglet. Si ce paramètre est réglé à -1, le contrôle utilisera la largeur de l’onglet par défaut.

### <a name="return-value"></a>Valeur de retour

La largeur minimale précédente de l’onglet.

### <a name="return-value"></a>Valeur de retour

Cette fonction de membre implémente le comportement du message Win32 [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth), tel que décrit dans le SDK Windows.

## <a name="ctabctrlsetpadding"></a><a name="setpadding"></a>CTabCtrl::SetPadding

Définit la quantité d’espace (remdding) autour de l’icône de chaque onglet et l’étiquette dans un contrôle d’onglet.

```cpp
void SetPadding(CSize size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Définit la quantité d’espace (remdding) autour de l’icône de chaque onglet et l’étiquette dans un contrôle d’onglet.

## <a name="ctabctrlsettooltips"></a><a name="settooltips"></a>CTabCtrl::SetToolTips

Attribue un contrôle de pointe d’outil à un contrôle d’onglet.

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Paramètres

*pWndTip*<br/>
Poignée du contrôle de l’extrémité de l’outil.

### <a name="remarks"></a>Notes

Vous pouvez obtenir le contrôle de pointe d’outil `GetToolTips`associé à un contrôle d’onglet en faisant un appel à .

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertySheet:GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)
