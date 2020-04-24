---
title: Classe CMFCButton
ms.date: 08/28/2018
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
helpviewer_keywords:
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
ms.openlocfilehash: e949feaaac3570e1518cfb488cc1c42a471a1c46
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754868"
---
# <a name="cmfcbutton-class"></a>Classe CMFCButton

La `CMFCButton` classe ajoute des fonctionnalités à la classe [CButton,](../../mfc/reference/cbutton-class.md) comme l’alignement du texte du bouton, la combinaison du texte du bouton et d’une image, la sélection d’un curseur et la spécit d’une pointe d’outil.

## <a name="syntax"></a>Syntaxe

```
class CMFCButton : public CButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCButton::CMFCButton`|Constructeur par défaut.|
|`CMFCButton::~CMFCButton`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCButton::CleanUp](#cleanup)|Réinitialise les variables internes et libère les ressources allouées telles que les images, les bitmaps et les icônes.|
|`CMFCButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCButton::DrawItem`|Appelé par le cadre quand un aspect visuel d’un bouton tiré par le propriétaire a changé. (Overrides [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Précise s’il faut afficher le texte intégral d’une pointe d’outils dans une grande fenêtre de pointe d’outils ou une version tronquée du texte dans une petite fenêtre de pointe à outils.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Précise si la police de texte bouton est la même que la police de menu d’application.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Précise si le style de la bordure bouton correspond au thème Windows actuel.|
|`CMFCButton::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Renvoie une référence au contrôle sous-jacent de l’outiltip.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Indique si une case à cocher ou un bouton radio est un bouton automatique.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Indique si un bouton est réglé en mode répétition automatique.|
|[CMFCButton::IsCheckBox](#ischeckbox)|Indique si un bouton est un bouton de la case à cocher.|
|[CMFCButton::IsChecked](#ischecked)|Indique si le bouton actuel est vérifié.|
|[CMFCButton::IsHighlighted](#ishighlighted)|Indique si un bouton est mis en surbrillance.|
|[CMFCButton::IsPressed](#ispressed)|Indique si un bouton est poussé et surligné.|
|[CMFCButton::IsPushed](#ispushed)|Indique si un bouton est poussé.|
|[CMFCButton::IsRadioButton](#isradiobutton)|Indique si un bouton est un bouton radio.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Indique si le style de la bordure du bouton correspond au thème Windows actuel.|
|`CMFCButton::OnDrawParentBackground`|Dessine l’arrière-plan du parent d’un bouton dans la zone spécifiée. (Overrides [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows De TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Définit un bouton en mode répétition automatique.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Définit l’image pour un bouton vérifié.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Définit la couleur de fond pour le texte du bouton.|
|[CMFCButton::SetImage](#setimage)|Définit l’image pour un bouton.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Définit l’image du curseur.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Définit le curseur à l’image d’une main.|
|[CMFCButton::SetStdImage](#setstdimage)|Utilise `CMenuImages` un objet pour définir l’image bouton.|
|[CMFCButton::SetTextColor](#settextcolor)|Définit la couleur du texte du bouton pour un bouton qui n’est pas sélectionné.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Définit la couleur du texte du bouton pour un bouton sélectionné.|
|[CMFCButton::SetTooltip](#settooltip)|Associe une boîte à outils à un bouton.|
|[CMFCButton::SizeToContent](#sizetocontent)|Resizes un bouton pour contenir son texte et son image boutonné.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|Appelé par le cadre pour dessiner un bouton.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Appelé par le cadre pour dessiner la bordure d’un bouton.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Appelé par le cadre pour dessiner le rectangle de mise au point pour un bouton.|
|[CMFCButton::OnDrawText](#ondrawtext)|Appelé par le cadre pour dessiner le texte du bouton.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Appelé par le cadre pour dessiner l’arrière-plan du texte bouton.|
|[CMFCButton::SelectFont](#selectfont)|Récupère la police associée au contexte de l’appareil spécifié.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Spécifie l’alignement du texte du bouton.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Précise s’il faut utiliser des thèmes Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Indique s’il faut dessiner un rectangle de mise au point autour d’un bouton.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Spécifie le style du bouton, comme sans bordure, plat, semi-plat, ou 3D.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Lorsque TRUE, permet de dessiner un bouton désactivé comme grisé.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Indique s’il faut mettre en surbrillance un bouton de style BS_CHECKBOX lorsque le curseur plane au-dessus.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Indique s’il faut répondre aux événements boutonné vers le bas.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Indique s’il faut afficher une image sur le côté droit du bouton.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Indique si l’image est sur le dessus du bouton.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Indique si le bouton est transparent.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Indique si le dernier clic a été un double clic.|

## <a name="remarks"></a>Notes

D’autres types de boutons `CMFCButton` sont dérivés de la classe, tels que la classe [CMFCURLLinkButton,](../../mfc/reference/cmfclinkctrl-class.md) qui prend en charge les hyperliens, et la `CMFCColorButton` classe, qui prend en charge une boîte de dialogue de cueilleur de couleurs.

Le style `CMFCButton` d’un objet peut être *3D*, *plat,* *semi-plat* ou *pas de frontière*. Le texte du bouton peut être aligné à gauche, en haut ou au centre d’un bouton. Au moment de l’exécution, vous pouvez contrôler si le bouton affiche du texte, une image, ou un texte et une image. Vous pouvez également spécifier qu’une image de curseur particulier s’affiche lorsque le curseur plane sur un bouton.

Créez un contrôle de bouton directement dans votre code, soit en utilisant l’outil **MFC Class Wizard** et un modèle de boîte de dialogue. Si vous créez un contrôle `CMFCButton` de bouton directement, ajoutez une variable `Create` à `CMFCButton` votre application, puis appelez le constructeur et les méthodes de l’objet. Si vous utilisez le **MFC** `CButton` Class Wizard , ajoutez une variable à `CButton` votre `CMFCButton`application, puis modifiez le type de la variable à partir de .

Pour traiter les messages de notification dans une application de boîte de dialogue, ajoutez une entrée de carte de message et un gestionnaire d’événements pour chaque notification. Les notifications envoyées par un `CMFCButton` objet sont `CButton` les mêmes que celles envoyées par un objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer les propriétés du `CMFCButton` bouton en utilisant diverses méthodes dans la classe. L’exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxbutton.h

## <a name="cmfcbuttoncleanup"></a><a name="cleanup"></a>CMFCButton::CleanUp

Réinitialise les variables internes et libère les ressources allouées telles que les images, les bitmaps et les icônes.

```
virtual void CleanUp();
```

## <a name="cmfcbuttonenablefulltexttooltip"></a><a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip

Précise s’il faut afficher le texte intégral d’une pointe d’outils dans une grande fenêtre de pointe d’outils ou une version tronquée du texte dans une petite fenêtre de pointe à outils.

```cpp
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
[dans] VRAI pour afficher tout le texte; FALSE pour afficher du texte tronqué.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonenablemenufont"></a><a name="enablemenufont"></a>CMFCButton::EnableMenuFont

Précise si la police de texte bouton est la même que la police de menu d’application.

```cpp
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
[dans] VRAI pour utiliser la police de menu d’application comme police de texte de bouton ; FALSE pour utiliser la police du système. La valeur par défaut est TRUE.

*bRedraw (en)*<br/>
[dans] VRAI pour redessiner immédiatement l’écran; autrement, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Si vous n’utilisez pas cette méthode pour spécifier la police de texte bouton, vous pouvez spécifier la police avec la méthode [CWnd::SetFont.](../../mfc/reference/cwnd-class.md#setfont) Si vous ne spécifiez pas du tout une police, le cadre définit une police par défaut.

## <a name="cmfcbuttonenablewindowstheming"></a><a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

Précise si le style de la bordure bouton correspond au thème Windows actuel.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour utiliser le thème Windows actuel pour dessiner les bordures de bouton; FALSE de ne pas utiliser le thème Windows. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Cette méthode affecte tous les boutons de `CMFCButton` votre application qui sont dérivés de la classe.

## <a name="cmfcbuttongettooltipctrl"></a><a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl

Renvoie une référence au contrôle sous-jacent de l’outiltip.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Valeur de retour

Une référence au contrôle sous-jacent de l’outiltip.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonisautocheck"></a><a name="isautocheck"></a>CMFCButton::IsAutoCheck

Indique si une case à cocher ou un bouton radio est un bouton automatique.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton a le style BS_AUTOCHECKBOX ou BS_AUTORADIOBUTTON; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonisautorepeatcommandmode"></a><a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

Indique si un bouton est réglé en mode répétition automatique.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton est réglé en mode auto-répétition; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez la méthode [CMFCButton::SetAutorepeatMode](#setautorepeatmode) pour régler un bouton en mode auto-répétition.

## <a name="cmfcbuttonischeckbox"></a><a name="ischeckbox"></a>CMFCButton::IsCheckBox

Indique si un bouton est un bouton de la case à cocher.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton a BS_CHECKBOX ou BS_AUTOCHECKBOX style; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonischecked"></a><a name="ischecked"></a>CMFCButton::IsChecked

Indique si le bouton actuel est vérifié.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton actuel est vérifié; autrement, FALSE.

### <a name="remarks"></a>Notes

Le cadre utilise différentes façons d’indiquer que différents types de boutons sont vérifiés. Par exemple, un bouton radio est vérifié lorsqu’il contient un point; une case à cocher est cochée lorsqu’elle contient un **X**.

## <a name="cmfcbuttonishighlighted"></a><a name="ishighlighted"></a>CMFCButton::IsHighlighted

Indique si un bouton est mis en surbrillance.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton est mis en surbrillance; autrement, FALSE.

### <a name="remarks"></a>Notes

Un bouton est mis en surbrillance lorsque la souris plane sur le bouton.

## <a name="cmfcbuttonispressed"></a><a name="ispressed"></a>CMFCButton::IsPressed

Indique si un bouton est poussé et surligné.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton est appuyé; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonispushed"></a><a name="ispushed"></a>CMFCButton::IsPushed

Indique si un bouton est poussé.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton est poussé; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonisradiobutton"></a><a name="isradiobutton"></a>CMFCButton::IsRadioButton

Indique si un bouton est un bouton radio.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le style bouton est BS_RADIOBUTTON ou BS_AUTORADIOBUTTON; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttoniswindowsthemingenabled"></a><a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

Indique si le style de la bordure du bouton correspond au thème Windows actuel.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Valeur de retour

VRAI si le style de la bordure bouton correspond au thème Windows actuel; autrement, FALSE.

## <a name="cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

Précise s’il faut utiliser des thèmes Windows XP lors du dessin du bouton.

```
BOOL m_bDontUseWinXPTheme;
```

## <a name="cmfcbuttonm_bdrawfocus"></a><a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus

Indique s’il faut dessiner un rectangle de mise au point autour d’un bouton.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Notes

Définissez `m_bDrawFocus` le membre à TRUE pour spécifier que le cadre dessinera un rectangle de mise au point autour du texte et de l’image du bouton si le bouton reçoit la mise au point.

Le `CMFCButton` constructeur initialise ce membre à TRUE.

## <a name="cmfcbuttonm_bgraydisabled"></a><a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

Lorsque TRUE, permet de dessiner un bouton désactivé comme grisé.

```
BOOL m_bGrayDisabled;
```

## <a name="cmfcbuttonm_bhighlightchecked"></a><a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

Indique s’il faut mettre en surbrillance un bouton de style BS_CHECKBOX lorsque le curseur plane au-dessus.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Notes

Définissez `m_bHighlightChecked` le membre à TRUE pour spécifier que le cadre mettra en évidence un bouton de style BS_CHECKBOX lorsque la souris plane au-dessus d’elle.

## <a name="cmfcbuttonm_bresponseonbuttondown"></a><a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

Indique s’il faut répondre aux événements boutonné vers le bas.

```
BOOL m_bResponseOnButtonDown;
```

## <a name="cmfcbuttonm_brightimage"></a><a name="m_brightimage"></a>CMFCButton::m_bRightImage

Indique s’il faut afficher une image sur le côté droit du bouton.

```
BOOL m_bRightImage;
```

## <a name="cmfcbuttonm_btopimagem_btopimage"></a><a name="m_bTopImage"></a>CMFCButton::m_bTopImage](#m_bTopImage)

Indique si l’image est sur le dessus du bouton.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Notes

Définissez `m_bRightImage` le membre à TRUE pour spécifier que le cadre affichera l’image du bouton à droite de l’étiquette de texte du bouton.

## <a name="cmfcbuttonm_btransparent"></a><a name="m_btransparent"></a>CMFCButton::m_bTransparent

Indique si le bouton est transparent.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Notes

Définissez `m_bTransparent` le membre à TRUE pour spécifier que le cadre rendra le bouton transparent. Le `CMFCButton` constructeur initialise ce membre à FALSE.

## <a name="cmfcbuttonm_nalignstyle"></a><a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

Spécifie l’alignement du texte du bouton.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Notes

Utilisez l’une `CMFCButton::AlignStyle` des valeurs d’énumération suivantes pour spécifier l’alignement du texte du bouton :

|Valeur|Description|
|-----------|-----------------|
|ALIGN_CENTER|(Par défaut) Aligne le texte du bouton au centre du bouton.|
|ALIGN_LEFT|Aligne le texte du bouton sur le côté gauche du bouton.|
|ALIGN_RIGHT|Aligne le texte du bouton sur le côté droit du bouton.|

Le `CMFCButton` constructeur initialise ce membre pour ALIGN_CENTER.

## <a name="cmfcbuttonm_bwasdblclkm_bwasdblclk"></a><a name="m_bWasDblClk"></a>CMFCButton::m_bWasDblClk](#m_bWasDblClk)

Indique si le dernier clic a été un double clic.

```
BOOL m_bWasDblClk;
```

## <a name="cmfcbuttonm_nflatstyle"></a><a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle

Spécifie le style du bouton, comme sans bordure, plat, semi-plat, ou 3D.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Notes

Le tableau suivant `CMFCButton::m_nFlatStyle` répertorie les valeurs d’énumération qui spécifient l’apparence d’un bouton.

|Valeur|Description|
|-----------|-----------------|
|BUTTONSTYLE_3D|(Par défaut) Le bouton semble avoir des côtés hauts et tridimensionnels. Lorsque le bouton est cliqué, le bouton semble être pressé dans une indentation profonde.|
|BUTTONSTYLE_FLAT|Lorsque la souris ne s’arrête pas sur le bouton, le bouton semble être bidimensionnel et n’a pas les côtés levés. Lorsque la souris s’arrête sur le bouton, le bouton semble avoir des côtés bas et tridimensionnels. Lorsque le bouton est cliqué, le bouton semble être pressé dans une indentation peu profonde.|
|BUTTONSTYLE_SEMIFLAT|Le bouton semble avoir des côtés bas et tridimensionnels. Lorsque le bouton est cliqué, le bouton semble être pressé dans une indentation profonde.|
|BUTTONSTYLE_NOBORDERS|Le bouton n’a pas les côtés surélevés et apparaît toujours en deux dimensions. Le bouton ne semble pas être pressé dans une indentation quand il est cliqué.|

Le `CMFCButton` constructeur initialise ce membre pour BUTTONSTYLE_3D.

### <a name="example"></a>Exemple

L’exemple suivant montre comment définir `m_nFlatStyle` les valeurs `CMFCButton` de la variable du membre dans la classe. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

## <a name="cmfcbuttonondraw"></a><a name="ondraw"></a>CMFCButton::OnDraw

Appelé par le cadre pour dessiner un bouton.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Une référence à un rectangle qui limite le bouton.

*uiState (uiState)*<br/>
[dans] L’état du bouton actuel. Pour plus d’informations, consultez le `itemState` sujet de la structure [DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct)

### <a name="remarks"></a>Notes

Remplacez cette méthode pour utiliser votre propre code pour dessiner un bouton.

## <a name="cmfcbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCButton::OnDrawBorder

Appelé par le cadre pour dessiner la bordure d’un bouton.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*rectClient*<br/>
[dans] Une référence à un rectangle qui limite le bouton.

*uiState (uiState)*<br/>
[dans] L’état du bouton actuel. Pour plus d’informations, consultez le `itemState` sujet de la structure [DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct)

### <a name="remarks"></a>Notes

Remplacez cette méthode pour utiliser votre propre code pour dessiner la frontière.

## <a name="cmfcbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect

Appelé par le cadre pour dessiner le rectangle de mise au point pour un bouton.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*rectClient*<br/>
[dans] Une référence à un rectangle qui limite le bouton.

### <a name="remarks"></a>Notes

Remplacez cette méthode pour utiliser votre propre code pour dessiner le rectangle de mise au point.

## <a name="cmfcbuttonondrawtext"></a><a name="ondrawtext"></a>CMFCButton::OnDrawText

Appelé par le cadre pour dessiner le texte du bouton.

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Une référence à un rectangle qui limite le bouton.

*strText (en)*<br/>
[dans] Le texte à dessiner.

*uiDTFlags uiDTFlags*<br/>
[dans] Drapeaux qui spécifient comment formater le texte. Pour plus d’informations, voir le paramètre *nFormat* de la méthode [CDC::DrawText.](../../mfc/reference/cdc-class.md#drawtext)

*uiState (uiState)*<br/>
[in] Réservée.

### <a name="remarks"></a>Notes

Remplacez cette méthode pour utiliser votre propre code pour dessiner le texte du bouton.

## <a name="cmfcbuttononfillbackground"></a><a name="onfillbackground"></a>CMFCButton::OnFillBackground

Appelé par le cadre pour dessiner l’arrière-plan du texte bouton.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*rectClient*<br/>
[dans] Une référence à un rectangle qui limite le bouton.

### <a name="remarks"></a>Notes

Remplacez cette méthode pour utiliser votre propre code pour dessiner l’arrière-plan d’un bouton.

## <a name="cmfcbuttonselectfont"></a><a name="selectfont"></a>CMFCButton::SelectFont

Récupère la police associée au contexte de l’appareil spécifié.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

### <a name="return-value"></a>Valeur de retour

Remplacez cette méthode pour utiliser votre propre code pour récupérer la police.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonsetautorepeatmode"></a><a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode

Définit un bouton en mode répétition automatique.

```cpp
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Paramètres

*nTimeDelay (en)*<br/>
[dans] Un numéro non natif qui spécifie l’intervalle entre les messages envoyés à la fenêtre parente. L’intervalle est mesuré en millisecondes et sa valeur par défaut est de 500 millisecondes. Spécifiez zéro pour désactiver le mode de message automatique- répétition.

### <a name="remarks"></a>Notes

Cette méthode provoque le bouton d’envoyer constamment WM_COMMAND messages à la fenêtre parente jusqu’à ce que le bouton est libéré, ou le paramètre *nTimeDelay* est réglé à zéro.

## <a name="cmfcbuttonsetcheckedimage"></a><a name="setcheckedimage"></a>CMFCButton::SetCheckedImage

Définit l’image pour un bouton vérifié.

```cpp
void SetCheckedImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetCheckedImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetCheckedImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>Paramètres

*hIcon (en)*<br/>
[dans] Portez-le à l’icône qui contient la bitmap et le masque pour la nouvelle image.

*bAutoDestroy*<br/>
[dans] VRAI pour spécifier que les ressources de bitmap soient détruites automatiquement; autrement, FALSE. La valeur par défaut est TRUE.

*hIconHot (en)*<br/>
[dans] Portez-le à l’icône qui contient l’image pour l’état sélectionné.

*hBitmap (en)*<br/>
[dans] Portez-le à la bitmap qui contient l’image pour l’état non sélectionné.

*hBitmapHot (en)*<br/>
[dans] Portez-le à la bitmap qui contient l’image pour l’état sélectionné.

*bMap3dColors (en)*<br/>
[dans] Spécifie une couleur transparente pour le fond du bouton; c’est-à-dire, le visage du bouton. VRAI pour utiliser la valeur de couleur RGB(192, 192, 192); FALSE pour utiliser la `AFX_GLOBAL_DATA::clrBtnFace`valeur de couleur définie par .

*uiBmpResId*<br/>
[dans] ID de ressource pour l’image non sélectionnée.

*uiBmpHotResId uiBmpHotResId*<br/>
[dans] ID de ressource pour l’image sélectionnée.

*hIconDisabled*<br/>
[dans] Poignée à l’icône pour l’image désactivée.

*hBitmapDisabled*<br/>
[dans] Manipuler à la bitmap qui contient l’image désactivée.

*uiBmpDsblResID*<br/>
[dans] Id de ressource de la bitmap désactivée.

*bAlphaBlend*<br/>
[dans] VRAI pour utiliser seulement des images 32 bits qui utilisent le canal alpha; FALSE, de ne pas utiliser que des images alpha canal. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonsetfacecolor"></a><a name="setfacecolor"></a>CMFCButton::SetFaceColor

Définit la couleur de fond pour le texte du bouton.

```cpp
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*crFace (en)*<br/>
[dans] Une valeur de couleur RGB.

*bRedraw (en)*<br/>
[dans] VRAI pour redessiner l’écran immédiatement; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une nouvelle couleur de remplissage pour le fond du bouton (visage). Notez que l’arrière-plan n’est pas rempli lorsque le [CMFCButton::m_bTransparent](#m_btransparent) variable membre est VRAI.

## <a name="cmfcbuttonsetimage"></a><a name="setimage"></a>CMFCButton::SetImage

Définit l’image pour un bouton.

```cpp
void SetImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>Paramètres

*hIcon (en)*<br/>
[dans] Portez-le à l’icône qui contient la bitmap et le masque pour la nouvelle image.

*bAutoDestroy*<br/>
[dans] VRAI pour spécifier que les ressources de bitmap soient détruites automatiquement; autrement, FALSE. La valeur par défaut est TRUE.

*hIconHot (en)*<br/>
[dans] Portez-le à l’icône qui contient l’image pour l’état sélectionné.

*hBitmap (en)*<br/>
[dans] Portez-le à la bitmap qui contient l’image pour l’état non sélectionné.

*hBitmapHot (en)*<br/>
[dans] Portez-le à la bitmap qui contient l’image pour l’état sélectionné.

*uiBmpResId*<br/>
[dans] ID de ressource pour l’image non sélectionnée.

*uiBmpHotResId uiBmpHotResId*<br/>
[dans] ID de ressource pour l’image sélectionnée.

*bMap3dColors (en)*<br/>
[dans] Spécifie une couleur transparente pour le fond du bouton; c’est-à-dire, le visage du bouton. VRAI pour utiliser la valeur de couleur RGB(192, 192, 192); FALSE pour utiliser la `AFX_GLOBAL_DATA::clrBtnFace`valeur de couleur définie par .

*hIconDisabled*<br/>
[dans] Poignée à l’icône pour l’image désactivée.

*hBitmapDisabled*<br/>
[dans] Manipuler à la bitmap qui contient l’image désactivée.

*uiBmpDsblResID*<br/>
[dans] Id de ressource de la bitmap désactivée.

*bAlphaBlend*<br/>
[dans] VRAI pour utiliser seulement des images 32 bits qui utilisent le canal alpha; FALSE, de ne pas utiliser que des images alpha canal. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes `SetImage` versions `CMFCButton` de la méthode dans la classe. L’exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

## <a name="cmfcbuttonsetmousecursor"></a><a name="setmousecursor"></a>CMFCButton::SetMouseCursor

Définit l’image du curseur.

```cpp
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Paramètres

*hcursor*<br/>
[dans] La poignée d’un curseur.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour associer une image curseur, comme le curseur, avec le bouton. Le curseur est chargé à partir des ressources d’application.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `SetMouseCursor` utiliser `CMFCButton` la méthode dans la classe. L’exemple fait partie du code de [l’échantillon New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

## <a name="cmfcbuttonsetmousecursorhand"></a><a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

Définit le curseur à l’image d’une main.

```cpp
void SetMouseCursorHand();
```

### <a name="remarks"></a>Notes

Utilisez cette méthode pour associer l’image curseur d’une main avec le bouton. Le curseur est chargé à partir des ressources d’application.

## <a name="cmfcbuttonsetstdimage"></a><a name="setstdimage"></a>CMFCButton::SetStdImage

Utilise `CMenuImages` un objet pour définir l’image bouton.

```cpp
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] Un des identificateurs d’image `CMenuImage::IMAGES_IDS` bouton qui est défini dans le recensement. Les valeurs d’image spécifient des images telles que des flèches, des épingles et des boutons radio.

*state*<br/>
[dans] Un des identifiants d’état d’image de bouton qui est défini dans l’énumération. `CMenuImages::IMAGE_STATE` Les états d’image spécifient des couleurs de bouton telles que le noir, le gris, le gris clair, le blanc et le gris foncé. La valeur par défaut est `CMenuImages::ImageBlack`.

*idDisabled*<br/>
[dans] Un des identificateurs d’image `CMenuImage::IMAGES_IDS` bouton qui est défini dans le recensement. L’image indique que le bouton est désactivé. La valeur par défaut est `CMenuImages::IdArrowDown`la première image bouton ( ).

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonsettextcolor"></a><a name="settextcolor"></a>CMFCButton::SetTextColor

Définit la couleur du texte du bouton pour un bouton qui n’est pas sélectionné.

```cpp
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Paramètres

*clrText*<br/>
[dans] Une valeur de couleur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonsettexthotcolor"></a><a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

Définit la couleur du texte du bouton pour un bouton sélectionné.

```cpp
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Paramètres

*clrTextHot*<br/>
[dans] Une valeur de couleur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonsettooltip"></a><a name="settooltip"></a>CMFCButton::SetTooltip

Associe une boîte à outils à un bouton.

```cpp
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Paramètres

*lpszToolTipText*<br/>
[dans] Pointeur sur le texte pour le bout d’outil. Spécifier NULL pour désactiver l’outiltip.

### <a name="remarks"></a>Notes

## <a name="cmfcbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCButton::SizeToContent

Resizes un bouton pour contenir son texte et son image boutonné.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Paramètres

*bCalcOnly*<br/>
[dans] VRAI pour calculer, mais pas changer, la nouvelle taille du bouton; FALSE pour changer la taille du bouton. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Un `CSize` objet qui contient la nouvelle taille du bouton.

### <a name="remarks"></a>Notes

Par défaut, cette méthode calcule une nouvelle taille qui comprend une marge horizontale de 10 pixels et une marge verticale de 5 pixels.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl, classe](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[Classe CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton, classe](../../mfc/reference/cmfcmenubutton-class.md)
