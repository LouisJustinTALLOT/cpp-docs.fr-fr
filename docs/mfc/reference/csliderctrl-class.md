---
title: Classe CSliderCtrl
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 2e3572b34f930bb6a7d99b437c01c8aaf970e6c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751275"
---
# <a name="csliderctrl-class"></a>Classe CSliderCtrl

Fournit les fonctionnalités du contrôle commun de curseur Windows.

## <a name="syntax"></a>Syntaxe

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Construit un objet `CSliderCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|Efface la sélection actuelle dans un contrôle de curseur.|
|[CSliderCtrl::ClearTics](#cleartics)|Supprime les marques de tiques actuelles d’un contrôle de curseur.|
|[CSliderCtrl::Créer](#create)|Crée un contrôle de curseur `CSliderCtrl` et le fixe à un objet.|
|[CSliderCtrl::CreateEx](#createex)|Crée un contrôle de curseur avec les styles `CSliderCtrl` Windows étendus spécifiés et le fixe à un objet.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Récupère la poignée à une fenêtre de contrôle de curseur copain à un endroit donné.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Récupère la taille du canal du contrôle du curseur.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Récupère la taille de la ligne d’un contrôle de curseur.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Récupère le nombre de marques de tiques dans un contrôle de curseur.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Récupère la taille de la page d’un contrôle de curseur.|
|[CSliderCtrl::GetPos](#getpos)|Récupère la position actuelle du curseur.|
|[CSliderCtrl::GetRange](#getrange)|Récupère les positions minimales et maximales pour un curseur.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Récupère la position maximale pour un curseur.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Récupère la position minimale pour un curseur.|
|[CSliderCtrl::GetSelection](#getselection)|Récupère la gamme de la sélection actuelle.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Récupère la longueur du curseur dans le contrôle actuel du guidon.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Récupère la taille du pouce du contrôle du curseur.|
|[CSliderCtrl::GetTic](#gettic)|Récupère la position de la marque de tique spécifiée.|
|[CSliderCtrl::GetTicArray](#getticarray)|Récupère la gamme de positions de marque de tiques pour un contrôle de curseur.|
|[CSliderCtrl::GetTicPos](#getticpos)|Récupère la position de la marque de tique spécifiée, dans les coordonnées des clients.|
|[CSliderCtrl::GetToolTips](#gettooltips)|Récupère la poignée au contrôle de la pointe d’outil assigné au contrôle du curseur, le cas échéant.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Assigne une fenêtre comme fenêtre de copain pour un contrôle de curseur.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Définit la taille de la ligne d’un contrôle de curseur.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Définit la taille de la page d’un contrôle de curseur.|
|[CSliderCtrl::SetPos](#setpos)|Définit la position actuelle du curseur.|
|[CSliderCtrl::SetRange](#setrange)|Définit les positions minimales et maximales pour un curseur.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Définit la position maximale pour un curseur.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Définit la position minimale pour un curseur.|
|[CSliderCtrl::SetSelection](#setselection)|Définit la gamme de la sélection actuelle.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Définit la longueur du curseur dans le contrôle actuel du guidon.|
|[CSliderCtrl::SetTic](#settic)|Définit la position de la marque de tique spécifiée.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Définit la fréquence des marques de tiques par incrément de contrôle du curseur.|
|[CSliderCtrl::SetTipSide](#settipside)|Positionne un contrôle de pointe utilisé par un contrôle de barre de piste.|
|[CSliderCtrl::SetToolTips](#settooltips)|Attribue un contrôle de pointe à un contrôle de curseur.|

## <a name="remarks"></a>Notes

Un « contrôle de curseur » (également connu sous le nom de barre de piste) est une fenêtre contenant un curseur et des marques de tiques facultatives. Lorsque l’utilisateur déplace le curseur, en utilisant la souris ou les touches de direction, le contrôle envoie des messages de notification pour indiquer la modification.

Les commandes de curseur sont utiles lorsque vous souhaitez que l’utilisateur sélectionne une valeur discrète ou un ensemble de valeurs consécutives dans une plage. Par exemple, vous pouvez utiliser un contrôle de curseur pour permettre à l’utilisateur de définir le taux de répétition du clavier en déplaçant le curseur vers une marque de tique donnée.

Ce contrôle (et `CSliderCtrl` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT version 3.51 et plus tard.

Le curseur se déplace par incréments que vous spécifiez lorsque vous le créez. Par exemple, si vous spécifiez que le curseur doit avoir une portée de cinq, le curseur ne peut occuper que six positions : une position sur le côté gauche du contrôle du curseur et une position pour chaque incrément dans la plage. Typiquement, chacune de ces positions est identifiée par une marque de tiques.

Vous créez un curseur en utilisant `Create` le `CSliderCtrl`constructeur et la fonction membre de . Une fois que vous avez créé un contrôle `CSliderCtrl` de curseur, vous pouvez utiliser les fonctions des membres pour changer beaucoup de ses propriétés. Les modifications que vous pouvez apporter comprennent la définition des positions minimales et maximales pour le curseur, le dessin des marques de tiques, la définition d’une plage de sélection et le repositionnement du curseur.

Pour plus d’informations sur l’utilisation `CSliderCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation [CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a>CSliderCtrl::ClearSel

Efface la sélection actuelle dans un contrôle de curseur.

```cpp
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*bRedraw (en)*<br/>
Drapeau redessiner. Si ce paramètre est VRAI, le curseur est redessiné après la sélection est effacé; sinon le curseur n’est pas redessiné.

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a>CSliderCtrl::ClearTics

Supprime les marques de tiques actuelles d’un contrôle de curseur.

```cpp
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*bRedraw (en)*<br/>
Drapeau redessiner. Si ce paramètre est VRAI, le curseur est redessiné après que les marques de tiques sont effacées; sinon le curseur n’est pas redessiné.

## <a name="csliderctrlcreate"></a><a name="create"></a>CSliderCtrl::Créer

Crée un contrôle de curseur `CSliderCtrl` et le fixe à un objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du contrôle du curseur. Appliquer toute combinaison de styles de [contrôle de curseur](/windows/win32/Controls/trackbar-control-styles), décrits dans le SDK Windows, sur le contrôle.

*Rect*<br/>
Spécifie la taille et la position du contrôle du curseur. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Spécifie la fenêtre parente du `CDialog`contrôle du curseur, généralement un . Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle du curseur.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CSliderCtrl` en deux étapes. Tout d’abord, appelez le `Create`constructeur, puis appelez , ce qui `CSliderCtrl` crée le contrôle du curseur et le fixe à l’objet.

Selon les valeurs définies pour *dwStyle*, le contrôle du curseur peut avoir une orientation verticale ou horizontale. Il peut avoir des marques de tiques de chaque côté, des deux côtés, ou ni l’un ni l’autre. Il peut également être utilisé pour spécifier une gamme de valeurs consécutives.

Pour appliquer des styles de fenêtre étendus au `Create`contrôle du curseur, appelez [CreateEx](#createex) au lieu de .

## <a name="csliderctrlcreateex"></a><a name="createex"></a>CSliderCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CSliderCtrl` et l’associe à l’objet.

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
Spécifie le style du contrôle du curseur. Appliquer toute combinaison de styles de [contrôle de curseur](/windows/win32/Controls/trackbar-control-styles), décrits dans le SDK Windows, sur le contrôle.

*Rect*<br/>
Une référence à une structure [RECT](/windows/win32/api/windef/ns-windef-rect) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl

Construit un objet `CSliderCtrl`.

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a>CSliderCtrl::GetBuddy

Récupère la poignée à une fenêtre de contrôle de curseur copain à un endroit donné.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*fLocation*<br/>
Une valeur Boolean qui indique laquelle des poignées de fenêtre de deux copains à récupérer. Il peut s'agir de l'une des valeurs suivantes :

- TRUE Récupère la poignée au copain à gauche du curseur. Si le contrôle du curseur utilise le style TBS_VERT, le message récupérera le copain au-dessus du curseur.

- FALSE Récupère la poignée au copain à droite du curseur. Si le contrôle du curseur utilise le style TBS_VERT, le message récupérera le copain en dessous du curseur.

### <a name="return-value"></a>Valeur de retour

Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre de copain à l’emplacement spécifié par *fLocation*, ou NULL si aucune fenêtre de copain n’existe à cet endroit.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy), tel que décrit dans le SDK Windows. Pour une description des styles de contrôle du curseur, voir [Trackbar Control Styles](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a>CSliderCtrl::GetChannelRect

Récupère la taille et la position du rectangle de délimitation pour le canal d’un contrôle de curseur.

```cpp
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Paramètres

*lprc (lprc)*<br/>
Pointeur d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient la taille et la position du rectangle de délimitation du canal lorsque la fonction revient.

### <a name="remarks"></a>Notes

Le canal est la zone sur laquelle le curseur se déplace et qui contient le point culminant quand une plage est sélectionnée.

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a>CSliderCtrl::GetLineSize

Récupère la taille de la ligne pour un contrôle de curseur.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille d’une ligne pour le contrôle du curseur.

### <a name="remarks"></a>Notes

La taille de la ligne influe sur la quantité de mouvements du curseur pour les notifications TB_LINEUP et TB_LINEDOWN. Le paramètre par défaut pour la taille de la ligne est de 1.

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a>CSliderCtrl::GetNumTics

Récupère le nombre de marques de tiques dans un contrôle de curseur.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de marques de tiques dans le contrôle du curseur.

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a>CSliderCtrl::GetPageSize

Récupère la taille de la page pour un contrôle de curseur.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille d’une page pour le contrôle du curseur.

### <a name="remarks"></a>Notes

La taille de la page influe sur la quantité de mouvements du curseur pour les notifications TB_PAGEUP et TB_PAGEDOWN.

## <a name="csliderctrlgetpos"></a><a name="getpos"></a>CSliderCtrl::GetPos

Récupère la position actuelle du curseur dans un contrôle de curseur.

```
int GetPos() const;
```

### <a name="return-value"></a>Valeur de retour

Position actuelle.

## <a name="csliderctrlgetrange"></a><a name="getrange"></a>CSliderCtrl::GetRange

Récupère les positions maximales et minimales pour le curseur dans un contrôle de curseur.

```cpp
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
Référence à un intégrant qui reçoit le poste minimum.

*Nmax*<br/>
Référence à un intégrant qui reçoit la position maximale.

### <a name="remarks"></a>Notes

Cette fonction copie les valeurs dans les entiers référencés par *nMin* et *nMax*.

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a>CSliderCtrl::GetRangeMax

Récupère la position maximale pour le curseur dans un contrôle de curseur.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valeur de retour

La position maximale du contrôle.

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a>CSliderCtrl::GetRangeMin

Récupère la position minimale pour le curseur dans un contrôle de curseur.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valeur de retour

La position minimale du contrôle.

## <a name="csliderctrlgetselection"></a><a name="getselection"></a>CSliderCtrl::GetSelection

Récupère les positions de départ et de fin de la sélection actuelle dans un contrôle de curseur.

```cpp
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
Référence à un intégrant qui reçoit la position de départ de la sélection actuelle.

*Nmax*<br/>
Référence à un intégrant qui reçoit la position de fin de la sélection actuelle.

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a>CSliderCtrl::GetThumbLength

Récupère la longueur du curseur dans le contrôle actuel du guidon.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur du curseur, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message TBM_GETTHUMBLENGTH,](/windows/win32/Controls/tbm-getthumblength) qui est décrit dans le SDK Windows.

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a>CSliderCtrl::GetThumbRect

Récupère la taille et la position du rectangle de délimitation pour le curseur (pouce) dans un contrôle de curseur.

```cpp
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Paramètres

*lprc (lprc)*<br/>
Un pointeur `CRect` vers un objet qui contient le rectangle de délimitation pour le curseur lorsque la fonction revient.

## <a name="csliderctrlgettic"></a><a name="gettic"></a>CSliderCtrl::GetTic

Récupère la position d’une marque de tiques dans un contrôle de curseur.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Paramètres

*nTic (en)*<br/>
Indice zéro identifiant une marque de tiques.

### <a name="return-value"></a>Valeur de retour

La position de la marque de tique spécifiée ou - 1 si *nTic* ne spécifie pas un index valide.

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a>CSliderCtrl::GetTicArray

Récupère l’adresse du tableau contenant les positions des marques de tiques pour un contrôle de curseur.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Valeur de retour

L’adresse du tableau contenant des positions de marque de tiques pour le contrôle du curseur.

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a>CSliderCtrl::GetTicPos

Récupère la position physique actuelle d’une marque de tiques dans un contrôle de curseur.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Paramètres

*nTic (en)*<br/>
Indice zéro identifiant une marque de tiques.

### <a name="return-value"></a>Valeur de retour

La position physique, dans les coordonnées du client, de la marque de tique spécifiée ou - 1 si *nTic* ne spécifie pas un index valide.

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a>CSliderCtrl::GetToolTips

Récupère la poignée au contrôle de la pointe d’outil assigné au contrôle du curseur, le cas échéant.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un objet [CToolTipCtrl,](../../mfc/reference/ctooltipctrl-class.md) ou NULL si les outils ne sont pas utilisés. Si le contrôle du curseur n’utilise pas le style TBS_TOOLTIPS, la valeur de retour est NULL.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips), tel que décrit dans le SDK Windows. Notez que cette `CToolTipCtrl` fonction de membre renvoie un objet au lieu d’une poignée à un contrôle.

