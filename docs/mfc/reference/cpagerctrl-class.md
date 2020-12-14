---
description: 'En savoir plus sur : classe CPagerCtrl'
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
ms.openlocfilehash: ba01d07ebd6d638a1d505d555e44e9562e4bd27b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345223"
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
|[CPagerCtrl :: CPagerCtrl](#cpagerctrl)|Construit un objet `CPagerCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPagerCtrl :: Create](#create)|Crée un contrôle de pagineur avec les styles spécifiés et l’attache à l' `CPagerCtrl` objet actuel.|
|[CPagerCtrl :: CreateEx](#createex)|Crée un contrôle de pagineur avec les styles étendus spécifiés et l’attache à l' `CPagerCtrl` objet actuel.|
|[CPagerCtrl :: ForwardMouse](#forwardmouse)|Active ou désactive le transfert de messages [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) à la fenêtre contenue dans le contrôle de pagineur actuel.|
|[CPagerCtrl :: GetBkColor](#getbkcolor)|Récupère la couleur d’arrière-plan du contrôle de pagineur actuel.|
|[CPagerCtrl :: GetBorder](#getborder)|Récupère la taille de bordure du contrôle de pagineur en cours.|
|[CPagerCtrl :: GetButtonSize](#getbuttonsize)|Récupère la taille de bouton du contrôle de pagineur actuel.|
|[CPagerCtrl :: GetButtonState](#getbuttonstate)|Récupère l’état du bouton spécifié dans le contrôle de pagineur actuel.|
|[CPagerCtrl :: GetDropTarget](#getdroptarget)|Récupère l’interface [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) pour le contrôle de pagineur actuel.|
|[CPagerCtrl :: GetScrollPos](#getscrollpos)|Récupère la position de défilement du contrôle de pagineur actuel.|
|[CPagerCtrl :: IsButtonDepressed](#isbuttondepressed)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans l' `pressed` État.|
|[CPagerCtrl :: IsButtonGrayed](#isbuttongrayed)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans l' `grayed` État.|
|[CPagerCtrl :: IsButtonHot](#isbuttonhot)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans l' `hot` État.|
|[CPagerCtrl :: IsButtonInvisible](#isbuttoninvisible)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans l' `invisible` État.|
|[CPagerCtrl :: IsButtonNormal](#isbuttonnormal)|Indique si le bouton spécifié du contrôle de pagineur actuel est dans l' `normal` État.|
|[CPagerCtrl :: RecalcSize](#recalcsize)|Fait en sorte que le contrôle de pagineur en cours recalcule la taille de la fenêtre contenue.|
|[CPagerCtrl :: SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan du contrôle de pagineur actuel.|
|[CPagerCtrl :: SetBorder](#setborder)|Définit la taille de bordure du contrôle de pagineur actuel.|
|[CPagerCtrl :: SetButtonSize](#setbuttonsize)|Définit la taille de bouton du contrôle de pagineur actuel.|
|[CPagerCtrl :: SetChild](#setchild)|Définit la fenêtre contenue pour le contrôle de pagineur en cours.|
|[CPagerCtrl :: SetScrollPos](#setscrollpos)|Définit la position de défilement du contrôle de pagineur actuel.|

## <a name="remarks"></a>Notes

Un contrôle de pagineur est une fenêtre qui contient une autre fenêtre linéaire et plus grande que la fenêtre conteneur, et vous permet de faire défiler la fenêtre contenue dans la vue. Le contrôle de pagineur affiche deux boutons de défilement qui disparaissent automatiquement quand la fenêtre contenue est défilant dans l’étendue la plus éloignée et qui s’affichent dans le cas contraire. Vous pouvez créer un contrôle de pagineur qui fait défiler horizontalement ou verticalement.

Par exemple, si votre application a une barre d’outils qui n’est pas assez grande pour afficher tous ses éléments, vous pouvez affecter la barre d’outils à un contrôle de pagineur et les utilisateurs pourront faire défiler la barre d’outils vers la gauche ou la droite pour accéder à tous les éléments. Microsoft Internet Explorer version 4,0 (commctrl.dll version 4,71) introduit le contrôle de pagineur.

La `CPagerCtrl` classe est dérivée de la classe [CWnd](../../mfc/reference/cwnd-class.md) . Pour plus d’informations et pour obtenir une illustration d’un contrôle de pagineur, consultez [contrôles de pagineur](/windows/win32/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a> CPagerCtrl :: CPagerCtrl

Construit un objet `CPagerCtrl`.

```
CPagerCtrl();
```

### <a name="remarks"></a>Notes

Utilisez la méthode [CPagerCtrl :: Create](#create) ou [CPagerCtrl :: CreateEx](#createex) pour créer un contrôle de pagineur et l’attacher à l' `CPagerCtrl` objet.

## <a name="cpagerctrlcreate"></a><a name="create"></a> CPagerCtrl :: Create

Crée un contrôle de pagineur avec les styles spécifiés et l’attache à l' `CPagerCtrl` objet actuel.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*\
dans Combinaison d’opérations de bits de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles) à appliquer au contrôle.

*rectangulaire*\
dans Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui contient la position et la taille du contrôle dans les coordonnées clientes.

*pParentWnd*\
dans Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle. Ce paramètre ne peut pas être NULL.

*nID*\
dans ID du contrôle.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Pour créer un contrôle de pagineur, déclarez une `CPagerCtrl` variable, puis appelez la méthode [CPagerCtrl :: Create](#create) ou [CPagerCtrl :: CreateEx](#createex) sur cette variable.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de pagineur, puis utilise la méthode [CPagerCtrl :: SetChild](#setchild) pour associer un contrôle de bouton très long au contrôle de pagineur. L’exemple utilise ensuite la méthode [CPagerCtrl :: SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle de pagineur à 20 pixels, et la méthode [CPagerCtrl :: setBorder](#setborder) pour définir l’épaisseur de la bordure sur 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a> CPagerCtrl :: CreateEx

Crée un contrôle de pagineur avec les styles étendus spécifiés et l’attache à l' `CPagerCtrl` objet actuel.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*\
dans Combinaison d’opérations de bits de styles étendus à appliquer au contrôle. Pour plus d’informations, consultez le paramètre *dwExStyle* de la fonction [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .

*dwStyle*\
dans Combinaison d’opérations de bits de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles) à appliquer au contrôle.

*rectangulaire*\
dans Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui contient la position et la taille du contrôle dans les coordonnées clientes.

*pParentWnd*\
dans Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle. Ce paramètre ne peut pas être NULL.

*nID*\
dans ID du contrôle.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Pour créer un contrôle de pagineur, déclarez une `CPagerCtrl` variable, puis appelez la méthode [CPagerCtrl :: Create](#create) ou [CPagerCtrl :: CreateEx](#createex) sur cette variable.

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a> CPagerCtrl :: ForwardMouse

Active ou désactive le transfert de messages [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) à la fenêtre contenue dans le contrôle de pagineur actuel.

```cpp
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Paramètres

*bForward*\
dans TRUE pour transférer les messages de la souris, ou FALSe pour ne pas les transférer.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse) , qui est décrit dans le SDK Windows.

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a> CPagerCtrl :: GetBorder

Récupère la taille de bordure du contrôle de pagineur en cours.

```
int GetBorder() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille de la bordure actuelle, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETBORDER](/windows/win32/Controls/pgm-getborder) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl :: GetBorder](#getborder) pour récupérer l’épaisseur de la bordure du contrôle de pagineur.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a> CPagerCtrl :: GetBkColor

Récupère la couleur d’arrière-plan du contrôle de pagineur actuel.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur [COLORREF](/windows/win32/gdi/colorref) qui contient la couleur d’arrière-plan actuelle du contrôle de pagineur.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl :: SetBkColor](#setbkcolor) pour définir la couleur d’arrière-plan du contrôle de pagineur sur rouge, et la méthode [CPagerCtrl :: GetBkColor](#getbkcolor) pour confirmer que la modification a été apportée.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a> CPagerCtrl :: GetButtonSize

Récupère la taille de bouton du contrôle de pagineur actuel.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille actuelle du bouton, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize) , qui est décrit dans le SDK Windows.

Si le contrôle de pagineur a le style de PGS_HORZ, la taille du bouton détermine la largeur des boutons du pagineur et, si le contrôle de pagineur a le style de PGS_VERT, la taille du bouton détermine la hauteur des boutons du pagineur. Pour plus d’informations, consultez [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles).

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a> CPagerCtrl :: GetButtonState

Récupère l’état du bouton de défilement spécifié dans le contrôle de pagineur actuel.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Paramètres

*iButton*\
dans Indique le bouton pour lequel l’État est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, consultez [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Valeur renvoyée

État du bouton spécifié par le paramètre *iButton* . L’État est PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED ou PGF_HOT. Pour plus d’informations, consultez la section valeur de retour du message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , qui est décrit dans le SDK Windows.

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a> CPagerCtrl :: GetDropTarget

Récupère l’interface [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) pour le contrôle de pagineur actuel.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `IDropTarget` interface pour le contrôle de pagineur en cours.

### <a name="remarks"></a>Notes

`IDropTarget` est l’une des interfaces que vous implémentez pour prendre en charge les opérations de glisser-déplacer dans votre application.

Cette méthode envoie le message [PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget) , qui est décrit dans le SDK Windows. L’appelant de cette méthode est chargé d’appeler le `Release` membre de l’interface [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) lorsque l’interface n’est plus nécessaire.

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a> CPagerCtrl :: GetScrollPos

Récupère la position de défilement du contrôle de pagineur actuel.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valeur renvoyée

Position de défilement actuelle, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETPOS](/windows/win32/Controls/pgm-getpos) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl :: GetScrollPos](#getscrollpos) pour récupérer la position de défilement actuelle du contrôle de pagineur. Si le contrôle de pagineur n’est pas déjà défilé sur zéro, la position la plus à gauche, l’exemple utilise la méthode [CPagerCtrl :: SetScrollPos](#setscrollpos) pour définir la position de défilement sur zéro.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a> CPagerCtrl :: IsButtonDepressed

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans l’état enfoncé.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Paramètres

*iButton*\
dans Indique le bouton pour lequel l’État est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, consultez [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton spécifié est à l’état enfoncé ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , qui est décrit dans le SDK Windows. Il teste ensuite si l’état retourné est PGF_DEPRESSED. Pour plus d’informations, consultez la section valeur de retour du message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a> CPagerCtrl :: IsButtonGrayed

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est grisé.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Paramètres

*iButton*\
dans Indique le bouton pour lequel l’État est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, consultez [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton spécifié est grisé ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , qui est décrit dans le SDK Windows. Il teste ensuite si l’état retourné est PGF_GRAYED. Pour plus d’informations, consultez la section valeur de retour du message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a> CPagerCtrl :: IsButtonHot

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans un état actif.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Paramètres

*iButton*\
dans Indique le bouton pour lequel l’État est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, consultez [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton spécifié est à l’état actif ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , qui est décrit dans le SDK Windows. Il teste ensuite si l’état retourné est PGF_HOT. Pour plus d’informations, consultez la section valeur de retour du message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a> CPagerCtrl :: IsButtonInvisible

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans un État invisible.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Paramètres

*iButton*\
dans Indique le bouton pour lequel l’État est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, consultez [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton spécifié est dans un État invisible ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Windows rend le bouton de défilement dans une direction particulière invisible quand la fenêtre contenue est défilant dans son étendue la plus éloignée car le fait de cliquer sur le bouton ne peut plus faire apparaître plus d’une fenêtre contenue dans la vue.

Cette méthode envoie le message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , qui est décrit dans le SDK Windows. Il teste ensuite si l’état retourné est PGF_INVISIBLE. Pour plus d’informations, consultez la section valeur de retour du message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl :: IsButtonInvisible](#isbuttoninvisible) pour déterminer si les boutons de défilement vers la gauche et vers la droite du contrôle de pagineur sont visibles.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a> CPagerCtrl :: IsButtonNormal

Indique si le bouton de défilement spécifié du contrôle de pagineur actuel est dans un état normal.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Paramètres

*iButton*\
dans Indique le bouton pour lequel l’État est récupéré. Si le style de contrôle de pagineur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle de pagineur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, consultez [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles).

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton spécifié est dans un état normal ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , qui est décrit dans le SDK Windows. Il teste ensuite si l’état retourné est PGF_NORMAL. Pour plus d’informations, consultez la section valeur de retour du message [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a> CPagerCtrl :: RecalcSize

Fait en sorte que le contrôle de pagineur en cours recalcule la taille de la fenêtre contenue.

```cpp
void RecalcSize();
```

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize) , qui est décrit dans le SDK Windows. Par conséquent, le contrôle de pagineur envoie la notification [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) pour obtenir les dimensions déroulantes de la fenêtre contenue.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl :: RecalcSize](#recalcsize) pour demander au contrôle de pagineur actuel de recalculer sa taille.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Exemple

L’exemple suivant utilise la [réflexion de message](../../mfc/tn062-message-reflection-for-windows-controls.md) pour permettre au contrôle de pagineur de recalculer sa propre taille au lieu d’exiger que la boîte de dialogue parente du contrôle effectue le calcul. L’exemple dérive la `MyPagerCtrl` classe de la [classe CPagerCtrl](../../mfc/reference/cpagerctrl-class.md), puis utilise une table des messages pour associer la notification [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) au `OnCalcsize` Gestionnaire de notifications. Dans cet exemple, le gestionnaire de notification définit la largeur et la hauteur du contrôle de pagineur sur des valeurs fixes.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a> CPagerCtrl :: SetBkColor

Définit la couleur d’arrière-plan du contrôle de pagineur actuel.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Paramètres

*clrBk*\
dans Valeur [COLORREF](/windows/win32/gdi/colorref) qui contient la nouvelle couleur d’arrière-plan du contrôle de pagineur.

### <a name="return-value"></a>Valeur renvoyée

Valeur [COLORREF](/windows/win32/gdi/colorref) qui contient la couleur d’arrière-plan précédente du contrôle de pagineur.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl :: SetBkColor](#setbkcolor) pour définir la couleur d’arrière-plan du contrôle de pagineur sur rouge, et la méthode [CPagerCtrl :: GetBkColor](#getbkcolor) pour confirmer que la modification a été apportée.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a> CPagerCtrl :: SetBorder

Définit la taille de bordure du contrôle de pagineur actuel.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Paramètres

*iBorder*\
dans Nouvelle taille de bordure, exprimée en pixels. Si le paramètre *iBorder* est négatif, la taille de la bordure est définie sur zéro.

### <a name="return-value"></a>Valeur renvoyée

Taille de la bordure précédente, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_SETBORDER](/windows/win32/Controls/pgm-setborder) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de pagineur, puis utilise la méthode [CPagerCtrl :: SetChild](#setchild) pour associer un contrôle de bouton très long au contrôle de pagineur. L’exemple utilise ensuite la méthode [CPagerCtrl :: SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle de pagineur à 20 pixels, et la méthode [CPagerCtrl :: setBorder](#setborder) pour définir l’épaisseur de la bordure sur 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a> CPagerCtrl :: SetButtonSize

Définit la taille de bouton du contrôle de pagineur actuel.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Paramètres

*iButtonSize*\
dans Nouvelle taille du bouton, mesurée en pixels.

### <a name="return-value"></a>Valeur renvoyée

Taille du bouton précédent, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos) , qui est décrit dans le SDK Windows.

Si le contrôle de pagineur a le style de PGS_HORZ, la taille du bouton détermine la largeur des boutons du pagineur et, si le contrôle de pagineur a le style de PGS_VERT, la taille du bouton détermine la hauteur des boutons du pagineur. La taille de bouton par défaut est trois-quarts de la largeur de la barre de défilement, tandis que la taille minimale du bouton est de 12 pixels. Pour plus d’informations, consultez [styles de contrôle de pagineur](/windows/win32/Controls/pager-control-styles).

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de pagineur, puis utilise la méthode [CPagerCtrl :: SetChild](#setchild) pour associer un contrôle de bouton très long au contrôle de pagineur. L’exemple utilise ensuite la méthode [CPagerCtrl :: SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle de pagineur à 20 pixels, et la méthode [CPagerCtrl :: setBorder](#setborder) pour définir l’épaisseur de la bordure sur 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a> CPagerCtrl :: SetChild

Définit la fenêtre contenue pour le contrôle de pagineur en cours.

```cpp
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Paramètres

*hwndChild*\
dans Handle de la fenêtre à contenu.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_SETCHILD](/windows/win32/Controls/pgm-setchild) , qui est décrit dans le SDK Windows.

Cette méthode ne modifie pas le parent de la fenêtre contenue ; Il assigne uniquement un handle de fenêtre au contrôle de pagineur pour le défilement. Dans la plupart des cas, la fenêtre contenue est une fenêtre enfant du contrôle pager.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de pagineur, puis utilise la méthode [CPagerCtrl :: SetChild](#setchild) pour associer un contrôle de bouton très long au contrôle de pagineur. L’exemple utilise ensuite la méthode [CPagerCtrl :: SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle de pagineur à 20 pixels, et la méthode [CPagerCtrl :: setBorder](#setborder) pour définir l’épaisseur de la bordure sur 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a> CPagerCtrl :: SetScrollPos

Définit la position de défilement du contrôle de pagineur actuel.

```cpp
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Paramètres

*iPos*\
dans Nouvelle position de défilement, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PGM_SETPOS](/windows/win32/Controls/pgm-setpos) , qui est décrit dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CPagerCtrl, classe](../../mfc/reference/cpagerctrl-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Contrôles de pagineur](/windows/win32/Controls/pager-controls)
