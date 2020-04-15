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
ms.openlocfilehash: fdf91549fd1b911de3af82bb940b92fe5e220b92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365104"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

Encapsule les fonctionnalités d'un « contrôle info-bulle », une petite fenêtre contextuelle qui affiche une ligne de texte unique qui décrit le rôle d'un outil dans une application.

## <a name="syntax"></a>Syntaxe

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Construit un objet `CToolTipCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CToolTipCtrl::Activer](#activate)|Active et désactive le contrôle de la pointe de l’outil.|
|[CToolTipCtrl::AddTool](#addtool)|Enregistre un outil avec le contrôle de pointe d’outil.|
|[CToolTipCtrl::AdjustRect](#adjustrect)|Convertit entre le rectangle d’affichage de texte d’un contrôle de pointe d’outil et son rectangle de fenêtre.|
|[CToolTipCtrl::Créer](#create)|Crée un contrôle de pointe d’outil et le fixe à un `CToolTipCtrl` objet.|
|[CToolTipCtrl::CreateEx](#createex)|Crée un contrôle de pointe d’outil avec les `CToolTipCtrl` styles windows étendus spécifiés et le fixe à un objet.|
|[CToolTipCtrl::DelTool](#deltool)|Supprime un outil du contrôle de pointe de l’outil.|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Récupère la taille de la pointe de l’outil.|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Récupère les informations, telles que la taille, la position et le texte, de la fenêtre tooltip que le contrôle actuel de la pointe d’outils affiche.|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Récupère les durées initiales, pop-up et reshow qui sont actuellement réglées pour un contrôle de pointe d’outil.|
|[CToolTipCtrl::GetMargin](#getmargin)|Récupère les marges supérieure, gauche, inférieure et droite qui sont réglées pour une fenêtre de pointe d’outil.|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Récupère la largeur maximale pour une fenêtre de pointe d’outil.|
|[CToolTipCtrl::GetText](#gettext)|Récupère le texte qu’un contrôle de pointe d’outil maintient pour un outil.|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Récupère la couleur de fond dans une fenêtre de pointe d’outil.|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Récupère la couleur du texte dans une fenêtre de pointe d’outil.|
|[CToolTipCtrl::GetTitle](#gettitle)|Récupère le titre du contrôle actuel de la pointe d’outils.|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Récupère un compte des outils entretenus par un contrôle de pointe d’outil.|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Récupère les informations qu’un contrôle de pointe d’outil maintient au sujet d’un outil.|
|[CToolTipCtrl::HitTest](#hittest)|Teste un point pour déterminer s’il se trouve dans le rectangle de délimitation de l’outil donné. Si c’est le cas, récupère des informations sur l’outil.|
|[CToolTipCtrl::Pop](#pop)|Enlève une fenêtre de pointe d’outil affichée de la vue.|
|[CToolTipCtrl::Popup](#popup)|Provoque l’affichage actuel du contrôle ToolTip aux coordonnées du dernier message de souris.|
|[CToolTipCtrl::RelaisEvent](#relayevent)|Passe un message de souris à un contrôle de pointe d’outil pour le traitement.|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Définit les durées initiales, pop-up et reshow pour un contrôle de pointe d’outil.|
|[CToolTipCtrl::SetMargin](#setmargin)|Définit les marges supérieure, gauche, inférieure et droite pour une fenêtre de pointe d’outil.|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Définit la largeur maximale pour une fenêtre de pointe d’outil.|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Définit la couleur de fond dans une fenêtre de pointe d’outil.|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Définit la couleur du texte dans une fenêtre de pointe d’outil.|
|[CToolTipCtrl::SetTitle](#settitle)|Ajoute une icône standard et une chaîne de titre à une pointe d’outil.|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Définit l’information qu’un bout d’outil conserve pour un outil.|
|[CToolTipCtrl::SetToolRect](#settoolrect)|Définit un nouveau rectangle de délimitation pour un outil.|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Définit le style visuel de la fenêtre de pointe d’outil.|
|[CToolTipCtrl::Mise à jour](#update)|Force le redessin de l’outil actuel.|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Définit le texte de pointe de l’outil pour un outil.|

## <a name="remarks"></a>Notes

Un « outil » est soit une fenêtre, comme une fenêtre ou un contrôle pour enfants, soit une zone rectangulaire définie par l’application dans la zone cliente d’une fenêtre. Une astuce d’outil est cachée la plupart du temps, apparaissant seulement lorsque l’utilisateur met le curseur sur un outil et le laisse là pendant environ une demi-seconde. La pointe de l’outil apparaît près du curseur et disparaît lorsque l’utilisateur clique sur un bouton de souris ou déplace le curseur hors de l’outil.

`CToolTipCtrl`fournit la fonctionnalité pour contrôler l’heure et la durée initiales de la pointe de l’outil, les largeurs de marge entourant le texte de pointe d’outil, la largeur de la fenêtre de pointe d’outil elle-même, et la couleur de fond et de texte de la pointe d’outil. Un seul contrôle de l’astuce d’outil peut fournir des informations pour plus d’un outil.

La `CToolTipCtrl` classe fournit la fonctionnalité du contrôle de pointe d’outil commun de Windows. Ce contrôle (et `CToolTipCtrl` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT versions 3.51 et plus tard.

Pour plus d’informations sur les conseils d’outils habilitants, voir [Conseils d’outils dans Windows non dérivé de CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Pour plus d’informations sur l’utilisation `CToolTipCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation [CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="ctooltipctrlactivate"></a><a name="activate"></a>CToolTipCtrl::Activer

Appelez cette fonction pour activer ou désactiver un contrôle de pointe d’outil.

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*bActivate (en)*<br/>
Précise si le contrôle de la pointe de l’outil doit être activé ou désactivé.

### <a name="remarks"></a>Notes

Si *bActivate* est VRAI, le contrôle est activé; si FALSE, il est désactivé.

Lorsqu’un contrôle de l’extrémité d’outil est actif, l’information sur les conseils d’outil apparaît lorsque le curseur est inscrit sur un outil qui est enregistré avec le contrôle; lorsqu’il est inactif, l’information sur les conseils d’outils n’apparaît pas, même lorsque le curseur est sur un outil.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertySheet:GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladdtool"></a><a name="addtool"></a>CToolTipCtrl::AddTool

Enregistre un outil avec le contrôle de pointe d’outil.

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

*Pwnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTextE (en)*<br/>
ID de la ressource de chaîne qui contient le texte pour l’outil.

*lpRectTool*<br/>
Pointeur vers une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) contenant des coordonnées du rectangle de délimitation de l’outil. Les coordonnées sont relatives au coin supérieur gauche de la zone cliente de la fenêtre identifiée par *pWnd*.

