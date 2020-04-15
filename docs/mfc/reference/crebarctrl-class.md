---
title: Classe CReBarCtrl
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
ms.openlocfilehash: 776892d71e2cb0f5d57512754cd7fa12730eb044
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367444"
---
# <a name="crebarctrl-class"></a>Classe CReBarCtrl

Encapsule les fonctionnalités d'un contrôle rebar, qui est un conteneur de fenêtre enfant.

## <a name="syntax"></a>Syntaxe

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Construit un objet `CReBarCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|Place le contrôle de la barre d’armature en mode drag-and-drop.|
|[CReBarCtrl::Créer](#create)|Crée le contrôle des barres d’armature et le fixe à l’objet. `CReBarCtrl`|
|[CReBarCtrl::CreateEx](#createex)|Crée un contrôle de barre d’armature avec `CReBarCtrl` les styles Windows étendus spécifiés et le fixe à un objet.|
|[CReBarCtrl::DeleteBand](#deleteband)|Supprime une bande à partir d’un contrôle de barres d’armature.|
|[CReBarCtrl::DragMove](#dragmove)|Mises à jour de la position de `BeginDrag`traînée dans le contrôle de la barre d’armature après un appel à .|
|[CReBarCtrl::EndDrag](#enddrag)|Termine l’opération de drag-and-drop du contrôle des barres d’armature.|
|[CReBarCtrl::GetBandBorders](#getbandborders)|Récupère les frontières d’une bande.|
|[CReBarCtrl::GetBandCount](#getbandcount)|Récupère le nombre de bandes actuellement sous le contrôle des barres d’armature.|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Récupère des informations sur une bande spécifiée dans un contrôle de barres d’armature.|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Récupère les marges d’un groupe.|
|[CReBarCtrl::GetBarHeight](#getbarheight)|Récupère la hauteur du contrôle des barres d’armature.|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Récupère les informations sur le contrôle des barres d’armature et la liste d’images qu’elle utilise.|
|[CReBarCtrl::GetBkColor](#getbkcolor)|Récupère la couleur de fond par défaut d’un contrôle des barres d’armature.|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Récupère la structure [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) associée au contrôle des barres d’armature.|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Récupère le pointeur d’interface d’un contrôle de `IDropTarget` barre d’armature.|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Obtient le style étendu du contrôle actuel des barres d’armature.|
|[CReBarCtrl::GetImageList](#getimagelist)|Récupère la liste d’images associée à un contrôle de barres d’armature.|
|[CReBarCtrl::GetPalette](#getpalette)|Récupère la palette actuelle du contrôle des barres d’armature.|
|[CReBarCtrl::GetRect](#getrect)|Récupère le rectangle de délimitation pour une bande donnée dans un contrôle de barre d’armature.|
|[CReBarCtrl::GetRowCount](#getrowcount)|Récupère le nombre de rangées de bandes dans un contrôle de barre d’armature.|
|[CReBarCtrl::GetRowHeight](#getrowheight)|Récupère la hauteur d’une rangée spécifiée dans un contrôle de barre d’armature.|
|[CReBarCtrl::GetTextColor](#gettextcolor)|Récupère la couleur de texte par défaut d’un contrôle des barres d’armature.|
|[CReBarCtrl::GetToolTips](#gettooltips)|Récupère la poignée à n’importe quel contrôle de pointe d’outil associé au contrôle de barre d’armature.|
|[CReBarCtrl::HitTest](#hittest)|Détermine quelle partie d’une bande de barres d’armature se trouve à un point donné à l’écran, si une bande de barres d’armature existe à ce moment-là.|
|[CReBarCtrl::IDToIndex](#idtoindex)|Convertit un identifiant de bande (ID) en un index de bande dans un contrôle de barre d’armature.|
|[CReBarCtrl::InsertBand](#insertband)|Insère une nouvelle bande dans un contrôle des barres d’armature.|
|[CReBarCtrl::MaximizeBand](#maximizeband)|Resizes une bande dans un contrôle de barre d’armature à sa plus grande taille.|
|[CReBarCtrl::MinimizeBand](#minimizeband)|Resizes une bande dans un contrôle de barre d’armature à sa plus petite taille.|
|[CReBarCtrl::MoveBand](#moveband)|Déplace une bande d’un index à l’autre.|
|[CReBarCtrl::PushChevron](#pushchevron)|Programmatique pousse un chevron.|
|[CReBarCtrl::RestoreBand](#restoreband)|Resizes une bande dans un contrôle de barre d’armature à sa taille idéale.|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Définit les caractéristiques d’une bande existante dans un contrôle de barre d’armature.|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Définit la largeur de la bande amarré spécifiée dans le contrôle actuel des barres d’armature.|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Définit les caractéristiques d’un contrôle des barres d’armature.|
|[CReBarCtrl::SetBkColor](#setbkcolor)|Définit la couleur de fond par défaut d’un contrôle des barres d’armature.|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Définit le schéma de couleur pour les boutons sur un contrôle de barre d’armature.|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Définit les styles étendus pour le contrôle actuel des barres d’armature.|
|[CReBarCtrl::SetImageList](#setimagelist)|Définit la liste d’images d’un contrôle des barres d’armature.|
|[CReBarCtrl::SetOwner](#setowner)|Définit la fenêtre du propriétaire d’une barre d’armature.|
|[CReBarCtrl::SetPalette](#setpalette)|Définit la palette actuelle du contrôle des barres d’armature.|
|[CReBarCtrl::SetTextColor](#settextcolor)|Définit la couleur de texte par défaut d’un contrôle des barres d’armature.|
|[CReBarCtrl::SetToolTips](#settooltips)|Associe un contrôle de pointe d’outil avec le contrôle des barres d’armature.|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Définit le style visuel du contrôle des barres d’armature.|
|[CReBarCtrl::ShowBand](#showband)|Affiche ou cache une bande donnée dans un contrôle de barres d’armature.|
|[CReBarCtrl::SizeToRect](#sizetorect)|S’adapte à un contrôle de barre d’armature sur un rectangle spécifié.|

## <a name="remarks"></a>Notes

L’application dans laquelle se trouve le contrôle de la barre d’armature assigne la fenêtre de l’enfant contenue par le contrôle de la barre d’armature à la bande de barre d’armature. La fenêtre de l’enfant est généralement un autre contrôle commun.

Les commandes de barres d’armature contiennent une ou plusieurs bandes. Chaque bande peut contenir une combinaison d’une barre de pince, d’une bitmap, d’une étiquette de texte et d’une fenêtre pour enfants. La bande ne peut contenir qu’un seul de ces éléments.

Le contrôle des barres d’armature peut afficher la fenêtre de l’enfant sur une bitmap de fond spécifiée. Toutes les bandes de contrôle des barres d’armature peuvent être resized, sauf celles qui utilisent le style RBBS_FIXEDSIZE. Lorsque vous repositionnez ou ressiez une bande de contrôle des barres d’armature, le contrôle des barres d’armature gère la taille et la position de la fenêtre enfant assignée à cette bande. Pour resize ou modifier l’ordre des bandes dans le contrôle, cliquez et faites glisser la barre de pincement d’un groupe.

L’illustration suivante montre un contrôle des barres d’armature qui comporte trois bandes :

- La bande 0 contient un contrôle plat et transparent de barre d’outils.

- La bande 1 contient à la fois des boutons de décrochage standard transparents et transparents.

- Bande 2 contient une boîte combo et quatre boutons standard.

   ![Exemple du menu Rebar](../../mfc/reference/media/vc4scc1.gif "Exemple du menu Rebar")

## <a name="rebar-control"></a>Contrôle des barres d’armature

Soutien aux commandes des barres d’armature :

- Listes d’images.

- Manipulation des messages.

- Fonctionnalité de tirage personnalisé.

- Une variété de styles de contrôle en plus des styles de fenêtre standard. Pour une liste de ces styles, voir [Rebar Control Styles](/windows/win32/Controls/rebar-control-styles) dans le SDK Windows.

Pour plus d’informations, voir [Utilisation de CReBarCtrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a>CReBarCtrl::BeginDrag

Implémente le comportement du message Win32 [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag), tel que décrit dans le SDK Windows.

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
Indice zéro de la bande que l’opération de drag-and-drop affectera.

*dwPos dwPos*<br/>
Une valeur DWORD qui contient les coordonnées de la souris de départ. La coordonnées horizontales est contenue dans le LOWORD et la coordonnées verticales est contenue dans le HIWORD. Si vous passez (DWORD)-1, le contrôle des barres d’armature utilisera la `GetMessage` `PeekMessage`position de la souris la dernière fois que le fil du contrôle a appelé ou .

## <a name="crebarctrlcreate"></a><a name="create"></a>CReBarCtrl::Créer

Crée le contrôle des barres d’armature et le fixe à l’objet. `CReBarCtrl`

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie la combinaison de styles de contrôle des barres d’armature appliqués au contrôle. Consultez [Rebar Control Styles](/windows/win32/Controls/rebar-control-styles) dans le Windows SDK pour une liste de styles pris en charge.

*Rect*<br/>
Une référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou une structure [RECT,](/previous-versions/dd162897\(v=vs.85\)) qui est la position et la taille du contrôle des barres d’armature.

*pParentWnd*<br/>
Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle des barres d’armature. Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de commande du contrôle de la barre d’armature.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet a été créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Créez un contrôle des barres d’armature en deux étapes :

1. Appelez [CReBarCtrl](#crebarctrl) pour `CReBarCtrl` construire un objet.

1. Appelez cette fonction de membre, qui crée le contrôle `CReBarCtrl` de barre d’armature Windows et l’attache à l’objet.

Lorsque vous `Create`appelez, les contrôles communs sont parasécés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a>CReBarCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CReBarCtrl` et l’associe à l’objet.

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
Spécifie la combinaison de styles de contrôle des barres d’armature appliqués au contrôle. Pour une liste de styles pris en charge, voir [Rebar Control Styles](/windows/win32/Controls/rebar-control-styles) dans le SDK Windows.

