---
title: CTabCtrl (classe)
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
ms.openlocfilehash: a0ca4cbad48c420250fe39e131de5504b1ae70f3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420924"
---
# <a name="ctabctrl-class"></a>CTabCtrl (classe)

Fournit les fonctionnalités du contrôle commun d'onglet Windows.

## <a name="syntax"></a>Syntaxe

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CTabCtrl :: CTabCtrl](#ctabctrl)|Construit un objet `CTabCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CTabCtrl :: AdjustRect](#adjustrect)|Calcule la zone d’affichage d’un contrôle onglet en fonction d’un rectangle de fenêtre, ou calcule le rectangle de la fenêtre qui correspondrait à une zone d’affichage donnée.|
|[CTabCtrl :: Create](#create)|Crée un contrôle onglet et l’attache à une instance d’un objet `CTabCtrl`.|
|[CTabCtrl :: CreateEx](#createex)|Crée un contrôle onglet avec les styles étendus Windows spécifiés et l’attache à une instance d’un objet `CTabCtrl`.|
|[CTabCtrl ::D eleteAllItems](#deleteallitems)|Supprime tous les éléments d’un contrôle onglet.|
|[CTabCtrl ::D eleteItem](#deleteitem)|Supprime un élément d’un contrôle onglet.|
|[CTabCtrl ::D eselectAll](#deselectall)|Réinitialise des éléments dans un contrôle onglet, en effaçant tous ceux qui ont été enfoncés.|
|[CTabCtrl ::D rawItem](#drawitem)|Dessine un élément spécifié d’un contrôle onglet.|
|[CTabCtrl :: GetCurFocus](#getcurfocus)|Récupère l’onglet avec le focus actuel d’un contrôle onglet.|
|[CTabCtrl :: GetCurSel](#getcursel)|Détermine l’onglet actuellement sélectionné dans un contrôle onglet.|
|[CTabCtrl :: GetExtendedStyle](#getextendedstyle)|Récupère les styles étendus en cours d’utilisation pour le contrôle Tab.|
|[CTabCtrl :: GetImageList](#getimagelist)|Récupère la liste d’images associée à un contrôle onglet.|
|[CTabCtrl :: GetItem](#getitem)|Récupère des informations sur un onglet dans un contrôle onglet.|
|[CTabCtrl :: GetItemCount](#getitemcount)|Récupère le nombre d’onglets dans le contrôle onglet.|
|[CTabCtrl :: GetItemRect](#getitemrect)|Récupère le rectangle englobant d’un onglet dans un contrôle onglet.|
|[CTabCtrl :: GetItemState](#getitemstate)|Récupère l’état de l’élément de contrôle onglet indiqué.|
|[CTabCtrl :: GetRowCount](#getrowcount)|Récupère le nombre actuel de lignes d’onglets dans un contrôle onglet.|
|[CTabCtrl :: GetToolTips](#gettooltips)|Récupère le handle du contrôle d’info-bulle associé à un contrôle onglet.|
|[CTabCtrl :: HighlightItem](#highlightitem)|Définit l’état de surbrillance d’un élément d’onglet.|
|[CTabCtrl :: HitTest](#hittest)|Détermine l’onglet, le cas échéant, à la position d’écran spécifiée.|
|[CTabCtrl :: InsertItem](#insertitem)|Insère un nouvel onglet dans un contrôle onglet.|
|[CTabCtrl :: RemoveImage](#removeimage)|Supprime une image de la liste d’images d’un contrôle onglet.|
|[CTabCtrl :: SetCurFocus](#setcurfocus)|Définit le focus sur un onglet spécifié dans un contrôle onglet.|
|[CTabCtrl :: SetCurSel](#setcursel)|Sélectionne un onglet dans un contrôle onglet.|
|[CTabCtrl :: SetExtendedStyle](#setextendedstyle)|Définit les styles étendus pour un contrôle onglet.|
|[CTabCtrl :: SetImageList](#setimagelist)|Assigne une liste d’images à un contrôle onglet.|
|[CTabCtrl :: SetItem](#setitem)|Définit tout ou partie des attributs d’un onglet.|
|[CTabCtrl :: SetItemExtra](#setitemextra)|Définit le nombre d’octets par onglet réservé pour les données définies par l’application dans un contrôle onglet.|
|[CTabCtrl :: SetItemSize](#setitemsize)|Définit la largeur et la hauteur d’un élément.|
|[CTabCtrl :: SetItemState](#setitemstate)|Définit l’état de l’élément de contrôle onglet indiqué.|
|[CTabCtrl :: SetMinTabWidth](#setmintabwidth)|Définit la largeur minimale des éléments dans un contrôle onglet.|
|[CTabCtrl :: SetPadding](#setpadding)|Définit la quantité d’espace (remplissage) autour de l’icône et de l’étiquette de chaque onglet dans un contrôle onglet.|
|[CTabCtrl :: SetToolTips](#settooltips)|Assigne un contrôle d’info-bulle à un contrôle onglet.|

## <a name="remarks"></a>Notes

Un contrôle d’onglet est analogue aux séparateurs d’un bloc-notes ou aux étiquettes d’un fichier CAB. En utilisant un contrôle tab, une application peut définir plusieurs pages pour la même zone d’une fenêtre ou d’une boîte de dialogue. Chaque page se compose d’un ensemble d’informations ou d’un groupe de contrôles que l’application affiche lorsque l’utilisateur sélectionne l’onglet correspondant. Un type spécial de contrôle onglet affiche des onglets qui ressemblent à des boutons. Le fait de cliquer sur un bouton doit immédiatement exécuter une commande au lieu d’afficher une page.

Ce contrôle (et par conséquent la classe `CTabCtrl`) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT version 3,51 et versions ultérieures.

Pour plus d’informations sur l’utilisation de `CTabCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="adjustrect"></a>CTabCtrl :: AdjustRect

Calcule la zone d’affichage d’un contrôle onglet en fonction d’un rectangle de fenêtre, ou calcule le rectangle de la fenêtre qui correspondrait à une zone d’affichage donnée.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*bLarger*<br/>
Indique l’opération à effectuer. Si ce paramètre a la valeur TRUE, *lpRect* spécifie un rectangle d’affichage et reçoit le rectangle de fenêtre correspondant. Si ce paramètre a la valeur FALSe, *lpRect* spécifie un rectangle de fenêtre et reçoit le rectangle d’affichage correspondant.

*lpRect*<br/>
Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui spécifie le rectangle donné et reçoit le rectangle calculé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>CTabCtrl :: Create

Crée un contrôle onglet et l’attache à une instance d’un objet `CTabCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle onglet. Appliquez n’importe quelle combinaison de [styles de contrôle onglet](/windows/win32/Controls/tab-control-styles), décrite dans la SDK Windows. Consultez la **section Notes** pour obtenir la liste des styles de fenêtre que vous pouvez également appliquer au contrôle.

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle onglet. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle onglet, généralement une `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle onglet.

### <a name="return-value"></a>Valeur de retour

TRUE si l’initialisation de l’objet a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Vous construisez un objet `CTabCtrl` en deux étapes. Tout d’abord, appelez le constructeur, puis appelez `Create`, qui crée le contrôle onglet et l’attache à l’objet `CTabCtrl`.

Outre les styles de contrôle d’onglet, vous pouvez appliquer les styles de fenêtre suivants à un contrôle onglet :

- WS_CHILD crée une fenêtre enfant qui représente le contrôle onglet. Ne peut pas être utilisé avec le style WS_POPUP.

- WS_VISIBLE crée un contrôle onglet qui est initialement visible.

- WS_DISABLED crée une fenêtre qui est initialement désactivée.

- WS_GROUP spécifie le premier contrôle d’un groupe de contrôles dans lequel l’utilisateur peut passer d’un contrôle à l’autre à l’aide des touches de direction. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le contrôle suivant avec le style de WS_GROUP met fin au groupe de styles et démarre le groupe suivant (autrement dit, un groupe se termine à l’emplacement où commence le prochain).

- WS_TABSTOP spécifie un nombre quelconque de contrôles par le biais desquels l’utilisateur peut se déplacer à l’aide de la touche TAB. La touche TAB déplace l’utilisateur vers le contrôle suivant spécifié par le style de WS_TABSTOP.

Pour créer un contrôle onglet avec des styles de fenêtre étendus, appelez [CTabCtrl :: CreateEx](#createex) au lieu de `Create`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>CTabCtrl :: CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à l’objet `CTabCtrl`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle onglet. Appliquez n’importe quelle combinaison de [styles de contrôle onglet](/windows/win32/Controls/tab-control-styles), décrite dans la SDK Windows. Consultez la **section Notes** dans [créer](#create) pour obtenir la liste des styles de fenêtre que vous pouvez également appliquer au contrôle.

*rectangulaire*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préversion de style étendu Windows **WS_EX_** .

`CreateEx` crée le contrôle avec les styles Windows étendus spécifiés par *dwExStyle*. Définir des styles étendus spécifiques à un contrôle à l’aide de [SetExtendedStyle](#setextendedstyle). Par exemple, utilisez `CreateEx` pour définir de tels styles comme WS_EX_CONTEXTHELP, mais utilisez `SetExtendedStyle` pour définir des styles de ce type comme TCS_EX_FLATSEPARATORS. Pour plus d’informations, consultez les styles décrits dans [contrôler les styles étendus](/windows/win32/Controls/tab-control-extended-styles) dans le SDK Windows.

##  <a name="ctabctrl"></a>CTabCtrl :: CTabCtrl

Construit un objet `CTabCtrl`.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>CTabCtrl ::D eleteAllItems

Supprime tous les éléments d’un contrôle onglet.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="deleteitem"></a>CTabCtrl ::D eleteItem

Supprime l’élément spécifié d’un contrôle onglet.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Valeur de base zéro de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>CTabCtrl ::D eselectAll

Réinitialise des éléments dans un contrôle onglet, en effaçant tous ceux qui ont été enfoncés.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Paramètres

*fExcludeFocus*<br/>
Indicateur qui spécifie la portée de la désélection de l’élément. Si ce paramètre est défini sur FALSe, tous les boutons d’onglet seront réinitialisés. S’il est défini sur TRUE, tous les éléments d’onglet, à l’exception de celui qui est actuellement sélectionné, sont réinitialisés.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32, [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), comme décrit dans le SDK Windows.

##  <a name="drawitem"></a>CTabCtrl ::D rawItem

Appelée par l’infrastructure quand un aspect visuel d’un contrôle d’onglet owner-draw change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) décrivant l’élément à peindre.

### <a name="remarks"></a>Notes

Le membre `itemAction` de la structure `DRAWITEMSTRUCT` définit l’action de dessin à effectuer.

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre pour implémenter le dessin pour un objet `CTabCtrl` owner-draw.

L’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction membre.

##  <a name="getcurfocus"></a>CTabCtrl :: GetCurFocus

Récupère l’index de l’onglet avec le focus actuel.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’onglet avec le focus actuel.

##  <a name="getcursel"></a>CTabCtrl :: GetCurSel

Récupère l’onglet actuellement sélectionné dans un contrôle onglet.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’onglet sélectionné en cas de réussite ou-1 si aucun onglet n’est sélectionné.

##  <a name="getextendedstyle"></a>CTabCtrl :: GetExtendedStyle

Récupère les styles étendus en cours d’utilisation pour le contrôle Tab.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Valeur de retour

Représente les styles étendus en cours d’utilisation pour le contrôle onglet. Cette valeur est une combinaison de [styles étendus de contrôle onglet](/windows/win32/Controls/tab-control-extended-styles), comme décrit dans la SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)de message Win32, comme décrit dans le SDK Windows.

##  <a name="getimagelist"></a>CTabCtrl :: GetImageList

Récupère la liste d’images associée à un contrôle onglet.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, pointeur vers la liste d’images du contrôle onglet ; Sinon, NULL.

##  <a name="getitem"></a>CTabCtrl :: GetItem

Récupère des informations sur un onglet dans un contrôle onglet.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro de l’onglet.

*pTabCtrlItem*<br/>
Pointeur vers une structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , utilisé pour spécifier les informations à récupérer. Permet également de recevoir des informations sur l’onglet. Cette structure est utilisée avec les fonctions membres `InsertItem`, `GetItem`et `SetItem`.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Lorsque le message est envoyé, le membre `mask` spécifie les attributs à retourner. Si le membre de `mask` spécifie la valeur de TCIF_TEXT, le membre de `pszText` doit contenir l’adresse de la mémoire tampon qui reçoit le texte de l’élément et le membre `cchTextMax` doit spécifier la taille de la mémoire tampon.

- `mask`

   Valeur spécifiant les membres de structure `TCITEM` à récupérer ou à définir. Ce membre peut être zéro ou une combinaison des valeurs suivantes :

   - TCIF_TEXT le membre `pszText` est valide.

   - TCIF_IMAGE le membre `iImage` est valide.

   - TCIF_PARAM le membre `lParam` est valide.

   - TCIF_RTLREADING le texte de `pszText` s’affiche à l’aide de l’ordre de lecture de droite à gauche sur les systèmes Hébreux ou arabes.

   - TCIF_STATE le membre `dwState` est valide.

- `pszText`

   Pointeur vers une chaîne se terminant par un caractère null qui contient le texte de l’onglet si la structure contient des informations sur un onglet. Si la structure reçoit des informations, ce membre spécifie l’adresse de la mémoire tampon qui reçoit le texte de l’onglet.

- `cchTextMax`

   Taille de la mémoire tampon vers laquelle pointe `pszText`. Ce membre est ignoré si la structure ne reçoit pas d’informations.

- `iImage` index dans la liste d’images du contrôle onglet, ou-1 s’il n’y a aucune image pour l’onglet.

- `lParam`

   Données définies par l’application associées à l’onglet. S’il y a plus de quatre octets de données définies par l’application par onglet, une application doit définir une structure et l’utiliser à la place de la structure `TCITEM`. Le premier membre de la structure définie par l’application doit être une structure [TCITEMHEADER](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw). La structure `TCITEMHEADER` est identique à la structure `TCITEM`, mais sans le membre `lParam`. La différence entre la taille de votre structure et la taille de la structure de `TCITEMHEADER` doit être égale au nombre d’octets supplémentaires par tabulation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>CTabCtrl :: GetItemCount

Récupère le nombre d’onglets dans le contrôle onglet.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le contrôle onglet.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet :: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>CTabCtrl :: GetItemRect

Récupère le rectangle englobant pour l’onglet spécifié dans un contrôle onglet.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro de l’élément d’onglet.

*lpRect*<br/>
Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui reçoit le rectangle englobant de l’onglet. Ces coordonnées utilisent le mode de mappage actuel de la fenêtre d’affichage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet :: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>CTabCtrl :: GetItemState

Récupère l’état de l’élément de contrôle d’onglet identifié par *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Numéro d’index de base zéro de l’élément pour lequel les informations d’État doivent être récupérées.

*dwMask*<br/>
Masque spécifiant les indicateurs d’état de l’élément à retourner. Pour obtenir la liste des valeurs, consultez le membre mask de la structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , comme décrit dans la SDK Windows.

### <a name="return-value"></a>Valeur de retour

Référence à une valeur DWORD recevant les informations d’État. Il peut s'agir de l'une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|L’élément de contrôle onglet est sélectionné.|
|TCIS_HIGHLIGHTED|L’élément de contrôle d’onglet est mis en surbrillance, et l’onglet et le texte sont dessinés à l’aide de la couleur de surbrillance actuelle. Lorsque vous utilisez la couleur de surbrillance, il s’agit d’une véritable interpolation, et non d’une couleur dépendante.|

### <a name="remarks"></a>Notes

L’état d’un élément est spécifié par le membre `dwState` de la structure `TCITEM`.

##  <a name="getrowcount"></a>CTabCtrl :: GetRowCount

Récupère le nombre actuel de lignes dans un contrôle onglet.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de lignes d’onglets dans le contrôle onglet.

### <a name="remarks"></a>Notes

Seuls les contrôles onglet avec le style TCS_MULTILINE peuvent avoir plusieurs lignes d’onglets.

##  <a name="gettooltips"></a>CTabCtrl :: GetToolTips

Récupère le handle du contrôle d’info-bulle associé à un contrôle onglet.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valeur de retour

Handle du contrôle d’info-bulle en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Un contrôle onglet crée un contrôle d’info-bulle s’il a le style TCS_TOOLTIPS. Vous pouvez également assigner un contrôle d’info-bulle à un contrôle onglet à l’aide de la fonction membre `SetToolTips`.

##  <a name="highlightitem"></a>CTabCtrl :: HighlightItem

Définit l’état de surbrillance d’un élément d’onglet.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Paramètres

*idItem*<br/>
Index de base zéro d’un élément de contrôle d’onglet.

*fHighlight*<br/>
Valeur spécifiant l’état de mise en surbrillance à définir. Si cette valeur est TRUE, l’onglet est mis en surbrillance ; Si la valeur est FALSe, l’onglet est défini sur son état par défaut.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction membre implémente la [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem)de message Win32, comme décrit dans le SDK Windows.

##  <a name="hittest"></a>CTabCtrl :: HitTest

Détermine l’onglet, le cas échéant, à la position d’écran spécifiée.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Paramètres

*pHitTestInfo*<br/>
Pointeur vers une structure [TCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) , comme décrit dans le SDK Windows, qui spécifie la position à l’écran à tester.

### <a name="return-value"></a>Valeur de retour

Retourne l’index de base zéro de l’onglet ou-1 si aucun onglet n’est à la position spécifiée.

##  <a name="insertitem"></a>CTabCtrl :: InsertItem

Insère un nouvel onglet dans un contrôle onglet existant.

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

*nItem*<br/>
Index de base zéro du nouvel onglet.

*pTabCtrlItem*<br/>
Pointeur vers une structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) qui spécifie les attributs de l’onglet.

*lpszItem*<br/>
Adresse d’une chaîne terminée par le caractère null qui contient le texte de l’onglet.

*nImage*<br/>
Index de base zéro d’une image à insérer à partir d’une liste d’images.

*nMask*<br/>
Spécifie les attributs de structure de `TCITEM` à définir. Il peut s’agir de zéro ou d’une combinaison des valeurs suivantes :

- TCIF_TEXT le membre `pszText` est valide.

- TCIF_IMAGE le membre `iImage` est valide.

- TCIF_PARAM le membre *lParam* est valide.

- TCIF_RTLREADING le texte de `pszText` s’affiche à l’aide de l’ordre de lecture de droite à gauche sur les systèmes Hébreux ou arabes.

- TCIF_STATE le membre *dwState* est valide.

*lParam*<br/>
Données définies par l’application associées à l’onglet.

*dwState*<br/>
Spécifie des valeurs pour les États de l’élément. Pour plus d’informations, consultez [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) dans le SDK Windows.

*dwStateMask*<br/>
Spécifie les États à définir. Pour plus d’informations, consultez [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Index de base zéro du nouvel onglet en cas de réussite ; sinon-1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>CTabCtrl :: RemoveImage

Supprime l’image spécifiée de la liste d’images d’un contrôle onglet.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image à supprimer.

### <a name="remarks"></a>Notes

Le contrôle onglet met à jour l’index d’image de chaque onglet afin que chaque onglet reste associé à la même image.

##  <a name="setcurfocus"></a>CTabCtrl :: SetCurFocus

Définit le focus sur un onglet spécifié dans un contrôle onglet.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Spécifie l’index de l’onglet qui obtient le focus.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus)de message Win32, comme décrit dans le SDK Windows.

##  <a name="setcursel"></a>CTabCtrl :: SetCurSel

Sélectionne un onglet dans un contrôle onglet.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro de l’élément à sélectionner.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’onglet précédemment sélectionné en cas de réussite, sinon-1.

### <a name="remarks"></a>Notes

Un contrôle onglet n’envoie pas de message de notification TCN_SELCHANGING ou TCN_SELCHANGE lorsqu’un onglet est sélectionné à l’aide de cette fonction. Ces notifications sont envoyées à l’aide de WM_NOTIFY, quand l’utilisateur clique ou utilise le clavier pour modifier les onglets.

##  <a name="setextendedstyle"></a>CTabCtrl :: SetExtendedStyle

Définit les styles étendus pour un contrôle onglet.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Paramètres

*dwNewStyle*<br/>
Valeur spécifiant une combinaison de styles étendus de contrôles onglet.

*dwExMask*<br/>
Valeur DWORD qui indique les styles de *dwNewStyle* à affecter. Seuls les styles étendus dans *dwExMask* seront modifiés. Tous les autres styles seront conservés tels quels. Si ce paramètre est égal à zéro, tous les styles dans *dwNewStyle* seront affectés.

### <a name="return-value"></a>Valeur de retour

Valeur DWORD qui contient les [styles étendus du contrôle onglet](/windows/win32/Controls/tab-control-extended-styles)précédent, comme décrit dans la SDK Windows.

### <a name="return-value"></a>Valeur de retour

Cette fonction membre implémente le comportement de la [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)de message Win32, comme décrit dans le SDK Windows.

##  <a name="setimagelist"></a>CTabCtrl :: SetImageList

Assigne une liste d’images à un contrôle onglet.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList*<br/>
Pointeur vers la liste d’images à assigner au contrôle onglet.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la liste d’images précédente ou NULL s’il n’existe aucune liste d’images précédente.

##  <a name="setitem"></a>CTabCtrl :: SetItem

Définit tout ou partie des attributs d’un onglet.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro de l’élément.

*pTabCtrlItem*<br/>
Pointeur vers une structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) qui contient les nouveaux attributs d’élément. Le membre `mask` spécifie les attributs à définir. Si le membre de `mask` spécifie la valeur TCIF_TEXT, le membre `pszText` est l’adresse d’une chaîne terminée par le caractère null et le membre `cchTextMax` est ignoré.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [GetItem](#getitem).

##  <a name="setitemextra"></a>CTabCtrl :: SetItemExtra

Définit le nombre d’octets par onglet réservé pour les données définies par l’application dans un contrôle onglet.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre d’octets supplémentaires à définir.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)de message Win32, comme décrit dans le SDK Windows.

##  <a name="setitemsize"></a>CTabCtrl :: SetItemSize

Définit la largeur et la hauteur des éléments du contrôle des tabulations.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Nouvelles largeur et hauteur, en pixels, des éléments du contrôle des tabulations.

### <a name="return-value"></a>Valeur de retour

Retourne les anciennes largeur et hauteur des éléments du contrôle des tabulations.

##  <a name="setitemstate"></a>CTabCtrl :: SetItemState

Définit l’état de l’élément de contrôle d’onglet identifié par *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Numéro d’index de base zéro de l’élément pour lequel les informations d’État doivent être définies.

*dwMask*<br/>
Masque spécifiant les indicateurs d’état de l’élément à définir. Pour obtenir la liste des valeurs, consultez le membre mask de la structure [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , comme décrit dans la SDK Windows.

*dwState*<br/>
Référence à une valeur DWORD contenant les informations d’État. Il peut s'agir de l'une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|L’élément de contrôle onglet est sélectionné.|
|TCIS_HIGHLIGHTED|L’élément de contrôle d’onglet est mis en surbrillance, et l’onglet et le texte sont dessinés à l’aide de la couleur de surbrillance actuelle. Lorsque vous utilisez la couleur de surbrillance, il s’agit d’une véritable interpolation, et non d’une couleur dépendante.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="setmintabwidth"></a>CTabCtrl :: SetMinTabWidth

Définit la largeur minimale des éléments dans un contrôle onglet.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Paramètres

*adéquat*<br/>
Largeur minimale à définir pour un élément de contrôle d’onglet. Si ce paramètre a la valeur-1, le contrôle utilise la largeur d’onglet par défaut.

### <a name="return-value"></a>Valeur de retour

Largeur minimale de tabulation précédente.

### <a name="return-value"></a>Valeur de retour

Cette fonction membre implémente le comportement de la [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)de message Win32, comme décrit dans le SDK Windows.

##  <a name="setpadding"></a>CTabCtrl :: SetPadding

Définit la quantité d’espace (remplissage) autour de l’icône et de l’étiquette de chaque onglet dans un contrôle onglet.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Définit la quantité d’espace (remplissage) autour de l’icône et de l’étiquette de chaque onglet dans un contrôle onglet.

##  <a name="settooltips"></a>CTabCtrl :: SetToolTips

Assigne un contrôle d’info-bulle à un contrôle onglet.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Paramètres

*pWndTip*<br/>
Handle du contrôle d’info-bulle.

### <a name="remarks"></a>Notes

Vous pouvez obtenir le contrôle d’info-bulle associé à un contrôle onglet en effectuant un appel à `GetToolTips`.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet :: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl, classe](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)