*nIDTool (en)*<br/>
ID de l’outil.

*lpszText*<br/>
Pointeur vers le texte pour l’outil. Si ce paramètre contient la valeur LPSTR_TEXTCALLBACK, TTN_NEEDTEXT messages de notification vont au parent de la fenêtre qui *pointe* vers.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les paramètres *lpRectTool* et *nIDTool* doivent tous deux être valides, ou si *lpRectTool* est NULL, *nIDTool* doit être 0.

Un contrôle de pointe d’outil peut être associé à plus d’un outil. Appelez cette fonction pour enregistrer un outil avec le contrôle de pointe d’outil, de sorte que les informations stockées dans la pointe de l’outil sont affichées lorsque le curseur est sur l’outil.

> [!NOTE]
> Vous ne pouvez pas définir une `AddTool`pointe d’outil à un contrôle statique à l’aide de .

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertySheet:GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladjustrect"></a><a name="adjustrect"></a>CToolTipCtrl::AdjustRect

Convertit entre le rectangle d’affichage de texte d’un contrôle d’outil et son rectangle de fenêtre.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Paramètres

*lprc (lprc)*<br/>
Pointeur vers une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) qui contient soit un rectangle de fenêtre de pointe d’outil ou un rectangle d’affichage de texte.

*bLarger (en)*<br/>
Si VRAI, *lprc* est utilisé pour spécifier un rectangle d’affichage de texte, et il reçoit le rectangle de fenêtre correspondant. Si FALSE, *lprc* est utilisé pour spécifier un rectangle de fenêtre, et il reçoit le rectangle d’affichage de texte correspondant.

