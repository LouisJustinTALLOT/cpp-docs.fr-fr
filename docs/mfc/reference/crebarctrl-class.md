---
description: 'En savoir plus sur : CReBarCtrl Class'
title: CReBarCtrl (classe)
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 75caee2fb0b6bb883ecb421325d41b25c38252b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301228"
---
# <a name="crebarctrl-class"></a>CReBarCtrl (classe)

Encapsule les fonctionnalités d'un contrôle rebar, qui est un conteneur de fenêtre enfant.

## <a name="syntax"></a>Syntaxe

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CReBarCtrl :: CReBarCtrl](#crebarctrl)|Construit un objet `CReBarCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CReBarCtrl :: BeginDrag](#begindrag)|Place le contrôle rebar en mode glisser-déplacer.|
|[CReBarCtrl :: Create](#create)|Crée le contrôle rebar et l’attache à l' `CReBarCtrl` objet.|
|[CReBarCtrl :: CreateEx](#createex)|Crée un contrôle rebar avec les styles étendus Windows spécifiés et l’attache à un `CReBarCtrl` objet.|
|[CReBarCtrl ::D eleteBand](#deleteband)|Supprime une bande d’un contrôle rebar.|
|[CReBarCtrl ::D ragMove](#dragmove)|Met à jour la position de glissement dans le contrôle rebar après un appel à `BeginDrag` .|
|[CReBarCtrl :: EndDrag](#enddrag)|Termine l’opération de glisser-déplacer du contrôle rebar.|
|[CReBarCtrl :: GetBandBorders](#getbandborders)|Récupère les bordures d’une bande.|
|[CReBarCtrl :: GetBandCount](#getbandcount)|Récupère le nombre de bandes actuellement dans le contrôle rebar.|
|[CReBarCtrl :: GetBandInfo](#getbandinfo)|Récupère des informations sur une bande spécifiée dans un contrôle rebar.|
|[CReBarCtrl :: GetBandMargins](#getbandmargins)|Récupère les marges d’une bande.|
|[CReBarCtrl :: GetBarHeight](#getbarheight)|Récupère la hauteur du contrôle rebar.|
|[CReBarCtrl :: GetBarInfo](#getbarinfo)|Récupère des informations sur le contrôle rebar et la liste d’images qu’il utilise.|
|[CReBarCtrl :: GetBkColor](#getbkcolor)|Récupère la couleur d’arrière-plan par défaut d’un contrôle rebar.|
|[CReBarCtrl :: GetColorScheme](#getcolorscheme)|Récupère la structure [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) associée au contrôle rebar.|
|[CReBarCtrl :: GetDropTarget](#getdroptarget)|Récupère le pointeur d’interface d’un contrôle rebar `IDropTarget` .|
|[CReBarCtrl :: GetExtendedStyle](#getextendedstyle)|Obtient le style étendu du contrôle rebar actuel.|
|[CReBarCtrl :: GetImageList](#getimagelist)|Récupère la liste d’images associée à un contrôle rebar.|
|[CReBarCtrl :: GetPalette](#getpalette)|Récupère la palette actuelle du contrôle rebar.|
|[CReBarCtrl :: GetRect](#getrect)|Récupère le rectangle englobant pour une bande donnée dans un contrôle rebar.|
|[CReBarCtrl :: GetRowCount](#getrowcount)|Récupère le nombre de lignes de bande dans un contrôle rebar.|
|[CReBarCtrl :: GetRowHeight](#getrowheight)|Récupère la hauteur d’une ligne spécifiée dans un contrôle rebar.|
|[CReBarCtrl :: GetTextColor](#gettextcolor)|Récupère la couleur de texte par défaut d’un contrôle rebar.|
|[CReBarCtrl :: GetToolTips](#gettooltips)|Récupère le handle de tout contrôle d’info-bulle associé au contrôle rebar.|
|[CReBarCtrl :: HitTest](#hittest)|Détermine la partie d’une bande rebar située à un point donné sur l’écran, si une bande rebar existe à ce point.|
|[CReBarCtrl :: IDToIndex](#idtoindex)|Convertit un identificateur de bande (ID) en un index de bande dans un contrôle rebar.|
|[CReBarCtrl :: InsertBand](#insertband)|Insère une nouvelle bande dans un contrôle rebar.|
|[CReBarCtrl :: MaximizeBand](#maximizeband)|Redimensionne une bande dans un contrôle rebar à sa plus grande taille.|
|[CReBarCtrl :: MinimizeBand](#minimizeband)|Redimensionne une bande dans un contrôle rebar à sa plus petite taille.|
|[CReBarCtrl :: MoveBand](#moveband)|Déplace une bande d’un index vers un autre.|
|[CReBarCtrl ::P ushChevron](#pushchevron)|Fait un push d’un chevron par programmation.|
|[CReBarCtrl :: RestoreBand](#restoreband)|Redimensionne une bande dans un contrôle rebar à sa taille idéale.|
|[CReBarCtrl :: SetBandInfo](#setbandinfo)|Définit les caractéristiques d’une bande existante dans un contrôle rebar.|
|[CReBarCtrl :: SetBandWidth](#setbandwidth)|Définit la largeur de la bande ancrée spécifiée dans le contrôle rebar actuel.|
|[CReBarCtrl :: SetBarInfo](#setbarinfo)|Définit les caractéristiques d’un contrôle rebar.|
|[CReBarCtrl :: SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan par défaut d’un contrôle rebar.|
|[CReBarCtrl :: SetColorScheme](#setcolorscheme)|Définit le modèle de couleurs pour les boutons sur un contrôle rebar.|
|[CReBarCtrl :: SetExtendedStyle](#setextendedstyle)|Définit les styles étendus pour le contrôle rebar actuel.|
|[CReBarCtrl :: SetImageList](#setimagelist)|Définit la liste d’images d’un contrôle rebar.|
|[CReBarCtrl :: SetOwner](#setowner)|Définit la fenêtre propriétaire d’un contrôle rebar.|
|[CReBarCtrl :: SetPalette](#setpalette)|Définit la palette actuelle du contrôle rebar.|
|[CReBarCtrl :: SetTextColor](#settextcolor)|Définit la couleur de texte par défaut d’un contrôle rebar.|
|[CReBarCtrl :: SetToolTips](#settooltips)|Associe un contrôle d’info-bulle au contrôle rebar.|
|[CReBarCtrl :: SetWindowTheme](#setwindowtheme)|Définit le style visuel du contrôle rebar.|
|[CReBarCtrl :: ShowBand](#showband)|Affiche ou masque une bande donnée dans un contrôle rebar.|
|[CReBarCtrl :: SizeToRect](#sizetorect)|Ajuste un contrôle rebar à un rectangle spécifié.|

## <a name="remarks"></a>Notes

L’application dans laquelle le contrôle rebar réside assigne la fenêtre enfant contenue dans le contrôle rebar à la bande rebar. La fenêtre enfant est généralement un autre contrôle courant.

Les contrôles Rebar contiennent une ou plusieurs bandes. Chaque bande peut contenir une combinaison d’une barre de redimensionnement, d’une image bitmap, d’une étiquette de texte et d’une fenêtre enfant. La bande ne peut contenir qu’un seul de ces éléments.

Le contrôle rebar peut afficher la fenêtre enfant sur une image d’arrière-plan spécifiée. Toutes les bandes de contrôle rebar peuvent être redimensionnées, à l’exception de celles qui utilisent le style RBBS_FIXEDSIZE. Lorsque vous repositionnez ou redimensionnez une bande de contrôle rebar, le contrôle rebar gère la taille et la position de la fenêtre enfant assignée à cette bande. Pour redimensionner ou modifier l’ordre des bandes dans le contrôle, cliquez et faites glisser la barre de redimensionnement d’une bande.

L’illustration suivante montre un contrôle rebar qui a trois bandes :

- La bande 0 contient un contrôle de barre d’outils plat et transparent.

- La bande 1 contient à la fois des boutons déroulants standard et transparent.

- La bande 2 contient une zone de liste déroulante et quatre boutons standard.

   ![Exemple du menu Rebar](../../mfc/reference/media/vc4scc1.gif "Exemple du menu Rebar")

## <a name="rebar-control"></a>Contrôle rebar

Les contrôles Rebar prennent en charge :

- Listes d’images.

- Gestion des messages.

- Fonctionnalité de dessin personnalisée.

- Divers styles de contrôle en plus des styles de fenêtre standard. Pour obtenir la liste de ces styles, consultez [styles de contrôle rebar](/windows/win32/Controls/rebar-control-styles) dans le SDK Windows.

Pour plus d’informations, consultez [utilisation de CReBarCtrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a> CReBarCtrl :: BeginDrag

Implémente le comportement de la [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)de message Win32, comme décrit dans le SDK Windows.

```cpp
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande affecté par l’opération de glisser-déplacer.

*dwPos*<br/>
Valeur DWORD qui contient les coordonnées de début de la souris. La coordonnée horizontale est contenue dans le LOWORD et la coordonnée verticale est contenue dans le HIWORD. Si vous transmettez (DWORD)-1, le contrôle rebar utilise la position de la souris la dernière fois que le thread du contrôle a appelé `GetMessage` ou `PeekMessage` .

## <a name="crebarctrlcreate"></a><a name="create"></a> CReBarCtrl :: Create

Crée le contrôle rebar et l’attache à l' `CReBarCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie la combinaison de styles de contrôle rebar appliquée au contrôle. Pour obtenir la liste des styles pris en charge, consultez [styles du contrôle rebar](/windows/win32/Controls/rebar-control-styles) dans le SDK Windows.

*rectangulaire*<br/>
Référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) , qui est la position et la taille du contrôle rebar.

*pParentWnd*<br/>
Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle rebar. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle du contrôle rebar.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet a été créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Créez un contrôle rebar en deux étapes :

1. Appelez [CReBarCtrl](#crebarctrl) pour construire un `CReBarCtrl` objet.

1. Appelez cette fonction membre, qui crée le contrôle rebar Windows et l’attache à l' `CReBarCtrl` objet.

Lorsque vous appelez `Create` , les contrôles communs sont initialisés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a> CReBarCtrl :: CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à l' `CReBarCtrl` objet.

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
Spécifie la combinaison de styles de contrôle rebar appliquée au contrôle. Pour obtenir la liste des styles pris en charge, consultez [styles de contrôle rebar](/windows/win32/Controls/rebar-control-styles) dans le SDK Windows.

*rectangulaire*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [Create](#create) pour appliquer des styles Windows étendus, spécifiés par la préversion de style étendu Windows **WS_EX_**.

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a> CReBarCtrl :: CReBarCtrl

Crée un objet `CReBarCtrl`.

```
CReBarCtrl();
```

### <a name="example"></a>Exemple

  Consultez l’exemple de [CReBarCtrl :: Create](#create).

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a> CReBarCtrl ::D eleteBand

Implémente le comportement de la [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)de message Win32, comme décrit dans le SDK Windows.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la bande a été supprimée avec succès ; Sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a> CReBarCtrl ::D ragMove

Implémente le comportement de la [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove)de message Win32, comme décrit dans le SDK Windows.

```cpp
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Paramètres

*dwPos*<br/>
Valeur DWORD qui contient les nouvelles coordonnées de la souris. La coordonnée horizontale est contenue dans le LOWORD et la coordonnée verticale est contenue dans le HIWORD. Si vous transmettez (DWORD)-1, le contrôle rebar utilise la position de la souris la dernière fois que le thread du contrôle a appelé `GetMessage` ou `PeekMessage` .

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a> CReBarCtrl :: EndDrag

Implémente le comportement de la [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)de message Win32, comme décrit dans le SDK Windows.

```cpp
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a> CReBarCtrl :: GetBandBorders

Implémente le comportement de la [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)de message Win32, comme décrit dans le SDK Windows.

```cpp
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande pour laquelle les bordures seront récupérées.

*République*<br/>
Pointeur vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui recevra les bordures de bande. Si le contrôle rebar a le style RBS_BANDBORDERS, chaque membre de cette structure recevra le nombre de pixels, sur le côté correspondant de la bande, qui constituent la bordure. Si le contrôle rebar n’a pas le style RBS_BANDBORDERS, seul le membre de gauche de cette structure reçoit des informations valides. Pour obtenir une description des styles de contrôle rebar, consultez [styles de contrôle rebar](/windows/win32/Controls/rebar-control-styles) dans le SDK Windows.

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a> CReBarCtrl :: GetBandCount

Implémente le comportement de la [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)de message Win32, comme décrit dans le SDK Windows.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de bandes affectées au contrôle.

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a> CReBarCtrl :: GetBandInfo

Implémente le comportement de la [RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) de message Win32, comme décrit dans le SDK Windows.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande pour laquelle les informations sont récupérées.

*prbbi*<br/>
Pointeur vers une structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) pour recevoir les informations de bande. Vous devez définir le `cbSize` membre de cette structure sur `sizeof(REBARBANDINFO)` et définir le `fMask` membre sur les éléments que vous souhaitez récupérer avant d’envoyer ce message.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a> CReBarCtrl :: GetBandMargins

Récupère les marges de la bande.

```cpp
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Paramètres

*pMargins*<br/>
Pointeur vers une structure de [marges](/windows/win32/api/uxtheme/ns-uxtheme-margins)qui recevra les informations.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités du message [RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins) , comme décrit dans le SDK Windows.

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a> CReBarCtrl :: GetBarHeight

Récupère la hauteur de la barre Rebar.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur qui représente la hauteur, en pixels, du contrôle.

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a> CReBarCtrl :: GetBarInfo

Implémente le comportement de la [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)de message Win32, comme décrit dans le SDK Windows.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Paramètres

*prbi*<br/>
Pointeur vers une structure [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) qui recevra les informations de contrôle rebar. Vous devez définir le membre *cbSize* de cette structure sur `sizeof(REBARINFO)` avant d’envoyer ce message.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a> CReBarCtrl :: GetBkColor

Implémente le comportement de la [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)de message Win32, comme décrit dans le SDK Windows.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur COLORREF qui représente la couleur d’arrière-plan par défaut actuelle.

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a> CReBarCtrl :: GetColorScheme

Récupère la structure [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) pour le contrôle rebar.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Paramètres

*lpcs*<br/>
Pointeur vers une structure [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) , comme décrit dans la SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

La `COLORSCHEME` structure comprend la couleur de surbrillance du bouton et la couleur de l’ombre du bouton.

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a> CReBarCtrl :: GetDropTarget

Implémente le comportement de la [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)de message Win32, comme décrit dans le SDK Windows.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) .

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a> CReBarCtrl :: GetExtendedStyle

Obtient les styles étendus du contrôle rebar actuel.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valeur renvoyée

Combinaison d’opérations de bits d’indicateurs qui indiquent les styles étendus. Les indicateurs possibles sont RBS_EX_SPLITTER et RBS_EX_TRANSPARENT. Pour plus d’informations, consultez le paramètre *dwMask* de la méthode [CReBarCtrl :: SetExtendedStyle](#setextendedstyle) .

### <a name="remarks"></a>Notes

Cette méthode envoie le message [RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove) , qui est décrit dans le SDK Windows.

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a> CReBarCtrl :: GetImageList

Obtient l' `CImageList` objet associé à un contrôle rebar.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) . Retourne la valeur NULL si aucune liste d’images n’est définie pour le contrôle.

### <a name="remarks"></a>Notes

Cette fonction membre utilise les informations de taille et de masque stockées dans la structure [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) , comme décrit dans la SDK Windows.

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a> CReBarCtrl :: GetPalette

Récupère la palette actuelle du contrôle rebar.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [cpalette](../../mfc/reference/cpalette-class.md) qui spécifie la palette actuelle du contrôle rebar.

### <a name="remarks"></a>Notes

Notez que cette fonction membre utilise un `CPalette` objet comme valeur de retour, plutôt qu’un HPALETTE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a> CReBarCtrl :: GetRect

Implémente le comportement de la [RB_GETRECT](/windows/win32/Controls/rb-getrect)de message Win32, comme décrit dans le SDK Windows.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro d’une bande dans le contrôle rebar.

*République*<br/>
Pointeur vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui recevra les limites de la bande rebar.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a> CReBarCtrl :: GetRowCount

Implémente le comportement de la [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)de message Win32, comme décrit dans le SDK Windows.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur UINT qui représente le nombre de lignes de bande dans le contrôle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a> CReBarCtrl :: GetRowHeight

Implémente le comportement de la [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)de message Win32, comme décrit dans le SDK Windows.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Paramètres

*uRow*<br/>
Index de base zéro de la bande dont la hauteur sera récupérée.

### <a name="return-value"></a>Valeur renvoyée

Valeur UINT qui représente la hauteur de ligne, en pixels.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a> CReBarCtrl :: GetTextColor

Implémente le comportement de la [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)de message Win32, comme décrit dans le SDK Windows.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur COLORREF qui représente la couleur de texte par défaut actuelle.

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a> CReBarCtrl :: GetToolTips

Implémente le comportement de la [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)de message Win32, comme décrit dans le SDK Windows.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) .

### <a name="remarks"></a>Notes

Notez que l’implémentation MFC de `GetToolTips` retourne un pointeur vers un `CToolTipCtrl` , plutôt qu’un HWND.

## <a name="crebarctrlhittest"></a><a name="hittest"></a> CReBarCtrl :: HitTest

Implémente le comportement de la [RB_HITTEST](/windows/win32/Controls/rb-hittest)de message Win32, comme décrit dans le SDK Windows.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Paramètres

*prbht*<br/>
Pointeur vers une structure [RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo) . Avant d’envoyer le message, le `pt` membre de cette structure doit être initialisé au point qui sera testé, en coordonnées clientes.

### <a name="return-value"></a>Valeur renvoyée

Index de base zéro de la bande au point donné, ou-1 si aucune bande rebar n’était au point.

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a> CReBarCtrl :: IDToIndex

Implémente le comportement de la [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)de message Win32, comme décrit dans le SDK Windows.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Paramètres

*uBandID*<br/>
Identificateur défini par l’application de la bande spécifiée, passé dans le `wID` membre de la structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) lorsque la bande est insérée.

### <a name="return-value"></a>Valeur renvoyée

Index de la bande de base zéro en cas de réussite, ou-1 dans le cas contraire. Si des index de bande dupliqués existent, le premier est retourné.

## <a name="crebarctrlinsertband"></a><a name="insertband"></a> CReBarCtrl :: InsertBand

Implémente le comportement de la [RB_INSERTBAND](/windows/win32/Controls/rb-insertband)de message Win32, comme décrit dans le SDK Windows.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Paramètres

*uIndex*<br/>
Index de base zéro de l’emplacement où la bande sera insérée. Si vous affectez la valeur-1 à ce paramètre, le contrôle ajoutera la nouvelle bande au dernier emplacement.

*prbbi*<br/>
Pointeur vers une structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) qui définit la bande à insérer. Vous devez définir le membre *cbSize* de cette structure sur `sizeof(REBARBANDINFO)` avant d’appeler cette fonction.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a> CReBarCtrl :: MaximizeBand

Redimensionne une bande dans un contrôle rebar à sa plus grande taille.

```cpp
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande à agrandir.

### <a name="remarks"></a>Notes

Implémente le comportement de la [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) de message Win32 avec la `fIdeal` valeur 0, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a> CReBarCtrl :: MinimizeBand

Redimensionne une bande dans un contrôle rebar à sa plus petite taille.

```cpp
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande à réduire.

### <a name="remarks"></a>Notes

Implémente le comportement de la [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a> CReBarCtrl :: MoveBand

Implémente le comportement de la [RB_MOVEBAND](/windows/win32/Controls/rb-moveband)de message Win32, comme décrit dans le SDK Windows.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Paramètres

*uFrom*<br/>
Index de base zéro de la bande à déplacer.

*utomatique*<br/>
Index de base zéro de la nouvelle position de la bande. La valeur de ce paramètre ne doit jamais être supérieure au nombre de bandes moins un. Pour obtenir le nombre de bandes, appelez [GetBandCount](#getbandcount).

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a> CReBarCtrl ::P ushChevron

Implémente le comportement de la [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)de message Win32, comme décrit dans le SDK Windows.

```cpp
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande dont le Chevron doit faire l’objet d’un push.

*lAppValue*<br/>
Valeur 32 bits définie par l’application. Consultez *lAppValue* dans [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron) dans le SDK Windows.

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a> CReBarCtrl :: RestoreBand

Redimensionne une bande dans un contrôle rebar à sa taille idéale.

```cpp
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande à agrandir.

### <a name="remarks"></a>Notes

Implémente le comportement de la [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) de message Win32 avec la `fIdeal` valeur 1, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a> CReBarCtrl :: SetBandInfo

Implémente le comportement de la [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)de message Win32, comme décrit dans le SDK Windows.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro de la bande devant recevoir les nouveaux paramètres.

*prbbi*<br/>
Pointeur vers une structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) qui définit la bande à insérer. Vous devez définir le `cbSize` membre de cette structure sur `sizeof(REBARBANDINFO)` avant d’envoyer ce message.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a> CReBarCtrl :: SetBandWidth

Définit la largeur de la bande ancrée spécifiée dans le contrôle rebar actuel.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Paramètres

*uBand*\
dans Index de base zéro d’une bande rebar.

*cxWidth*\
dans Nouvelle largeur de la bande rebar, en pixels.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_rebar` , qui est utilisée pour accéder au contrôle rebar actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit chaque bande rebar sur la même largeur.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a> CReBarCtrl :: SetBarInfo

Implémente le comportement de la [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)de message Win32, comme décrit dans le SDK Windows.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Paramètres

*prbi*<br/>
Pointeur vers une structure [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) qui contient les informations à définir. Vous devez définir le `cbSize` membre de cette structure sur `sizeof(REBARINFO)` avant d’envoyer ce message

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a> CReBarCtrl :: SetBkColor

Implémente le comportement de la [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)de message Win32, comme décrit dans le SDK Windows.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Language*<br/>
Valeur COLORREF qui représente la nouvelle couleur d’arrière-plan par défaut.

### <a name="return-value"></a>Valeur renvoyée

Valeur [COLORREF](/windows/win32/gdi/colorref) qui représente la couleur d’arrière-plan par défaut précédente.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la définition de la couleur d’arrière-plan et sur la définition de la valeur par défaut, consultez cette rubrique.

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a> CReBarCtrl :: SetColorScheme

Définit le modèle de couleurs pour les boutons sur un contrôle rebar.

```cpp
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Paramètres

*lpcs*<br/>
Pointeur vers une structure [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) , comme décrit dans la SDK Windows.

### <a name="remarks"></a>Notes

La `COLORSCHEME` structure comprend la couleur de surbrillance du bouton et la couleur de l’ombre du bouton.

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a> CReBarCtrl :: SetExtendedStyle

Définit les styles étendus pour le contrôle rebar actuel.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Paramètres

*dwMask*\
dans Combinaison de bits (OR) d’indicateurs qui spécifie les indicateurs du paramètre *dwStyleEx* qui s’appliquent. Utilisez une ou plusieurs des valeurs suivantes :

- `RBS_EX_SPLITTER`: Par défaut, affichez le séparateur en bas en mode horizontal et à droite en mode vertical.
- `RBS_EX_TRANSPARENT`: Transférer le message d' [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) vers la fenêtre parente.

*dwStyleEx*\
dans Combinaison de bits (OR) d’indicateurs qui spécifient les styles à appliquer. Pour définir un style, spécifiez le même indicateur que celui utilisé dans le paramètre *dwMask* . Pour réinitialiser un style, spécifiez zéro binaire.

### <a name="return-value"></a>Valeur renvoyée

Style étendu précédent.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle) , qui est décrit dans le SDK Windows.

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a> CReBarCtrl :: SetImageList

Assigne une liste d’images à un contrôle rebar.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList*<br/>
Pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) contenant la liste d’images à assigner au contrôle rebar.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlsetowner"></a><a name="setowner"></a> CReBarCtrl :: SetOwner

Implémente le comportement de la [RB_SETPARENT](/windows/win32/Controls/rb-setparent)de message Win32, comme décrit dans le SDK Windows.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers un `CWnd` objet à définir en tant que propriétaire du contrôle rebar.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est le propriétaire actuel du contrôle rebar.

### <a name="remarks"></a>Notes

Notez que cette fonction membre utilise des pointeurs vers des `CWnd` objets pour le propriétaire actuel et le propriétaire sélectionné du contrôle rebar, plutôt que des handles vers Windows.

> [!NOTE]
> Cette fonction membre ne change pas le parent réel qui a été défini lors de la création du contrôle ; au lieu de cela, il envoie des messages de notification à la fenêtre que vous spécifiez.

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a> CReBarCtrl :: SetPalette

Implémente le comportement de la [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)de message Win32, comme décrit dans le SDK Windows.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Paramètres

*hPal*<br/>
HPALETTE qui spécifie la nouvelle palette que le contrôle rebar utilisera.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [cpalette](../../mfc/reference/cpalette-class.md) qui spécifie la palette précédente du contrôle rebar.

### <a name="remarks"></a>Notes

Notez que cette fonction membre utilise un `CPalette` objet comme valeur de retour, plutôt qu’un HPALETTE.

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a> CReBarCtrl :: SetTextColor

Implémente le comportement de la [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)de message Win32, comme décrit dans le SDK Windows.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Language*<br/>
Valeur COLORREF qui représente la nouvelle couleur de texte dans l' `CReBarCtrl` objet.

### <a name="return-value"></a>Valeur renvoyée

Valeur [COLORREF](/windows/win32/gdi/colorref) représentant la couleur de texte précédente associée à l' `CReBarCtrl` objet.

### <a name="remarks"></a>Notes

Elle est fournie pour prendre en charge la flexibilité des couleurs de texte dans un contrôle rebar.

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a> CReBarCtrl :: SetToolTips

Associe un contrôle d’info-bulle à un contrôle rebar.

```cpp
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Paramètres

*pToolTip*<br/>
Pointeur vers un objet [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Notes

Vous devez détruire l' `CToolTipCtrl` objet une fois que vous avez fini de l’utiliser.

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a> CReBarCtrl :: SetWindowTheme

Définit le style visuel du contrôle rebar.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Paramètres

*pszSubAppName*<br/>
Pointeur vers une chaîne Unicode qui contient le style visuel rebar à définir.

### <a name="return-value"></a>Valeur renvoyée

La valeur de retour n’est pas utilisée.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités du message [RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme) , comme décrit dans le SDK Windows.

## <a name="crebarctrlshowband"></a><a name="showband"></a> CReBarCtrl :: ShowBand

Implémente le comportement de la [RB_SHOWBAND](/windows/win32/Controls/rb-showband)de message Win32, comme décrit dans le SDK Windows.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Paramètres

*uBand*<br/>
Index de base zéro d’une bande dans le contrôle rebar.

*fShow*<br/>
Indique si la bande doit être affichée ou masquée. Si cette valeur est TRUE, la bande est affichée. Dans le cas contraire, la bande sera masquée.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a> CReBarCtrl :: SizeToRect

Implémente le comportement de la [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)de message Win32, comme décrit dans le SDK Windows.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui spécifie le rectangle sur lequel le contrôle rebar doit être redimensionné.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Notez que cette fonction membre utilise un `CRect` objet en tant que paramètre, plutôt qu’une `RECT` structure.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