Pour une description des styles de contrôle du curseur, voir [Trackbar Control Styles](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a>CSliderCtrl::SetBuddy

Assigne une fenêtre comme fenêtre de copain pour un contrôle de curseur.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWndBuddy*<br/>
Un pointeur `CWnd` à un objet qui sera réglé comme le copain du contrôle du curseur.

*fLocation*<br/>
Valeur spécifiant l’emplacement où afficher la fenêtre du copain. Cette valeur peut être l'une des suivantes :

- VRAI Le copain apparaîtra à gauche de la barre de piste si le contrôle du guidon utilise le style TBS_HORZ. Si la barre de piste utilise le style TBS_VERT, le copain apparaît au-dessus du contrôle du guidon.

- FALSE Le copain apparaîtra à droite de la barre de piste si le contrôle du guidon utilise le style TBS_HORZ. Si le guidon utilise le style TBS_VERT, le copain apparaît sous le contrôle du guidon.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui a été précédemment affecté au contrôle du curseur à cet endroit.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy), tel que décrit dans le SDK Windows. Notez que cette fonction `CWnd` de membre utilise des indications sur les objets, plutôt que des poignées de fenêtre pour sa valeur de retour et son paramètre.

Pour une description des styles de contrôle du curseur, voir [Trackbar Control Styles](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a>CSliderCtrl::SetLineSize

Définit la taille de la ligne pour un contrôle de curseur.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize (en)*<br/>
La nouvelle taille de la ligne du contrôle du curseur.

### <a name="return-value"></a>Valeur de retour

La taille de la ligne précédente.

### <a name="remarks"></a>Notes

La taille de la ligne influe sur la quantité de mouvements du curseur pour les notifications TB_LINEUP et TB_LINEDOWN.

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a>CSliderCtrl::SetPageSize

Définit la taille de la page pour un contrôle de curseur.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize (en)*<br/>
La nouvelle taille de la page du contrôle du curseur.

### <a name="return-value"></a>Valeur de retour

La taille de la page précédente.

### <a name="remarks"></a>Notes

La taille de la page influe sur la quantité de mouvements du curseur pour les notifications TB_PAGEUP et TB_PAGEDOWN.

## <a name="csliderctrlsetpos"></a><a name="setpos"></a>CSliderCtrl::SetPos

Définit la position actuelle du curseur dans un contrôle de curseur.

```cpp
void SetPos(int nPos);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Spécifie la nouvelle position du curseur.

## <a name="csliderctrlsetrange"></a><a name="setrange"></a>CSliderCtrl::SetRange

Définit la plage (positions minimales et maximales) pour le curseur dans un contrôle de curseur.

```cpp
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
Position minimale pour le curseur.

*Nmax*<br/>
Position maximale pour le curseur.

*bRedraw (en)*<br/>
Le drapeau redessiner. Si ce paramètre est VRAI, le curseur est redessiné après la mise en place de la plage; sinon le curseur n’est pas redessiné.

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a>CSliderCtrl::SetRangeMax

Définit la plage maximale pour le curseur dans un contrôle de curseur.

```cpp
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*Nmax*<br/>
Position maximale pour le curseur.

*bRedraw (en)*<br/>
Le drapeau redessiner. Si ce paramètre est VRAI, le curseur est redessiné après la mise en place de la plage; sinon le curseur n’est pas redessiné.

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a>CSliderCtrl::SetRangeMin

Définit la plage minimale pour le curseur dans un contrôle de curseur.

```cpp
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
Position minimale pour le curseur.

*bRedraw (en)*<br/>
Le drapeau redessiner. Si ce paramètre est VRAI, le curseur est redessiné après la mise en place de la plage; sinon le curseur n’est pas redessiné.

## <a name="csliderctrlsetselection"></a><a name="setselection"></a>CSliderCtrl::SetSelection

Définit les positions de départ et de fin de la sélection actuelle dans un contrôle de curseur.

```cpp
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
Position de départ pour le curseur.

*Nmax*<br/>
Position de fin pour le curseur.

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a>CSliderCtrl::SetThumbLength

Définit la longueur du curseur dans le contrôle actuel du guidon.

```cpp
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*nLength (en)*|[dans] Longueur du curseur, en pixels.|

### <a name="remarks"></a>Notes

Cette méthode exige que le contrôle du guidon soit réglé pour [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) style.

Cette méthode envoie le [message TBM_SETTHUMBLENGTH,](/windows/win32/Controls/tbm-setthumblength) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_sliderCtrl`définit la variable, qui est utilisée pour accéder au contrôle actuel du guidon. L’exemple définit également `thumbLength`une variable, qui est utilisée pour stocker la longueur par défaut du composant du pouce du contrôle de la barre de voie. Ces variables sont utilisées dans l’exemple suivant.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le composant du pouce du contrôle du guidon à deux fois sa longueur par défaut.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a>CSliderCtrl::SetTic

Définit la position d’une marque de tique dans un contrôle de curseur.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Paramètres

*nTic (en)*<br/>
Position de la marque de tique. Ce paramètre doit spécifier une valeur positive.

### <a name="return-value"></a>Valeur de retour

Nonzero si la marque de tique est définie; sinon 0.

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a>CSliderCtrl::SetTicFreq

Définit la fréquence avec laquelle les marques de tiques sont affichées dans un curseur.

```cpp
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Paramètres

*nFreq (en)*<br/>
Fréquence des marques de tiques.

### <a name="remarks"></a>Notes

Par exemple, si la fréquence est réglée à 2, une marque de tiques est affichée pour chaque autre incrément dans la plage du curseur. Le paramètre par défaut pour la fréquence est de 1 (c’est-à-dire que chaque incrément dans la plage est associé à une marque de tiques).

Vous devez créer le contrôle avec le style TBS_AUTOTICKS pour utiliser cette fonction. Pour plus d’informations, voir [CSliderCtrl::Créer](#create).

## <a name="csliderctrlsettipside"></a><a name="settipside"></a>CSliderCtrl::SetTipSide

Positionne un contrôle de pointe utilisé par un contrôle de barre de piste.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Paramètres

*nLocation*<br/>
Valeur représentant l’emplacement où afficher le contrôle de la pointe d’outil. Pour une liste de valeurs possibles, voir le message Win32 [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside), tel que décrit dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Une valeur qui représente l’emplacement précédent du contrôle de l’outil. La valeur de rendement est l’une des valeurs possibles pour *nLocation*.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 TBM_SETTIPSIDE, tel que décrit dans le SDK Windows. Contrôles de curseur qui utilisent les outils d’affichage de style TBS_TOOLTIPS. Pour une description des styles de contrôle du curseur, voir [Trackbar Control Styles](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a>CSliderCtrl::SetToolTips

Attribue un contrôle de pointe à un contrôle de curseur.

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Paramètres

*pWndTip*<br/>
Un pointeur à un objet [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) contenant les outils à utiliser avec le contrôle du curseur.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips), tel que décrit dans le SDK Windows. Lorsqu’un contrôle de curseur est créé avec le style TBS_TOOLTIPS, il crée un contrôle par défaut de bout d’outils qui apparaît à côté du curseur, affichant la position actuelle du curseur. Pour une description des styles de contrôle du curseur, voir [Trackbar Control Styles](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl, classe](../../mfc/reference/cprogressctrl-class.md)