### <a name="return-value"></a>Valeur de retour

Nonzero si le rectangle est ajusté avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre calcule le rectangle d’affichage de texte d’un contrôle de pointe d’outil à partir de son rectangle de fenêtre, ou le rectangle de fenêtre de pointe d’outil nécessaire pour afficher un rectangle d’affichage de texte spécifié.

Cette fonction de membre implémente le comportement du message Win32 [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlcreate"></a><a name="create"></a>CToolTipCtrl::Créer

Crée un contrôle de pointe d’outil et le fixe à un `CToolTipCtrl` objet.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Spécifie la fenêtre parente du `CDialog`contrôle de l’extrémité de l’outil, habituellement un . Ce ne doit pas être NULL.

*dwStyle (en)*<br/>
Spécifie le style du contrôle de l’extrémité de l’outil. Consultez la section **Remarques** pour plus d’informations.

### <a name="return-value"></a>Valeur de retour

Nonzero si `CToolTipCtrl` l’objet est créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CToolTipCtrl` en deux étapes. Tout d’abord, appelez `CToolTipCtrl` le constructeur pour `Create` construire l’objet, puis appelez `CToolTipCtrl` pour créer le contrôle de pointe de l’outil et l’attacher à l’objet.

Le paramètre *dwStyle* peut être n’importe quelle combinaison de [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles). En outre, un contrôle de pointe d’outil a deux styles spécifiques à la classe : TTS_ALWAYSTIP et TTS_NOPREFIX.

|Style|Signification|
|-----------|-------------|
|TTS_ALWAYSTIP|Précise que la pointe de l’outil apparaîtra lorsque le curseur est sur un outil, que la fenêtre propriétaire du contrôle de la pointe de l’outil soit active ou inactive. Sans ce style, le contrôle de pointe d’outil apparaît lorsque la fenêtre propriétaire de l’outil est active, mais pas quand elle est inactive.|
|TTS_NOPREFIX|Ce style empêche le système de dépouiller le caractère ampersand (&) d’une chaîne. Si un contrôle de pointe d’outil n’a pas le style TTS_NOPREFIX, le système dépouille automatiquement les caractères ampersand, permettant à une application d’utiliser la même chaîne qu’un élément de menu et comme texte dans un contrôle de pointe d’outil.|

Un contrôle de pointe d’outil a le WS_POPUP et WS_EX_TOOLWINDOW les styles de fenêtre, indépendamment du fait que vous les spécifiiez lors de la création du contrôle.

Pour créer un contrôle de pointe d’outil avec des styles de fenêtres `Create`étendues, appelez [CToolTipCtrl::CreateEx](#createex) au lieu de .

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertySheet:GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlcreateex"></a><a name="createex"></a>CToolTipCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CToolTipCtrl` et l’associe à l’objet.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*dwStyle (en)*<br/>
Spécifie le style du contrôle de l’extrémité de l’outil. Voir la section **Remarques** de [Créer](#create) pour plus d’informations.

*dwStyleEx*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour une liste de styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Nonzero si réussi autrement 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au `Create` lieu d’appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

## <a name="ctooltipctrlctooltipctrl"></a><a name="ctooltipctrl"></a>CToolTipCtrl::CToolTipCtrl

Construit un objet `CToolTipCtrl`.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Notes

Vous devez `Create` appeler après la construction de l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

## <a name="ctooltipctrldeltool"></a><a name="deltool"></a>CToolTipCtrl::DelTool

Supprime l’outil spécifié par *pWnd* et *nIDTool* de la collection d’outils pris en charge par un contrôle de pointe d’outil.

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool (en)*<br/>
ID de l’outil.

## <a name="ctooltipctrlgetbubblesize"></a><a name="getbubblesize"></a>CToolTipCtrl::GetBubbleSize

Récupère la taille de la pointe de l’outil.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Paramètres

*lpToolInfo*<br/>
Un pointeur sur la structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) de la pointe d’outil.

### <a name="return-value"></a>Valeur de retour

La taille de la pointe de l’outil.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlgetcurrenttool"></a><a name="getcurrenttool"></a>CToolTipCtrl::GetCurrentTool

Récupère les informations, telles que la taille, la position et le texte, de la fenêtre de pointe d’outils affichées par le contrôle actuel de la pointe d’outils.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpToolInfo*|[out] Pointeur vers une structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) qui reçoit des informations sur la fenêtre actuelle de pointe d’outil.|

