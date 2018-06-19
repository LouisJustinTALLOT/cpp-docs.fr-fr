---
title: Classe de CMFCButton | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73a3bb877bec385a9f7e56191286c9b560da8610
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378824"
---
# <a name="cmfcbutton-class"></a>Classe de CMFCButton
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
|`CMFCButton::DrawItem`|Appelé par l’infrastructure quand un aspect visuel d’un bouton owner-drawn a changé. (Substitue [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Spécifie s’il faut afficher le texte intégral d’une info-bulle dans une fenêtre d’info-bulle de grande taille ou une version tronquée du texte dans une fenêtre d’info-bulle petit.|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|Spécifie si la police de texte du bouton est le même que la police du menu application.|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Spécifie si le style de la bordure de bouton correspond au thème Windows en cours.|  
|`CMFCButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Retourne une référence au contrôle d’info-bulle sous-jacent.|  
|[CMFCButton::IsAutoCheck](#isautocheck)|Indique si une case à cocher ou une case d’option est un bouton automatique.|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Indique si un bouton est défini en mode de répétition automatique.|  
|[CMFCButton::IsCheckBox](#ischeckbox)|Indique si un bouton est un bouton de la case à cocher.|  
|[CMFCButton::IsChecked](#ischecked)|Indique si le bouton actuels est vérifié.|  
|[CMFCButton::IsHighlighted](#ishighlighted)|Indique si un bouton est mis en surbrillance.|  
|[CMFCButton::IsPressed](#ispressed)|Indique si un bouton est envoyé et mis en surbrillance.|  
|[CMFCButton::IsPushed](#ispushed)|Indique si un bouton est enfoncé.|  
|[CMFCButton::IsRadioButton](#isradiobutton)|Indique si un bouton est une case d’option.|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Indique si le style de la bordure de bouton correspond au thème Windows en cours.|  
|`CMFCButton::OnDrawParentBackground`|Dessine l’arrière-plan du parent d’un bouton dans la zone spécifiée. (Substitue [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|Convertit les messages de fenêtre avant d’être distribués à le [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) fonctions Windows. (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Définit un bouton en mode de répétition automatique.|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Définit l’image d’un bouton activé.|  
|[CMFCButton::SetFaceColor](#setfacecolor)|Définit la couleur d’arrière-plan pour le texte du bouton.|  
|[CMFCButton::SetImage](#setimage)|Définit l’image d’un bouton.|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|Définit l’image de curseur.|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Définit le curseur de l’image d’une main.|  
|[CMFCButton::SetStdImage](#setstdimage)|Utilise un `CMenuImages` objet pour définir l’image du bouton.|  
|[CMFCButton::SetTextColor](#settextcolor)|Définit la couleur du texte du bouton pour un bouton qui n’est pas sélectionné.|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Définit la couleur du texte du bouton pour un bouton est sélectionné.|  
|[CMFCButton::SetTooltip](#settooltip)|Associe une info-bulle à un bouton.|  
|[CMFCButton::SizeToContent](#sizetocontent)|Redimensionne un bouton pour qu’il contienne le texte du bouton et l’image.|  
  
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
  
|Name|Description|  
|----------|-----------------|  
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Indique s’il faut dessiner un rectangle de focus autour d’un bouton.|  
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Indique s’il faut mettre en surbrillance un bouton de style BS_CHECKBOX lorsque le curseur pointe sur elle.|  
|[CMFCButton::m_bRightImage](#m_brightimage)|Indique s’il faut afficher une image sur le côté droit du bouton.|  
|[CMFCButton::m_bTransparent](#m_btransparent)|Indique si le bouton est transparent.|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Spécifie l’alignement du texte du bouton.|  
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Spécifie le style du bouton, tels que plat de point-virgule sans bordure, à deux dimensions ou en 3D.|  
  
## <a name="remarks"></a>Notes  
 Autres types de boutons sont dérivés de la `CMFCButton` class, telle que la [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) (classe), qui prend en charge les liens hypertexte, et le `CMFCColorButton` (classe), qui prend en charge une boîte de dialogue de sélecteur de couleurs.  
  
 Le style d’un `CMFCButton` objet peut être *3D*, *plat*, *plat point-virgule* ou *aucune bordure*. Texte du bouton peut être aligné à gauche, haut ou au centre d’un bouton. Au moment de l’exécution, vous pouvez contrôler si le bouton affiche texte, une image, ou du texte et une image. Vous pouvez également spécifier une image de curseur particulier affichera lorsque le curseur pointe sur un bouton.  
  
 Créer un contrôle bouton directement dans votre code, ou à l’aide de la **Assistant classe MFC** outil et un modèle de boîte de dialogue. Si vous créez un contrôle bouton directement, ajouter un `CMFCButton` variable à votre application, puis appelez le constructeur et `Create` méthodes de la `CMFCButton` objet. Si vous utilisez la **Assistant classe MFC**, ajoutez un `CButton` variable à votre application, puis modifiez le type de la variable de `CButton` à `CMFCButton`.  
  
 Pour gérer les messages de notification dans une application de boîte de dialogue, ajoutez une entrée de mappage de message et un gestionnaire d’événements pour chaque notification. Les notifications envoyées par un `CMFCButton` objet sont les mêmes que celles envoyées par un `CButton` objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer les propriétés du bouton à l’aide de différentes méthodes de la `CMFCButton` classe. L’exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
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
 [in] `bOn`  
 `TRUE` Pour afficher tout le texte ; `FALSE` au texte tronqué.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont  
 Spécifie si la police de texte du bouton est le même que la police du menu application.  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bOn`  
 `TRUE` Pour utiliser la police du menu application en tant que la police de texte de bouton. `FALSE` à utiliser la police système. La valeur par défaut est `TRUE`.  
  
 [in] `bRedraw`  
 `TRUE` à se redessiner immédiatement avec l’écran ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Si vous n’utilisez pas cette méthode pour spécifier la police de texte de bouton, vous pouvez spécifier la police avec la [CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont) (méthode). Si vous ne spécifiez pas une police du tout, le framework définit une police par défaut.  
  
##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming  
 Spécifie si le style de la bordure de bouton correspond au thème Windows en cours.  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE` Pour utiliser le thème actuel de Windows pour dessiner les bordures du bouton ; `FALSE` à ne pas utiliser le thème de Windows. La valeur par défaut est `TRUE`.  
  
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
 `TRUE` Si le bouton a le style BS_AUTOCHECKBOX ou BS_AUTORADIOBUTTON ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode  
 Indique si un bouton est défini en mode de répétition automatique.  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le bouton est défini en mode de répétition automatique ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CMFCButton::SetAutorepeatMode](#setautorepeatmode) méthode pour définir un bouton en mode de répétition automatique.  
  
##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox  
 Indique si un bouton est un bouton de la case à cocher.  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le bouton a le style BS_CHECKBOX ou de BS_AUTOCHECKBOX ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ischecked"></a>  CMFCButton::IsChecked  
 Indique si le bouton actuels est vérifié.  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le bouton est activé ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure utilise différentes façons pour indiquer que les différents types de boutons sont sélectionnés. Par exemple, une case d’option est activée lorsqu’elle contient un point ; une case à cocher est activée lorsqu’elle contient un **X**.  
  
##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted  
 Indique si un bouton est mis en surbrillance.  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le bouton est mis en surbrillance ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Un bouton apparaît en surbrillance lorsque la souris pointe sur le bouton.  
  
##  <a name="ispressed"></a>  CMFCButton::IsPressed  
 Indique si un bouton est envoyé et mis en surbrillance.  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le bouton est activé ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ispushed"></a>  CMFCButton::IsPushed  
 Indique si un bouton est enfoncé.  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le bouton est enfoncé ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton  
 Indique si un bouton est une case d’option.  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le style de bouton est BS_RADIOBUTTON ou BS_AUTORADIOBUTTON ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled  
 Indique si le style de la bordure de bouton correspond au thème Windows en cours.  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le style de la bordure de bouton correspondant au thème Windows en cours ; dans le cas contraire, `FALSE`.  
  
##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus  
 Indique s’il faut dessiner un rectangle de focus autour d’un bouton.  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>Notes  
 Définir le `m_bDrawFocus` membre `TRUE` pour indiquer que le framework sera dessiner un rectangle de focus autour du texte du bouton et de l’image si le bouton reçoit le focus.  
  
 Le `CMFCButton` constructeur initialise à ce membre `TRUE`.  
  
##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked  
 Indique s’il faut mettre en surbrillance un bouton de style BS_CHECKBOX lorsque le curseur pointe sur elle.  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>Notes  
 Définir le `m_bHighlightChecked` membre `TRUE` pour spécifier que le framework met en surbrillance un bouton de style BS_CHECKBOX lorsque la souris passe dessus.  
  
##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage  
 Indique s’il faut afficher une image sur le côté droit du bouton.  
  
```  
BOOL m_bRightImage;  
```  
  
### <a name="remarks"></a>Notes  
 Définir le `m_bRightImage` membre `TRUE` pour spécifier que le framework affiche l’image du bouton à droite de l’étiquette de texte du bouton.  
  
##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent  
 Indique si le bouton est transparent.  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>Notes  
 Définir le `m_bTransparent` membre `TRUE` pour spécifier que le framework effectue le bouton transparent. Le `CMFCButton` constructeur initialise à ce membre `FALSE`.  
  
##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle  
 Spécifie l’alignement du texte du bouton.  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>Notes  
 Utilisez une des opérations suivantes `CMFCButton::AlignStyle` des valeurs d’énumération pour spécifier l’alignement du texte du bouton :  
  
|Value|Description|  
|-----------|-----------------|  
|ALIGN_CENTER|(Par défaut) Aligne le texte du bouton au centre du bouton.|  
|ALIGN_LEFT|Aligne le texte du bouton sur le côté gauche du bouton.|  
|ALIGN_RIGHT|Aligne le texte du bouton à droite du bouton.|  
  
 Le `CMFCButton` constructeur initialise à ALIGN_CENTER ce membre.  
  
##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle  
 Spécifie le style du bouton, tels que plat de point-virgule sans bordure, à deux dimensions ou en 3D.  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>Notes  
 Le tableau suivant répertorie les `CMFCButton::m_nFlatStyle` des valeurs d’énumération qui spécifient l’apparence d’un bouton.  
  
|Value|Description|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|(Par défaut) Le bouton semble avoir des côtés haute, en trois dimensions. Lorsque le bouton est activé, le bouton semble enfoncé dans un retrait approfondi.|  
|BUTTONSTYLE_FLAT|Lorsque la souris n’interrompez pas sur le bouton, le bouton semble être à deux dimensions et n’a pas déclenchées côtés. Lorsque la souris s’arrête sur le bouton, le bouton semble se côtés bas, à trois dimensions. Lorsque le bouton est activé, le bouton semble enfoncé dans un retrait superficiels.|  
|BUTTONSTYLE_SEMIFLAT|Le bouton s’affiche pour que les côtés bas, à trois dimensions. Lorsque le bouton est activé, le bouton semble enfoncé dans un retrait approfondi.|  
|BUTTONSTYLE_NOBORDERS|Le bouton de ne pas avoir déclenché côtés et apparaît toujours à deux dimensions. Le bouton ne semble pas être activé dans une mise en retrait lorsqu’il est activé.|  
  
 Le `CMFCButton` constructeur initialise à ce membre `BUTTONSTYLE_3D`.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir les valeurs de la `m_nFlatStyle` variable de membre dans la `CMFCButton` classe. Cet exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
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
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `rect`  
 Une référence à un rectangle qui englobe le bouton.  
  
 [in] `uiState`  
 L’état actuel de bouton. Pour plus d’informations, consultez la `itemState` membre de la [drawitemstruct, Structure](../../mfc/reference/drawitemstruct-structure.md) rubrique.  
  
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
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `rectClient`  
 Une référence à un rectangle qui englobe le bouton.  
  
 [in] `uiState`  
 L’état actuel de bouton. Pour plus d’informations, consultez la `itemState` membre de la [drawitemstruct, Structure](../../mfc/reference/drawitemstruct-structure.md) rubrique.  
  
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
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `rectClient`  
 Une référence à un rectangle qui englobe le bouton.  
  
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
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `rect`  
 Une référence à un rectangle qui englobe le bouton.  
  
 [in] `strText`  
 Texte à dessiner.  
  
 [in] `uiDTFlags`  
 Indicateurs qui spécifient comment mettre en forme le texte. Pour plus d’informations, consultez la `nFormat` paramètre de la [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) (méthode).  
  
 [in] `uiState`  
 (Réservé).  
  
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
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `rectClient`  
 Une référence à un rectangle qui englobe le bouton.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode pour utiliser votre propre code pour dessiner l’arrière-plan d’un bouton.  
  
##  <a name="selectfont"></a>  CMFCButton::SelectFont  
 Récupère la police qui est associée au contexte de périphérique spécifié.  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
### <a name="return-value"></a>Valeur de retour  
 Substituez cette méthode pour utiliser votre propre code pour récupérer la police.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode  
 Définit un bouton en mode de répétition automatique.  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nTimeDelay`  
 Un nombre non négatif qui spécifie l’intervalle entre les messages sont envoyés à la fenêtre parente. L’intervalle est mesurée en millisecondes et sa valeur par défaut est 500 millisecondes. Spécifiez zéro pour désactiver le mode de répétition automatique message.  
  
### <a name="remarks"></a>Notes  
 Cette méthode provoque le bouton pour envoyer des messages WM_COMMAND constamment à la fenêtre parente jusqu'à ce que le bouton est relâché, ou le `nTimeDelay` paramètre est défini à zéro.  
  
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
 [in] `hIcon`  
 Handle vers l’icône qui contient l’image bitmap et un masque pour la nouvelle image.  
  
 [in] `bAutoDestroy`  
 `TRUE` Pour spécifier que les ressources bitmap d’être détruit automatiquement ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.  
  
 [in] `hIconHot`  
 Handle vers l’icône qui contient l’image pour l’état sélectionné.  
  
 [in] `hBitmap`  
 Handle vers l’image bitmap qui contient l’image pour l’état non sélectionné.  
  
 [in] `hBitmapHot`  
 Handle vers l’image bitmap qui contient l’image pour l’état sélectionné.  
  
 [in] `bMap3dColors`  
 Spécifie une couleur transparente pour l’arrière-plan du bouton. Autrement dit, la face du bouton. `TRUE` Pour utiliser la valeur de couleur RVB (192, 192, 192) ; `FALSE` à utiliser la valeur de couleur définie par `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] `uiBmpResId`  
 ID de ressource pour l’image non sélectionné.  
  
 [in] `uiBmpHotResId`  
 ID de ressource pour l’image sélectionnée.  
  
 [in] `hIconDisabled`  
 Handle vers l’icône de l’image désactivée.  
  
 [in] `hBitmapDisabled`  
 Handle vers l’image bitmap qui contient l’image désactivée.  
  
 [in] `uiBmpDsblResID`  
 ID de ressource de l’image bitmap désactivé.  
  
 [in] `bAlphaBlend`  
 `TRUE` utiliser uniquement des images 32 bits qui utilisent le canal alpha. `FALSE`, de ne pas utiliser uniquement des images de canal alpha. La valeur par défaut est `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor  
 Définit la couleur d’arrière-plan pour le texte du bouton.  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `crFace`  
 Une valeur de couleur RVB.  
  
 [in] `bRedraw`  
 `TRUE` pour redessiner l’écran immédiatement ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour définir une nouvelle couleur de remplissage pour l’arrière-plan du bouton (face). Notez que l’arrière-plan n’est pas remplie quand la [CMFCButton::m_bTransparent](#m_btransparent) variable membre est `TRUE`.  
  
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
 [in] `hIcon`  
 Handle vers l’icône qui contient l’image bitmap et un masque pour la nouvelle image.  
  
 [in] `bAutoDestroy`  
 `TRUE` Pour spécifier que les ressources bitmap d’être détruit automatiquement ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.  
  
 [in] `hIconHot`  
 Handle vers l’icône qui contient l’image pour l’état sélectionné.  
  
 [in] `hBitmap`  
 Handle vers l’image bitmap qui contient l’image pour l’état non sélectionné.  
  
 [in] `hBitmapHot`  
 Handle vers l’image bitmap qui contient l’image pour l’état sélectionné.  
  
 [in] `uiBmpResId`  
 ID de ressource pour l’image non sélectionné.  
  
 [in] `uiBmpHotResId`  
 ID de ressource pour l’image sélectionnée.  
  
 [in] `bMap3dColors`  
 Spécifie une couleur transparente pour l’arrière-plan du bouton. Autrement dit, la face du bouton. `TRUE` Pour utiliser la valeur de couleur RVB (192, 192, 192) ; `FALSE` à utiliser la valeur de couleur définie par `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] `hIconDisabled`  
 Handle vers l’icône de l’image désactivée.  
  
 [in] `hBitmapDisabled`  
 Handle vers l’image bitmap qui contient l’image désactivée.  
  
 [in] `uiBmpDsblResID`  
 ID de ressource de l’image bitmap désactivé.  
  
 [in] `bAlphaBlend`  
 `TRUE` utiliser uniquement des images 32 bits qui utilisent le canal alpha. `FALSE`, de ne pas utiliser uniquement des images de canal alpha. La valeur par défaut est `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser les différentes versions de la `SetImage` méthode dans la `CMFCButton` classe. L’exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor  
 Définit l’image de curseur.  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `hcursor`  
 Le handle d’un curseur.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour associer une image de curseur, tels que le curseur de la main, avec le bouton. Le curseur est chargé à partir des ressources d’application.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `SetMouseCursor` méthode dans la `CMFCButton` classe. L’exemple fait partie du code dans le [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand  
 Définit le curseur de l’image d’une main.  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour associer l’image de curseur d’une main avec le bouton. Le curseur est chargé à partir des ressources d’application.  
  
##  <a name="setstdimage"></a>  CMFCButton::SetStdImage  
 Utilise un `CMenuImages` objet pour définir l’image du bouton.  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `id`  
 Un des identificateurs d’image de bouton qui est défini dans le `CMenuImage::IMAGES_IDS` énumération. Les valeurs de l’image spécifient des images telles que des flèches, des codes confidentiels et cases d’option.  
  
 [in] `state`  
 Un des identificateurs de bouton image état est défini dans le `CMenuImages::IMAGE_STATE` énumération. Les États d’image spécifient des couleurs du bouton telles que les gris foncé et blancs gris noir, gris clair. La valeur par défaut est `CMenuImages::ImageBlack`.  
  
 [in] `idDisabled`  
 Un des identificateurs d’image de bouton qui est défini dans le `CMenuImage::IMAGES_IDS` énumération. L’image indique que le bouton est désactivé. La valeur par défaut est la première image de bouton ( `CMenuImages::IdArrowDown`).  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settextcolor"></a>  CMFCButton::SetTextColor  
 Définit la couleur du texte du bouton pour un bouton qui n’est pas sélectionné.  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `clrText`  
 Une valeur de couleur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor  
 Définit la couleur du texte du bouton pour un bouton est sélectionné.  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `clrTextHot`  
 Une valeur de couleur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="settooltip"></a>  CMFCButton::SetTooltip  
 Associe une info-bulle à un bouton.  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszToolTipText`  
 Pointeur vers le texte de l’info-bulle. Spécifiez NULL pour désactiver l’info-bulle.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent  
 Redimensionne un bouton pour qu’il contienne le texte du bouton et l’image.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bCalcOnly`  
 `TRUE` pour calculer, mais pas modifier, la nouvelle taille du bouton ; `FALSE` pour modifier la taille du bouton. La valeur par défaut est `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 A `CSize` objet qui contient la nouvelle taille du bouton.  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette méthode calcule une nouvelle taille qui inclut une marge horizontale de 10 pixels et une marge verticale de 5 pixels.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)   
 [Classe de CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton, classe](../../mfc/reference/cmfcmenubutton-class.md)