*Rect*<br/>
Une référence à une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a>CReBarCtrl::CReBarCtrl

Crée un objet `CReBarCtrl` .

```
CReBarCtrl();
```

### <a name="example"></a>Exemple

  Voir l’exemple pour [CReBarCtrl::Créer](#create).

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a>CReBarCtrl::DeleteBand

Implémente le comportement du message Win32 [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband), tel que décrit dans le SDK Windows.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
L’index zéro de la bande à supprimer.

### <a name="return-value"></a>Valeur de retour

Nonzero si la bande a supprimé avec succès; autrement zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a>CReBarCtrl::DragMove

Implémente le comportement du message Win32 [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove), tel que décrit dans le SDK Windows.

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Paramètres

*dwPos dwPos*<br/>
Une valeur DWORD qui contient les nouvelles coordonnées de souris. La coordonnées horizontales est contenue dans le LOWORD et la coordonnées verticales est contenue dans le HIWORD. Si vous passez (DWORD)-1, le contrôle des barres d’armature utilisera la `GetMessage` `PeekMessage`position de la souris la dernière fois que le fil du contrôle a appelé ou .

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a>CReBarCtrl::EndDrag

Implémente le comportement du message Win32 [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag), tel que décrit dans le SDK Windows.

```
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a>CReBarCtrl::GetBandBorders

Implémente le comportement du message Win32 [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders), tel que décrit dans le SDK Windows.

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
Indice zéro de la bande pour laquelle les frontières seront récupérées.

*Rpc*<br/>
Un pointeur vers une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) qui recevra les frontières de la bande. Si le contrôle des barres d’armature a le style RBS_BANDBORDERS, chaque membre de cette structure recevra le nombre de pixels, du côté correspondant de la bande, qui constituent la frontière. Si le contrôle des barres d’armature n’a pas le style RBS_BANDBORDERS, seul le membre gauche de cette structure reçoit des informations valides. Pour une description des styles de contrôle des barres d’armature, voir [Rebar Control Styles](/windows/win32/Controls/rebar-control-styles) dans le SDK Windows.

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a>CReBarCtrl::GetBandCount

Implémente le comportement du message Win32 [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount), tel que décrit dans le SDK Windows.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de bandes assignées au contrôle.

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a>CReBarCtrl::GetBandInfo

Implémente le comportement du message Win32 [RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) tel que décrit dans le SDK Windows.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
Indice zéro de la bande pour laquelle l’information sera récupérée.

*prbbi*<br/>
Un pointeur vers une structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) pour recevoir les informations de bande. Vous devez `cbSize` configurer le `sizeof(REBARBANDINFO)` membre de `fMask` cette structure et définir le membre vers les éléments que vous souhaitez récupérer avant d’envoyer ce message.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a>CReBarCtrl::GetBandMargins

Récupère les marges du groupe.

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Paramètres

*pMargins (pMargins)*<br/>
Un pointeur vers une structure [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins)qui recevra l’information.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message [RB_GETBANDMARGINS,](/windows/win32/Controls/rb-getbandmargins) tel que décrit dans le SDK Windows.

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a>CReBarCtrl::GetBarHeight

Récupère la hauteur de la barre d’armature.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur qui représente la hauteur, en pixels, du contrôle.

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a>CReBarCtrl::GetBarInfo

Implémente le comportement du message Win32 [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo), tel que décrit dans le SDK Windows.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Paramètres

*prbi (prbi)*<br/>
Un pointeur vers une structure [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) qui recevra les informations de contrôle des barres d’armature. Vous devez définir le membre *cbSize* de cette structure avant d’envoyer `sizeof(REBARINFO)` ce message.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a>CReBarCtrl::GetBkColor

Implémente le comportement du message Win32 [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor), tel que décrit dans le SDK Windows.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur COLORREF qui représente la couleur de fond par défaut actuelle.

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>CReBarCtrl::GetColorScheme

Récupère la structure [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) pour le contrôle des barres d’armature.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Paramètres

*Retard*<br/>
Un pointeur vers une structure [COLORSCHEME,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) tel que décrit dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

La `COLORSCHEME` structure comprend la couleur de mise en surbrillance du bouton et la couleur de l’ombre bouton.

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a>CReBarCtrl::GetDropTarget

Implémente le comportement du message Win32 [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget), tel que décrit dans le SDK Windows.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une interface [IDropTarget.](/windows/win32/api/oleidl/nn-oleidl-idroptarget)

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CReBarCtrl::GetExtendedStyle

Obtient les styles étendus du contrôle actuel des barres d’armature.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Une combinaison bitwise (OU) de drapeaux qui indiquent les styles étendus. Les drapeaux possibles sont RBS_EX_SPLITTER et RBS_EX_TRANSPARENT. Pour plus d’informations, consultez le paramètre *dwMask* de la méthode [CReBarCtrl::SetExtendedStyle.](#setextendedstyle)

### <a name="remarks"></a>Notes

Cette méthode envoie le [message RB_GETEXTENDEDSTYLE,](/windows/win32/Controls/rb-dragmove) qui est décrit dans le SDK Windows.

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a>CReBarCtrl::GetImageList

Obtient `CImageList` l’objet associé à un contrôle de barre d’armature.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CImageList.](../../mfc/reference/cimagelist-class.md) Retourne NULL si aucune liste d’images n’est définie pour le contrôle.

### <a name="remarks"></a>Notes

Cette fonction de membre utilise des informations de taille et de masque stockées dans la structure [REBARINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) comme décrit dans le SDK Windows.

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a>CReBarCtrl::GetPalette

Récupère la palette actuelle du contrôle des barres d’armature.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CPalette](../../mfc/reference/cpalette-class.md) spécifiant la palette actuelle du contrôle des barres d’armature.

### <a name="remarks"></a>Notes

Notez que cette `CPalette` fonction de membre utilise un objet comme valeur de retour, plutôt qu’un HPALETTE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a>CReBarCtrl::GetRect

Implémente le comportement du message Win32 [RB_GETRECT](/windows/win32/Controls/rb-getrect), tel que décrit dans le SDK Windows.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
Indice zéro d’une bande dans le contrôle des barres d’armature.

*Rpc*<br/>
Un pointeur vers une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) qui recevra les limites de la bande de barres d’armature.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a>CReBarCtrl::GetRowCount

Implémente le comportement du message Win32 [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount), tel que décrit dans le SDK Windows.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur UINT qui représente le nombre de rangées de bande dans le contrôle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a>CReBarCtrl::GetRowHeight

Implémente le comportement du message Win32 [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight), tel que décrit dans le SDK Windows.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Paramètres

*uRow*<br/>
Indice zéro de la bande qui verra sa taille récupérée.

### <a name="return-value"></a>Valeur de retour

Une valeur UINT qui représente la hauteur de la rangée, en pixels.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a>CReBarCtrl::GetTextColor

Implémente le comportement du message Win32 [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor), tel que décrit dans le SDK Windows.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur COLORREF qui représente la couleur actuelle du texte par défaut.

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a>CReBarCtrl::GetToolTips

Implémente le comportement du message Win32 [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips), tel que décrit dans le SDK Windows.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un objet [CToolTipCtrl.](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Notes

Notez que la `GetToolTips` mise en œuvre MFC de renvois un pointeur à un `CToolTipCtrl`, plutôt que d’un HWND.

## <a name="crebarctrlhittest"></a><a name="hittest"></a>CReBarCtrl::HitTest

Implémente le comportement du message Win32 [RB_HITTEST](/windows/win32/Controls/rb-hittest), tel que décrit dans le SDK Windows.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Paramètres

*prbht prbht*<br/>
Un pointeur vers une structure [RBHITTESTINFO.](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo) Avant d’envoyer `pt` le message, le membre de cette structure doit être parasélisé au point qui sera testé, dans les coordonnées des clients.

### <a name="return-value"></a>Valeur de retour

L’indice zéro de la bande au point donné, ou -1 si aucune bande de barres d’armature n’était au point.

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a>CReBarCtrl::IDToIndex

Implémente le comportement du message Win32 [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex), tel que décrit dans le SDK Windows.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Paramètres

*uBandID (en)*<br/>
L’identifiant défini par l’application de `wID` la bande spécifiée, passé dans le membre de la structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) lorsque la bande est insérée.

### <a name="return-value"></a>Valeur de retour

L’indice de bande à base de zéro en cas de succès, ou -1 autrement. S’il existe des indices de bande en double, le premier est retourné.

## <a name="crebarctrlinsertband"></a><a name="insertband"></a>CReBarCtrl::InsertBand

Implémente le comportement du message Win32 [RB_INSERTBAND](/windows/win32/Controls/rb-insertband), tel que décrit dans le SDK Windows.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Paramètres

*uIndex (en)*<br/>
Index à base zéro de l’endroit où la bande sera insérée. Si vous définissez ce paramètre à -1, le contrôle ajoutera la nouvelle bande au dernier endroit.

*prbbi*<br/>
Un pointeur vers une structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) qui définit la bande à insérer. Vous devez définir le membre *cbSize* de cette structure avant d’appeler `sizeof(REBARBANDINFO)` cette fonction.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a>CReBarCtrl::MaximizeBand

Resizes une bande dans un contrôle de barre d’armature à sa plus grande taille.

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
L’index zéro de la bande à maximiser.

### <a name="remarks"></a>Notes

Implémente le comportement du message Win32 [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) avec `fIdeal` défini à 0, tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a>CReBarCtrl::MinimizeBand

Resizes une bande dans un contrôle de barre d’armature à sa plus petite taille.

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
L’index zéro de la bande à minimiser.

### <a name="remarks"></a>Notes

Implémente le comportement du message Win32 [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a>CReBarCtrl::MoveBand

Implémente le comportement du message Win32 [RB_MOVEBAND](/windows/win32/Controls/rb-moveband), tel que décrit dans le SDK Windows.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Paramètres

*uDe*<br/>
Indice zéro de la bande à déplacer.

*Uto*<br/>
Indice zéro de la nouvelle position de bande. Cette valeur de paramètre ne doit jamais être supérieure au nombre de bandes moins une. Pour obtenir le nombre de bandes, appelez [GetBandCount](#getbandcount).

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a>CReBarCtrl::PushChevron

Implémente le comportement du message Win32 [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron), tel que décrit dans le SDK Windows.

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
Indice zéro de la bande dont le chevron doit être poussé.

*lAppValue*<br/>
Une application définissait la valeur 32 bits. Voir *lAppValue* dans [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron) dans le SDK Windows.

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a>CReBarCtrl::RestoreBand

Resizes une bande dans un contrôle de barre d’armature à sa taille idéale.

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
L’index zéro de la bande à maximiser.

### <a name="remarks"></a>Notes

Implémente le comportement du message Win32 [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) avec `fIdeal` défini à 1, tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a>CReBarCtrl::SetBandInfo

Implémente le comportement du message Win32 [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo), tel que décrit dans le SDK Windows.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
L’index zéro de la bande pour recevoir les nouveaux paramètres.

*prbbi*<br/>
Pointeur vers une structure [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) qui définit la bande à insérer. Vous devez `cbSize` définir le membre `sizeof(REBARBANDINFO)` de cette structure avant d’envoyer ce message.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a>CReBarCtrl::SetBandWidth

Définit la largeur de la bande amarré spécifiée dans le contrôle actuel des barres d’armature.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*uBand (en)*|[dans] Indice zéro d’une bande de barres d’armature.|
|*cxWidth (en)*|[dans] Nouvelle largeur de la bande de barre d’armature, en pixels.|

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message RB_SETBANDWIDTH,](/windows/win32/Controls/rb-setbandwidth) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_rebar`définit la variable, qui est utilisée pour accéder au contrôle actuel des barres d’armature. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit chaque bande de barre d’armature pour être la même largeur.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a>CReBarCtrl::SetBarInfo

Implémente le comportement du message Win32 [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo), tel que décrit dans le SDK Windows.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Paramètres

*prbi (prbi)*<br/>
Un pointeur vers une structure [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) qui contient les informations à définir. Vous devez `cbSize` définir le membre `sizeof(REBARINFO)` de cette structure avant d’envoyer ce message

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a>CReBarCtrl::SetBkColor

Implémente le comportement du message Win32 [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor), tel que décrit dans le SDK Windows.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Clr*<br/>
La valeur COLORREF qui représente la nouvelle couleur de fond par défaut.

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) qui représente la couleur de fond par défaut précédente.