### <a name="return-value"></a>Valeur de retour

VRAI si l’information est récupérée avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message TTM_GETCURRENTTOOL,](/windows/win32/Controls/ttm-getcurrenttool) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant récupère des informations sur la fenêtre actuelle de la pointe d’outils.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

## <a name="ctooltipctrlgetdelaytime"></a><a name="getdelaytime"></a>CToolTipCtrl::GetDelayTime

Récupère les durées initiales, pop-up et reshow actuellement définies pour un contrôle de pointe d’outil.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Paramètres

*dwDuration*<br/>
Indicateur qui précise quelle valeur de durée sera récupérée. Ce paramètre peut être l’une des valeurs suivantes :

- TTDT_AUTOPOP Récupérer la durée pendant laquelle la fenêtre de pointe de l’outil reste visible si le pointeur est stationnaire dans le rectangle de délimitation d’un outil.

- TTDT_INITIAL Récupérer la durée pendant laquelle le pointeur doit rester immobile dans le rectangle de délimitation d’un outil avant que la fenêtre de pointe de l’outil n’apparaisse.

- TTDT_RESHOW Récupérer le temps qu’il faut pour que les fenêtres de pointe d’outils ultérieures apparaissent pendant que le pointeur se déplace d’un outil à l’autre.

### <a name="return-value"></a>Valeur de retour

Le délai spécifié, en millisecondes

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlgetmargin"></a><a name="getmargin"></a>CToolTipCtrl::GetMargin

Récupère les marges supérieure, gauche, inférieure et droite pour une fenêtre de pointe d’outil.

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Paramètres

*lprc (lprc)*<br/>
Adresse d’une `RECT` structure qui recevra l’information sur la marge. Les membres de la structure [RECT](/previous-versions/dd162897\(v=vs.85\)) ne définissent pas un rectangle de délimitation. Aux fins de ce message, les membres de la structure sont interprétés comme suit :

|Membre|Représentation|
|------------|--------------------|
|`top`|Distance entre la bordure supérieure et le dessus du texte de pointe d’outil, en pixels.|
|`left`|Distance entre la bordure gauche et l’extrémité gauche du texte de pointe, en pixels.|
|`bottom`|Distance entre la bordure inférieure et le bas du texte de pointe, en pixels.|
|`right`|Distance entre la bordure droite et l’extrémité droite du texte de pointe, en pixels.|

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlgetmaxtipwidth"></a><a name="getmaxtipwidth"></a>CToolTipCtrl::GetMaxTipWidth

Récupère la largeur maximale pour une fenêtre de pointe d’outil.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur maximale pour une fenêtre de pointe d’outil.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlgettext"></a><a name="gettext"></a>CToolTipCtrl::GetText

Récupère le texte qu’un contrôle de pointe d’outil maintient pour un outil.

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Référence à `CString` un objet qui reçoit le texte de l’outil.

*Pwnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool (en)*<br/>
ID de l’outil.

### <a name="remarks"></a>Notes

Les paramètres *pWnd* et *nIDTool* identifient l’outil. Si cet outil a déjà été enregistré avec le `CToolTipCtrl::AddTool`contrôle de pointe de l’outil par le biais d’un appel précédent à , l’objet référencé par le paramètre *str* est attribué le texte de l’outil.

## <a name="ctooltipctrlgettipbkcolor"></a><a name="gettipbkcolor"></a>CToolTipCtrl::GetTipBkColor

Récupère la couleur de fond dans une fenêtre de pointe d’outil.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) qui représente la couleur de fond.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlgettiptextcolor"></a><a name="gettiptextcolor"></a>CToolTipCtrl::GetTipTextColor

Récupère la couleur du texte dans une fenêtre de pointe d’outil.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) qui représente la couleur du texte.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlgettitle"></a><a name="gettitle"></a>CToolTipCtrl::GetTitle

