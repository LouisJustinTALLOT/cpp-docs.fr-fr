---
title: CMFCButton, classe
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
ms.openlocfilehash: 7628ac353d01c2a6853e35a35bd1f702d3bb041e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505860"
---
# <a name="cmfcbutton-class"></a>CMFCButton, classe

La `CMFCButton` classe ajoute des fonctionnalités à la classe [CButton](../../mfc/reference/cbutton-class.md) , telles que l’alignement du texte du bouton, la combinaison d’un texte de bouton et d’une image, la sélection d’un curseur et la spécification d’une info-bulle.

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
|[CMFCButton::CleanUp](#cleanup)|Réinitialise des variables internes et libère des ressources allouées telles que des images, des bitmaps et des icônes.|
|`CMFCButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCButton::DrawItem`|Appelé par le Framework quand un aspect visuel d’un bouton owner-drawn a changé. (Substitue [CButton::D rawitem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Spécifie s’il faut afficher le texte intégral d’une info-bulle dans une grande fenêtre d’info-bulle ou une version tronquée du texte dans une petite fenêtre d’info-bulle.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Spécifie si la police du texte du bouton est identique à celle du menu de l’application.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Spécifie si le style de la bordure du bouton correspond au thème Windows actuel.|
|`CMFCButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Retourne une référence au contrôle ToolTip sous-jacent.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Indique si une case à cocher ou une case d’option est un bouton automatique.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Indique si un bouton est défini en mode de répétition automatique.|
|[CMFCButton::IsCheckBox](#ischeckbox)|Indique si un bouton est un bouton de case à cocher.|
|[CMFCButton:: IsChecked](#ischecked)|Indique si le bouton en cours est activé.|
|[CMFCButton::IsHighlighted](#ishighlighted)|Indique si un bouton est mis en surbrillance.|
|[CMFCButton:: IsPressed](#ispressed)|Indique si un bouton est poussé et mis en surbrillance.|
|[CMFCButton::IsPushed](#ispushed)|Indique si un bouton fait l’objet d’un push.|
|[CMFCButton::IsRadioButton](#isradiobutton)|Indique si un bouton est une case d’option.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Indique si le style de la bordure du bouton correspond au thème Windows actuel.|
|`CMFCButton::OnDrawParentBackground`|Dessine l’arrière-plan du parent d’un bouton dans la zone spécifiée. (Substitue [AFX_GLOBAL_DATA::D rawparentbackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Définit un bouton pour le mode de répétition automatique.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Définit l’image d’un bouton activé.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Définit la couleur d’arrière-plan du texte du bouton.|
|[CMFCButton::SetImage](#setimage)|Définit l’image d’un bouton.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Définit l’image de curseur.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Définit le curseur sur l’image d’une main.|
|[CMFCButton::SetStdImage](#setstdimage)|Utilise un `CMenuImages` objet pour définir l’image du bouton.|
|[CMFCButton::SetTextColor](#settextcolor)|Définit la couleur du texte du bouton pour un bouton qui n’est pas sélectionné.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Définit la couleur du texte du bouton d’un bouton sélectionné.|
|[CMFCButton::SetTooltip](#settooltip)|Associe une info-bulle à un bouton.|
|[CMFCButton:: SizeToContent](#sizetocontent)|Redimensionne un bouton pour qu’il contienne son texte de bouton et son image.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCButton:: OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner un bouton.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Appelé par l’infrastructure pour dessiner la bordure d’un bouton.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Appelé par l’infrastructure pour dessiner le rectangle de focus pour un bouton.|
|[CMFCButton::OnDrawText](#ondrawtext)|Appelé par l’infrastructure pour dessiner le texte du bouton.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Appelé par l’infrastructure pour dessiner l’arrière-plan du texte du bouton.|
|[CMFCButton::SelectFont](#selectfont)|Récupère la police associée au contexte de périphérique spécifié.|

### <a name="data-members"></a>Membres de données

|Nom|Description|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Spécifie l’alignement du texte du bouton.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Spécifie si les thèmes Windows XP doivent être utilisés.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Indique s’il faut dessiner un rectangle de focus autour d’un bouton.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Spécifie le style du bouton, tel que sans bordure, plat, semi-plat ou 3D.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Si la valeur est TRUE, active le dessin d’un bouton désactivé.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Indique s’il faut mettre en surbrillance un bouton de style BS_CHECKBOX quand le curseur pointe dessus.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Indique s’il convient de répondre aux événements Button OFF.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Indique s’il faut afficher une image sur le côté droit du bouton.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Indique si l’image se trouve au-dessus du bouton.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Indique si le bouton est transparent.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Indique si le dernier événement Click était un double-clic.|

## <a name="remarks"></a>Notes

D’autres types de boutons sont dérivés `CMFCButton` de la classe, tels que la classe [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) , qui prend en charge les liens `CMFCColorButton` hypertexte et la classe, qui prend en charge une boîte de dialogue Sélecteur de couleurs.

Le style d’un `CMFCButton` objet peut être *3D*, *plat*, *semi-plat* ou *sans bordure*. Le texte du bouton peut être aligné à gauche, en haut ou au centre d’un bouton. Au moment de l’exécution, vous pouvez contrôler si le bouton affiche du texte, une image ou du texte et une image. Vous pouvez également spécifier qu’une image de curseur particulière soit affichée lorsque le curseur pointe sur un bouton.

Créez un contrôle Button soit directement dans votre code, soit à l’aide de l’outil de l' **Assistant classe MFC** et d’un modèle de boîte de dialogue. Si vous créez un contrôle Button directement, ajoutez une `CMFCButton` variable à votre application, puis appelez le constructeur et `Create` les méthodes de l' `CMFCButton` objet. Si vous utilisez l' **Assistant classe MFC**, ajoutez une `CButton` variable à votre application, puis remplacez le type de `CMFCButton`la variable par `CButton` .

Pour gérer les messages de notification dans une application de boîte de dialogue, ajoutez une entrée de la table des messages et un gestionnaire d’événements pour chaque notification. Les notifications envoyées par `CMFCButton` un objet sont les mêmes que celles envoyées par `CButton` un objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer les propriétés du bouton à l’aide de différentes méthodes dans la `CMFCButton` classe. L’exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

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

**En-tête:** afxbutton. h

##  <a name="cleanup"></a>  CMFCButton::CleanUp

Réinitialise des variables internes et libère des ressources allouées telles que des images, des bitmaps et des icônes.

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip

Spécifie s’il faut afficher le texte intégral d’une info-bulle dans une grande fenêtre d’info-bulle ou une version tronquée du texte dans une petite fenêtre d’info-bulle.

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
dans TRUE pour afficher tout le texte; FALSe pour afficher le texte tronqué.

### <a name="remarks"></a>Notes

##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont

Spécifie si la police du texte du bouton est identique à celle du menu de l’application.

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
dans TRUE pour utiliser la police de menu de l’application comme police du texte du bouton; FALSe pour utiliser la police système. La valeur par défaut est TRUE.

*bRedraw*<br/>
dans TRUE pour redessiner immédiatement l’écran; Sinon, FALSe. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Si vous n’utilisez pas cette méthode pour spécifier la police du texte du bouton, vous pouvez spécifier la police avec la méthode [CWnd:: SetFont](../../mfc/reference/cwnd-class.md#setfont) . Si vous ne spécifiez pas de police, l’infrastructure définit une police par défaut.

##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming

Spécifie si le style de la bordure du bouton correspond au thème Windows actuel.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour utiliser le thème Windows actuel pour dessiner des bordures de bouton; FALSe pour ne pas utiliser le thème Windows. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Cette méthode affecte tous les boutons de votre application qui sont dérivés `CMFCButton` de la classe.

##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl

Retourne une référence au contrôle ToolTip sous-jacent.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Valeur de retour

Référence au contrôle ToolTip sous-jacent.

### <a name="remarks"></a>Notes

##  <a name="isautocheck"></a>CMFCButton::IsAutoCheck

Indique si une case à cocher ou une case d’option est un bouton automatique.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton a le style BS_AUTOCHECKBOX ou BS_AUTORADIOBUTTON; Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

Indique si un bouton est défini en mode de répétition automatique.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton est défini en mode de répétition automatique; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez la méthode [CMFCButton:: SetAutorepeatMode](#setautorepeatmode) pour définir un bouton pour le mode de répétition automatique.

##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox

Indique si un bouton est un bouton de case à cocher.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton a le style BS_CHECKBOX ou BS_AUTOCHECKBOX; Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="ischecked"></a>  CMFCButton::IsChecked

Indique si le bouton en cours est activé.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton actuel est activé; Sinon, FALSe.

### <a name="remarks"></a>Notes

L’infrastructure utilise des méthodes différentes pour indiquer que différents genres de boutons sont vérifiés. Par exemple, une case d’option est cochée lorsqu’elle contient un point; une case à cocher est activée lorsqu’elle contient un **X**.

##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted

Indique si un bouton est mis en surbrillance.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton est mis en surbrillance; Sinon, FALSe.

### <a name="remarks"></a>Notes

Un bouton est mis en surbrillance lorsque la souris pointe sur le bouton.

##  <a name="ispressed"></a>  CMFCButton::IsPressed

Indique si un bouton est poussé et mis en surbrillance.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton est enfoncé; Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="ispushed"></a>CMFCButton::IsPushed

Indique si un bouton fait l’objet d’un push.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton fait l’objet d’un push; Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton

Indique si un bouton est une case d’option.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le style de bouton est BS_RADIOBUTTON ou BS_AUTORADIOBUTTON; Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled

Indique si le style de la bordure du bouton correspond au thème Windows actuel.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Valeur de retour

TRUE si le style de la bordure du bouton correspond au thème Windows actuel; Sinon, FALSe.

## <a name="a-namem_bdontusewinxptheme-cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/> CMFCButton::m_bDontUseWinXPTheme

Spécifie si les thèmes Windows XP doivent être utilisés lors du dessin du bouton.

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus

Indique s’il faut dessiner un rectangle de focus autour d’un bouton.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Notes

Affectez `m_bDrawFocus` la valeur true au membre pour spécifier que le Framework dessinera un rectangle de focus autour du texte et de l’image du bouton si le bouton reçoit le focus.

Le `CMFCButton` constructeur initialise ce membre à true.

##  <a name="m_bGrayDisabled"></a>  CMFCButton::m_bGrayDisabled

Si la valeur est TRUE, active le dessin d’un bouton désactivé.

```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked

Indique s’il faut mettre en surbrillance un bouton de style BS_CHECKBOX quand le curseur pointe dessus.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Notes

Affectez `m_bHighlightChecked` la valeur true au membre pour spécifier que le Framework met en surbrillance un bouton de style BS_CHECKBOX lorsque la souris pointe sur lui.

##  <a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

Indique s’il convient de répondre aux événements Button OFF.

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage

Indique s’il faut afficher une image sur le côté droit du bouton.

```
BOOL m_bRightImage;
```

##  <a name="m_bTopImage"></a>CMFCButton:: m_bTopImage] (#m_bTopImage)

Indique si l’image se trouve au-dessus du bouton.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Notes

Affectez `m_bRightImage` la valeur true au membre pour spécifier que le Framework affichera l’image du bouton à droite de l’étiquette de texte du bouton.

##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent

Indique si le bouton est transparent.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Notes

Affectez `m_bTransparent` la valeur true au membre pour spécifier que le Framework rendra le bouton transparent. Le `CMFCButton` constructeur initialise ce membre à false.

##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle

Spécifie l’alignement du texte du bouton.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Notes

Utilisez l’une des valeurs `CMFCButton::AlignStyle` d’énumération suivantes pour spécifier l’alignement du texte du bouton:

|Valeur|Description|
|-----------|-----------------|
|ALIGN_CENTER|Valeurs Aligne le texte du bouton au centre du bouton.|
|ALIGN_LEFT|Aligne le texte du bouton sur le côté gauche du bouton.|
|ALIGN_RIGHT|Aligne le texte du bouton sur le côté droit du bouton.|

Le `CMFCButton` constructeur initialise ce membre à ALIGN_CENTER.

##  <a name="m_bWasDblClk"></a>  CMFCButton::m_bWasDblClk](#m_bWasDblClk)|

Indique si le dernier événement Click était un double-clic. |

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle

Spécifie le style du bouton, tel que sans bordure, plat, semi-plat ou 3D.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Notes

Le tableau suivant répertorie `CMFCButton::m_nFlatStyle` les valeurs d’énumération qui spécifient l’apparence d’un bouton.

|`Value`|Description|
|-----------|-----------------|
|BUTTONSTYLE_3D|Valeurs Le bouton semble comporter des côtés supérieurs à trois dimensions. Lorsque l’utilisateur clique sur le bouton, le bouton s’affiche pour une mise en retrait profonde.|
|BUTTONSTYLE_FLAT|Lorsque la souris ne s’arrête pas sur le bouton, le bouton apparaît comme étant à deux dimensions et n’a pas de côté en relief. Lorsque la souris s’arrête au-dessus du bouton, le bouton semble avoir des côtés bas, à trois dimensions. Lorsque l’utilisateur clique sur le bouton, le bouton s’affiche pour une mise en retrait superficielle.|
|BUTTONSTYLE_SEMIFLAT|Le bouton semble avoir des côtés bas à trois dimensions. Lorsque l’utilisateur clique sur le bouton, le bouton s’affiche pour une mise en retrait profonde.|
|BUTTONSTYLE_NOBORDERS|Le bouton n’a pas de côtés en relief et s’affiche toujours en deux dimensions. Le bouton n’apparaît pas dans une mise en retrait quand l’utilisateur clique dessus.|

Le `CMFCButton` constructeur initialise ce membre à BUTTONSTYLE_3D.

### <a name="example"></a>Exemple

L’exemple suivant montre comment définir les valeurs de la `m_nFlatStyle` variable de membre dans la `CMFCButton` classe. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

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
dans Pointeur vers un contexte de périphérique (Device Context).

*rect*<br/>
dans Référence à un rectangle qui délimite le bouton.

*uiState*<br/>
dans État actuel du bouton. Pour plus d’informations, consultez `itemState` le membre de la rubrique de la [structure drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) .

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
dans Pointeur vers un contexte de périphérique (Device Context).

*rectClient*<br/>
dans Référence à un rectangle qui délimite le bouton.

*uiState*<br/>
dans État actuel du bouton. Pour plus d’informations, consultez `itemState` le membre de la rubrique de la [structure drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) .

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
dans Pointeur vers un contexte de périphérique (Device Context).

*rectClient*<br/>
dans Référence à un rectangle qui délimite le bouton.

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
dans Pointeur vers un contexte de périphérique (Device Context).

*rect*<br/>
dans Référence à un rectangle qui délimite le bouton.

*strText*<br/>
dans Texte à dessiner.

*uiDTFlags*<br/>
dans Indicateurs qui spécifient comment mettre en forme le texte. Pour plus d’informations, consultez le paramètre *nFormat* de la méthode [rawtext CDC::D](../../mfc/reference/cdc-class.md#drawtext) .

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
dans Pointeur vers un contexte de périphérique (Device Context).

*rectClient*<br/>
dans Référence à un rectangle qui délimite le bouton.

### <a name="remarks"></a>Notes

Substituez cette méthode pour utiliser votre propre code pour dessiner l’arrière-plan d’un bouton.

##  <a name="selectfont"></a>  CMFCButton::SelectFont

Récupère la police associée au contexte de périphérique spécifié.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

### <a name="return-value"></a>Valeur de retour

Substituez cette méthode pour utiliser votre propre code pour récupérer la police.

### <a name="remarks"></a>Notes

##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode

Définit un bouton pour le mode de répétition automatique.

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Paramètres

*nTimeDelay*<br/>
dans Nombre non négatif qui spécifie l’intervalle entre les messages envoyés à la fenêtre parente. L’intervalle est mesuré en millisecondes et sa valeur par défaut est de 500 millisecondes. Spécifiez zéro pour désactiver le mode de répétition automatique du message.

### <a name="remarks"></a>Notes

Cette méthode fait en sorte que le bouton envoie constamment des messages WM_COMMAND à la fenêtre parente jusqu’à ce que le bouton soit relâché ou que le paramètre *nTimeDelay* soit défini à zéro.

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
dans Handle de l’icône qui contient la bitmap et le masque de la nouvelle image.

*bAutoDestroy*<br/>
dans TRUE pour spécifier que les ressources bitmap doivent être détruites automatiquement; Sinon, FALSe. La valeur par défaut est TRUE.

*hIconHot*<br/>
dans Handle vers l’icône qui contient l’image pour l’état sélectionné.

*hBitmap*<br/>
dans Handle vers la bitmap qui contient l’image pour l’état non sélectionné.

*hBitmapHot*<br/>
dans Handle vers la bitmap qui contient l’image pour l’état sélectionné.

*bMap3dColors*<br/>
dans Spécifie une couleur transparente pour l’arrière-plan du bouton; autrement dit, la face du bouton. TRUE pour utiliser la valeur de couleur RVB (192, 192, 192); FALSe pour utiliser la valeur de couleur `AFX_GLOBAL_DATA::clrBtnFace`définie par.

*uiBmpResId*<br/>
dans ID de ressource pour l’image non sélectionnée.

*uiBmpHotResId*<br/>
dans ID de ressource pour l’image sélectionnée.

*hIconDisabled*<br/>
dans Handle de l’icône pour l’image désactivée.

*hBitmapDisabled*<br/>
dans Handle vers la bitmap qui contient l’image désactivée.

*uiBmpDsblResID*<br/>
dans ID de ressource de l’image bitmap désactivée.

*bAlphaBlend*<br/>
dans TRUE pour utiliser uniquement des images 32 bits qui utilisent le canal alpha; FALSe, pour ne pas utiliser uniquement les images de canal alpha. La valeur par défaut est FALSe.

### <a name="remarks"></a>Notes

##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor

Définit la couleur d’arrière-plan du texte du bouton.

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*crFace*<br/>
dans Valeur de couleur RVB.

*bRedraw*<br/>
dans TRUE pour redessiner immédiatement l’écran; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une nouvelle couleur de remplissage pour l’arrière-plan du bouton (face). Notez que l’arrière-plan n’est pas rempli quand la variable membre [CMFCButton:: m_bTransparent](#m_btransparent) a la valeur true.

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
dans Handle de l’icône qui contient la bitmap et le masque de la nouvelle image.

*bAutoDestroy*<br/>
dans TRUE pour spécifier que les ressources bitmap doivent être détruites automatiquement; Sinon, FALSe. La valeur par défaut est TRUE.

*hIconHot*<br/>
dans Handle vers l’icône qui contient l’image pour l’état sélectionné.

*hBitmap*<br/>
dans Handle vers la bitmap qui contient l’image pour l’état non sélectionné.

*hBitmapHot*<br/>
dans Handle vers la bitmap qui contient l’image pour l’état sélectionné.

*uiBmpResId*<br/>
dans ID de ressource pour l’image non sélectionnée.

*uiBmpHotResId*<br/>
dans ID de ressource pour l’image sélectionnée.

*bMap3dColors*<br/>
dans Spécifie une couleur transparente pour l’arrière-plan du bouton; autrement dit, la face du bouton. TRUE pour utiliser la valeur de couleur RVB (192, 192, 192); FALSe pour utiliser la valeur de couleur `AFX_GLOBAL_DATA::clrBtnFace`définie par.

*hIconDisabled*<br/>
dans Handle de l’icône pour l’image désactivée.

*hBitmapDisabled*<br/>
dans Handle vers la bitmap qui contient l’image désactivée.

*uiBmpDsblResID*<br/>
dans ID de ressource de l’image bitmap désactivée.

*bAlphaBlend*<br/>
dans TRUE pour utiliser uniquement des images 32 bits qui utilisent le canal alpha; FALSe, pour ne pas utiliser uniquement les images de canal alpha. La valeur par défaut est FALSe.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de différentes versions de la `SetImage` méthode dans la `CMFCButton` classe. L’exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor

Définit l’image de curseur.

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Paramètres

*hcursor*<br/>
dans Handle d’un curseur.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour associer une image de curseur, telle que le curseur de la main, au bouton. Le curseur est chargé à partir des ressources de l’application.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `SetMouseCursor` méthode dans la `CMFCButton` classe. L’exemple fait partie du code de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand

Définit le curseur sur l’image d’une main.

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>Notes

Utilisez cette méthode pour associer l’image de curseur d’un main au bouton. Le curseur est chargé à partir des ressources de l’application.

##  <a name="setstdimage"></a>  CMFCButton::SetStdImage

Utilise un `CMenuImages` objet pour définir l’image du bouton.

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Un des identificateurs d’image de bouton qui est défini dans `CMenuImage::IMAGES_IDS` l’énumération. Les valeurs de l’image spécifient des images telles que des flèches, des broches et des cases d’option.

*state*<br/>
dans Un des identificateurs d’état d’image de bouton qui est défini `CMenuImages::IMAGE_STATE` dans l’énumération. Les États d’image spécifient des couleurs de bouton telles que le noir, le gris, le gris clair, le blanc et le gris foncé. La valeur par défaut est `CMenuImages::ImageBlack`.

*idDisabled*<br/>
dans Un des identificateurs d’image de bouton qui est défini dans `CMenuImage::IMAGES_IDS` l’énumération. L’image indique que le bouton est désactivé. La valeur par défaut est la première image de `CMenuImages::IdArrowDown`bouton ().

### <a name="remarks"></a>Notes

##  <a name="settextcolor"></a>  CMFCButton::SetTextColor

Définit la couleur du texte du bouton pour un bouton qui n’est pas sélectionné.

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Paramètres

*clrText*<br/>
dans Valeur de couleur RVB.

### <a name="remarks"></a>Notes

##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor

Définit la couleur du texte du bouton d’un bouton sélectionné.

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Paramètres

*clrTextHot*<br/>
dans Valeur de couleur RVB.

### <a name="remarks"></a>Notes

##  <a name="settooltip"></a>  CMFCButton::SetTooltip

Associe une info-bulle à un bouton.

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Paramètres

*lpszToolTipText*<br/>
dans Pointeur vers le texte de l’info-bulle. Spécifiez NULL pour désactiver l’info-bulle.

### <a name="remarks"></a>Notes

##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent

Redimensionne un bouton pour qu’il contienne son texte de bouton et son image.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Paramètres

*bCalcOnly*<br/>
dans TRUE pour calculer, mais pas modifier, la nouvelle taille du bouton; FALSe pour modifier la taille du bouton. La valeur par défaut est FALSe.

### <a name="return-value"></a>Valeur de retour

`CSize` Objet qui contient la nouvelle taille du bouton.

### <a name="remarks"></a>Notes

Par défaut, cette méthode calcule une nouvelle taille qui comprend une marge horizontale de 10 pixels et une marge verticale de 5 pixels.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl, classe](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton, classe](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton, classe](../../mfc/reference/cmfcmenubutton-class.md)