### <a name="remarks"></a>Notes

Voir ce sujet pour plus d’informations sur le moment de définir la couleur de fond, et comment définir la valeur par défaut.

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CReBarCtrl::SetColorScheme

Définit le schéma de couleur pour les boutons sur un contrôle de barre d’armature.

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Paramètres

*Retard*<br/>
Un pointeur vers une structure [COLORSCHEME,](/windows/win32/api/commctrl/ns-commctrl-colorscheme) tel que décrit dans le SDK Windows.

### <a name="remarks"></a>Notes

La `COLORSCHEME` structure comprend à la fois la couleur de mise en surbrillance du bouton et la couleur de l’ombre bouton.

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CReBarCtrl::SetExtendedStyle

Définit les styles étendus pour le contrôle actuel des barres d’armature.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwMask*|[dans] Une combinaison bitwise (OU) de drapeaux qui spécifient quels drapeaux dans le paramètre *dwStyleEx* s’appliquent. Utilisez une ou plusieurs des valeurs suivantes :<br /><br /> RBS_EX_SPLITTER: Par défaut, afficher le diviseur sur le fond en mode horizontal, et à droite en mode vertical.<br /><br /> RBS_EX_TRANSPARENT : Transmettons le [message WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) à la fenêtre parente.|
|*dwStyleEx*|[dans] Une combinaison bitwise (OU) de drapeaux qui spécifient les styles à appliquer. Pour définir un style, spécifiez le même drapeau qui est utilisé dans le paramètre *dwMask.* Pour réinitialiser un style, spécifiez le zéro binaire.|