Récupère le titre du contrôle actuel de la pointe d’outils.

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pttgt pttgt*|[out] Pointeur vers une structure [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) qui contient des informations sur le contrôle ToolTip. Lorsque cette méthode revient, le membre *pszTitle* de la structure [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) pointe vers le texte du titre.|

### <a name="remarks"></a>Notes

Cette méthode envoie le [message TTM_GETTITLE,](/windows/win32/Controls/ttm-gettitle) qui est décrit dans le SDK Windows.

## <a name="ctooltipctrlgettoolcount"></a><a name="gettoolcount"></a>CToolTipCtrl::GetToolCount

Récupère un compte des outils enregistrés avec le contrôle de pointe de l’outil.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Valeur de retour

Un compte d’outils enregistrés avec le contrôle de pointe d’outil.

## <a name="ctooltipctrlgettoolinfo"></a><a name="gettoolinfo"></a>CToolTipCtrl::GetToolInfo

Récupère les informations qu’un contrôle de pointe d’outil maintient au sujet d’un outil.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Paramètres

*ToolInfo (en anglais)*<br/>
Référence à `TOOLINFO` un objet qui reçoit le texte de l’outil.

*Pwnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool (en)*<br/>
ID de l’outil.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les `hwnd` `uId` membres et les membres de la structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) référencés par *CToolInfo* identifient l’outil. Si cet outil a été enregistré avec le `AddTool`contrôle `TOOLINFO` de pointe d’outil par un appel précédent à , la structure est remplie d’informations sur l’outil.

## <a name="ctooltipctrlhittest"></a><a name="hittest"></a>CToolTipCtrl::HitTest

Teste un point pour déterminer s’il se trouve dans le rectangle de délimitation de l’outil donné et, dans l’affirmative, récupérer des informations sur l’outil.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*Pt*<br/>
Pointeur `CPoint` vers un objet contenant les coordonnées du point à tester.

*lpToolInfo*<br/>
Pointeur vers la structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) qui contient des informations sur l’outil.

### <a name="return-value"></a>Valeur de retour

Nonzero si le point spécifié par les informations de test est dans le rectangle de délimitation de l’outil; sinon 0.

### <a name="remarks"></a>Notes

Si cette fonction renvoie une valeur non zéro, la structure pointée par *lpToolInfo* est remplie d’informations sur l’outil dans lequel le rectangle se trouve le point.

La `TTHITTESTINFO` structure est définie comme suit :

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   Spécifie la poignée de l’outil.

- `pt`

   Spécifie les coordonnées d’un point si le point est dans le rectangle de délimitation de l’outil.

- `ti`

   Informations sur l’outil. Pour plus d’informations sur la `TOOLINFO` structure, voir [CToolTipCtrl::GetToolInfo](#gettoolinfo).

## <a name="ctooltipctrlpop"></a><a name="pop"></a>CToolTipCtrl::Pop

Enlève une fenêtre de pointe d’outil affichée de la vue.

```
void Pop();
```

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_POP](/windows/win32/Controls/ttm-pop), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlpopup"></a><a name="popup"></a>CToolTipCtrl::Popup

Provoque l’affichage actuel du contrôle de l’outil aux coordonnées du dernier message de souris.

```
void Popup();
```

### <a name="remarks"></a>Notes

Cette méthode envoie le [message TTM_POPUP,](/windows/win32/Controls/ttm-popup) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant affiche une fenêtre de pointe d’outil.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

## <a name="ctooltipctrlrelayevent"></a><a name="relayevent"></a>CToolTipCtrl::RelaisEvent

Passe un message de souris à un contrôle de pointe d’outil pour le traitement.

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Paramètres

*lpMsg*<br/>
Pointeur vers une structure [MSG](/windows/win32/api/winuser/ns-winuser-msg) qui contient le message à relayer.

### <a name="remarks"></a>Notes

Un contrôle de l’astuce d’outil ne `RelayEvent`traite que les messages suivants, qui lui sont envoyés par :

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertySheet:GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlsetdelaytime"></a><a name="setdelaytime"></a>CToolTipCtrl::SetDelayTime

Définit le délai pour un contrôle de pointe d’outil.

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Paramètres

*nDelay (en)*<br/>
Spécifie le nouveau délai, en millisecondes.

