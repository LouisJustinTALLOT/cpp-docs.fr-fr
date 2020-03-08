---
title: CToolTipCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: bf32671eb3535de1bf072e24bc642145e87c84ee
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865446"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

Encapsule les fonctionnalités d'un « contrôle info-bulle », une petite fenêtre contextuelle qui affiche une ligne de texte unique qui décrit le rôle d'un outil dans une application.

## <a name="syntax"></a>Syntaxe

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CToolTipCtrl :: CToolTipCtrl](#ctooltipctrl)|Construit un objet `CToolTipCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CToolTipCtrl :: Activate](#activate)|Active et désactive le contrôle d’info-bulle.|
|[CToolTipCtrl :: AddTool](#addtool)|Inscrit un outil avec le contrôle d’info-bulle.|
|[CToolTipCtrl :: AdjustRect](#adjustrect)|Effectue une conversion entre le rectangle d’affichage de texte d’un contrôle d’info-bulle et le rectangle de sa fenêtre.|
|[CToolTipCtrl :: Create](#create)|Crée un contrôle d’info-bulle et l’attache à un objet `CToolTipCtrl`.|
|[CToolTipCtrl :: CreateEx](#createex)|Crée un contrôle d’info-bulle avec les styles étendus Windows spécifiés et l’attache à un objet `CToolTipCtrl`.|
|[CToolTipCtrl ::D elTool](#deltool)|Supprime un outil du contrôle d’info-bulle.|
|[CToolTipCtrl :: GetBubbleSize](#getbubblesize)|Récupère la taille de l’info-bulle.|
|[CToolTipCtrl :: GetCurrentTool](#getcurrenttool)|Récupère des informations, telles que la taille, la position et le texte, de la fenêtre d’info-bulle affichée par le contrôle ToolTip actuel.|
|[CToolTipCtrl :: GetDelayTime](#getdelaytime)|Récupère les durées initiales, contextuelles et de réaffichages qui sont actuellement définies pour un contrôle d’info-bulle.|
|[CToolTipCtrl :: GetMargin](#getmargin)|Récupère les marges supérieure, gauche, inférieure et droite définies pour une fenêtre d’info-bulle.|
|[CToolTipCtrl :: GetMaxTipWidth](#getmaxtipwidth)|Récupère la largeur maximale d’une fenêtre d’info-bulle.|
|[CToolTipCtrl :: GetText](#gettext)|Récupère le texte qu’un contrôle d’info-bulle gère pour un outil.|
|[CToolTipCtrl :: GetTipBkColor](#gettipbkcolor)|Récupère la couleur d’arrière-plan dans une fenêtre d’info-bulle.|
|[CToolTipCtrl :: GetTipTextColor](#gettiptextcolor)|Récupère la couleur de texte dans une fenêtre d’info-bulle.|
|[CToolTipCtrl :: GetTitle](#gettitle)|Récupère le titre du contrôle ToolTip actuel.|
|[CToolTipCtrl :: GetToolCount](#gettoolcount)|Récupère le nombre d’outils maintenus par un contrôle d’info-bulle.|
|[CToolTipCtrl :: GetToolInfo](#gettoolinfo)|Récupère les informations qu’un contrôle d’info-bulle gère à propos d’un outil.|
|[CToolTipCtrl :: HitTest](#hittest)|Teste un point pour déterminer s’il se trouve dans le rectangle englobant de l’outil donné. Dans ce cas, récupère des informations sur l’outil.|
|[CToolTipCtrl ::P op](#pop)|Supprime une fenêtre d’info-bulle affichée de l’affichage.|
|[CToolTipCtrl ::P opup](#popup)|Provoque l’affichage du contrôle ToolTip actuel aux coordonnées du dernier message de la souris.|
|[CToolTipCtrl :: RelayEvent](#relayevent)|Transmet un message de souris à un contrôle d’info-bulle pour traitement.|
|[CToolTipCtrl :: SetDelayTime](#setdelaytime)|Définit les durées initiales, contextuelles et de réaffichage pour un contrôle d’info-bulle.|
|[CToolTipCtrl :: SetMargin](#setmargin)|Définit les marges supérieure, gauche, inférieure et droite d’une fenêtre d’info-bulle.|
|[CToolTipCtrl :: SetMaxTipWidth](#setmaxtipwidth)|Définit la largeur maximale d’une fenêtre d’info-bulle.|
|[CToolTipCtrl :: SetTipBkColor](#settipbkcolor)|Définit la couleur d’arrière-plan dans une fenêtre d’info-bulle.|
|[CToolTipCtrl :: SetTipTextColor](#settiptextcolor)|Définit la couleur du texte dans une fenêtre d’info-bulle.|
|[CToolTipCtrl :: SetTitle](#settitle)|Ajoute une icône standard et une chaîne de titre à une info-bulle.|
|[CToolTipCtrl :: SetToolInfo](#settoolinfo)|Définit les informations gérées par une info-bulle pour un outil.|
|[CToolTipCtrl :: SetToolRect](#settoolrect)|Définit un nouveau rectangle englobant pour un outil.|
|[CToolTipCtrl :: SetWindowTheme](#setwindowtheme)|Définit le style visuel de la fenêtre d’info-bulle.|
|[CToolTipCtrl :: Update](#update)|Force le redessinage de l’outil actuel.|
|[CToolTipCtrl :: UpdateTipText](#updatetiptext)|Définit le texte d’info-bulle d’un outil.|

## <a name="remarks"></a>Notes

Un « outil » est une fenêtre, telle qu’une fenêtre ou un contrôle enfant, ou une zone rectangulaire définie par l’application dans la zone cliente d’une fenêtre. Une info-bulle est masquée la plupart du temps, n’apparaissant que lorsque l’utilisateur place le curseur sur un outil et le laisse pendant environ une demi-seconde. L’info-bulle apparaît près du curseur et disparaît lorsque l’utilisateur clique sur un bouton de la souris ou déplace le curseur de l’outil.

`CToolTipCtrl` fournit les fonctionnalités permettant de contrôler l’heure et la durée initiales de l’info-bulle, les largeurs de marge entourant le texte d’info-bulle, la largeur de la fenêtre d’info-bulle proprement dite et la couleur d’arrière-plan et de texte de l’info-bulle. Un seul contrôle d’info-bulle peut fournir des informations pour plusieurs outils.

La classe `CToolTipCtrl` fournit les fonctionnalités du contrôle commun d’info-bulle Windows. Ce contrôle (et par conséquent la classe `CToolTipCtrl`) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT versions 3,51 et ultérieures.

Pour plus d’informations sur l’activation des info-bulles, consultez info- [bulles dans Windows non dérivées de CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Pour plus d’informations sur l’utilisation de `CToolTipCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="activate"></a>CToolTipCtrl :: Activate

Appelez cette fonction pour activer ou désactiver un contrôle d’info-bulle.

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*bActivate*<br/>
Spécifie si le contrôle d’info-bulle doit être activé ou désactivé.

### <a name="remarks"></a>Notes

Si *bActivate* a la valeur true, le contrôle est activé ; Si la valeur est FALSe, elle est désactivée.

Lorsqu’un contrôle d’info-bulle est actif, les informations d’info-bulle s’affichent lorsque le curseur se trouve sur un outil inscrit avec le contrôle. lorsqu’il est inactif, les informations relatives aux info-bulles ne s’affichent pas, même lorsque le curseur se trouve sur un outil.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet :: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="addtool"></a>CToolTipCtrl :: AddTool

Inscrit un outil avec le contrôle d’info-bulle.

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDText*<br/>
ID de la ressource de type chaîne qui contient le texte de l’outil.

*lpRectTool*<br/>
Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) contenant les coordonnées du rectangle englobant de l’outil. Les coordonnées sont relatives au coin supérieur gauche de la zone cliente de la fenêtre identifiée par *pwnd*.

*nIDTool*<br/>
ID de l’outil.

*lpszText*<br/>
Pointeur vers le texte de l’outil. Si ce paramètre contient la valeur LPSTR_TEXTCALLBACK, TTN_NEEDTEXT messages de notification sont envoyés au parent de la fenêtre vers laquelle *pwnd* pointe.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les paramètres *lpRectTool* et *nIDTool* doivent être tous deux valides, ou si *lpRectTool* a la valeur null, *nIDTool* doit avoir la valeur 0.

Un contrôle d’info-bulle peut être associé à plusieurs outils. Appelez cette fonction pour inscrire un outil avec le contrôle d’info-bulle, afin que les informations stockées dans l’info-bulle s’affichent lorsque le curseur se trouve sur l’outil.

> [!NOTE]
>  Vous ne pouvez pas définir une info-bulle sur un contrôle statique à l’aide de `AddTool`.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet :: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="adjustrect"></a>CToolTipCtrl :: AdjustRect

Effectue une conversion entre le rectangle d’affichage de texte d’un contrôle ToolTip et le rectangle de sa fenêtre.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Paramètres

*lprc*<br/>
Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui contient un rectangle de fenêtre d’info-bulle ou un rectangle d’affichage de texte.

*bLarger*<br/>
Si la valeur est TRUE, *LPRC* est utilisé pour spécifier un rectangle d’affichage de texte et reçoit le rectangle de fenêtre correspondant. Si la valeur est FALSe, *LPRC* est utilisé pour spécifier un rectangle de fenêtre et reçoit le rectangle d’affichage de texte correspondant.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le rectangle est correctement ajusté ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre calcule le rectangle d’affichage du texte d’un contrôle d’info-bulle à partir du rectangle de sa fenêtre, ou le rectangle de la fenêtre d’info-bulle nécessaire pour afficher un rectangle d’affichage de texte spécifié.

Cette fonction membre implémente le comportement de la [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)de message Win32, comme décrit dans le SDK Windows.

##  <a name="create"></a>CToolTipCtrl :: Create

Crée un contrôle d’info-bulle et l’attache à un objet `CToolTipCtrl`.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle d’info-bulle, généralement un `CDialog`. Il ne doit pas être NULL.

*dwStyle*<br/>
Spécifie le style du contrôle d’info-bulle. Pour plus d’informations, consultez la section **Notes** .

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet `CToolTipCtrl` est créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez une `CToolTipCtrl` en deux étapes. Tout d’abord, appelez le constructeur pour construire l’objet `CToolTipCtrl`, puis appelez `Create` pour créer le contrôle d’info-bulle et l’attacher à l’objet `CToolTipCtrl`.

Le paramètre *dwStyle* peut être n’importe quelle combinaison de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles). En outre, un contrôle d’info-bulle a deux styles spécifiques à la classe : TTS_ALWAYSTIP et TTS_NOPREFIX.

|Style|Signification|
|-----------|-------------|
|TTS_ALWAYSTIP|Spécifie que l’info-bulle s’affiche lorsque le curseur se trouve sur un outil, que la fenêtre propriétaire du contrôle d’info-bulle soit active ou inactive. Sans ce style, le contrôle d’info-bulle apparaît lorsque la fenêtre propriétaire de l’outil est active, mais pas lorsqu’il est inactif.|
|TTS_NOPREFIX|Ce style empêche le système de déformer le caractère perluète (&) d’une chaîne. Si un contrôle d’info-bulle n’a pas le style de TTS_NOPREFIX, le système supprime automatiquement les caractères de l’esperluette, ce qui permet à une application d’utiliser la même chaîne qu’à la fois comme élément de menu et comme texte dans un contrôle d’info-bulle.|

Un contrôle d’info-bulle a les styles de fenêtre WS_POPUP et WS_EX_TOOLWINDOW, que vous les spécifiiez ou non lors de la création du contrôle.

Pour créer un contrôle d’info-bulle avec les styles Windows étendus, appelez [CToolTipCtrl :: CreateEx](#createex) au lieu de `Create`.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet :: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="createex"></a>CToolTipCtrl :: CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à l’objet `CToolTipCtrl`.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*dwStyle*<br/>
Spécifie le style du contrôle d’info-bulle. Pour plus d’informations, consultez la section **Notes** de la rubrique [Create](#create) .

*dwStyleEx*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de `Create` pour appliquer des styles Windows étendus, spécifiés par la préversion de style étendu Windows **WS_EX_** .

##  <a name="ctooltipctrl"></a>CToolTipCtrl :: CToolTipCtrl

Construit un objet `CToolTipCtrl`.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Notes

Vous devez appeler `Create` après la construction de l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>CToolTipCtrl ::D elTool

Supprime l’outil spécifié par *pwnd* et *nIDTool* de la collection d’outils pris en charge par un contrôle d’info-bulle.

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool*<br/>
ID de l’outil.

##  <a name="getbubblesize"></a>CToolTipCtrl :: GetBubbleSize

Récupère la taille de l’info-bulle.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Paramètres

*lpToolInfo*<br/>
Pointeur vers la structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) de l’info-bulle.

### <a name="return-value"></a>Valeur de retour

Taille de l’info-bulle.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)de message Win32, comme décrit dans le SDK Windows.

##  <a name="getcurrenttool"></a>CToolTipCtrl :: GetCurrentTool

Récupère des informations, telles que la taille, la position et le texte, de la fenêtre d’info-bulle affichée par le contrôle ToolTip actuel.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpToolInfo*|à Pointeur vers une structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) qui reçoit des informations sur la fenêtre d’info-bulle actuelle.|

### <a name="return-value"></a>Valeur de retour

TRUE si les informations sont récupérées avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant récupère des informations sur la fenêtre d’info-bulle actuelle.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>CToolTipCtrl :: GetDelayTime

Récupère les durées initiales, contextuelles et de réaffichages actuellement définies pour un contrôle d’info-bulle.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Paramètres

*dwDuration*<br/>
Indicateur qui spécifie la valeur de durée qui sera extraite. Ce paramètre peut prendre l’une des valeurs suivantes :

- TTDT_AUTOPOP récupérer la durée pendant laquelle la fenêtre d’info-bulle reste visible si le pointeur est immobile dans le rectangle englobant d’un outil.

- TTDT_INITIAL récupérer la durée pendant laquelle le pointeur doit rester immobile dans le rectangle englobant d’un outil avant que la fenêtre d’info-bulle ne s’affiche.

- TTDT_RESHOW récupérer le temps nécessaire pour que les fenêtres d’info-bulle suivantes s’affichent lorsque le pointeur se déplace d’un outil à un autre.

### <a name="return-value"></a>Valeur de retour

Délai spécifié, en millisecondes.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime)de message Win32, comme décrit dans le SDK Windows.

##  <a name="getmargin"></a>CToolTipCtrl :: GetMargin

Récupère les marges supérieure, gauche, inférieure et droite définies pour une fenêtre d’info-bulle.

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Paramètres

*lprc*<br/>
Adresse d’une structure `RECT` qui recevra les informations sur les marges. Les membres de la structure [Rect](/previous-versions/dd162897\(v=vs.85\)) ne définissent pas de rectangle englobant. Dans le cadre de ce message, les membres de la structure sont interprétés comme suit :

|Membre|Représentation|
|------------|--------------------|
|`top`|Distance, en pixels, entre la bordure supérieure et la partie supérieure du texte de l’info-bulle.|
|`left`|Distance entre la bordure gauche et l’extrémité gauche du texte info-bulle, en pixels.|
|`bottom`|Distance entre la bordure inférieure et le bas du texte info-bulle, en pixels.|
|`right`|Distance entre la bordure droite et l’extrémité droite du texte info-bulle, en pixels.|

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)de message Win32, comme décrit dans le SDK Windows.

##  <a name="getmaxtipwidth"></a>CToolTipCtrl :: GetMaxTipWidth

Récupère la largeur maximale d’une fenêtre d’info-bulle.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur maximale d’une fenêtre d’info-bulle.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)de message Win32, comme décrit dans le SDK Windows.

##  <a name="gettext"></a>CToolTipCtrl :: GetText

Récupère le texte qu’un contrôle d’info-bulle gère pour un outil.

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet `CString` qui reçoit le texte de l’outil.

*pWnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool*<br/>
ID de l’outil.

### <a name="remarks"></a>Notes

Les paramètres *pwnd* et *nIDTool* identifient l’outil. Si cet outil a déjà été inscrit avec le contrôle d’info-bulle par le biais d’un appel précédent à `CToolTipCtrl::AddTool`, le texte de l’outil est assigné à l’objet référencé par le paramètre *Str* .

##  <a name="gettipbkcolor"></a>CToolTipCtrl :: GetTipBkColor

Récupère la couleur d’arrière-plan dans une fenêtre d’info-bulle.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur [COLORREF](/windows/win32/gdi/colorref) qui représente la couleur d’arrière-plan.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor)de message Win32, comme décrit dans le SDK Windows.

##  <a name="gettiptextcolor"></a>CToolTipCtrl :: GetTipTextColor

Récupère la couleur de texte dans une fenêtre d’info-bulle.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur [COLORREF](/windows/win32/gdi/colorref) qui représente la couleur du texte.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)de message Win32, comme décrit dans le SDK Windows.

##  <a name="gettitle"></a>CToolTipCtrl :: GetTitle

Récupère le titre du contrôle ToolTip actuel.

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pttgt*|à Pointeur vers une structure [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) qui contient des informations sur le contrôle ToolTip. Lorsque cette méthode est retournée, le membre *pszTitle* de la structure [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) pointe vers le texte du titre.|

### <a name="remarks"></a>Notes

Cette méthode envoie le message [TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle) , qui est décrit dans le SDK Windows.

##  <a name="gettoolcount"></a>CToolTipCtrl :: GetToolCount

Récupère le nombre d’outils inscrits avec le contrôle d’info-bulle.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’outils inscrits avec le contrôle d’info-bulle.

##  <a name="gettoolinfo"></a>CToolTipCtrl :: GetToolInfo

Récupère les informations qu’un contrôle d’info-bulle gère à propos d’un outil.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Paramètres

*ToolInfo*<br/>
Référence à un objet `TOOLINFO` qui reçoit le texte de l’outil.

*pWnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool*<br/>
ID de l’outil.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les membres `hwnd` et `uId` de la structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) référencée par *CToolInfo* identifient l’outil. Si cet outil a été inscrit avec le contrôle d’info-bulle par le biais d’un appel précédent à `AddTool`, la structure de `TOOLINFO` est remplie d’informations sur l’outil.

##  <a name="hittest"></a>CToolTipCtrl :: HitTest

Teste un point pour déterminer s’il se trouve dans le rectangle englobant de l’outil donné et, si c’est le cas, récupérer des informations sur l’outil.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*pt*<br/>
Pointeur vers un objet `CPoint` contenant les coordonnées du point à tester.

*lpToolInfo*<br/>
Pointeur vers la structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) qui contient des informations sur l’outil.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le point spécifié par les informations de test de positionnement se trouve dans le rectangle englobant de l’outil ; Sinon, 0.

### <a name="remarks"></a>Notes

Si cette fonction retourne une valeur différente de zéro, la structure vers laquelle pointe *lpToolInfo* est remplie avec des informations sur l’outil dans le rectangle où le point se trouve.

La structure `TTHITTESTINFO` est définie comme suit :

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   Spécifie le handle de l’outil.

- `pt`

   Spécifie les coordonnées d’un point si le point se trouve dans le rectangle englobant de l’outil.

- `ti`

   Informations sur l’outil. Pour plus d’informations sur la structure `TOOLINFO`, consultez [CToolTipCtrl :: GetToolInfo](#gettoolinfo).

##  <a name="pop"></a>CToolTipCtrl ::P op

Supprime une fenêtre d’info-bulle affichée de la vue.

```
void Pop();
```

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_POP](/windows/win32/Controls/ttm-pop)de message Win32, comme décrit dans le SDK Windows.

##  <a name="popup"></a>CToolTipCtrl ::P opup

Provoque l’affichage du contrôle ToolTip actuel aux coordonnées du dernier message de la souris.

```
void Popup();
```

### <a name="remarks"></a>Notes

Cette méthode envoie le message [TTM_POPUP](/windows/win32/Controls/ttm-popup) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant affiche une fenêtre d’info-bulle.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>CToolTipCtrl :: RelayEvent

Transmet un message de souris à un contrôle d’info-bulle pour traitement.

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*lpMsg*<br/>
Pointeur vers une structure [MSG](/windows/win32/api/winuser/ns-winuser-msg) qui contient le message à relayer.

### <a name="remarks"></a>Notes

Un contrôle d’info-bulle traite uniquement les messages suivants, qui lui sont envoyés par `RelayEvent`:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet :: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="setdelaytime"></a>CToolTipCtrl :: SetDelayTime

Définit le délai d’attente pour un contrôle d’info-bulle.

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Paramètres

*nDelay*<br/>
Spécifie le nouveau délai, en millisecondes.

*dwDuration*<br/>
Indicateur qui spécifie la valeur de durée qui sera extraite. Pour obtenir une description des valeurs valides, consultez [CToolTipCtrl :: GetDelayTime](#getdelaytime) .

*iTime*<br/>
Délai d’attente spécifié, en millisecondes.

### <a name="remarks"></a>Notes

Le délai est la durée pendant laquelle le curseur doit rester sur un outil avant que la fenêtre d’info-bulle ne s’affiche. Le délai par défaut est de 500 millisecondes.

##  <a name="setmargin"></a>CToolTipCtrl :: SetMargin

Définit les marges supérieure, gauche, inférieure et droite d’une fenêtre d’info-bulle.

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Paramètres

*lprc*<br/>
Adresse d’une structure `RECT` qui contient les informations sur les marges à définir. Les membres de la structure `RECT` ne définissent pas de rectangle englobant. Pour obtenir une description des informations sur les marges, consultez [CToolTipCtrl :: getMargin](#getmargin) .

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)de message Win32, comme décrit dans le SDK Windows.

##  <a name="setmaxtipwidth"></a>CToolTipCtrl :: SetMaxTipWidth

Définit la largeur maximale d’une fenêtre d’info-bulle.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Paramètres

*iWidth*<br/>
Largeur maximale de la fenêtre d’info-bulle à définir.

### <a name="return-value"></a>Valeur de retour

Largeur maximale du Conseil.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)de message Win32, comme décrit dans le SDK Windows.

##  <a name="settipbkcolor"></a>CToolTipCtrl :: SetTipBkColor

Définit la couleur d’arrière-plan dans une fenêtre d’info-bulle.

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Language*<br/>
Nouvelle couleur d'arrière-plan.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor)de message Win32, comme décrit dans le SDK Windows.

##  <a name="settiptextcolor"></a>CToolTipCtrl :: SetTipTextColor

Définit la couleur du texte dans une fenêtre d’info-bulle.

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Language*<br/>
Nouvelle couleur du texte.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor)de message Win32, comme décrit dans le SDK Windows.

##  <a name="settitle"></a>CToolTipCtrl :: SetTitle

Ajoute une icône standard et une chaîne de titre à une info-bulle.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Paramètres

*uIcon*<br/>
Consultez l' *icône* dans [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) dans le SDK Windows.

*lpstrTitle*<br/>
Pointeur vers la chaîne de titre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)de message Win32, comme décrit dans le SDK Windows.

##  <a name="settoolinfo"></a>CToolTipCtrl :: SetToolInfo

Définit les informations gérées par une info-bulle pour un outil.

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Paramètres

*lpToolInfo*<br/>
Pointeur vers une structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) qui spécifie les informations à définir.

##  <a name="settoolrect"></a>CToolTipCtrl :: SetToolRect

Définit un nouveau rectangle englobant pour un outil.

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool*<br/>
ID de l’outil.

*lpRect*<br/>
Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) spécifiant le nouveau rectangle englobant.

##  <a name="setwindowtheme"></a>CToolTipCtrl :: SetWindowTheme

Définit le style visuel de la fenêtre d’info-bulle.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Paramètres

*pszSubAppName*<br/>
Pointeur vers une chaîne Unicode qui contient le style visuel à définir.

### <a name="return-value"></a>Valeur de retour

La valeur de retour n’est pas utilisée.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités du message [TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme) , comme décrit dans le SDK Windows.

##  <a name="update"></a>CToolTipCtrl :: Update

Force le redessinage de l’outil actuel.

```
void Update();
```

##  <a name="updatetiptext"></a>CToolTipCtrl :: UpdateTipText

Met à jour le texte d’info-bulle pour les outils de ce contrôle.

```
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Pointeur vers le texte de l’outil.

*pWnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool*<br/>
ID de l’outil.

*nIDText*<br/>
ID de la ressource de type chaîne qui contient le texte de l’outil.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBar, classe](../../mfc/reference/ctoolbar-class.md)
