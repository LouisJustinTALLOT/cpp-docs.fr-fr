---
title: CPagerCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
ms.openlocfilehash: 648bc17f0f130b831aa619b90ed13ba6be35b4d4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417580"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl, classe

La classe `CPagerCtrl` inclut dans un wrapper le contrôle pager Windows, qui peut afficher une fenêtre contenue qui ne tient pas dans la fenêtre conteneur.

## <a name="syntax"></a>Syntaxe

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Construit un objet `CPagerCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPagerCtrl::Create](#create)|Crée un contrôle de pagineur avec des styles spécifiés et l’attache à actuel `CPagerCtrl` objet.|
|[CPagerCtrl::CreateEx](#createex)|Crée un contrôle de pagineur avec des styles étendus spécifiés et l’attache à actuel `CPagerCtrl` objet.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Active ou désactive le transfert [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) messages dans la fenêtre qui est contenue dans le contrôle pager actuel.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Récupère la couleur d’arrière-plan du contrôle de pagineur actuel.|
|[CPagerCtrl::GetBorder](#getborder)|Récupère la taille de bordure du contrôle de pagineur actuel.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Récupère la taille des boutons du contrôle de pagineur actuel.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Récupère l’état du bouton spécifié dans le contrôle pager actuel.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Récupère le [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interface pour le contrôle de pagineur actuel.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Récupère la position de défilement du contrôle de pagineur actuel.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans `pressed` état.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans `grayed` état.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans `hot` état.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans `invisible` état.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans `normal` état.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Force le contrôle de pagineur actuel à recalculer la taille de la fenêtre de relation contenant-contenue.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan du contrôle de pagineur actuel.|
|[CPagerCtrl::SetBorder](#setborder)|Définit la taille de bordure du contrôle de pagineur actuel.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Définit la taille des boutons du contrôle de pagineur actuel.|
|[CPagerCtrl::SetChild](#setchild)|Définit la fenêtre de relation contenant-contenue pour le contrôle de pagineur actuel.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Définit la position de défilement du contrôle de pagineur actuel.|

## <a name="remarks"></a>Notes

Un contrôle de pagineur est une fenêtre qui contient une autre fenêtre qui est linéaire et supérieure à la fenêtre conteneur et vous permet de faire défiler la fenêtre de relation contenant-contenue dans la vue. Le contrôle de pagineur affiche deux boutons de défilement qui disparaissent automatiquement lorsque vous faites défiler la fenêtre de relation contenant-contenue à son étendue plus éloignée et réapparaître dans le cas contraire. Vous pouvez créer un contrôle de pagineur qui fait défiler horizontalement ou verticalement.

Par exemple, si votre application comporte une barre d’outils n’est pas assez large pour afficher tous ses éléments, vous pouvez affecter la barre d’outils à un contrôle de pagineur et les utilisateurs pourront faire défiler la barre d’outils à gauche ou droite pour accéder à tous les éléments. Microsoft Internet Explorer Version 4.0 (version commctrl.dll 4.71) présente le contrôle de pagineur.

Le `CPagerCtrl` classe est dérivée de la [CWnd](../../mfc/reference/cwnd-class.md) classe. Pour plus d’informations et obtenir une illustration d’un contrôle de pagineur, consultez [contrôles Pager](/windows/desktop/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="cpagerctrl"></a>  CPagerCtrl::CPagerCtrl

Construit un objet `CPagerCtrl`.

```
CPagerCtrl();
```

### <a name="remarks"></a>Notes

Utilisez le [CPagerCtrl::Create](#create) ou [CPagerCtrl::CreateEx](#createex) méthode pour créer un contrôle de pagineur et l’attacher à la `CPagerCtrl` objet.

##  <a name="create"></a>  CPagerCtrl::Create

Crée un contrôle de pagineur avec des styles spécifiés et l’attache à actuel `CPagerCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwStyle*|[in] Une combinaison au niveau du bit (ou) de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles) à appliquer au contrôle.|
|*rect*|[in] Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure qui contient la position et la taille du contrôle dans les coordonnées clientes.|
|*pParentWnd*|[in] Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parent du contrôle. Ce paramètre ne peut pas être NULL.|
|*nID*|[in] L’ID du contrôle.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Pour créer un contrôle de pagineur, déclarez un `CPagerCtrl` variable, puis appelez le [CPagerCtrl::Create](#create) ou [CPagerCtrl::CreateEx](#createex) méthode sur cette variable.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de pagineur, puis utilise le [CPagerCtrl::SetChild](#setchild) méthode pour associer un contrôle de bouton très longue avec le contrôle de pagineur. L’exemple utilise ensuite la [CPagerCtrl::SetButtonSize](#setbuttonsize) méthode pour définir la hauteur du contrôle de pagineur à 20 pixels et le [CPagerCtrl::SetBorder](#setborder) méthode pour définir l’épaisseur de bordure de 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>  CPagerCtrl::CreateEx

Crée un contrôle de pagineur avec des styles étendus spécifiés et l’attache à actuel `CPagerCtrl` objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwExStyle*|[in] Une combinaison au niveau du bit des styles étendus à appliquer au contrôle. Pour plus d’informations, consultez le *dwExStyle* paramètre de la [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) (fonction).|
|*dwStyle*|[in] Une combinaison au niveau du bit (ou) de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles) à appliquer au contrôle.|
|*rect*|[in] Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure qui contient la position et la taille du contrôle dans les coordonnées clientes.|
|*pParentWnd*|[in] Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parent du contrôle. Ce paramètre ne peut pas être NULL.|
|*nID*|[in] L’ID du contrôle.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Pour créer un contrôle de pagineur, déclarez un `CPagerCtrl` variable, puis appelez le [CPagerCtrl::Create](#create) ou [CPagerCtrl::CreateEx](#createex) méthode sur cette variable.

##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse

Active ou désactive le transfert [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) messages dans la fenêtre qui est contenue dans le contrôle pager actuel.

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*bForward*|[in] True pour les messages de la souris vers l’avant, ou FALSE pour ne pas transférer les messages de la souris.|

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_FORWARDMOUSE](/windows/desktop/Controls/pgm-forwardmouse) message, qui est décrite dans le SDK Windows.