*dwDuration*<br/>
Indicateur qui précise quelle valeur de durée sera récupérée. Voir [CToolTipCtrl:GetDelayTime](#getdelaytime) pour une description des valeurs valides.

*iTime*<br/>
Le temps de retard spécifié, en millisecondes.

### <a name="remarks"></a>Notes

Le délai est la durée pendante pendant que le curseur doit rester sur un outil avant que la fenêtre de pointe de l’outil n’apparaisse. Le délai par défaut est de 500 millisecondes.

## <a name="ctooltipctrlsetmargin"></a><a name="setmargin"></a>CToolTipCtrl::SetMargin

Définit les marges supérieure, gauche, inférieure et droite pour une fenêtre de pointe d’outil.

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Paramètres

*lprc (lprc)*<br/>
Adresse d’une `RECT` structure qui contient les informations de marge à définir. Les membres `RECT` de la structure ne définissent pas un rectangle de délimitation. Voir [CToolTipCtrl:GetMargin](#getmargin) pour une description des informations de marge.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlsetmaxtipwidth"></a><a name="setmaxtipwidth"></a>CToolTipCtrl::SetMaxTipWidth

Définit la largeur maximale pour une fenêtre de pointe d’outil.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Paramètres

*iWidth (en)*<br/>
La largeur maximale de la fenêtre de pointe d’outil à régler.

### <a name="return-value"></a>Valeur de retour

La largeur maximale précédente de pointe.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlsettipbkcolor"></a><a name="settipbkcolor"></a>CToolTipCtrl::SetTipBkColor

Définit la couleur de fond dans une fenêtre de pointe d’outil.

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Clr*<br/>
Nouvelle couleur d'arrière-plan.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlsettiptextcolor"></a><a name="settiptextcolor"></a>CToolTipCtrl::SetTipTextColor

Définit la couleur du texte dans une fenêtre de pointe d’outil.

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Paramètres

*Clr*<br/>
La nouvelle couleur de texte.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlsettitle"></a><a name="settitle"></a>CToolTipCtrl::SetTitle

Ajoute une icône standard et une chaîne de titre à une pointe d’outil.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Paramètres

*uIcon*<br/>
Voir *l’icône* dans [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) dans le SDK Windows.

*lpstrTitle (lpstrTitle)*<br/>
Pointeur à la chaîne de titre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle), tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlsettoolinfo"></a><a name="settoolinfo"></a>CToolTipCtrl::SetToolInfo

Définit l’information qu’un bout d’outil conserve pour un outil.

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Paramètres

*lpToolInfo*<br/>
Un pointeur vers une structure [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) qui spécifie l’information à définir.

## <a name="ctooltipctrlsettoolrect"></a><a name="settoolrect"></a>CToolTipCtrl::SetToolRect

Définit un nouveau rectangle de délimitation pour un outil.

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool (en)*<br/>
ID de l’outil.

*lpRect*<br/>
Pointeur vers une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) spécifiant le nouveau rectangle de délimitation.

## <a name="ctooltipctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolTipCtrl::SetWindowTheme

Définit le style visuel de la fenêtre de pointe d’outil.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Paramètres

*pszSubAppName*<br/>
Un pointeur à une chaîne Unicode qui contient le style visuel à définir.

### <a name="return-value"></a>Valeur de retour

La valeur de retour n’est pas utilisée.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du message [TTM_SETWINDOWTHEME,](/windows/win32/Controls/ttm-setwindowtheme) tel que décrit dans le SDK Windows.

## <a name="ctooltipctrlupdate"></a><a name="update"></a>CToolTipCtrl::Mise à jour

Force le redessin de l’outil actuel.

```
void Update();
```

## <a name="ctooltipctrlupdatetiptext"></a><a name="updatetiptext"></a>CToolTipCtrl::UpdateTipText

Mise à jour du texte de pointe de l’outil pour les outils de ce contrôle.

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
Pointeur vers le texte pour l’outil.

*Pwnd*<br/>
Pointeur vers la fenêtre qui contient l’outil.

*nIDTool (en)*<br/>
ID de l’outil.

*nIDTextE (en)*<br/>
ID de la ressource de chaîne qui contient le texte pour l’outil.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBar, classe](../../mfc/reference/ctoolbar-class.md)
