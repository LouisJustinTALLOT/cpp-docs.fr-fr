---
title: CSliderCtrl (classe)
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
ms.openlocfilehash: 8fffdfc002b25fdcd72dcbbf53e7e6c321f55296
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502518"
---
# <a name="csliderctrl-class"></a>CSliderCtrl (classe)

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
|[CSliderCtrl::ClearSel](#clearsel)|Efface la sélection actuelle dans un contrôle Slider.|
|[CSliderCtrl::ClearTics](#cleartics)|Supprime les graduations actuelles d’un contrôle Slider.|
|[CSliderCtrl::Create](#create)|Crée un contrôle Slider et l’attache à un `CSliderCtrl` objet.|
|[CSliderCtrl::CreateEx](#createex)|Crée un contrôle Slider avec les styles étendus Windows spécifiés et l’attache à un `CSliderCtrl` objet.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Récupère le handle d’une fenêtre associée de contrôle Slider à un emplacement donné.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Récupère la taille du canal du contrôle Slider.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Récupère la taille de ligne d’un contrôle Slider.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Récupère le nombre de graduations dans un contrôle Slider.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Récupère la taille de page d’un contrôle Slider.|
|[CSliderCtrl::GetPos](#getpos)|Récupère la position actuelle du curseur.|
|[CSliderCtrl::GetRange](#getrange)|Récupère les positions minimale et maximale d’un curseur.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Récupère la position maximale d’un curseur.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Récupère la position minimale pour un curseur.|
|[CSliderCtrl::GetSelection](#getselection)|Récupère la plage de la sélection actuelle.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Récupère la longueur du curseur dans le contrôle TrackBar actuel.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Récupère la taille du curseur du contrôle Slider.|
|[CSliderCtrl::GetTic](#gettic)|Récupère la position de la graduation spécifiée.|
|[CSliderCtrl::GetTicArray](#getticarray)|Récupère le tableau des positions des graduations pour un contrôle Slider.|
|[CSliderCtrl::GetTicPos](#getticpos)|Récupère la position de la graduation spécifiée, en coordonnées clientes.|
|[CSliderCtrl::GetToolTips](#gettooltips)|Récupère le handle du contrôle ToolTip affecté au contrôle Slider, le cas échéant.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Assigne une fenêtre comme fenêtre associée pour un contrôle Slider.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Définit la taille de ligne d’un contrôle Slider.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Définit la taille de page d’un contrôle Slider.|
|[CSliderCtrl::SetPos](#setpos)|Définit la position actuelle du curseur.|
|[CSliderCtrl::SetRange](#setrange)|Définit les positions minimale et maximale d’un curseur.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Définit la position maximale d’un curseur.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Définit la position minimale d’un curseur.|
|[CSliderCtrl::SetSelection](#setselection)|Définit la plage de la sélection actuelle.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Définit la longueur du curseur dans le contrôle TrackBar actuel.|
|[CSliderCtrl::SetTic](#settic)|Définit la position de la graduation spécifiée.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Définit la fréquence des graduations par incrément du contrôle Slider.|
|[CSliderCtrl::SetTipSide](#settipside)|Positionne un contrôle ToolTip utilisé par un contrôle TrackBar.|
|[CSliderCtrl::SetToolTips](#settooltips)|Assigne un contrôle ToolTip à un contrôle Slider.|

## <a name="remarks"></a>Notes

Un « contrôle Slider » (également appelé TrackBar) est une fenêtre contenant un curseur et des graduations facultatives. Lorsque l’utilisateur déplace le curseur, à l’aide de la souris ou des touches de direction, le contrôle envoie des messages de notification pour indiquer la modification.

Les contrôles Slider sont utiles lorsque vous souhaitez que l’utilisateur sélectionne une valeur discrète ou un ensemble de valeurs consécutives dans une plage. Par exemple, vous pouvez utiliser un contrôle Slider pour permettre à l’utilisateur de définir la vitesse de répétition du clavier en déplaçant le curseur vers une graduation donnée.

Ce contrôle (et par conséquent `CSliderCtrl` la classe) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT version 3,51 et versions ultérieures.

Le curseur se déplace par incréments que vous spécifiez au moment de sa création. Par exemple, si vous spécifiez que le curseur doit avoir une plage de cinq, le curseur ne peut occuper que six positions : une position à gauche du contrôle Slider et une position pour chaque incrément de la plage. En règle générale, chacune de ces positions est identifiée par une graduation.

Vous créez un curseur à l’aide du constructeur et de `Create` la fonction membre `CSliderCtrl`de. Une fois que vous avez créé un contrôle Slider, vous pouvez utiliser des fonctions `CSliderCtrl` membres dans pour modifier un grand nombre de ses propriétés. Les modifications que vous pouvez apporter incluent la définition des positions minimale et maximale pour le curseur, le dessin des graduations, la définition d’une plage de sélection et le repositionnement du curseur.

Pour plus d’informations sur `CSliderCtrl`l’utilisation de, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="clearsel"></a>  CSliderCtrl::ClearSel

Efface la sélection actuelle dans un contrôle Slider.

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*bRedraw*<br/>
Indicateur de redessin. Si ce paramètre a la valeur TRUE, le curseur est redessiné après l’effacement de la sélection ; dans le cas contraire, le curseur n’est pas redessiné.

##  <a name="cleartics"></a>  CSliderCtrl::ClearTics

Supprime les graduations actuelles d’un contrôle Slider.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*bRedraw*<br/>
Indicateur de redessin. Si ce paramètre a la valeur TRUE, le curseur est redessiné après l’effacement des graduations ; dans le cas contraire, le curseur n’est pas redessiné.

##  <a name="create"></a>  CSliderCtrl::Create

Crée un contrôle Slider et l’attache à un `CSliderCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle Slider. Appliquez une combinaison quelconque de [styles de contrôle Slider](/windows/win32/Controls/trackbar-control-styles), décrite dans le SDK Windows, au contrôle.

*rect*<br/>
Spécifie la taille et la position du contrôle Slider. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle Slider, généralement `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle Slider.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’initialisation a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez `CSliderCtrl` un en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`appelez, qui crée le contrôle Slider et l’attache à l' `CSliderCtrl` objet.

Selon les valeurs définies pour *dwStyle*, le contrôle Slider peut avoir une orientation verticale ou horizontale. Elle peut avoir des graduations de part et d’autre, ou aucune des deux. Elle peut également être utilisée pour spécifier une plage de valeurs consécutives.

Pour appliquer des styles de fenêtre étendus au contrôle Slider, appelez [CreateEx](#createex) au `Create`lieu de.

##  <a name="createex"></a>  CSliderCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à `CSliderCtrl` l’objet.

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
Spécifie le style du contrôle Slider. Appliquez une combinaison quelconque de [styles de contrôle Slider](/windows/win32/Controls/trackbar-control-styles), décrite dans le SDK Windows, au contrôle.

*rect*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [Create](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_** .

##  <a name="csliderctrl"></a>  CSliderCtrl::CSliderCtrl

Construit un objet `CSliderCtrl`.

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>  CSliderCtrl::GetBuddy

Récupère le handle d’une fenêtre associée de contrôle Slider à un emplacement donné.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*fLocation*<br/>
Valeur booléenne qui indique le ou les deux handles de fenêtre associée à récupérer. Peut avoir l'une des valeurs suivantes :

- TRUE récupère le handle de l’ami à gauche du curseur. Si le contrôle Slider utilise le style TBS_VERT, le message récupère l’ami au-dessus du curseur.

- FALSe récupère le handle de l’ami à droite du curseur. Si le contrôle Slider utilise le style TBS_VERT, le message récupère l’ami sous le curseur.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre associée à l’emplacement spécifié par *FLOCATION*, ou null si aucune fenêtre associée n’existe à cet emplacement.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)de message Win32, comme décrit dans la SDK Windows. Pour obtenir une description des styles de contrôle Slider, consultez la rubrique [styles de contrôle TrackBar](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

##  <a name="getchannelrect"></a>  CSliderCtrl::GetChannelRect

Récupère la taille et la position du rectangle englobant pour le canal d’un contrôle Slider.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Paramètres

*lprc*<br/>
Pointeur vers un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient la taille et la position du rectangle englobant du canal quand la fonction retourne une valeur.

### <a name="remarks"></a>Notes

Le canal est la zone sur laquelle le curseur se déplace et qui contient la surbrillance lorsqu’une plage est sélectionnée.

##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize

Récupère la taille de la ligne pour un contrôle Slider.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Valeur de retour

Taille d’une ligne pour le contrôle Slider.

### <a name="remarks"></a>Notes

La taille de ligne affecte le déplacement du curseur pour les notifications TB_LINEUP et TB_LINEDOWN. La valeur par défaut de la taille de ligne est 1.

##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics

Récupère le nombre de graduations dans un contrôle Slider.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de graduations dans le contrôle Slider.

##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize

Récupère la taille de la page pour un contrôle Slider.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Valeur de retour

Taille d’une page pour le contrôle Slider.

### <a name="remarks"></a>Notes

La taille de la page a une incidence sur le déplacement du curseur pour les notifications TB_PAGEUP et TB_PAGEDOWN.

##  <a name="getpos"></a>  CSliderCtrl::GetPos

Récupère la position actuelle du curseur dans un contrôle Slider.

```
int GetPos() const;
```

### <a name="return-value"></a>Valeur de retour

Position actuelle.

##  <a name="getrange"></a>  CSliderCtrl::GetRange

Récupère les positions maximale et minimale du curseur dans un contrôle Slider.

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
Référence à un entier qui reçoit la position minimale.

*nMax*<br/>
Référence à un entier qui reçoit la position maximale.

### <a name="remarks"></a>Notes

Cette fonction copie les valeurs dans les entiers référencés par *nMin* et *nmax*.

##  <a name="getrangemax"></a>  CSliderCtrl::GetRangeMax

Récupère la position maximale du curseur dans un contrôle Slider.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valeur de retour

Position maximale du contrôle.

##  <a name="getrangemin"></a>  CSliderCtrl::GetRangeMin

Récupère la position minimale du curseur dans un contrôle Slider.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valeur de retour

Position minimale du contrôle.

##  <a name="getselection"></a>  CSliderCtrl::GetSelection

Récupère les positions de début et de fin de la sélection actuelle dans un contrôle Slider.

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
Référence à un entier qui reçoit la position de départ de la sélection actuelle.

*nMax*<br/>
Référence à un entier qui reçoit la position de fin de la sélection actuelle.

##  <a name="getthumblength"></a>  CSliderCtrl::GetThumbLength

Récupère la longueur du curseur dans le contrôle TrackBar actuel.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur du curseur, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength) , qui est décrit dans le SDK Windows.

##  <a name="getthumbrect"></a>  CSliderCtrl::GetThumbRect

Récupère la taille et la position du rectangle englobant pour le curseur (Thumb) dans un contrôle Slider.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Paramètres

*lprc*<br/>
Pointeur vers un `CRect` objet qui contient le rectangle englobant pour le curseur lorsque la fonction retourne.

##  <a name="gettic"></a>  CSliderCtrl::GetTic

Récupère la position d’une graduation dans un contrôle Slider.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Paramètres

*nTic*<br/>
Index de base zéro identifiant une graduation.

### <a name="return-value"></a>Valeur de retour

Position de la graduation spécifiée, ou-1 si *nTic* ne spécifie pas d’index valide.

##  <a name="getticarray"></a>  CSliderCtrl::GetTicArray

Récupère l’adresse du tableau contenant les positions des graduations pour un contrôle Slider.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Valeur de retour

Adresse du tableau contenant les positions des graduations du contrôle Slider.

##  <a name="getticpos"></a>  CSliderCtrl::GetTicPos

Récupère la position physique actuelle d’une graduation dans un contrôle Slider.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Paramètres

*nTic*<br/>
Index de base zéro identifiant une graduation.

### <a name="return-value"></a>Valeur de retour

Position physique, en coordonnées clientes, de la graduation spécifiée ou-1 si *nTic* ne spécifie pas d’index valide.

##  <a name="gettooltips"></a>  CSliderCtrl::GetToolTips

Récupère le handle du contrôle ToolTip affecté au contrôle Slider, le cas échéant.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) , ou null si les info-bulles ne sont pas utilisées. Si le contrôle Slider n’utilise pas le style TBS_TOOLTIPS, la valeur de retour est NULL.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)de message Win32, comme décrit dans la SDK Windows. Notez que cette fonction membre retourne un `CToolTipCtrl` objet au lieu d’un handle vers un contrôle.

Pour obtenir une description des styles de contrôle Slider, consultez la rubrique [styles de contrôle TrackBar](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

##  <a name="setbuddy"></a>  CSliderCtrl::SetBuddy

Assigne une fenêtre comme fenêtre associée pour un contrôle Slider.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWndBuddy*<br/>
Pointeur vers un `CWnd` objet qui sera défini en tant que associé du contrôle Slider.

*fLocation*<br/>
Valeur spécifiant l’emplacement d’affichage de la fenêtre associée. Cette valeur peut être l’une des suivantes :

- TRUE l’ami s’affiche à gauche du TrackBar si le contrôle TrackBar utilise le style TBS_HORZ. Si le TrackBar utilise le style TBS_VERT, l’ami s’affiche au-dessus du contrôle TrackBar.

- FALSe, l’ami apparaît à droite du TrackBar si le contrôle TrackBar utilise le style TBS_HORZ. Si le TrackBar utilise le style TBS_VERT, l’ami apparaît sous le contrôle TrackBar.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) précédemment assigné au contrôle Slider à cet emplacement.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)de message Win32, comme décrit dans la SDK Windows. Notez que cette fonction membre utilise des pointeurs `CWnd` vers des objets plutôt que des handles de fenêtre pour la valeur de retour et le paramètre.

Pour obtenir une description des styles de contrôle Slider, consultez la rubrique [styles de contrôle TrackBar](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize

Définit la taille de la ligne d’un contrôle Slider.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize*<br/>
Nouvelle taille de ligne du contrôle Slider.

### <a name="return-value"></a>Valeur de retour

Taille de ligne précédente.

### <a name="remarks"></a>Notes

La taille de ligne affecte le déplacement du curseur pour les notifications TB_LINEUP et TB_LINEDOWN.

##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize

Définit la taille de la page pour un contrôle Slider.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize*<br/>
Nouvelle taille de page du contrôle Slider.

### <a name="return-value"></a>Valeur de retour

Taille de page précédente.

### <a name="remarks"></a>Notes

La taille de la page a une incidence sur le déplacement du curseur pour les notifications TB_PAGEUP et TB_PAGEDOWN.

##  <a name="setpos"></a>  CSliderCtrl::SetPos

Définit la position actuelle du curseur dans un contrôle Slider.

```
void SetPos(int nPos);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Spécifie la nouvelle position du curseur.

##  <a name="setrange"></a>  CSliderCtrl::SetRange

Définit la plage (positions minimale et maximale) du curseur dans un contrôle Slider.

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
Position minimale du curseur.

*nMax*<br/>
Position maximale du curseur.

*bRedraw*<br/>
Indicateur de redessin. Si ce paramètre a la valeur TRUE, le curseur est redessiné après la définition de la plage ; dans le cas contraire, le curseur n’est pas redessiné.

##  <a name="setrangemax"></a>  CSliderCtrl::SetRangeMax

Définit la plage maximale du curseur dans un contrôle Slider.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*nMax*<br/>
Position maximale du curseur.

*bRedraw*<br/>
Indicateur de redessin. Si ce paramètre a la valeur TRUE, le curseur est redessiné après la définition de la plage ; dans le cas contraire, le curseur n’est pas redessiné.

##  <a name="setrangemin"></a>  CSliderCtrl::SetRangeMin

Définit la plage minimale du curseur dans un contrôle Slider.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
Position minimale du curseur.

*bRedraw*<br/>
Indicateur de redessin. Si ce paramètre a la valeur TRUE, le curseur est redessiné après la définition de la plage ; dans le cas contraire, le curseur n’est pas redessiné.

##  <a name="setselection"></a>  CSliderCtrl::SetSelection

Définit les positions de début et de fin de la sélection actuelle dans un contrôle Slider.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
Position de départ du curseur.

*nMax*<br/>
Position de fin du curseur.

##  <a name="setthumblength"></a>  CSliderCtrl::SetThumbLength

Définit la longueur du curseur dans le contrôle TrackBar actuel.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*nLength*|dans Longueur du curseur, en pixels.|

### <a name="remarks"></a>Notes

Cette méthode exige que le contrôle TrackBar soit défini sur [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) style.

Cette méthode envoie le message [TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable `m_sliderCtrl`,, qui est utilisée pour accéder au contrôle TrackBar actuel. L’exemple définit également une variable, `thumbLength`, qui est utilisée pour stocker la longueur par défaut du composant Thumb du contrôle TrackBar. Ces variables sont utilisées dans l’exemple suivant.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le composant Thumb du contrôle TrackBar à deux fois sa longueur par défaut.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>  CSliderCtrl::SetTic

Définit la position d’une graduation dans un contrôle Slider.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Paramètres

*nTic*<br/>
Position de la graduation. Ce paramètre doit spécifier une valeur positive.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la graduation est définie ; Sinon, 0.

##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq

Définit la fréquence d’affichage des graduations dans un curseur.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Paramètres

*nFreq*<br/>
Fréquence des graduations.

### <a name="remarks"></a>Notes

Par exemple, si la fréquence est définie sur 2, une graduation est affichée pour chaque autre incrément dans la plage du curseur. La valeur par défaut de la fréquence est 1 (autrement dit, chaque incrément de la plage est associé à une graduation).

Vous devez créer le contrôle avec le style TBS_AUTOTICKS pour utiliser cette fonction. Pour plus d’informations, consultez [CSliderCtrl :: Create](#create).

##  <a name="settipside"></a>  CSliderCtrl::SetTipSide

Positionne un contrôle ToolTip utilisé par un contrôle TrackBar.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Paramètres

*nLocation*<br/>
Valeur représentant l’emplacement d’affichage du contrôle ToolTip. Pour obtenir la liste des valeurs possibles, consultez le message Win32 [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside), comme décrit dans la SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur qui représente l’emplacement précédent du contrôle ToolTip. La valeur de retour est égale à l’une des valeurs possibles de *nemplacement*.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du TBM_SETTIPSIDE de message Win32, comme décrit dans la SDK Windows. Les contrôles Slider qui utilisent le style TBS_TOOLTIPS affichent des info-bulles. Pour obtenir une description des styles de contrôle Slider, consultez la rubrique [styles de contrôle TrackBar](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips

Assigne un contrôle ToolTip à un contrôle Slider.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Paramètres

*pWndTip*<br/>
Pointeur vers un objet [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) contenant les info-bulles à utiliser avec le contrôle Slider.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips)de message Win32, comme décrit dans la SDK Windows. Lorsqu’un contrôle Slider est créé avec le style TBS_TOOLTIPS, il crée un contrôle ToolTip par défaut qui apparaît à côté du curseur, affichant la position actuelle du curseur. Pour obtenir une description des styles de contrôle Slider, consultez la rubrique [styles de contrôle TrackBar](/windows/win32/Controls/trackbar-control-styles) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl, classe](../../mfc/reference/cprogressctrl-class.md)
