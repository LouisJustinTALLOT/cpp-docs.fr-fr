---
title: AFX_GLOBAL_DATA (structure)
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::InitD2D
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: 60f7513075e8da7e17f2113c01b954af5a690aaf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363667"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA (structure)

La structure `AFX_GLOBAL_DATA` contient des champs et des méthodes qui permettent de gérer l’infrastructure ou de personnaliser l’apparence et le comportement de votre application.

## <a name="syntax"></a>Syntaxe

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Construit une structure `AFX_GLOBAL_DATA` .|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|Libère les ressources allouées par l’infrastructure, telles que les pinceaux, les polices et les DLL.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Crée une transformation de rotation qui pivote autour d’un point spécifié selon un angle spécifié.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Dessine l’arrière-plan du parent d’un contrôle dans la zone spécifiée.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Dessine le texte spécifié dans le style visuel du thème spécifié.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Supprime la paire de balises XML spécifiée dans une mémoire tampon spécifiée.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Récupère la couleur actuelle de l’élément d’interface utilisateur spécifié.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Renvoie un pointeur à l’interface `ID2D1Factory` qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Récupère le curseur prédéfini qui a la forme d’une main et dont l’identificateur est `IDC_HAND`.|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Crée et stocke dans les données globales un pointeur vers l’interface ITaskBarList.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Crée et stocke dans les données globales un pointeur vers l’interface ITaskBarList3.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Récupère les mesures associées à la zone non cliente des fenêtres non réduites.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Détermine les positions des barres de masquage automatique de l’interpréteur de commandes.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Récupère la hauteur des caractères de texte dans la police actuelle.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Renvoie un pointeur à l’interface `IWICImagingFactory` qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Renvoie un pointeur à l’interface `IDWriteFactory` qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.|
|[AFX_GLOBAL_DATA::InitD2D](#initd2d)|Initialise les fabriques `D2D`, `DirectWrite`et `WIC` . Appelez cette méthode avant que la fenêtre principale soit initialisée.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Indique si les icônes 32 bits prédéfinies sont prises en charge.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Détermine si `D2D` a été initialisé.|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Fournit un moyen simple d’appeler la méthode Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) .|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Indique si les images sont actuellement affichées avec un contraste élevé.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Détecte l’état actuel des fonctionnalités de masquage automatique de la barre des tâches et de l’animation des menus du Bureau.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Inscrit la classe de fenêtre MFC spécifiée.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Libère les interfaces obtenues par les méthodes GetITaskbarList et GetITaskbarList3.|
|[AFX_GLOBAL_DATA::Resume](#resume)|Réinitialise les pointeurs de fonction internes qui accèdent à des méthodes prenant en charge [les thèmes et les styles visuels](/windows/win32/Controls/visual-styles-overview)Windows.|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Fournit un moyen simple d’appeler la méthode Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) .|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Crée la police logique spécifiée.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Crée et initialise un objet élément d’interpréteur de commandes à partir d’un nom de l’analyse.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Réinitialise les polices logiques qui sont utilisées par l’infrastructure.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Initialise les couleurs, la profondeur de couleur, les pinceaux, les stylets et les images qui sont utilisés par l’infrastructure.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Active ou désactive la prise en charge de Microsoft Active Accessibility. Active Accessibility fournit des méthodes fiables pour exposer des informations sur les éléments d’interface utilisateur.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Indique si la prise en charge de Microsoft Active Accessibility est activée.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Indique si le système d’exploitation prend en charge les fenêtres superposées.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Indique si le système d’exploitation actuel prend en charge la simulation de transparence.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Indique si l’application est exécutée sur le système d’exploitation Windows 7 ou ultérieur|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Spécifie la couleur de dégradé de la légende active. Généralement utilisé pour les volets d’ancrage.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Spécifie la couleur de dégradé de la légende inactive. Généralement utilisé pour les volets d’ancrage.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Indique si l’infrastructure utilise des icônes de couleur 32 bits prédéfinies ou des icônes d’une résolution inférieure.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Indique si une police système est utilisée pour les menus, les barres d’outils et les rubans.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Stocke le handle du curseur en forme de main.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Stocke le handle du curseur d’étirement horizontal.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Stocke le handle du curseur d’étirement vertical.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Stocke le handle de l’icône d’outil.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Spécifie le décalage entre la barre d’outils de masquage automatique la plus à gauche et le côté gauche de la barre d’ancrage.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Spécifie l’intervalle entre les barres d’outils de masquage automatique.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Spécifie l’épaisseur du cadre de glissement qui est utilisé pour communiquer l’état d’ancrage.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Spécifie l’épaisseur du cadre de glissement qui est utilisé pour communiquer l’état flottant.|

### <a name="remarks"></a>Notes

La plupart des données dans la structure `AFX_GLOBAL_DATA` sont initialisées au démarrage de votre application.

### <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Spécifications

**En-tête :** afxglobals.h

## <a name="afx_global_databisosalphablendingsupport"></a><a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

Indique si le système d’exploitation prend en charge le mélange alpha.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Notes

TRUE indique que le mélange alpha est soutenu; autrement, FALSE.

## <a name="afx_global_datacleanup"></a><a name="cleanup"></a>AFX_GLOBAL_DATA::CleanUp

Libère les ressources allouées par l’infrastructure, telles que les pinceaux, les polices et les DLL.

```
void CleanUp();
```

## <a name="afx_global_datad2d1makerotatematrix"></a><a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D2D1MakeRotateMatrix

Crée une transformation de rotation qui pivote autour d’un point spécifié selon un angle spécifié.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Paramètres

*angle*<br/>
Angle de rotation dans le sens des aiguilles d'une montre, en degrés.

*Centre*<br/>
Le point sur lequel tourner.

*Matrice*<br/>
Lorsque cette méthode revient, contient la nouvelle transformation de rotation. Vous devez allouer le stockage pour ce paramètre.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de succès, ou une valeur d’erreur autrement.

## <a name="afx_global_datadrawparentbackground"></a><a name="drawparentbackground"></a>AFX_GLOBAL_DATA::DrawParentBackground

Dessine l’arrière-plan du parent d’un contrôle dans la zone spécifiée.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[dans] Pointeur vers la fenêtre d’un contrôle.

*pDC*<br/>
[dans] Pointeur vers un contexte d’appareil.

*lpRect*<br/>
[dans] Pointeur vers un rectangle qui limite la zone à dessiner. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

## <a name="afx_global_datadrawtextonglass"></a><a name="drawtextonglass"></a>AFX_GLOBAL_DATA::DrawTextOnGlass

Dessine le texte spécifié dans le style visuel du thème spécifié.

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*hTheme*<br/>
[dans] Gérer les données thématiques d’une fenêtre, ou NULL. Le cadre utilise le thème spécifié pour dessiner le texte si ce paramètre n’est pas NULL et les thèmes sont pris en charge. Sinon, l’infrastructure n’utilise pas de thème pour dessiner le texte.

Utilisez la méthode [OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) pour créer un HTHEME.

*pDC*<br/>
[dans] Pointeur vers un contexte d’appareil.

*iPartId (en)*<br/>
[dans] La partie de contrôle qui a l’apparence de texte désirée. Pour plus d’informations, consultez la colonne Composants de la table figurant dans [Composants et états](/windows/win32/controls/parts-and-states). Si cette valeur est égale à 0, le texte est dessiné avec la police par défaut ou une police sélectionnée dans le contexte de l’appareil.

*iStateId (en)*<br/>
[dans] L’état de contrôle qui a l’apparence de texte désirée. Pour plus d’informations, consultez la colonne États de la table figurant dans [Composants et états](/windows/win32/controls/parts-and-states).

*strText (en)*<br/>
[dans] Le texte à dessiner.

*Rect*<br/>
[dans] La limite de la zone dans laquelle le texte spécifié est dessiné.

*dwFlags*<br/>
[dans] Une combinaison bitwise (OU) de drapeaux qui spécifient comment le texte spécifié est dessiné.

Si le *paramètre hTheme* est `NULL` ou si les thèmes ne sont pas pris en charge et activés, le paramètre *nFormat* de la [méthode CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) décrit les drapeaux valides. Si les thèmes sont pris en charge, le paramètre *dwFlags* de la méthode [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) décrit les drapeaux valides.

*nGlowSize (en)*<br/>
[dans] La taille d’un effet de lueur qui est dessiné sur l’arrière-plan avant de dessiner le texte spécifié. La valeur par défaut est 0.

*clrText*<br/>
[dans] La couleur dans laquelle le texte spécifié est dessiné. La valeur par défaut est la couleur par défaut.

### <a name="return-value"></a>Valeur de retour

VRAI si un thème est utilisé pour dessiner le texte spécifié; autrement, FALSE.

### <a name="remarks"></a>Notes

Un thème définit le style visuel d’une application. Un thème n’est pas utilisé pour dessiner le texte si le *paramètre hTheme* est NULL, ou si la méthode [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) n’est pas prise en charge, ou si la composition [de Desktop Window Manager](/windows/win32/dwm/dwm-overview) (DWM) est désactivée.

## <a name="afx_global_dataenableaccessibilitysupport"></a><a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport

Active ou désactive la prise en charge de Microsoft Active Accessibility.

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour permettre un soutien à l’accessibilité; FALSE pour désactiver le soutien à l’accessibilité. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Active Accessibility est une technologie basée sur com qui améliore la façon dont les programmes et le système d’exploitation Windows fonctionnent en collaboration avec les produits de technologie d’assistance. Il fournit des méthodes fiables pour exposer des informations sur les éléments d’interface utilisateur. Cependant, un nouveau modèle d’accessibilité appelé Microsoft UI Automation est maintenant disponible. Pour une comparaison des deux technologies, voir [UI Automation et Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Utilisez la [méthode AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) pour déterminer si le support Microsoft Active Accessibility est activé.

## <a name="afx_global_dataexcludetag"></a><a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag

Supprime la paire de balises XML spécifiée dans une mémoire tampon spécifiée.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Paramètres

*strBuffer (strBuffer)*<br/>
[dans] Un tampon de texte.

*lpszTag (en)*<br/>
[dans] Le nom d’une paire d’étiquettes XML d’ouverture et de fermeture.

*strTag (en)*<br/>
[out] Lorsque cette méthode revient, le paramètre *strTag* contient le texte qui se situe entre les balises XML d’ouverture et de fermeture qui sont nommées par le paramètre *lpszTag.* Tout espace blanc de premier plan ou de fuite est coupé du résultat.

*bIsCharsList (en)*<br/>
[dans] VRAI pour convertir des symboles pour les personnages d’évasion dans le paramètre *strTag* en personnages d’évasion réels; FALSE de ne pas effectuer la conversion. La valeur par défaut est FALSE. Pour plus d'informations, consultez la section Notes.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Une paire de balises XML se compose d’étiquettes d’ouverture et de fermeture nommées qui indiquent le début et la fin d’une série de texte dans le tampon spécifié. Le paramètre *strBuffer* spécifie le tampon, et le paramètre *lpszTag* spécifie le nom des balises XML.

Utilisez les symboles dans le tableau suivant pour coder un ensemble de caractères d’échappement dans le tampon spécifié. Spécifiez VRAI pour le *paramètre bIsCharsList* pour convertir les symboles dans le paramètre *strTag* en caractères d’évasion réels. Le tableau suivant utilise la macro [_T)pour](../../c-runtime-library/data-type-mappings.md) spécifier le symbole et échapper aux chaînes de caractères.

|Symbole|Caractère d'échappement|
|------------|----------------------|
|_T ("\\t ")|_T|
|_T ("\\n")|_T|
|_T ("\\'r")|_T|
|_T ("\\b ")|_T ("b")|
|_T ("LT")|_T ("\<")|
|_T ("GT")|_T (">")|
|_T ("AMP")|_T ("&")|

## <a name="afx_global_datagetcolor"></a><a name="getcolor"></a>AFX_GLOBAL_DATA::GetColor

Récupère la couleur actuelle de l’élément d’interface utilisateur spécifié.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Paramètres

*nColor (en)*<br/>
[dans] Une valeur qui spécifie un élément d’interface utilisateur dont la couleur est récupérée. Pour une liste de valeurs valides, consultez le paramètre *nIndex* de la méthode [GetSysColor.](/windows/win32/api/winuser/nf-winuser-getsyscolor)

### <a name="return-value"></a>Valeur de retour

La valeur couleur RGB de l’élément d’interface utilisateur spécifiée. Pour plus d'informations, consultez la section Notes.

### <a name="remarks"></a>Notes

Si le *paramètre nColor* est hors de portée, la valeur de retour est nulle. Parce que zéro est également une valeur RGB valide, vous ne pouvez pas utiliser cette méthode pour déterminer si une couleur du système est prise en charge par le système d’exploitation actuel. Utilisez plutôt la méthode [GetSysColorBrush,](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) qui renvoie NULL si la couleur n’est pas prise en charge.

## <a name="afx_global_datagetdirect2dfactory"></a><a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory

Renvoie un pointeur à l’interface ID2D1Factory qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface ID2D1Factory si la création d’une usine réussit, ou NULL si la création échoue ou le système d’opération actuel n’ont pas de support D2D.

## <a name="afx_global_datagethandcursor"></a><a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor

Récupère le curseur prédéfini qui ressemble à une main et dont l’identifiant est IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Valeur de retour

La poignée du curseur de la main.

## <a name="afx_global_datagetnonclientmetrics"></a><a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics

Récupère les mesures associées à la zone non cliente des fenêtres non réduites.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Paramètres

*info*<br/>
[dans, dehors] Une structure [NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) qui contient les mesures évolutives associées à la zone non complexe d’une fenêtre non-dimensionnisée.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode réussit; autrement, FALSE.

## <a name="afx_global_datagettextheight"></a><a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight

Récupère la hauteur des caractères de texte dans la police actuelle.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Paramètres

*bHorz (en)*<br/>
[dans] VRAI pour récupérer la hauteur des caractères lorsque le texte s’exécute horizontalement; FALSE pour récupérer la hauteur des caractères lorsque le texte s’exécute verticalement. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

La hauteur de la police actuelle, qui est mesurée de son ascendant à son descendeur.

## <a name="afx_global_datagetwicfactory"></a><a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory

Retourne un pointeur à l’interface IWICImagingFactory qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface IWICImagingFactory si la création d’une usine réussit, ou NULL si la création échoue ou le système d’opération actuel n’ont pas de support WIC.

## <a name="afx_global_datagetwritefactory"></a><a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory

Retourne un pointeur à l’interface IDWriteFactory qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface IDWriteFactory si la création d’une usine réussit, ou NULL si la création échoue ou le système d’opération actuel n’ont pas de support DirectWrite.

## <a name="afx_global_datainitd2d"></a><a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D

Initialise les usines D2D, DirectWrite et WIC. Appelez cette méthode avant que la fenêtre principale soit initialisée.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Paramètres

*d2dFactoryType*<br/>
Le modèle de filetage de l’usine D2D et les ressources qu’elle crée.

*écrireFactoryType*<br/>
Une valeur qui précise si l’objet d’usine d’écriture sera partagé ou isolé

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si les usines étaient intilalizrd, FALSE - sinon

## <a name="afx_global_datais32biticons"></a><a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons

Indique si les icônes 32 bits prédéfinies sont prises en charge.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si les icônes 32 bits prédéfinies sont prises en charge; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode renvoie TRUE si le cadre prend en charge les icônes intégrées 32 bits, et si le système d’exploitation prend en charge 16 bits par pixel ou plus, et si les images ne sont pas affichées en contraste élevé.

## <a name="afx_global_dataisaccessibilitysupport"></a><a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport

Indique si la prise en charge de Microsoft Active Accessibility est activée.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le soutien à l’accessibilité est activé; autrement, FALSE.

### <a name="remarks"></a>Notes

Microsoft Active Accessibility était la solution antérieure pour rendre les applications accessibles. Microsoft UI Automation est le nouveau modèle d’accessibilité pour Microsoft Windows et est destiné à répondre aux besoins des produits de technologie d’assistance et des outils de test automatisés.

Utilisez la [méthode AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) pour activer ou désactiver le support d’accessibilité active.

## <a name="afx_global_dataisd2dinitialized"></a><a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialized

Détermine si le D2D a été parasécé

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si D2D a été paralémé; autrement FALSE.

## <a name="afx_global_dataisdwmcompositionenabled"></a><a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Fournit un moyen simple d’appeler la méthode Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) .

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Valeur de retour

VRAI si la composition [de Desktop Window Manager](/windows/win32/dwm/dwm-overview) (DWM) est activée; autrement, FALSE.

## <a name="afx_global_dataishighcontrastmode"></a><a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode

Indique si les images sont actuellement affichées avec un contraste élevé.

```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si les images sont actuellement affichées en mode contraste élevé noir ou blanc; autrement, FALSE.

### <a name="remarks"></a>Notes

En mode contraste élevé noir, les bords faisant face à la lumière sont blancs et l’arrière-plan est noir. En mode contraste élevé blanc, les bords faisant face à la lumière sont noirs et l’arrière-plan est blanc.

## <a name="afx_global_dataiswindowslayersupportavailable"></a><a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable

Indique si le système d’exploitation prend en charge les fenêtres superposées.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si les fenêtres superposées sont prises en charge; autrement, FALSE.

### <a name="remarks"></a>Notes

Si les fenêtres superposées sont prises en charge, les marqueurs *d’amarrage intelligents* utilisent des fenêtres superposées.

## <a name="afx_global_datam_busebuiltin32biticons"></a><a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

Indique si l’infrastructure utilise des icônes de couleur 32 bits prédéfinies ou des icônes d’une résolution inférieure.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Notes

TRUE précise que le cadre utilise des icônes de couleur 32 bits; FALSE spécifie les icônes à résolution inférieure. Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre à TRUE.

Ce membre doit être fixé au démarrage de l’application.

## <a name="afx_global_datam_busesystemfont"></a><a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont

Indique si une police système est utilisée pour les menus, les barres d’outils et les rubans.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Notes

TRUE spécifie d’utiliser une police système; autrement, FALSE. Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre à FALSE.

Tester ce membre n’est pas le seul moyen pour le cadre de déterminer la police à utiliser. La `AFX_GLOBAL_DATA::UpdateFonts` méthode teste également les polices par défaut et alternatives pour déterminer quels styles visuels sont disponibles pour être appliqués aux menus, barres d’outils et rubans.

## <a name="afx_global_datam_hcurhand"></a><a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand

Stocke le handle du curseur en forme de main.

```
HCURSOR m_hcurHand;
```

## <a name="afx_global_datam_hcurstretch"></a><a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch

Stocke le handle du curseur d’étirement horizontal.

```
HCURSOR m_hcurStretch;
```

## <a name="afx_global_datam_hcurstretchvert"></a><a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert

Stocke le handle du curseur d’étirement vertical.

```
HCURSOR m_hcurStretchVert;
```

## <a name="afx_global_datam_hicontool"></a><a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool

Stocke le handle de l’icône d’outil.

```
HICON m_hiconTool;
```

## <a name="afx_global_datam_nautohidetoolbarmargin"></a><a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

Specifie le décalage de la barre d’outils automatique la plus gauche vers le côté gauche de la barre du quai.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Notes

Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre à 4 pixels.

## <a name="afx_global_datam_nautohidetoolbarspacing"></a><a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

Spécifie l’intervalle entre les barres d’outils de masquage automatique.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Notes

Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre à 14 pixels.

## <a name="afx_global_datam_ndragframethicknessdock"></a><a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Spécifie l’épaisseur du cadre de traînée qui est utilisé pour indiquer l’état amarré.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Notes

Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre à 3 pixels.

## <a name="afx_global_datam_ndragframethicknessfloat"></a><a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

Spécifie l’épaisseur du cadre de traînée qui est utilisé pour indiquer l’état flottant.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Notes

Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre à 4 pixels.

## <a name="afx_global_dataonsettingchange"></a><a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange

Détecte l’état actuel des fonctionnalités de masquage automatique de la barre des tâches et de l’animation des menus du Bureau.

```
void OnSettingChange();
```

### <a name="remarks"></a>Notes

Cette méthode définit les variables de cadre à l’état de certains attributs du bureau de l’utilisateur. Cette méthode détecte l’état actuel de l’animation du menu, le menu fade, et les caractéristiques de l’autohide barre de tâche.

## <a name="afx_global_dataregisterwindowclass"></a><a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass

Inscrit la classe de fenêtre MFC spécifiée.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Paramètres

*lpszClassNamePrefix*<br/>
[dans] Le nom de la classe de fenêtre pour s’inscrire.

### <a name="return-value"></a>Valeur de retour

Le nom qualifié de la classe enregistrée si cette méthode réussit; autrement, une [exception de ressources](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Notes

La valeur de retour est une liste colon-délimitée de la chaîne de paramètre *lpszClassNamePrefix,* et les représentations de texte hexadecimal des poignées de l’instance actuelle d’application ; le curseur d’application, qui est le curseur de flèche dont l’identifiant est IDC_ARROW ; et la brosse de fond. Pour plus d’informations sur l’enregistrement des classes de fenêtre MFC, voir [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="afx_global_dataresume"></a><a name="resume"></a>AFX_GLOBAL_DATA::Cv

Réinitialise les pointeurs de fonction internes qui accèdent à des méthodes prenant en charge les thèmes et les styles visuels Windows.

```
BOOL Resume();
```

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode réussit; autrement, FALSE. En mode débogé, cette méthode affirme si cette méthode est infructueuse.

### <a name="remarks"></a>Notes

Cette méthode est appelée lorsque le cadre reçoit le [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) message.

## <a name="afx_global_datasetlayeredattrib"></a><a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib

Fournit un moyen simple d’appeler la méthode Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) .

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*Hwnd*<br/>
[dans] Manipuler à la fenêtre en couches.

*crKey (en)*<br/>
[dans] La clé de couleur de transparence que le [gestionnaire de fenêtre de bureau](/windows/win32/dwm/dwm-overview) utilise pour composer la fenêtre en couches.

*bAlpha*<br/>
[dans] La valeur alpha qui est utilisée pour décrire l’opacité de la fenêtre en couches.

*dwFlags*<br/>
[dans] Une combinaison bitwise (OU) de drapeaux qui spécifient les paramètres de la méthode à utiliser. Spécifiez LWA_COLORKEY d’utiliser le paramètre *crKey* comme couleur de transparence. Spécifier LWA_ALPHA d’utiliser le paramètre *bAlpha* pour déterminer l’opacité de la fenêtre en couches.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode réussit; autrement, FALSE.

## <a name="afx_global_datasetmenufont"></a><a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont

Crée la police logique spécifiée.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
[dans] Pointeur vers une structure qui contient les attributs d’une police.

*bHorz (en)*<br/>
[dans] VRAI pour spécifier que le texte s’exécute horizontalement; FALSE pour spécifier que le texte fonctionne verticalement.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode réussit; autrement, FALSE. En mode débogé, cette méthode affirme si cette méthode est infructueuse.

### <a name="remarks"></a>Notes

Cette méthode crée une police horizontale régulière, une police soulignée, et une police audacieuse qui est utilisé dans les éléments de menu par défaut. Cette méthode crée en option une police verticale régulière. Pour plus d’informations sur les polices logiques, voir [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="afx_global_dataupdatefonts"></a><a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts

Réinitialise les polices logiques qui sont utilisées par l’infrastructure.

```
void UpdateFonts();
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur `CFont::CreateFontIndirect`les polices logiques, voir .

## <a name="afx_global_dataupdatesyscolors"></a><a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors

Initialise les couleurs, la profondeur de couleur, les pinceaux, les stylets et les images qui sont utilisés par l’infrastructure.

```
void UpdateSysColors();
```

## <a name="afx_global_databiswindows7"></a><a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7

Indique si l’application est exécutée sous Windows 7 ou plus.

```
BOOL bIsWindows7;
```

## <a name="afx_global_dataclractivecaptiongradient"></a><a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient

Spécifie la couleur de gradient de la légende active. Généralement utilisé pour les volets d’ancrage.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="afx_global_dataclrinactivecaptiongradient"></a><a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clrInactiveCaptionGradient

Spécifie la couleur de gradient de la légende inactive. Généralement utilisé pour les volets d’ancrage.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="afx_global_datagetitaskbarlist"></a><a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarList

Crée et stocke dans les `ITaskBarList` données mondiales un pointeur de l’interface.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `ITaskbarList` à l’interface si la création d’un objet de liste de barres de tâches réussit ; NULL en cas de défaillance de la création ou si le système d’opération actuel est inférieur à Windows 7.

## <a name="afx_global_datagetitaskbarlist3"></a><a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3

Crée et stocke dans les `ITaskBarList3` données mondiales un pointeur de l’interface.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `ITaskbarList3` à l’interface si la création d’un objet de liste de barres de tâches réussit ; NULL en cas de défaillance de la création ou si le système d’opération actuel est inférieur à Windows 7.

## <a name="afx_global_datagetshellautohidebars"></a><a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars

Détermine les positions des barres de masquage automatique de l’interpréteur de commandes.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Valeur de retour

Une valeur integer avec des drapeaux codés qui spécifient les positions des barres de cache automatique. Il peut combiner les valeurs suivantes : AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="afx_global_datareleasetaskbarrefs"></a><a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs

Communiqués interfaces obtenues `GetITaskbarList3` par le biais de la et des `GetITaskbarList` méthodes.

```
void ReleaseTaskBarRefs();
```

## <a name="afx_global_datashellcreateitemfromparsingname"></a><a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemDeParsingName

Crée et initialise un objet élément d’interpréteur de commandes à partir d’un nom de l’analyse.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Paramètres

*pszPath (pszPath)*<br/>
[dans] Un pointeur à un nom d’affichage.

*Pbc*<br/>
Un pointeur à un contexte de liaison qui contrôle l’opération d’analyse.

*riid*<br/>
Une référence à une interface ID.

*Ppv*<br/>
[out] Lorsque cette fonction revient, contient le pointeur d’interface demandé en *riid*. Ce sera `IShellItem` généralement `IShellItem2`ou .

### <a name="return-value"></a>Valeur de retour

Retours S_OK en cas de succès; une valeur d’erreur autrement.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../hierarchy-chart.md)<br/>
[Structures, styles, rappels et tables de messages](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Composants et états](/windows/win32/controls/parts-and-states)<br/>
[CDC::DrawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Gestionnaire de fenêtrage](/windows/win32/dwm/dwm-overview)<br/>
[Activer et contrôler la composition du Gestionnaire de fenêtrage](/windows/win32/dwm/composition-ovw)<br/>
[UI Automation et Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[Fonction GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush GetSysColorBrush GetSysColorBrush GetS](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[NONCLIENTMETRICS Structure](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
