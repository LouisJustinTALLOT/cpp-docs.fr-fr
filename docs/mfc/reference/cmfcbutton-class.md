---
title: Cmfcbutton, classe
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
ms.openlocfilehash: 0659e5335e1ebc495280a4e0cb5c0167f3b45e1d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768212"
---
# <a name="cmfcbutton-class"></a>Cmfcbutton, classe

Le `CMFCButton` classe ajoute des fonctionnalités à la [CButton](../../mfc/reference/cbutton-class.md) classe telles que l’alignement du texte du bouton, combinaison de texte du bouton et une image, sélection d’un curseur et en spécifiant une info-bulle.

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
|[CMFCButton::CleanUp](#cleanup)|Réinitialise les variables internes et libère les ressources allouées, tels que des images, bitmaps et icônes.|
|`CMFCButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCButton::DrawItem`|Appelé par le framework lorsqu’un aspect visuel d’un bouton owner-drawn a été modifiée. (Substitue [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Spécifie s’il faut afficher le texte intégral d’une info-bulle dans une fenêtre d’info-bulle de grande taille ou une version tronquée du texte dans une fenêtre d’info-bulle petit.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Spécifie si la police de texte du bouton est identique à la police du menu application.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Spécifie si le style de la bordure du bouton correspond au thème Windows en cours.|
|`CMFCButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Retourne une référence au contrôle d’info-bulle sous-jacent.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Indique si une case à cocher ou une case d’option est un bouton automatique.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Indique si un bouton est défini en mode de répétition automatique.|
|[CMFCButton::IsCheckBox](#ischeckbox)|Indique si un bouton est un bouton de case à cocher.|
|[CMFCButton::IsChecked](#ischecked)|Indique si le bouton en cours est activé.|
|[CMFCButton::IsHighlighted](#ishighlighted)|Indique si un bouton est mis en surbrillance.|
|[CMFCButton::IsPressed](#ispressed)|Indique si un bouton est envoyé et mis en surbrillance.|
|[CMFCButton::IsPushed](#ispushed)|Indique si un bouton est enfoncé.|
|[CMFCButton::IsRadioButton](#isradiobutton)|Indique si un bouton est un bouton radio.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Indique si le style de la bordure du bouton correspond au thème Windows en cours.|
|`CMFCButton::OnDrawParentBackground`|Dessine l’arrière-plan parent d’un bouton dans la zone spécifiée. (Overrides [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils soient distribués à le [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) des fonctions de Windows. (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Définit un bouton en mode auto-repeat.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Définit l’image d’un bouton activé.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Définit la couleur d’arrière-plan pour le texte du bouton.|
|[CMFCButton::SetImage](#setimage)|Définit l’image d’un bouton.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Définit l’image de curseur.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Définit le curseur à l’image d’une main.|
|[CMFCButton::SetStdImage](#setstdimage)|Utilise un `CMenuImages` objet pour définir l’image du bouton.|
|[CMFCButton::SetTextColor](#settextcolor)|Définit la couleur du texte du bouton pour un bouton qui n’est pas sélectionné.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Définit la couleur du texte du bouton pour un bouton est sélectionné.|
|[CMFCButton::SetTooltip](#settooltip)|Associe une info-bulle à un bouton.|
|[CMFCButton::SizeToContent](#sizetocontent)|Redimensionne un bouton afin qu’il contienne son texte et bouton image.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner un bouton.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Appelé par l’infrastructure pour dessiner la bordure d’un bouton.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Appelé par l’infrastructure pour dessiner le rectangle de focus pour un bouton.|
|[CMFCButton::OnDrawText](#ondrawtext)|Appelé par l’infrastructure pour dessiner le texte du bouton.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Appelé par l’infrastructure pour dessiner l’arrière-plan du texte du bouton.|
|[CMFCButton::SelectFont](#selectfont)|Récupère la police qui est associée au contexte de périphérique spécifié.|

### <a name="data-members"></a>Membres de données

|Nom|Description|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Spécifie l’alignement du texte du bouton.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Spécifie s’il faut utiliser des thèmes Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Indique s’il faut dessiner un rectangle de focus autour d’un bouton.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Spécifie le style du bouton, tels que sans bordure, plat, plat point-virgule ou 3D.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Lorsque la valeur est TRUE, permet à un bouton désactivé être dessiné comme grisé.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Indique s’il faut mettre en surbrillance un bouton de style BS_CHECKBOX lorsque le curseur passe dessus.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Indique s’il faut répondre à la pression du bouton.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Indique s’il faut afficher une image sur le côté droit du bouton.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Indique si l’image est sur le bouton.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Indique si le bouton est transparent.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Indique si vous cliquez sur le dernier événement a été un double-clic.|

## <a name="remarks"></a>Notes

Autres types de boutons sont dérivés de la `CMFCButton` classe, telle que la [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) (classe), qui prend en charge des liens hypertexte, et le `CMFCColorButton` (classe), qui prend en charge une boîte de dialogue de sélecteur de couleurs.

Le style d’un `CMFCButton` objet peut être *3D*, *plat*, *plat point-virgule* ou *aucune bordure*. Texte du bouton peut être aligné à gauche, haut ou au centre d’un bouton. Au moment de l’exécution, vous pouvez contrôler si le bouton affiche texte, une image, ou du texte et une image. Vous pouvez également spécifier une image de curseur particulier affichera lorsque le curseur pointe sur un bouton.

Créer un contrôle bouton directement dans votre code, ou à l’aide de la **Assistant classe MFC** outil et un modèle de boîte de dialogue. Si vous créez directement un contrôle de bouton, ajouter un `CMFCButton` variable et votre application, puis appelez le constructeur et `Create` méthodes de la `CMFCButton` objet. Si vous utilisez le **Assistant classe MFC**, ajoutez un `CButton` variable à votre application, puis modifiez le type de la variable de `CButton` à `CMFCButton`.

Pour gérer les messages de notification dans une application de boîte de dialogue, ajoutez une entrée de mappage de message et un gestionnaire d’événements pour chaque notification. Les notifications envoyées par un `CMFCButton` objet sont les mêmes que celles envoyées par un `CButton` objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer les propriétés du bouton à l’aide de différentes méthodes de la `CMFCButton` classe. L’exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

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

## <a name="requirements"></a>Configuration requise

**En-tête :** afxbutton.h

##  <a name="cleanup"></a>  CMFCButton::CleanUp

Réinitialise les variables internes et libère les ressources allouées, tels que des images, bitmaps et icônes.

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip

Spécifie s’il faut afficher le texte intégral d’une info-bulle dans une fenêtre d’info-bulle de grande taille ou une version tronquée du texte dans une fenêtre d’info-bulle petit.

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
[in] TRUE pour afficher tout le texte ; FALSE pour le texte d’affichage tronqué.

### <a name="remarks"></a>Notes

##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont

Spécifie si la police de texte du bouton est identique à la police du menu application.

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
[in] TRUE pour utiliser la police du menu application comme la police de texte de bouton. FALSE pour utiliser la police système. La valeur par défaut est TRUE.

*bRedraw*<br/>
[in] Valeur TRUE à se redessiner immédiatement avec l’écran ; Sinon, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Si vous n’utilisez pas cette méthode pour spécifier la police de texte de bouton, vous pouvez spécifier la police avec la [CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont) (méthode). Si vous ne spécifiez pas du tout une police, le framework définit une police par défaut.

##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming

Spécifie si le style de la bordure du bouton correspond au thème Windows en cours.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[in] TRUE pour utiliser le thème Windows en cours pour dessiner les bordures du bouton ; FALSE pour ne pas utiliser le thème Windows. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Cette méthode affecte tous les boutons dans votre application qui sont dérivés de la `CMFCButton` classe.

##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl

Retourne une référence au contrôle d’info-bulle sous-jacent.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Valeur de retour

Une référence au contrôle d’info-bulle sous-jacent.

### <a name="remarks"></a>Notes

##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck

Indique si une case à cocher ou une case d’option est un bouton automatique.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton a le style BS_AUTOCHECKBOX ou BS_AUTORADIOBUTTON ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode

Indique si un bouton est défini en mode de répétition automatique.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton est défini en mode de répétition automatique ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez le [CMFCButton::SetAutorepeatMode](#setautorepeatmode) méthode pour définir un bouton en mode auto-repeat.

##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox

Indique si un bouton est un bouton de case à cocher.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton de style BS_CHECKBOX ou BS_AUTOCHECKBOX ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="ischecked"></a>  CMFCButton::IsChecked

Indique si le bouton en cours est activé.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton en cours est activé ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Le framework utilise des méthodes différentes pour indiquer que les différents types de boutons sont vérifiés. Par exemple, une case d’option est activée lorsqu’elle contient un point ; une case à cocher est activée lorsqu’elle contient un **X**.

##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted

Indique si un bouton est mis en surbrillance.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton est mis en surbrillance ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Un bouton est mis en surbrillance lorsque la souris pointe sur le bouton.

##  <a name="ispressed"></a>  CMFCButton::IsPressed

Indique si un bouton est envoyé et mis en surbrillance.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton est enfoncé ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="ispushed"></a>  CMFCButton::IsPushed

Indique si un bouton est enfoncé.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton est actionné ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton

Indique si un bouton est un bouton radio.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le style de bouton est BS_RADIOBUTTON ou BS_AUTORADIOBUTTON ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled

Indique si le style de la bordure du bouton correspond au thème Windows en cours.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Valeur de retour

TRUE si le style de la bordure du bouton correspondant au thème Windows en cours ; Sinon, FALSE.

## <a name="a-namembdontusewinxptheme-cmfcbuttonmbdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/> CMFCButton::m_bDontUseWinXPTheme

Spécifie s’il faut utiliser des thèmes Windows XP lorsque le bouton de dessin.

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus

Indique s’il faut dessiner un rectangle de focus autour d’un bouton.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Notes

Définir le `m_bDrawFocus` membre True pour spécifier que l’infrastructure dessiner un rectangle de focus autour de texte du bouton et de l’image si le bouton reçoit le focus.

Le `CMFCButton` constructeur initialise ce membre sur TRUE.

##  <a name="m_bGrayDisabled"></a>  CMFCButton::m_bGrayDisabled

Lorsque la valeur est TRUE, permet à un bouton désactivé être dessiné comme grisé.

```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked

Indique s’il faut mettre en surbrillance un bouton de style BS_CHECKBOX lorsque le curseur passe dessus.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Notes

Définir le `m_bHighlightChecked` membre sur TRUE pour spécifier que le framework met en évidence un bouton de style BS_CHECKBOX lorsque la souris passe dessus.

##  <a name="m_bResponseOnButtonDown"></a> CMFCButton::m_bResponseOnButtonDown

Indique s’il faut répondre à la pression du bouton.

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage

Indique s’il faut afficher une image sur le côté droit du bouton.

```
BOOL m_bRightImage;
```

##  <a name="m_bTopImage"></a>  CMFCButton::m_bTopImage](#m_bTopImage)

Indique si l’image est sur le bouton.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Notes

Définir le `m_bRightImage` membre sur TRUE pour spécifier que le framework affiche l’image du bouton à droite de l’étiquette de texte du bouton.

##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent

Indique si le bouton est transparent.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Notes

Définir le `m_bTransparent` membre sur TRUE pour indiquer que l’infrastructure de faire le bouton transparent. Le `CMFCButton` constructeur initialise ce membre sur FALSE.

##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle

Spécifie l’alignement du texte du bouton.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Notes

Utilisez une des opérations suivantes `CMFCButton::AlignStyle` valeurs d’énumération pour spécifier l’alignement du texte du bouton :

|Value|Description|
|-----------|-----------------|
|ALIGN_CENTER|(Valeur par défaut) Aligne le texte du bouton au centre du bouton.|
|ALIGN_LEFT|Aligne le texte du bouton à gauche du bouton.|
|ALIGN_RIGHT|Aligne le texte du bouton à droite du bouton.|

Le `CMFCButton` constructeur initialise ce membre en ALIGN_CENTER.

##  <a name="m_bWasDblClk"></a>  CMFCButton::m_bWasDblClk](#m_bWasDblClk)|

Indique si vous cliquez sur le dernier événement a été un double-clic. |

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle

Spécifie le style du bouton, tels que sans bordure, plat, plat point-virgule ou 3D.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les `CMFCButton::m_nFlatStyle` des valeurs d’énumération qui spécifient l’apparence d’un bouton.

|Value|Description|
|-----------|-----------------|
|BUTTONSTYLE_3D|(Valeur par défaut) Le bouton semble avoir des côtés haute, en trois dimensions. Lorsque le bouton est activé, le bouton apparaît à enfoncer dans une mise en retrait approfondie.|
|BUTTONSTYLE_FLAT|Lorsque la souris n’interrompez pas sur le bouton, le bouton semble être à deux dimensions et n’a pas déclenchées côtés. Lorsque la souris est maintenu sur le bouton, le bouton s’affiche pour que les côtés faibles, en trois dimensions. Lorsque le bouton est activé, le bouton apparaît à enfoncer dans une mise en retrait superficielle.|
|BUTTONSTYLE_SEMIFLAT|Le bouton semble avoir des côtés faibles, en trois dimensions. Lorsque le bouton est activé, le bouton apparaît à enfoncer dans une mise en retrait approfondie.|
|BUTTONSTYLE_NOBORDERS|Le bouton ne pas avoir déclenché côtés et apparaît toujours à deux dimensions. Le bouton n’apparaît pas à enfoncer dans une mise en retrait lorsque vous cliquez dessus.|

Le `CMFCButton` constructeur initialise ce membre en BUTTONSTYLE_3D.

### <a name="example"></a>Exemple

L’exemple suivant montre comment définir les valeurs de la `m_nFlatStyle` variable de membre dans la `CMFCButton` classe. Cet exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

##  <a name="ondraw"></a>  CMFCButton::OnDraw

Appelé par l’infrastructure pour dessiner un bouton.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*rect*<br/>
[in] Une référence à un rectangle qui délimite le bouton.

*uiState*<br/>
[in] L’état actuel de bouton. Pour plus d’informations, consultez le `itemState` membre de la [drawitemstruct, Structure](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) rubrique.

### <a name="remarks"></a>Notes

Substituez cette méthode pour utiliser votre propre code pour dessiner un bouton.

##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder

Appelé par l’infrastructure pour dessiner la bordure d’un bouton.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*rectClient*<br/>
[in] Une référence à un rectangle qui délimite le bouton.

*uiState*<br/>
[in] L’état actuel de bouton. Pour plus d’informations, consultez le `itemState` membre de la [drawitemstruct, Structure](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) rubrique.

### <a name="remarks"></a>Notes

Substituez cette méthode pour utiliser votre propre code pour dessiner la bordure.

##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect

Appelé par l’infrastructure pour dessiner le rectangle de focus pour un bouton.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*rectClient*<br/>
[in] Une référence à un rectangle qui délimite le bouton.

### <a name="remarks"></a>Notes

Substituez cette méthode pour utiliser votre propre code pour dessiner le rectangle de focus.

##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText

Appelé par l’infrastructure pour dessiner le texte du bouton.

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
[in] Pointeur vers un contexte de périphérique.

*rect*<br/>
[in] Une référence à un rectangle qui délimite le bouton.

*strText*<br/>
[in] Le texte à dessiner.

*uiDTFlags*<br/>
[in] Indicateurs qui spécifient comment mettre en forme le texte. Pour plus d’informations, consultez le *nFormat* paramètre de la [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) (méthode).

*uiState*<br/>
[in] Réservée.

### <a name="remarks"></a>Notes

Substituez cette méthode pour utiliser votre propre code pour dessiner le texte du bouton.

##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground

Appelé par l’infrastructure pour dessiner l’arrière-plan du texte du bouton.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*rectClient*<br/>
[in] Une référence à un rectangle qui délimite le bouton.

### <a name="remarks"></a>Notes

Substituez cette méthode pour utiliser votre propre code pour dessiner l’arrière-plan d’un bouton.

##  <a name="selectfont"></a>  CMFCButton::SelectFont

Récupère la police qui est associée au contexte de périphérique spécifié.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

### <a name="return-value"></a>Valeur de retour

Substituez cette méthode pour utiliser votre propre code pour récupérer la police.

### <a name="remarks"></a>Notes

##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode

Définit un bouton en mode auto-repeat.

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Paramètres

*nTimeDelay*<br/>
[in] Un nombre non négatif qui spécifie l’intervalle entre les messages sont envoyés vers la fenêtre parente. L’intervalle est mesuré en millisecondes, et sa valeur par défaut est 500 millisecondes. Spécifiez zéro pour désactiver le mode de répétition automatique message.

### <a name="remarks"></a>Notes

Cette méthode provoque le bouton Envoyer des messages WM_COMMAND constamment à la fenêtre parente jusqu'à ce que le bouton est relâché, ou le *nTimeDelay* paramètre est défini sur zéro.

##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage

Définit l’image d’un bouton activé.

```
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

*hIcon*<br/>
[in] Handle de l’icône qui contient l’image bitmap et un masque pour la nouvelle image.

*bAutoDestroy*<br/>
[in] TRUE pour spécifier que les ressources bitmap d’être détruit automatiquement ; Sinon, FALSE. La valeur par défaut est TRUE.

*hIconHot*<br/>
[in] Handle de l’icône qui contient l’image pour l’état sélectionné.

*hBitmap*<br/>
[in] Handle de bitmap qui contient l’image pour l’état non sélectionné.

*hBitmapHot*<br/>
[in] Handle de bitmap qui contient l’image pour l’état sélectionné.

*bMap3dColors*<br/>
[in] Spécifie une couleur transparente pour l’arrière-plan du bouton ; Autrement dit, la face du bouton. TRUE pour utiliser la valeur de couleur RVB (192, 192, 192) ; FALSE pour utiliser la valeur de couleur définie par `AFX_GLOBAL_DATA::clrBtnFace`.

*uiBmpResId*<br/>
[in] ID de ressource pour l’image non sélectionnée.

*uiBmpHotResId*<br/>
[in] ID de ressource pour l’image sélectionnée.

*hIconDisabled*<br/>
[in] Handle de l’icône de l’image désactivée.

*hBitmapDisabled*<br/>
[in] Handle de bitmap qui contient l’image désactivé.

*uiBmpDsblResID*<br/>
[in] ID de ressource de la bitmap désactivée.

*bAlphaBlend*<br/>
[in] True pour utiliser des images 32 bits uniquement qui utilisent le canal alpha ; FALSE pour ne pas utiliser les images de canal alpha uniquement. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor

Définit la couleur d’arrière-plan pour le texte du bouton.

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*crFace*<br/>
[in] Une valeur de couleur RVB.

*bRedraw*<br/>
[in] TRUE pour redessiner l’écran immédiatement ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une nouvelle couleur de remplissage pour l’arrière-plan du bouton (face). Notez que l’arrière-plan n’est pas remplie quand le [CMFCButton::m_bTransparent](#m_btransparent) variable membre a la valeur TRUE.

##  <a name="setimage"></a>  CMFCButton::SetImage

Définit l’image d’un bouton.

```
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

*hIcon*<br/>
[in] Handle de l’icône qui contient l’image bitmap et un masque pour la nouvelle image.

*bAutoDestroy*<br/>
[in] TRUE pour spécifier que les ressources bitmap d’être détruit automatiquement ; Sinon, FALSE. La valeur par défaut est TRUE.

*hIconHot*<br/>
[in] Handle de l’icône qui contient l’image pour l’état sélectionné.

*hBitmap*<br/>
[in] Handle de bitmap qui contient l’image pour l’état non sélectionné.

*hBitmapHot*<br/>
[in] Handle de bitmap qui contient l’image pour l’état sélectionné.

*uiBmpResId*<br/>
[in] ID de ressource pour l’image non sélectionnée.

*uiBmpHotResId*<br/>
[in] ID de ressource pour l’image sélectionnée.

*bMap3dColors*<br/>
[in] Spécifie une couleur transparente pour l’arrière-plan du bouton ; Autrement dit, la face du bouton. TRUE pour utiliser la valeur de couleur RVB (192, 192, 192) ; FALSE pour utiliser la valeur de couleur définie par `AFX_GLOBAL_DATA::clrBtnFace`.

*hIconDisabled*<br/>
[in] Handle de l’icône de l’image désactivée.

*hBitmapDisabled*<br/>
[in] Handle de bitmap qui contient l’image désactivé.

*uiBmpDsblResID*<br/>
[in] ID de ressource de la bitmap désactivée.

*bAlphaBlend*<br/>
[in] True pour utiliser des images 32 bits uniquement qui utilisent le canal alpha ; FALSE pour ne pas utiliser les images de canal alpha uniquement. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les différentes versions de la `SetImage` méthode dans la `CMFCButton` classe. L’exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor

Définit l’image de curseur.

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Paramètres

*hcursor*<br/>
[in] Le handle d’un curseur.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour associer une image de curseur, tels que le curseur de la main, avec le bouton. Le curseur est chargé à partir de ressources d’application.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `SetMouseCursor` méthode dans la `CMFCButton` classe. L’exemple fait partie du code dans le [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand

Définit le curseur à l’image d’une main.

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>Notes

Cette méthode permet d’associer l’image de curseur d’une main avec le bouton. Le curseur est chargé à partir de ressources d’application.

##  <a name="setstdimage"></a>  CMFCButton::SetStdImage

Utilise un `CMenuImages` objet pour définir l’image du bouton.

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] Un des identificateurs d’image de bouton qui est défini dans le `CMenuImage::IMAGES_IDS` énumération. Les valeurs d’image spécifient des images telles que des flèches, des codes confidentiels et des cases d’option.

*state*<br/>
[in] Un des identificateurs de bouton image état est défini dans le `CMenuImages::IMAGE_STATE` énumération. Les États d’image spécifient des couleurs de bouton telles que les gris foncé et blancs gris noir, gris clair. La valeur par défaut est `CMenuImages::ImageBlack`.

*idDisabled*<br/>
[in] Un des identificateurs d’image de bouton qui est défini dans le `CMenuImage::IMAGES_IDS` énumération. L’image indique que le bouton est désactivé. La valeur par défaut est la première image de bouton ( `CMenuImages::IdArrowDown`).

### <a name="remarks"></a>Notes

##  <a name="settextcolor"></a>  CMFCButton::SetTextColor

Définit la couleur du texte du bouton pour un bouton qui n’est pas sélectionné.

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Paramètres

*clrText*<br/>
[in] Une valeur de couleur RVB.

### <a name="remarks"></a>Notes

##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor

Définit la couleur du texte du bouton pour un bouton est sélectionné.

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Paramètres

*clrTextHot*<br/>
[in] Une valeur de couleur RVB.

### <a name="remarks"></a>Notes

##  <a name="settooltip"></a>  CMFCButton::SetTooltip

Associe une info-bulle à un bouton.

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Paramètres

*lpszToolTipText*<br/>
[in] Pointeur vers le texte de l’info-bulle. Spécifiez NULL pour désactiver l’info-bulle.

### <a name="remarks"></a>Notes

##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent

Redimensionne un bouton afin qu’il contienne son texte et bouton image.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Paramètres

*bCalcOnly*<br/>
[in] Pour calculer la valeur TRUE, mais pas modifiées, la nouvelle taille du bouton ; Pour modifier la taille du bouton, la valeur est FALSE. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Un `CSize` objet qui contient la nouvelle taille du bouton.

### <a name="remarks"></a>Notes

Par défaut, cette méthode calcule une nouvelle taille qui inclut une marge horizontale de 10 pixels et une marge verticale de 5 pixels.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl, classe](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton, classe](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton, classe](../../mfc/reference/cmfcmenubutton-class.md)