### <a name="return-value"></a>Valeur de retour

Le style étendu précédent.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message RB_SETEXTENDEDSTYLE,](/windows/win32/Controls/rb-setextendedstyle) qui est décrit dans le SDK Windows.

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a>CReBarCtrl::SetImageList

Assigne une liste d’images à un contrôle de barres d’armature.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*pImageList (en)*<br/>
Un pointeur vers un objet [CImageList](../../mfc/reference/cimagelist-class.md) contenant la liste d’images à attribuer au contrôle des barres d’armature.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlsetowner"></a><a name="setowner"></a>CReBarCtrl::SetOwner

Implémente le comportement du message Win32 [RB_SETPARENT](/windows/win32/Controls/rb-setparent), tel que décrit dans le SDK Windows.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Un pointeur `CWnd` à un objet à définir en tant que propriétaire du contrôle de barre d’armature.

### <a name="return-value"></a>Valeur de retour

Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est le propriétaire actuel du contrôle des barres d’armature.

### <a name="remarks"></a>Notes

Notez que cette fonction `CWnd` de membre utilise des indications pour les objets pour le propriétaire actuel et choisi du contrôle des barres d’armature, plutôt que des poignées aux fenêtres.

> [!NOTE]
> Cette fonction de membre ne change pas le parent réel qui a été fixé lors de la création du contrôle; il envoie plutôt des messages de notification à la fenêtre que vous spécifiez.

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a>CReBarCtrl::SetPalette

