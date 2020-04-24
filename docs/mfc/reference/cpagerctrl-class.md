---
title: Classe CPagerCtrl
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
ms.openlocfilehash: cd27a3acf26abe39831089546df317679f2ecab6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753703"
---
# <a name="cpagerctrl-class"></a>Classe CPagerCtrl

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
|[CPagerCtrl::Créer](#create)|Crée un contrôle de téléavertisseur avec `CPagerCtrl` des styles spécifiés et l’attache à l’objet actuel.|
|[CPagerCtrl::CreateEx](#createex)|Crée un contrôle de téléavertisseur avec des `CPagerCtrl` styles étendus spécifiés et l’attache à l’objet actuel.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Permet ou désactive le pas de [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) messages à la fenêtre contenue dans le contrôle actuel du téléavertisseur.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Récupère la couleur de fond du contrôle actuel du téléavertisseur.|
|[CPagerCtrl::GetBorder](#getborder)|Récupère la taille de la bordure du contrôle actuel du téléavertisseur.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Récupère la taille du bouton du contrôle actuel du téléavertisseur.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Récupère l’état du bouton spécifié dans le contrôle actuel du téléavertisseur.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Récupère l’interface [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) pour le contrôle actuel du téléavertisseur.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Récupère la position de défilement du contrôle actuel du téléavertisseur.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Indique si le bouton spécifié du contrôle `pressed` actuel du téléavertisseur est en état.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Indique si le bouton spécifié du contrôle `grayed` actuel du téléavertisseur est en état.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Indique si le bouton spécifié du contrôle `hot` actuel du téléavertisseur est en état.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Indique si le bouton spécifié du contrôle `invisible` actuel du téléavertisseur est en état.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Indique si le bouton spécifié du contrôle `normal` actuel du téléavertisseur est en état.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Provoque le contrôle actuel du téléavertisseur de recalculer la taille de la fenêtre contenue.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Définit la couleur de fond du contrôle actuel du téléavertisseur.|
|[CPagerCtrl::SetBorder](#setborder)|Définit la taille de la bordure du contrôle actuel du téléavertisseur.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Définit la taille du bouton du contrôle actuel du téléavertisseur.|
|[CPagerCtrl::SetChild](#setchild)|Définit la fenêtre contenue pour le contrôle actuel du téléavertisseur.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Définit la position de défilement du contrôle actuel du téléavertisseur.|

## <a name="remarks"></a>Notes

Un contrôle de téléavertisseur est une fenêtre qui contient une autre fenêtre qui est linéaire et plus grande que la fenêtre contenante, et vous permet de faire défiler la fenêtre contenue dans la vue. Le contrôle du téléavertisseur affiche deux boutons de défilement qui disparaissent automatiquement lorsque la fenêtre contenue est défichée à son plus loin, et réapparaissent autrement. Vous pouvez créer un contrôle de téléavertisseur qui défile horizontalement ou verticalement.

Par exemple, si votre application dispose d’une barre d’outils qui n’est pas assez large pour afficher tous ses éléments, vous pouvez attribuer la barre d’outils à un contrôle de téléavertisseur et les utilisateurs seront en mesure de faire défiler la barre d’outils vers la gauche ou la droite pour accéder à tous les éléments. Microsoft Internet Explorer Version 4.0 (commctrl.dll version 4.71) introduit le contrôle du téléavertisseur.

La `CPagerCtrl` classe est dérivée de la classe [CWnd.](../../mfc/reference/cwnd-class.md) Pour plus d’informations et une illustration d’un contrôle de téléavertisseur, voir [Pager Controls](/windows/win32/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl

Construit un objet `CPagerCtrl`.

```
CPagerCtrl();
```

### <a name="remarks"></a>Notes

Utilisez le [CPagerCtrl::Créer](#create) ou [CPagerCtrl::CreateEx](#createex) méthode pour créer un `CPagerCtrl` contrôle de téléavertisseur et l’attacher à l’objet.

## <a name="cpagerctrlcreate"></a><a name="create"></a>CPagerCtrl::Créer

Crée un contrôle de téléavertisseur avec `CPagerCtrl` des styles spécifiés et l’attache à l’objet actuel.

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
|*dwStyle (en)*|[dans] Une combinaison bitwise (OU) de styles de [fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et de styles de [contrôle de téléavertisseur](/windows/win32/Controls/pager-control-styles) à appliquer au contrôle.|
|*Rect*|[dans] Une référence à une structure [RECT](/windows/win32/api/windef/ns-windef-rect) qui contient la position et la taille du contrôle dans les coordonnées des clients.|
|*pParentWnd*|[dans] Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle. Ce paramètre ne peut pas être NULL.|
|*nID*|[dans] L’id du contrôle.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Pour créer un contrôle de `CPagerCtrl` téléavertisseur, déclarez une variable, puis appelez le [CPagerCtrl::Créer](#create) ou [CPagerCtrl::CreateEx](#createex) méthode sur cette variable.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de téléavertisseur, puis utilise la méthode [CPagerCtrl::SetChild](#setchild) pour associer un contrôle de bouton très long avec le contrôle du téléavertisseur. L’exemple utilise ensuite la méthode [CPagerCtrl::SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle du téléavertisseur à 20 pixels, et la méthode [CPagerCtrl::SetBorder](#setborder) pour définir l’épaisseur de la bordure à 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a>CPagerCtrl::CreateEx

Crée un contrôle de téléavertisseur avec des `CPagerCtrl` styles étendus spécifiés et l’attache à l’objet actuel.

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
|*dwExStyle (en anglais)*|[dans] Une combinaison peu sage de styles étendus à appliquer au contrôle. Pour plus d’informations, consultez le paramètre *dwExStyle* de la fonction [CreateWindowEx.](/windows/win32/api/winuser/nf-winuser-createwindowexw)|
|*dwStyle (en)*|[dans] Une combinaison bitwise (OU) de styles de [fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et de styles de [contrôle de téléavertisseur](/windows/win32/Controls/pager-control-styles) à appliquer au contrôle.|
|*Rect*|[dans] Une référence à une structure [RECT](/windows/win32/api/windef/ns-windef-rect) qui contient la position et la taille du contrôle dans les coordonnées des clients.|
|*pParentWnd*|[dans] Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle. Ce paramètre ne peut pas être NULL.|
|*nID*|[dans] L’id du contrôle.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Pour créer un contrôle de `CPagerCtrl` téléavertisseur, déclarez une variable, puis appelez le [CPagerCtrl::Créer](#create) ou [CPagerCtrl::CreateEx](#createex) méthode sur cette variable.

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a>CPagerCtrl::ForwardMouse

Permet ou désactive le pas de [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) messages à la fenêtre contenue dans le contrôle actuel du téléavertisseur.

```cpp
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*bDe vers l’avant*|[dans] VRAI pour transmettre des messages de souris, ou FALSE pour ne pas transmettre les messages de souris.|

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_FORWARDMOUSE,](/windows/win32/Controls/pgm-forwardmouse) qui est décrit dans le SDK Windows.

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a>CPagerCtrl::GetBorder

Récupère la taille de la bordure du contrôle actuel du téléavertisseur.

```
int GetBorder() const;
```

### <a name="return-value"></a>Valeur de retour

La taille actuelle de la frontière, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETBORDER,](/windows/win32/Controls/pgm-getborder) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl::GetBorder](#getborder) pour récupérer l’épaisseur de la bordure du contrôle du téléavertisseur.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a>CPagerCtrl::GetBkColor

Récupère la couleur de fond du contrôle actuel du téléavertisseur.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) qui contient la couleur de fond actuelle du contrôle du téléavertisseur.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETBKCOLOR,](/windows/win32/Controls/pgm-getbkcolor) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl::SetBkColor](#setbkcolor) pour définir la couleur de fond du contrôle du téléavertisseur en rouge, et la méthode [CPagerCtrl::GetBkColor](#getbkcolor) pour confirmer que le changement a été effectué.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize

Récupère la taille du bouton du contrôle actuel du téléavertisseur.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille actuelle du bouton, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETBUTTONSIZE,](/windows/win32/Controls/pgm-getbuttonsize) qui est décrit dans le SDK Windows.

Si le contrôle du téléavertisseur a le style PGS_HORZ, la taille du bouton détermine la largeur des boutons de téléavertisseur, et si le contrôle du téléavertisseur a le style PGS_VERT, la taille du bouton détermine la hauteur des boutons de téléavertisseur. Pour plus d’informations, voir [Pager Control Styles](/windows/win32/Controls/pager-control-styles).

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a>CPagerCtrl::GetButtonState

Récupère l’état du bouton de défilement spécifié dans le contrôle actuel du téléavertisseur.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton (en)*|[dans] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle du téléavertisseur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle du téléavertisseur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, voir [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

L’état du bouton spécifié par le paramètre *iButton.* L’État est soit PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED, soit PGF_HOT. Pour plus d’informations, consultez la section Valeur de retour du [message PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) qui est décrit dans le SDK Windows.

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a>CPagerCtrl::GetDropTarget

Récupère l’interface [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) pour le contrôle actuel du téléavertisseur.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `IDropTarget` à l’interface pour le contrôle actuel du téléavertisseur.

### <a name="remarks"></a>Notes

`IDropTarget`est l’une des interfaces que vous implémentez pour prendre en charge les opérations de drag-and-drop dans votre application.

Cette méthode envoie le [message PGM_GETDROPTARGET,](/windows/win32/Controls/pgm-getdroptarget) qui est décrit dans le SDK Windows. L’appelant de cette méthode est `Release` responsable d’appeler le membre de l’interface [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) lorsque l’interface n’est plus nécessaire.

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a>CPagerCtrl::GetScrollPos

Récupère la position de défilement du contrôle actuel du téléavertisseur.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valeur de retour

La position de défilement actuel, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETPOS,](/windows/win32/Controls/pgm-getpos) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl::GetScrollPos](#getscrollpos) pour récupérer la position de défilement actuelle du contrôle du téléavertisseur. Si le contrôle du téléavertisseur n’est pas déjà défilé à zéro, la position la plus gauche, l’exemple utilise la méthode [CPagerCtrl::SetScrollPos](#setscrollpos) méthode pour définir la position de défilement à zéro.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed

Indique si le bouton de défilement spécifié du contrôle actuel du téléavertisseur est en état de pression.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton (en)*|[dans] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle du téléavertisseur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle du téléavertisseur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, voir [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton spécifié est en état de pression; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) qui est décrit dans le SDK Windows. Il teste ensuite si l’état qui est retourné est PGF_DEPRESSED. Pour plus d’informations, consultez la section Valeur de retour du [message PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed

Indique si le bouton de défilement spécifié du contrôle actuel du téléavertisseur est en état grisé.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton (en)*|[dans] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle du téléavertisseur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle du téléavertisseur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, voir [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton spécifié est en état grisé; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) qui est décrit dans le SDK Windows. Il teste ensuite si l’état qui est retourné est PGF_GRAYED. Pour plus d’informations, consultez la section Valeur de retour du [message PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot

Indique si le bouton de défilement spécifié du contrôle actuel du téléavertisseur est en état de chaleur.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton (en)*|[dans] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle du téléavertisseur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle du téléavertisseur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, voir [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton spécifié est en état chaud; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) qui est décrit dans le SDK Windows. Il teste ensuite si l’état qui est retourné est PGF_HOT. Pour plus d’informations, consultez la section Valeur de retour du [message PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible

Indique si le bouton de défilement spécifié du contrôle actuel du téléavertisseur est en état invisible.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton (en)*|[dans] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle du téléavertisseur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle du téléavertisseur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, voir [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton spécifié est en état invisible; autrement, FALSE.

### <a name="remarks"></a>Notes

Windows rend le bouton de défilement dans une direction particulière invisible lorsque la fenêtre contenue est défilé à son point le plus éloigné parce que cliquer davantage sur le bouton ne peut pas apporter plus de la fenêtre contenue en vue.

Cette méthode envoie le [message PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) qui est décrit dans le SDK Windows. Il teste ensuite si l’état qui est retourné est PGF_INVISIBLE. Pour plus d’informations, consultez la section Valeur de retour du [message PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) pour déterminer si les boutons de défilement gauche et droit du commandeur de téléavertisseur sont visibles.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal

Indique si le bouton de défilement spécifié du contrôle actuel du téléavertisseur est en état normal.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButton (en)*|[dans] Indique le bouton pour lequel l’état est récupéré. Si le style de contrôle du téléavertisseur est PGS_HORZ, spécifiez PGB_TOPORLEFT pour le bouton gauche et PGB_BOTTOMORRIGHT pour le bouton droit. Si le style de contrôle du téléavertisseur est PGS_VERT, spécifiez PGB_TOPORLEFT pour le bouton supérieur et PGB_BOTTOMORRIGHT pour le bouton inférieur. Pour plus d’informations, voir [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton spécifié est en état normal; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) qui est décrit dans le SDK Windows. Il teste ensuite si l’état qui est retourné est PGF_NORMAL. Pour plus d’informations, consultez la section Valeur de retour du [message PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a>CPagerCtrl::RecalcSize

Provoque le contrôle actuel du téléavertisseur de recalculer la taille de la fenêtre contenue.

```cpp
void RecalcSize();
```

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_RECALCSIZE,](/windows/win32/Controls/pgm-recalcsize) qui est décrit dans le SDK Windows. Par conséquent, le contrôle du téléavertisseur envoie la notification [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) pour obtenir les dimensions défilementables de la fenêtre contenue.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl::RecalcSize](#recalcsize) pour demander le contrôle actuel du téléavertisseur pour recalculer sa taille.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Exemple

L’exemple suivant utilise la [réflexion de message](../../mfc/tn062-message-reflection-for-windows-controls.md) pour permettre au contrôle du téléavertisseur de recalculer sa propre taille au lieu d’exiger le dialogue parent du contrôle pour effectuer le calcul. L’exemple tire `MyPagerCtrl` la classe de la [classe CPagerCtrl](../../mfc/reference/cpagerctrl-class.md), puis utilise une `OnCalcsize` carte de message pour associer la notification [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) avec le gestionnaire de notification. Dans cet exemple, le gestionnaire de notification définit la largeur et la hauteur du contrôle du téléavertisseur à des valeurs fixes.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a>CPagerCtrl::SetBkColor

Définit la couleur de fond du contrôle actuel du téléavertisseur.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*clrBk*|[dans] Une valeur [COLORREF](/windows/win32/gdi/colorref) qui contient la nouvelle couleur d’arrière-plan du contrôle du téléavertisseur.|

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) qui contient la couleur de fond précédente du contrôle du téléavertisseur.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_SETBKCOLOR,](/windows/win32/Controls/pgm-setbkcolor) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant utilise la méthode [CPagerCtrl::SetBkColor](#setbkcolor) pour définir la couleur de fond du contrôle du téléavertisseur en rouge, et la méthode [CPagerCtrl::GetBkColor](#getbkcolor) pour confirmer que le changement a été effectué.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a>CPagerCtrl::SetBorder

Définit la taille de la bordure du contrôle actuel du téléavertisseur.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iBorder (en)*|[dans] La nouvelle taille de la bordure, mesurée en pixels. Si le *paramètre iBorder* est négatif, la taille de la bordure est définie à zéro.|

### <a name="return-value"></a>Valeur de retour

La taille précédente de la frontière, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_SETBORDER,](/windows/win32/Controls/pgm-setborder) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de téléavertisseur, puis utilise la méthode [CPagerCtrl::SetChild](#setchild) pour associer un contrôle de bouton très long avec le contrôle du téléavertisseur. L’exemple utilise ensuite la méthode [CPagerCtrl::SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle du téléavertisseur à 20 pixels, et la méthode [CPagerCtrl::SetBorder](#setborder) pour définir l’épaisseur de la bordure à 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize

Définit la taille du bouton du contrôle actuel du téléavertisseur.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iButtonSize*|[dans] La nouvelle taille du bouton, mesurée en pixels.|

### <a name="return-value"></a>Valeur de retour

La taille du bouton précédent, mesurée en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_SETBUTTONSIZE,](/windows/win32/Controls/pgm-setpos) qui est décrit dans le SDK Windows.

Si le contrôle du téléavertisseur a le style PGS_HORZ, la taille du bouton détermine la largeur des boutons de téléavertisseur, et si le contrôle du téléavertisseur a le style PGS_VERT, la taille du bouton détermine la hauteur des boutons de téléavertisseur. La taille du bouton par défaut est des trois quarts de la largeur de la barre de défilement, et la taille minimale du bouton est de 12 pixels. Pour plus d’informations, voir [Pager Control Styles](/windows/win32/Controls/pager-control-styles).

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de téléavertisseur, puis utilise la méthode [CPagerCtrl::SetChild](#setchild) pour associer un contrôle de bouton très long avec le contrôle du téléavertisseur. L’exemple utilise ensuite la méthode [CPagerCtrl::SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle du téléavertisseur à 20 pixels, et la méthode [CPagerCtrl::SetBorder](#setborder) pour définir l’épaisseur de la bordure à 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a>CPagerCtrl::SetChild

Définit la fenêtre contenue pour le contrôle actuel du téléavertisseur.

```cpp
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*hwndChild*|[dans] Poignée à la fenêtre à contenir.|

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_SETCHILD,](/windows/win32/Controls/pgm-setchild) qui est décrit dans le SDK Windows.

Cette méthode ne change pas le parent de la fenêtre contenue; il n’attribue qu’une poignée de fenêtre au contrôle du téléavertisseur pour le défilement. Dans la plupart des cas, la fenêtre contenue sera une fenêtre enfant du contrôle du téléavertisseur.

### <a name="example"></a>Exemple

L’exemple suivant crée un contrôle de téléavertisseur, puis utilise la méthode [CPagerCtrl::SetChild](#setchild) pour associer un contrôle de bouton très long avec le contrôle du téléavertisseur. L’exemple utilise ensuite la méthode [CPagerCtrl::SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle du téléavertisseur à 20 pixels, et la méthode [CPagerCtrl::SetBorder](#setborder) pour définir l’épaisseur de la bordure à 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a>CPagerCtrl::SetScrollPos

Définit la position de défilement du contrôle actuel du téléavertisseur.

```cpp
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Offices*|[dans] La nouvelle position de défilement, mesurée en pixels.|

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PGM_SETPOS,](/windows/win32/Controls/pgm-setpos) qui est décrit dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Classe CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Contrôles De pager](/windows/win32/Controls/pager-controls)