##  <a name="getborder"></a>  CPagerCtrl::GetBorder

Récupère la taille de bordure du contrôle de pagineur actuel.

```
int GetBorder() const;
```

### <a name="return-value"></a>Valeur de retour

La taille actuelle de la bordure, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETBORDER](/windows/desktop/Controls/pgm-getborder) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise le [CPagerCtrl::GetBorder](#getborder) méthode pour récupérer l’épaisseur de bordure du contrôle de pagineur.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor

Récupère la couleur d’arrière-plan du contrôle de pagineur actuel.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui contient la couleur d’arrière-plan actuelle du contrôle de pagineur.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETBKCOLOR](/windows/desktop/Controls/pgm-getbkcolor) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise le [CPagerCtrl::SetBkColor](#setbkcolor) méthode pour définir la couleur d’arrière-plan du contrôle de pagineur en rouge et la [CPagerCtrl::GetBkColor](#getbkcolor) méthode pour vérifier que la modification a été apportée.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize

Récupère la taille des boutons du contrôle de pagineur actuel.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille actuelle du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETBUTTONSIZE](/windows/desktop/Controls/pgm-getbuttonsize) message, qui est décrite dans le SDK Windows.

Si le contrôle de pagineur a le style PGS_HORZ, la taille du bouton détermine la largeur des boutons du pagineur et si le contrôle de pagineur a le style PGS_VERT, la taille du bouton détermine la hauteur des boutons du pagineur. Pour plus d’informations, consultez [Styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles).

##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState

Récupère l’état du bouton de défilement spécifiée dans le contrôle pager actuel.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton*|[in] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton en haut et PGB_BOTTOMORRIGHT pour le bouton du bas. Pour plus d’informations, consultez [Styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

L’état du bouton spécifié par le *iButton* paramètre. L’état est PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED ou PGF_HOT. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message, qui est décrite dans le SDK Windows.

##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget

Récupère le [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interface pour le contrôle de pagineur actuel.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `IDropTarget` interface pour le contrôle de pagineur actuel.

### <a name="remarks"></a>Notes

`IDropTarget` est une des interfaces vous implémenter pour prendre en charge les opérations de glisser-déplacer dans votre application.

Cette méthode envoie le [PGM_GETDROPTARGET](/windows/desktop/Controls/pgm-getdroptarget) message, qui est décrite dans le SDK Windows. L’appelant de cette méthode est chargée d’appeler le `Release` membre de la [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interface lors de l’interface n’est plus nécessaire.

##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos

Récupère la position de défilement du contrôle de pagineur actuel.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valeur de retour

La position de défilement actuelle, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETPOS](/windows/desktop/Controls/pgm-getpos) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise le [CPagerCtrl::GetScrollPos](#getscrollpos) méthode pour récupérer la position de défilement actuelle du contrôle de pagineur. Si le contrôle pager ne défile pas déjà à zéro, la position à l’extrême gauche, l’exemple utilise le [CPagerCtrl::SetScrollPos](#setscrollpos) méthode pour définir la position de défilement à zéro.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans un état appuyé.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton*|[in] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton en haut et PGB_BOTTOMORRIGHT pour le bouton du bas. Pour plus d’informations, consultez [Styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton spécifié est dans l’état enfoncé ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message, qui est décrite dans le SDK Windows. Il vérifie ensuite si l’état renvoyé est PGF_DEPRESSED. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message.

##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans un état grisé.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton*|[in] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton en haut et PGB_BOTTOMORRIGHT pour le bouton du bas. Pour plus d’informations, consultez [Styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton spécifié est dans un état grisé ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message, qui est décrite dans le SDK Windows. Il vérifie ensuite si l’état renvoyé est PGF_GRAYED. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message.

##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans un état actif.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton*|[in] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton en haut et PGB_BOTTOMORRIGHT pour le bouton du bas. Pour plus d’informations, consultez [Styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton spécifié est dans un état actif ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message, qui est décrite dans le SDK Windows. Il vérifie ensuite si l’état renvoyé est PGF_HOT. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message.

##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans un état invisible.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton*|[in] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton en haut et PGB_BOTTOMORRIGHT pour le bouton du bas. Pour plus d’informations, consultez [Styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton spécifié est dans un état invisible ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Windows rend le bouton de défilement dans une direction particulière invisible lorsque la fenêtre de relation contenant-contenue défile à son étendue plus éloigné, car en cliquant sur le bouton supplémentaire ne peut pas afficher de plus de la fenêtre contenue dans la vue.

Cette méthode envoie le [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message, qui est décrite dans le SDK Windows. Il vérifie ensuite si l’état renvoyé est PGF_INVISIBLE. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message.

### <a name="example"></a>Exemple

L’exemple suivant utilise le [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) méthode pour déterminer si le contrôle pager left et boutons de défilement vers la droite sont visibles.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans un état normal.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton*|[in] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton en haut et PGB_BOTTOMORRIGHT pour le bouton du bas. Pour plus d’informations, consultez [Styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton spécifié est dans un état normal ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message, qui est décrite dans le SDK Windows. Il vérifie ensuite si l’état renvoyé est PGF_NORMAL. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) message.

##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize

Force le contrôle de pagineur actuel à recalculer la taille de la fenêtre de relation contenant-contenue.

```
void RecalcSize();
```

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_RECALCSIZE](/windows/desktop/Controls/pgm-recalcsize) message, qui est décrite dans le SDK Windows. Par conséquent, le contrôle pager envoie le [PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize) notification pour obtenir les dimensions déroulantes de la fenêtre de relation contenant-contenue.

### <a name="example"></a>Exemple

L’exemple suivant utilise le [CPagerCtrl::RecalcSize](#recalcsize) méthode pour demander le contrôle pager actuel à recalculer sa taille.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Exemple

L’exemple suivant utilise [réflexion de message](../../mfc/tn062-message-reflection-for-windows-controls.md) pour activer le contrôle de pagineur à recalculer sa propre taille au lieu de demander la boîte de dialogue du contrôle parent pour effectuer le calcul. L’exemple dérive le `MyPagerCtrl` classe à partir de la [CPagerCtrl, classe](../../mfc/reference/cpagerctrl-class.md), utilise ensuite une table des messages à associer le [PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize) notification avec le `OnCalcsize` Gestionnaire de notification. Dans cet exemple, le Gestionnaire de notification définit la largeur et la hauteur du contrôle de pagineur à des valeurs fixes.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor

Définit la couleur d’arrière-plan du contrôle de pagineur actuel.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*clrBk*|[in] Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui contient la nouvelle couleur d’arrière-plan du contrôle de pagineur.|

### <a name="return-value"></a>Valeur de retour

Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui contient la couleur précédente de l’arrière-plan du contrôle de pagineur.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_SETBKCOLOR](/windows/desktop/Controls/pgm-setbkcolor) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise le [CPagerCtrl::SetBkColor](#setbkcolor) méthode pour définir la couleur d’arrière-plan du contrôle de pagineur en rouge et la [CPagerCtrl::GetBkColor](#getbkcolor) méthode pour vérifier que la modification a été apportée.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

Définit la taille de bordure du contrôle de pagineur actuel.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iBorder*|[in] La nouvelle taille de bordure, en pixels. Si le *iBorder* paramètre est négatif, la taille de la bordure est définie à zéro.|

### <a name="return-value"></a>Valeur de retour

La taille précédente de la bordure, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_SETBORDER](/windows/desktop/Controls/pgm-setborder) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de pagineur, puis utilise le [CPagerCtrl::SetChild](#setchild) méthode pour associer un contrôle de bouton très longue avec le contrôle de pagineur. L’exemple utilise ensuite la [CPagerCtrl::SetButtonSize](#setbuttonsize) méthode pour définir la hauteur du contrôle de pagineur à 20 pixels et le [CPagerCtrl::SetBorder](#setborder) méthode pour définir l’épaisseur de bordure de 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize

Définit la taille des boutons du contrôle de pagineur actuel.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButtonSize*|[in] La nouvelle taille du bouton, en pixels.|

### <a name="return-value"></a>Valeur de retour

La taille du bouton précédent, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_SETBUTTONSIZE](/windows/desktop/Controls/pgm-setpos) message, qui est décrite dans le SDK Windows.

Si le contrôle de pagineur a le style PGS_HORZ, la taille du bouton détermine la largeur des boutons du pagineur et si le contrôle de pagineur a le style PGS_VERT, la taille du bouton détermine la hauteur des boutons du pagineur. La taille du bouton par défaut est trois quarts de la largeur de la barre de défilement, et la taille de bouton minimale est de 12 pixels. Pour plus d’informations, consultez [Styles de contrôle de pagineur](/windows/desktop/Controls/pager-control-styles).

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de pagineur, puis utilise le [CPagerCtrl::SetChild](#setchild) méthode pour associer un contrôle de bouton très longue avec le contrôle de pagineur. L’exemple utilise ensuite la [CPagerCtrl::SetButtonSize](#setbuttonsize) méthode pour définir la hauteur du contrôle de pagineur à 20 pixels et le [CPagerCtrl::SetBorder](#setborder) méthode pour définir l’épaisseur de bordure de 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>  CPagerCtrl::SetChild

Définit la fenêtre de relation contenant-contenue pour le contrôle de pagineur actuel.

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*hwndChild*|[in] Handle de la fenêtre doit être contenu.|

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_SETCHILD](/windows/desktop/Controls/pgm-setchild) message, qui est décrite dans le SDK Windows.

Cette méthode ne modifie pas le parent de la fenêtre de relation contenant-contenu. Il affecte uniquement un handle de fenêtre pour le contrôle de pagineur pour le défilement. Dans la plupart des cas, la fenêtre de relation contenant-contenue sera une fenêtre enfant du contrôle de pagineur.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de pagineur, puis utilise le [CPagerCtrl::SetChild](#setchild) méthode pour associer un contrôle de bouton très longue avec le contrôle de pagineur. L’exemple utilise ensuite la [CPagerCtrl::SetButtonSize](#setbuttonsize) méthode pour définir la hauteur du contrôle de pagineur à 20 pixels et le [CPagerCtrl::SetBorder](#setborder) méthode pour définir l’épaisseur de bordure de 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos

Définit la position de défilement du contrôle de pagineur actuel.

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iPos*|[in] La nouvelle position de défilement, en pixels.|

### <a name="remarks"></a>Notes

Cette méthode envoie le [PGM_SETPOS](/windows/desktop/Controls/pgm-setpos) message, qui est décrite dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CPagerCtrl, classe](../../mfc/reference/cpagerctrl-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Contrôles de pagination](/windows/desktop/Controls/pager-controls)