Implémente le comportement du message Win32 [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette), tel que décrit dans le SDK Windows.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Paramètres

*hPal (en)*<br/>
Un HPALETTE qui spécifie la nouvelle palette que le contrôle des barres d’armature utilisera.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CPalette](../../mfc/reference/cpalette-class.md) spécifiant la palette précédente du contrôle des barres d’armature.

### <a name="remarks"></a>Notes

Notez que cette `CPalette` fonction de membre utilise un objet comme valeur de retour, plutôt qu’un HPALETTE.

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a>CReBarCtrl::SetTextColor

Implémente le comportement du message Win32 [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor), tel que décrit dans le SDK Windows.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Clr*<br/>
Une valeur COLORREF qui représente la `CReBarCtrl` nouvelle couleur de texte dans l’objet.

### <a name="return-value"></a>Valeur de retour

La valeur [COLORREF](/windows/win32/gdi/colorref) représentant la couleur `CReBarCtrl` de texte précédente associée à l’objet.

### <a name="remarks"></a>Notes

Il est fourni pour soutenir la flexibilité de couleur de texte dans un contrôle de barre d’armature.

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a>CReBarCtrl::SetToolTips

Associe un contrôle de pointe d’outil avec un contrôle de barre d’armature.

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Paramètres

*pToolTip*<br/>
Un pointeur à un objet [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Notes

Vous devez `CToolTipCtrl` détruire l’objet quand vous en avez fini avec lui.

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme

Définit le style visuel du contrôle des barres d’armature.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Paramètres

*pszSubAppName*<br/>
Un pointeur à une chaîne Unicode qui contient le style visuel de barre d’armature à définir.

### <a name="return-value"></a>Valeur de retour

La valeur de retour n’est pas utilisée.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message [RB_SETWINDOWTHEME,](/windows/win32/Controls/rb-setwindowtheme) tel que décrit dans le SDK Windows.

## <a name="crebarctrlshowband"></a><a name="showband"></a>CReBarCtrl::ShowBand

Implémente le comportement du message Win32 [RB_SHOWBAND](/windows/win32/Controls/rb-showband), tel que décrit dans le SDK Windows.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Paramètres

*uBand (en)*<br/>
Indice zéro d’une bande dans le contrôle des barres d’armature.

*fShow*<br/>
Indique si la bande doit être montrée ou cachée. Si cette valeur est VRAI, le groupe sera montré. Sinon, le groupe sera caché.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a>CReBarCtrl::SizeToRect

Implémente le comportement du message Win32 [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect), tel que décrit dans le SDK Windows.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Une référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui spécifie le rectangle que le contrôle de la barre d’armature doit être dimensionné.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Notez que cette `CRect` fonction de membre utilise `RECT` un objet comme paramètre, plutôt qu’une structure.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
