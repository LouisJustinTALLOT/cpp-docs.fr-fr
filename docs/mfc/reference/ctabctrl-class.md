---
title: CTabCtrl (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cfbcdf03a5c527d27d9bff8b37322011cba60bb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063508"
---
# <a name="ctabctrl-class"></a>CTabCtrl (classe)

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
|[CTabCtrl::AdjustRect](#adjustrect)|Calcule la zone d’affichage d’un contrôle onglet un rectangle de fenêtre donné, ou calcule le rectangle de la fenêtre qui correspond à une zone d’affichage donné.|
|[CTabCtrl::Create](#create)|Crée un contrôle onglet et l’attache à une instance d’un `CTabCtrl` objet.|
|[CTabCtrl::CreateEx](#createex)|Crée un contrôle onglet avec les styles étendus Windows spécifiés et l’attache à une instance d’un `CTabCtrl` objet.|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Supprime tous les éléments à partir d’un contrôle onglet.|
|[CTabCtrl::DeleteItem](#deleteitem)|Supprime un élément à partir d’un contrôle onglet.|
|[CTabCtrl::DeselectAll](#deselectall)|Réinitialise les éléments dans un contrôle onglet, en désactivant tous ceux qui ont été enfoncées.|
|[CTabCtrl::DrawItem](#drawitem)|Dessine un élément spécifié d’un contrôle onglet.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Récupère l’onglet avec le focus actuel d’un contrôle onglet.|
|[CTabCtrl::GetCurSel](#getcursel)|Détermine l’onglet actuellement sélectionné dans un contrôle onglet.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Récupère les styles étendus qui sont actuellement en cours d’utilisation pour le contrôle onglet.|
|[CTabCtrl::GetImageList](#getimagelist)|Récupère la liste d’images associée à un contrôle onglet.|
|[CTabCtrl::GetItem](#getitem)|Récupère des informations sur un onglet dans un contrôle onglet.|
|[CTabCtrl::GetItemCount](#getitemcount)|Récupère le nombre d’onglets dans le contrôle onglet.|
|[CTabCtrl::GetItemRect](#getitemrect)|Récupère le rectangle englobant d’un onglet dans un contrôle onglet.|
|[CTabCtrl::GetItemState](#getitemstate)|Récupère l’état de l’élément de contrôle d’onglet indiqué.|
|[CTabCtrl::GetRowCount](#getrowcount)|Récupère le nombre actuel de lignes d’onglets dans un contrôle onglet.|
|[CTabCtrl::GetToolTips](#gettooltips)|Récupère le handle du contrôle ToolTip associé à un contrôle onglet.|
|[CTabCtrl::HighlightItem](#highlightitem)|Définit l’état de mise en surbrillance d’un élément d’onglet.|
|[CTabCtrl::HitTest](#hittest)|Détermine quel onglet, le cas échéant, est à une position d’écran spécifiées.|
|[CTabCtrl::InsertItem](#insertitem)|Insère un nouvel onglet dans un contrôle onglet.|
|[CTabCtrl::RemoveImage](#removeimage)|Supprime une image à partir de la liste d’images d’un contrôle onglet.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Définit le focus sur un onglet spécifié dans un contrôle onglet.|
|[CTabCtrl::SetCurSel](#setcursel)|Sélectionne un onglet dans un contrôle onglet.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Définit les styles étendus pour un contrôle onglet.|
|[CTabCtrl::SetImageList](#setimagelist)|Affecte une liste d’images à un contrôle onglet.|
|[CTabCtrl::SetItem](#setitem)|Définit certains ou tous les attributs d’un onglet.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Définit le nombre d’octets par onglet réservé pour les données définies par l’application dans un contrôle onglet.|
|[CTabCtrl::SetItemSize](#setitemsize)|Définit la largeur et la hauteur d’un élément.|
|[CTabCtrl::SetItemState](#setitemstate)|Définit l’état de l’élément de contrôle d’onglet indiqué.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Définit la largeur minimale des éléments dans un contrôle onglet.|
|[CTabCtrl::SetPadding](#setpadding)|Définit la quantité d’espace (remplissage) autour de chaque onglet icône et une étiquette dans un contrôle onglet.|
|[CTabCtrl::SetToolTips](#settooltips)|Assigne un contrôle info-bulle à un contrôle onglet.|

## <a name="remarks"></a>Notes

Un « contrôle onglet » est semblable aux intercalaires d’un agenda ou les étiquettes dans un fichier CAB. En utilisant un contrôle tab, une application peut définir plusieurs pages pour la même zone d’une fenêtre ou d’une boîte de dialogue. Chaque page se compose d’un ensemble d’informations ou d’un groupe de contrôles qui l’application s’affiche lorsque l’utilisateur sélectionne l’onglet correspondant. Un type spécial de contrôle onglet affiche les onglets qui ressemblent à des boutons. En cliquant sur un bouton doit effectuer immédiatement une commande au lieu d’afficher une page.

Ce contrôle (et par conséquent la `CTabCtrl` classe) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT version 3.51 et ultérieures.

Pour plus d’informations sur l’utilisation de `CTabCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="adjustrect"></a>  CTabCtrl::AdjustRect

Calcule la zone d’affichage d’un contrôle onglet un rectangle de fenêtre donné, ou calcule le rectangle de la fenêtre qui correspond à une zone d’affichage donné.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*bLarger*<br/>
Indique l’opération à effectuer. Si ce paramètre est TRUE, *lpRect* spécifie un rectangle d’affichage et reçoit le rectangle de la fenêtre correspondante. Si ce paramètre est FALSE, *lpRect* spécifie un rectangle de la fenêtre et reçoit le rectangle d’affichage correspondant.

*lpRect*<br/>
Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui spécifie le rectangle donné et reçoit le rectangle calculé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>  CTabCtrl::Create

Crée un contrôle onglet et l’attache à une instance d’un `CTabCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle onglet. Appliquer n’importe quelle combinaison de [onglet styles de contrôle](/windows/desktop/Controls/tab-control-styles), comme décrit dans le SDK Windows. Consultez **remarques** pour obtenir la liste des styles de fenêtre que vous pouvez également appliquer au contrôle.

*Rect*<br/>
Spécifie la taille et la position du contrôle onglet. Il peut s’agir un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure.

*pParentWnd*<br/>
Spécifie les fenêtre du parent du contrôle onglet, généralement un `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID. du contrôle de l’onglet

### <a name="return-value"></a>Valeur de retour

TRUE si l’initialisation de l’objet a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Vous construisez un `CTabCtrl` objet en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, ce qui crée le contrôle onglet et l’attache à la `CTabCtrl` objet.

En plus de styles de contrôle d’onglet, vous pouvez appliquer les styles de fenêtre suivant à un contrôle tab :

- WS_CHILD crée une fenêtre enfant qui représente le contrôle onglet. Ne peut pas être utilisé avec le style WS_POPUP.

- WS_VISIBLE crée un contrôle onglet qui est visible initialement.

- WS_DISABLED crée une fenêtre qui est initialement désactivée.

- WS_GROUP Spécifie le premier contrôle d’un groupe de contrôles dans lesquels l’utilisateur peut se déplacer d’un contrôle à l’autre avec les touches de direction. Tous les contrôles définis avec le style WS_GROUP après le premier contrôle appartiennent au même groupe. Le prochain contrôle avec le style WS_GROUP termine le groupe de styles et démarre le prochain groupe (autrement dit, un groupe se termine dans lequel la suivante ne commence).

- WS_TABSTOP spécifie un d’un nombre quelconque de contrôles par le biais duquel l’utilisateur peut se déplacer à l’aide de la touche TAB. La touche TAB déplace l’utilisateur sur le contrôle suivant spécifié par le style WS_TABSTOP.

Pour créer un contrôle onglet avec des styles de fenêtre étendus, appelez [CTabCtrl::CreateEx](#createex) au lieu de `Create`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>  CTabCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe le `CTabCtrl` objet.

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
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le *dwExStyle* paramètre pour [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle onglet. Appliquer n’importe quelle combinaison de [onglet styles de contrôle](/windows/desktop/Controls/tab-control-styles), comme décrit dans le SDK Windows. Consultez **remarques** dans [créer](#create) pour obtenir la liste des styles de fenêtre que vous pouvez également appliquer au contrôle.

*Rect*<br/>
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure décrivant la taille et la position de la fenêtre doit être créée, dans les coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de fenêtre enfant. du contrôle

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite sinon 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows **WS_EX_**.

`CreateEx` crée le contrôle avec les styles étendus de Windows spécifiés par *dwExStyle*. Ensemble spécifique d’un contrôle en utilisant des styles étendus [SetExtendedStyle](#setextendedstyle). Par exemple, utilisez `CreateEx` pour définir des styles de ce type en tant que WS_EX_CONTEXTHELP, mais utiliser `SetExtendedStyle` pour définir des styles de ce type comme TCS_EX_FLATSEPARATORS. Pour plus d’informations, consultez les styles décrits dans [Styles étendus de contrôle d’onglet](/windows/desktop/Controls/tab-control-extended-styles) dans le SDK Windows.

##  <a name="ctabctrl"></a>  CTabCtrl::CTabCtrl

Construit un objet `CTabCtrl`.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>  CTabCtrl::DeleteAllItems

Supprime tous les éléments à partir d’un contrôle onglet.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="deleteitem"></a>  CTabCtrl::DeleteItem

Supprime l’élément spécifié à partir d’un contrôle onglet.

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

##  <a name="deselectall"></a>  CTabCtrl::DeselectAll

Réinitialise les éléments dans un contrôle onglet, en désactivant tous ceux qui ont été enfoncées.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Paramètres

*fExcludeFocus*<br/>
Indicateur qui spécifie la portée de la désélection de l’élément. Si ce paramètre est défini sur FALSE, tous les boutons d’onglet seront réinitialisés. Si elle est définie sur TRUE, toutes les onglet éléments à l’exception de celle actuellement sélectionnée est réinitialisée.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32, [TCM_DESELECTALL](/windows/desktop/Controls/tcm-deselectall), comme décrit dans le SDK Windows.

##  <a name="drawitem"></a>  CTabCtrl::DrawItem

Appelé par l’infrastructure lorsqu’un aspect visuel d’un mode owner-draw onglet contrôle change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur vers un [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) structure qui décrit l’élément à peindre.

### <a name="remarks"></a>Notes

Le `itemAction` membre de la `DRAWITEMSTRUCT` structure définit l’action de dessin qui doit être effectuée.

Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre pour implémenter le dessin pour un mode owner-draw `CTabCtrl` objet.

L’application doit restaurer tous les objets interface (GDI) périphérique graphique sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant ce membre de fonction se termine.

##  <a name="getcurfocus"></a>  CTabCtrl::GetCurFocus

Récupère l’index de l’onglet avec le focus actuel.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’onglet avec le focus actuel.

##  <a name="getcursel"></a>  CTabCtrl::GetCurSel

Récupère l’onglet actuellement sélectionné dans un contrôle onglet.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’onglet sélectionné en cas de réussite ou - 1 si aucun onglet n’est sélectionné.

##  <a name="getextendedstyle"></a>  CTabCtrl::GetExtendedStyle

Récupère les styles étendus qui sont actuellement en cours d’utilisation pour le contrôle onglet.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Valeur de retour

Représente les styles étendus en cours d’utilisation pour le contrôle onglet. Cette valeur est une combinaison de [onglet contrôle styles étendus](/windows/desktop/Controls/tab-control-extended-styles), comme décrit dans le SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [TCM_GETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-getextendedstyle), comme décrit dans le SDK Windows.

##  <a name="getimagelist"></a>  CTabCtrl::GetImageList

Récupère la liste d’images qui est associé à un contrôle onglet.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Si l’opération réussit, un pointeur vers la liste d’images de l’onglet contrôle ; Sinon, NULL.

##  <a name="getitem"></a>  CTabCtrl::GetItem

Récupère des informations sur un onglet dans un contrôle onglet.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro de l’onglet.

*pTabCtrlItem*<br/>
Pointeur vers un [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) structure, utilisée pour spécifier les informations à récupérer. Également utilisé pour recevoir des informations sur l’onglet. Cette structure est utilisée avec la `InsertItem`, `GetItem`, et `SetItem` fonctions membres.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE en cas de réussite ; FALSE sinon.

### <a name="remarks"></a>Notes

Lorsque le message est envoyé, le `mask` membre spécifie quels attributs retourner. Si le `mask` membre spécifie la valeur TCIF_TEXT, le `pszText` membre doit contenir l’adresse de la mémoire tampon qui reçoit le texte de l’élément et le `cchTextMax` membre doit spécifier la taille de la mémoire tampon.

- `mask`

   Valeur spécifiant quel `TCITEM` membres à récupérer ou définir de la structure. Ce membre peut être zéro ou une combinaison des valeurs suivantes :

   - TCIF_TEXT le `pszText` membre n’est valide.

   - TCIF_IMAGE le `iImage` membre n’est valide.

   - TCIF_PARAM le `lParam` membre n’est valide.

   - TCIF_RTLREADING le texte de `pszText` s’affiche à l’aide de l’ordre de lecture de droite à gauche sur les systèmes hébreu ou l’arabe.

   - TCIF_STATE le `dwState` membre n’est valide.

- `pszText`

   Pointeur vers une chaîne se terminant par null qui contient le texte de l’onglet si la structure contient des informations sur un onglet. Si la structure reçoit plus d’informations, ce membre spécifie l’adresse de la mémoire tampon qui reçoit le texte de l’onglet.

- `cchTextMax`

   Taille de la mémoire tampon vers laquelle pointe `pszText`. Ce membre est ignoré si la structure ne reçoit pas d’informations.

- `iImage` Index dans le contrôle onglet liste d’images, ou - 1 s’il n’existe aucune image de l’onglet.

- `lParam`

   Données définies par l’application associées à l’onglet. S’il existe plus de quatre octets de données défini par l’application par onglet, une application doit définir une structure et l’utiliser à la place de la `TCITEM` structure. Le premier membre de la structure définie par l’application doit être un [TCITEMHEADER](/windows/desktop/api/commctrl/ns-commctrl-tagtcitemheadera)structure. Le `TCITEMHEADER` structure est identique à la `TCITEM` de structure, mais sans le `lParam` membre. La différence entre la taille de votre structure et la taille de la `TCITEMHEADER` structure doit être égal au nombre d’octets supplémentaires par onglet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>  CTabCtrl::GetItemCount

Récupère le nombre d’onglets dans le contrôle onglet.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le contrôle onglet.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>  CTabCtrl::GetItemRect

Récupère le rectangle englobant pour l’onglet spécifié dans un contrôle onglet.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro de l’élément d’onglet.

*lpRect*<br/>
Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui reçoit le rectangle englobant de l’onglet. Ces coordonnées utilisent le mode de mappage en cours de la fenêtre d’affichage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>  CTabCtrl::GetItemState

Récupère l’état de l’élément de contrôle d’onglet identifié par *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Numéro d’index de base zéro de l’élément pour lequel récupérer les informations d’état.

*dwMask*<br/>
Masque spécifiant les de l’état de l’élément indicateurs à retourner. Pour obtenir la liste de valeurs, consultez le membre masque le [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) structure, comme décrit dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Une référence à une valeur DWORD reçoit les informations d’état. Peut avoir l'une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|L’élément de contrôle d’onglet est sélectionné.|
|TCIS_HIGHLIGHTED|L’élément de contrôle d’onglet est mis en surbrillance et l’onglet et le texte sont dessinées à l’aide de la couleur de surbrillance actuelle. Lorsque vous utilisez la couleur de surbrillance, il s’agit d’une interpolation true, pas une couleur dégradée.|

### <a name="remarks"></a>Notes

État d’un élément est spécifié par le `dwState` membre de la `TCITEM` structure.

##  <a name="getrowcount"></a>  CTabCtrl::GetRowCount

Récupère le nombre actuel de lignes dans un contrôle onglet.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de lignes d’onglets dans le contrôle onglet.

### <a name="remarks"></a>Notes

Uniquement les contrôles d’onglet qui ont le style TCS_MULTILINE peuvent avoir plusieurs lignes d’onglets.

##  <a name="gettooltips"></a>  CTabCtrl::GetToolTips

Récupère le handle du contrôle ToolTip associé à un contrôle onglet.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valeur de retour

Handle du contrôle info-bulle en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Un contrôle onglet crée un contrôle info-bulle s’il a le style TCS_TOOLTIPS. Vous pouvez également affecter un contrôle info-bulle à un contrôle onglet à l’aide de la `SetToolTips` fonction membre.

##  <a name="highlightitem"></a>  CTabCtrl::HighlightItem

Définit l’état de mise en surbrillance d’un élément d’onglet.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Paramètres

*idItem*<br/>
Index de base zéro d’un élément de contrôle d’onglet.

*fHighlight*<br/>
Valeur qui spécifie l’état de mise en surbrillance à définir. Si cette valeur est TRUE, l’onglet est mis en surbrillance ; Si la valeur est FALSE, l’onglet est défini à son état par défaut.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le message Win32 [TCM_HIGHLIGHTITEM](/windows/desktop/Controls/tcm-highlightitem), comme décrit dans le SDK Windows.

##  <a name="hittest"></a>  CTabCtrl::HitTest

Détermine quel onglet, le cas échéant, est à la position d’écran spécifiées.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Paramètres

*pHitTestInfo*<br/>
Pointeur vers un [TCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtchittestinfo) structure, comme décrit dans le SDK Windows, qui spécifie la position de l’écran à tester.

### <a name="return-value"></a>Valeur de retour

Retourne l’index de base zéro de l’onglet ou - 1 si aucun onglet n’est à la position spécifiée.

##  <a name="insertitem"></a>  CTabCtrl::InsertItem

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
Pointeur vers un [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) structure qui spécifie les attributs de l’onglet.

*lpszItem*<br/>
Adresse d’une chaîne se terminant par null qui contient le texte de l’onglet.

*nImage*<br/>
Index de base zéro d’une image à insérer à partir d’une liste d’images.

*nMask*<br/>
Spécifie quel `TCITEM` structure des attributs à définir. Peut être zéro ou une combinaison des valeurs suivantes :

- TCIF_TEXT le `pszText` membre n’est valide.

- TCIF_IMAGE le `iImage` membre n’est valide.

- TCIF_PARAM le *lParam* membre n’est valide.

- TCIF_RTLREADING le texte de `pszText` s’affiche à l’aide de l’ordre de lecture de droite à gauche sur les systèmes hébreu ou l’arabe.

- TCIF_STATE le *dwState* membre n’est valide.

*lParam*<br/>
Données définies par l’application associées à l’onglet.

*dwState*<br/>
Spécifie des valeurs pour les États de l’élément. Pour plus d’informations, consultez [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) dans le SDK Windows.

*dwStateMask*<br/>
Spécifie les États doivent être définies. Pour plus d’informations, consultez [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’onglet Nouveau cas de réussite ; Sinon, - 1.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>  CTabCtrl::RemoveImage

Supprime l’image spécifiée à partir de la liste d’images d’un contrôle onglet.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image à supprimer.

### <a name="remarks"></a>Notes

Le contrôle onglet met à jour l’index d’image de chaque onglet afin que chaque onglet reste associé à la même image.

##  <a name="setcurfocus"></a>  CTabCtrl::SetCurFocus

Définit le focus sur un onglet spécifié dans un contrôle onglet.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Spécifie l’index de l’onglet qui obtient le focus.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [TCM_SETCURFOCUS](/windows/desktop/Controls/tcm-setcurfocus), comme décrit dans le SDK Windows.

##  <a name="setcursel"></a>  CTabCtrl::SetCurSel

Sélectionne un onglet dans un contrôle onglet.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro de l’élément à sélectionner.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de l’onglet sélectionné précédemment en cas de réussite, sinon - 1.

### <a name="remarks"></a>Notes

Un contrôle tab n’envoie pas d’un message de notification TCN_SELCHANGING ou TCN_SELCHANGE lorsqu’un onglet est sélectionné à l’aide de cette fonction. Ces notifications sont envoyées, à l’aide de WM_NOTIFY, lorsque l’utilisateur clique ou utilise le clavier pour changer d’onglet.

##  <a name="setextendedstyle"></a>  CTabCtrl::SetExtendedStyle

Définit les styles étendus pour un contrôle onglet.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Paramètres

*dwNewStyle*<br/>
Valeur qui spécifie une combinaison de l’onglet contrôle des styles étendus.

*dwExMask*<br/>
Une valeur DWORD qui indique les styles dans *dwNewStyle* sont affectées. Uniquement les styles étendus dans *dwExMask* sera modifié. Tous les autres styles seront conservées en l’état. Si ce paramètre est zéro, tous les styles dans *dwNewStyle* seront affectées.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui contient le texte précédent [onglet contrôle styles étendus](/windows/desktop/Controls/tab-control-extended-styles), comme décrit dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Cette fonction membre implémente le comportement du message Win32 [TCM_SETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-setextendedstyle), comme décrit dans le SDK Windows.

##  <a name="setimagelist"></a>  CTabCtrl::SetImageList

Affecte une liste d’images à un contrôle onglet.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList*<br/>
Pointeur vers la liste d’images pour être assigné au contrôle onglet.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la précédente liste d’images ou NULL si aucune liste de l’image précédente.

##  <a name="setitem"></a>  CTabCtrl::SetItem

Définit certains ou tous les attributs d’un onglet.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Index de base zéro de l’élément.

*pTabCtrlItem*<br/>
Pointeur vers un [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) structure qui contient les nouveaux attributs de l’élément. Le `mask` membre spécifie les attributs à définir. Si le `mask` membre spécifie la valeur TCIF_TEXT, le `pszText` membre est l’adresse d’une chaîne se terminant par null et le `cchTextMax` membre est ignoré.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [GetItem](#getitem).

##  <a name="setitemextra"></a>  CTabCtrl::SetItemExtra

Définit le nombre d’octets par onglet réservé pour les données définies par l’application dans un contrôle onglet.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Le nombre d’octets supplémentaires à définir.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [TCM_SETITEMEXTRA](/windows/desktop/Controls/tcm-setitemextra), comme décrit dans le SDK Windows.

##  <a name="setitemsize"></a>  CTabCtrl::SetItemSize

Définit la largeur et la hauteur des éléments du contrôle des tabulations.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Nouvelles largeur et hauteur, en pixels, des éléments du contrôle des tabulations.

### <a name="return-value"></a>Valeur de retour

Retourne les anciennes largeur et hauteur des éléments du contrôle des tabulations.

##  <a name="setitemstate"></a>  CTabCtrl::SetItemState

Définit l’état de l’élément de contrôle d’onglet identifié par *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
Numéro d’index de base zéro de l’élément pour lequel définir les informations d’état.

*dwMask*<br/>
Masque spécifiant les de l’état de l’élément indicateurs à définir. Pour obtenir la liste de valeurs, consultez le membre masque le [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) structure, comme décrit dans le SDK Windows.

*dwState*<br/>
Une référence à une valeur DWORD qui contient les informations d’état. Peut avoir l'une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|L’élément de contrôle d’onglet est sélectionné.|
|TCIS_HIGHLIGHTED|L’élément de contrôle d’onglet est mis en surbrillance et l’onglet et le texte sont dessinées à l’aide de la couleur de surbrillance actuelle. Lorsque vous utilisez la couleur de surbrillance, il s’agit d’une interpolation true, pas une couleur dégradée.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="setmintabwidth"></a>  CTabCtrl::SetMinTabWidth

Définit la largeur minimale des éléments dans un contrôle onglet.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Paramètres

*CX*<br/>
Largeur minimale à définir pour un élément de contrôle d’onglet. Si ce paramètre est défini sur -1, le contrôle utilise la largeur d’onglet par défaut.

### <a name="return-value"></a>Valeur de retour

La largeur minimale onglet précédent.

### <a name="return-value"></a>Valeur de retour

Cette fonction membre implémente le comportement du message Win32 [TCM_SETMINTABWIDTH](/windows/desktop/Controls/tcm-setmintabwidth), comme décrit dans le SDK Windows.

##  <a name="setpadding"></a>  CTabCtrl::SetPadding

Définit la quantité d’espace (remplissage) autour de chaque onglet icône et une étiquette dans un contrôle onglet.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Définit la quantité d’espace (remplissage) autour de chaque onglet icône et une étiquette dans un contrôle onglet.

##  <a name="settooltips"></a>  CTabCtrl::SetToolTips

Assigne un contrôle info-bulle à un contrôle onglet.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Paramètres

*pWndTip*<br/>
Handle du contrôle ToolTip.

### <a name="remarks"></a>Notes

Vous pouvez obtenir le contrôle d’info-bulle associé à un contrôle onglet en effectuant un appel à `GetToolTips`.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl, classe](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)
