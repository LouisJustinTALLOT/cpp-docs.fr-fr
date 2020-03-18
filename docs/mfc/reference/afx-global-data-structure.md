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
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
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
ms.openlocfilehash: dda3056cbed18ef93e09b52cd9d0a6b00e1db177
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420588"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA (structure)

La structure `AFX_GLOBAL_DATA` contient des champs et des méthodes qui permettent de gérer l’infrastructure ou de personnaliser l’apparence et le comportement de votre application.

## <a name="syntax"></a>Syntaxe

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Construit une structure `AFX_GLOBAL_DATA` .|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[AFX_GLOBAL_DATA :: CleanUp](#cleanup)|Libère les ressources allouées par l’infrastructure, telles que les pinceaux, les polices et les DLL.|
|[AFX_GLOBAL_DATA ::D 2D1MakeRotateMatrix](#d2d1makerotatematrix)|Crée une transformation de rotation qui pivote autour d’un point spécifié selon un angle spécifié.|
|[AFX_GLOBAL_DATA ::D rawParentBackground](#drawparentbackground)|Dessine l’arrière-plan du parent d’un contrôle dans la zone spécifiée.|
|[AFX_GLOBAL_DATA ::D rawTextOnGlass](#drawtextonglass)|Dessine le texte spécifié dans le style visuel du thème spécifié.|
|[AFX_GLOBAL_DATA :: ExcludeTag](#excludetag)|Supprime la paire de balises XML spécifiée dans une mémoire tampon spécifiée.|
|[AFX_GLOBAL_DATA :: GetColor](#getcolor)|Récupère la couleur actuelle de l’élément d’interface utilisateur spécifié.|
|[AFX_GLOBAL_DATA :: GetDirect2dFactory](#getdirect2dfactory)|Renvoie un pointeur à l’interface `ID2D1Factory` qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.|
|[AFX_GLOBAL_DATA :: GetHandCursor](#gethandcursor)|Récupère le curseur prédéfini qui a la forme d’une main et dont l’identificateur est `IDC_HAND`.|
|[AFX_GLOBAL_DATA :: les](#getitaskbarlist)|Crée et stocke dans les données globales un pointeur vers l’interface ITaskBarList.|
|[AFX_GLOBAL_DATA :: GetITaskbarList3](#getitaskbarlist3)|Crée et stocke dans les données globales un pointeur vers l’interface ITaskBarList3.|
|[AFX_GLOBAL_DATA :: GetNonClientMetrics](#getnonclientmetrics)|Récupère les mesures associées à la zone non cliente des fenêtres non réduites.|
|[AFX_GLOBAL_DATA :: GetShellAutohideBars](#getshellautohidebars)|Détermine les positions des barres de masquage automatique de l’interpréteur de commandes.|
|[AFX_GLOBAL_DATA :: GetTextHeight](#gettextheight)|Récupère la hauteur des caractères de texte dans la police actuelle.|
|[AFX_GLOBAL_DATA :: GetWICFactory](#getwicfactory)|Renvoie un pointeur à l’interface `IWICImagingFactory` qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.|
|[AFX_GLOBAL_DATA :: GetWriteFactory](#getwritefactory)|Renvoie un pointeur à l’interface `IDWriteFactory` qui est stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.|
|[AFX_GLOBAL_DATA :: IsD2DInitialized](#isd2dinitialized)|Initialise les fabriques `D2D`, `DirectWrite`et `WIC` . Appelez cette méthode avant que la fenêtre principale soit initialisée.|
|[AFX_GLOBAL_DATA :: Is32BitIcons](#is32biticons)|Indique si les icônes 32 bits prédéfinies sont prises en charge.|
|[AFX_GLOBAL_DATA :: IsD2DInitialized](#isd2dinitialized)|Détermine si `D2D` a été initialisé.|
|[AFX_GLOBAL_DATA :: IsDwmCompositionEnabled](#isdwmcompositionenabled)|Fournit un moyen simple d’appeler la méthode Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) .|
|[AFX_GLOBAL_DATA :: IsHighContrastMode](#ishighcontrastmode)|Indique si les images sont actuellement affichées avec un contraste élevé.|
|[AFX_GLOBAL_DATA :: OnSettingChange](#onsettingchange)|Détecte l’état actuel des fonctionnalités de masquage automatique de la barre des tâches et de l’animation des menus du Bureau.|
|[AFX_GLOBAL_DATA :: RegisterWindowClass](#registerwindowclass)|Inscrit la classe de fenêtre MFC spécifiée.|
|[AFX_GLOBAL_DATA :: ReleaseTaskBarRefs](#releasetaskbarrefs)|Libère les interfaces obtenues par les méthodes GetITaskbarList et GetITaskbarList3.|
|[AFX_GLOBAL_DATA :: Resume](#resume)|Réinitialise les pointeurs de fonction internes qui accèdent à des méthodes prenant en charge [les thèmes et les styles visuels](/windows/win32/Controls/visual-styles-overview)Windows.|
|[AFX_GLOBAL_DATA :: SetLayeredAttrib](#setlayeredattrib)|Fournit un moyen simple d’appeler la méthode Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) .|
|[AFX_GLOBAL_DATA :: SetMenuFont](#setmenufont)|Crée la police logique spécifiée.|
|[AFX_GLOBAL_DATA :: ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Crée et initialise un objet élément d’interpréteur de commandes à partir d’un nom de l’analyse.|
|[AFX_GLOBAL_DATA :: UpdateFonts](#updatefonts)|Réinitialise les polices logiques qui sont utilisées par l’infrastructure.|
|[AFX_GLOBAL_DATA :: UpdateSysColors](#updatesyscolors)|Initialise les couleurs, la profondeur de couleur, les pinceaux, les stylets et les images qui sont utilisés par l’infrastructure.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[AFX_GLOBAL_DATA :: EnableAccessibilitySupport](#enableaccessibilitysupport)|Active ou désactive la prise en charge de Microsoft Active Accessibility. Active Accessibility fournit des méthodes fiables pour exposer des informations sur les éléments d’interface utilisateur.|
|[AFX_GLOBAL_DATA :: IsAccessibilitySupport](#isaccessibilitysupport)|Indique si la prise en charge de Microsoft Active Accessibility est activée.|
|[AFX_GLOBAL_DATA :: IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Indique si le système d’exploitation prend en charge les fenêtres superposées.|

### <a name="data-members"></a>Données membres

|Name|Description|
|----------|-----------------|
|[AFX_GLOBAL_DATA :: bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Indique si le système d’exploitation actuel prend en charge la simulation de transparence.|
|[AFX_GLOBAL_DATA :: bIsWindows7](#biswindows7)|Indique si l’application est exécutée sur le système d’exploitation Windows 7 ou ultérieur|
|[AFX_GLOBAL_DATA :: clrActiveCaptionGradient](#clractivecaptiongradient)|Spécifie la couleur de dégradé de la légende active. Généralement utilisé pour les volets d’ancrage.|
|[AFX_GLOBAL_DATA :: clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Spécifie la couleur de dégradé de la légende inactive. Généralement utilisé pour les volets d’ancrage.|
|[AFX_GLOBAL_DATA :: m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Indique si l’infrastructure utilise des icônes de couleur 32 bits prédéfinies ou des icônes d’une résolution inférieure.|
|[AFX_GLOBAL_DATA :: m_bUseSystemFont](#m_busesystemfont)|Indique si une police système est utilisée pour les menus, les barres d’outils et les rubans.|
|[AFX_GLOBAL_DATA :: m_hcurHand](#m_hcurhand)|Stocke le handle du curseur en forme de main.|
|[AFX_GLOBAL_DATA :: m_hcurStretch](#m_hcurstretch)|Stocke le handle du curseur d’étirement horizontal.|
|[AFX_GLOBAL_DATA :: m_hcurStretchVert](#m_hcurstretchvert)|Stocke le handle du curseur d’étirement vertical.|
|[AFX_GLOBAL_DATA :: m_hiconTool](#m_hicontool)|Stocke le handle de l’icône d’outil.|
|[AFX_GLOBAL_DATA :: m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Spécifie le décalage entre la barre d’outils de masquage automatique la plus à gauche et le côté gauche de la barre d’ancrage.|
|[AFX_GLOBAL_DATA :: m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Spécifie l’intervalle entre les barres d’outils de masquage automatique.|
|[AFX_GLOBAL_DATA :: m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Spécifie l’épaisseur du cadre de glissement qui est utilisé pour communiquer l’état d’ancrage.|
|[AFX_GLOBAL_DATA :: m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Spécifie l’épaisseur du cadre de glissement qui est utilisé pour communiquer l’état flottant.|

### <a name="remarks"></a>Notes

La plupart des données dans la structure `AFX_GLOBAL_DATA` sont initialisées au démarrage de votre application.

### <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Spécifications

**En-tête :** afxglobals.h

## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA :: bIsOSAlphaBlendingSupport

Indique si le système d’exploitation prend en charge la fusion alpha.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Notes

TRUE indique que la fusion alpha est prise en charge ; Sinon, FALSe.

## <a name="cleanup"></a>AFX_GLOBAL_DATA :: CleanUp

Libère les ressources allouées par l’infrastructure, telles que les pinceaux, les polices et les DLL.

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA ::D 2D1MakeRotateMatrix

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

*gestionnaire*<br/>
Point à partir duquel pivoter.

*comparatif*<br/>
Lorsque cette méthode est retournée, contient la nouvelle transformation de rotation. Vous devez allouer du stockage pour ce paramètre.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une valeur d’erreur dans le cas contraire.

## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA ::D rawParentBackground

Dessine l’arrière-plan du parent d’un contrôle dans la zone spécifiée.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Pointeur vers la fenêtre d’un contrôle.

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*lpRect*<br/>
dans Pointeur désignant un rectangle qui délimite la zone à dessiner. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA ::D rawTextOnGlass

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
dans Handle vers les données de thème d’une fenêtre, ou NULL. L’infrastructure utilise le thème spécifié pour dessiner le texte si ce paramètre n’est pas NULL et que les thèmes sont pris en charge. Sinon, l’infrastructure n’utilise pas de thème pour dessiner le texte.

Utilisez la méthode [OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) pour créer un htheme.

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*iPartId*<br/>
dans Partie de contrôle qui a l’apparence de texte souhaitée. Pour plus d’informations, consultez la colonne Composants de la table figurant dans [Composants et états](/windows/win32/controls/parts-and-states). Si cette valeur est égale à 0, le texte est dessiné avec la police par défaut ou une police sélectionnée dans le contexte de l’appareil.

*iStateId*<br/>
dans État du contrôle ayant l’apparence de texte souhaitée. Pour plus d’informations, consultez la colonne États de la table figurant dans [Composants et états](/windows/win32/controls/parts-and-states).

*strText*<br/>
dans Texte à dessiner.

*rectangulaire*<br/>
dans Limite de la zone dans laquelle le texte spécifié est dessiné.

*dwFlags*<br/>
dans Combinaison d’opérations de bits d’indicateurs qui spécifient comment le texte spécifié est dessiné.

Si le paramètre *hTheme* est `NULL` ou si les thèmes ne sont pas pris en charge et activés, le paramètre *nFormat* de la méthode [rawtext CDC ::D](../../mfc/reference/cdc-class.md#drawtext) décrit les indicateurs valides. Si les thèmes sont pris en charge, le paramètre *dwFlags* de la méthode [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) décrit les indicateurs valides.

*nGlowSize*<br/>
dans Taille d’un effet d’éclat dessiné sur l’arrière-plan avant de dessiner le texte spécifié. La valeur par défaut est 0.

*clrText*<br/>
dans Couleur dans laquelle le texte spécifié est dessiné. La valeur par défaut est la couleur par défaut.

### <a name="return-value"></a>Valeur de retour

TRUE si un thème est utilisé pour dessiner le texte spécifié ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Un thème définit le style visuel d’une application. Un thème n’est pas utilisé pour dessiner le texte si le paramètre *hTheme* a la valeur null, si la méthode [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) n’est pas prise en charge ou si la composition [Gestionnaire de fenêtrage](/windows/win32/dwm/dwm-overview) (DWM) est désactivée.

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA :: EnableAccessibilitySupport

Active ou désactive la prise en charge de Microsoft Active Accessibility.

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour activer la prise en charge de l’accessibilité ; FALSe pour désactiver la prise en charge de l’accessibilité. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Active Accessibility est une technologie COM qui améliore la façon dont les programmes et le système d’exploitation Windows fonctionnent conjointement avec les produits de technologie d’assistance. Il fournit des méthodes fiables pour exposer des informations sur les éléments de l’interface utilisateur. Toutefois, un modèle d’accessibilité plus récent appelé Microsoft UI Automation est désormais disponible. Pour une comparaison des deux technologies, consultez [UI Automation et Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Utilisez la méthode [AFX_GLOBAL_DATA :: IsAccessibilitySupport](#isaccessibilitysupport) pour déterminer si la prise en charge de Microsoft Active Accessibility est activée.

## <a name="excludetag"></a>AFX_GLOBAL_DATA :: ExcludeTag

Supprime la paire de balises XML spécifiée dans une mémoire tampon spécifiée.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Paramètres

*strBuffer*<br/>
dans Mémoire tampon de texte.

*lpszTag*<br/>
dans Nom d’une paire de balises XML d’ouverture et de fermeture.

*strTag*<br/>
à Lorsque cette méthode est retournée, le paramètre *strTag* contient le texte qui se trouve entre les balises XML d’ouverture et de fermeture qui sont nommées par le paramètre *lpszTag* . Les espaces de début ou de fin sont supprimés du résultat.

*bIsCharsList*<br/>
dans TRUE pour convertir les symboles des caractères d’échappement du paramètre *strTag* en caractères d’échappement réels ; FALSe pour ne pas effectuer la conversion. La valeur par défaut est FALSe. Pour plus d'informations, consultez la section Notes.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Une paire de balises XML se compose de balises d’ouverture et de fermeture nommées qui indiquent le début et la fin d’une exécution de texte dans la mémoire tampon spécifiée. Le paramètre *strBuffer* spécifie la mémoire tampon, tandis que le paramètre *lpszTag* spécifie le nom des balises XML.

Utilisez les symboles du tableau suivant pour encoder un ensemble de caractères d’échappement dans la mémoire tampon spécifiée. Spécifiez TRUE pour le paramètre *bIsCharsList* pour convertir les symboles du paramètre *strTag* en caractères d’échappement réels. Le tableau suivant utilise la macro [_T ()](../../c-runtime-library/data-type-mappings.md) pour spécifier les chaînes de caractères de symboles et de caractères d’échappement.

|Symbole|Caractère d'échappement|
|------------|----------------------|
|_T («\\\t »)|_T("\t")|
|_T («\\\n »)|_T (« \n »)|
|_T («\\\r »)|_T (« \r »)|
|_T («\\\b »)|_T (« \b »)|
|_T("LT")|_T («\<»)|
|_T("GT")|_T(">")|
|_T("AMP")|_T("&")|

## <a name="getcolor"></a>AFX_GLOBAL_DATA :: GetColor

Récupère la couleur actuelle de l’élément d’interface utilisateur spécifié.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Paramètres

*nColor*<br/>
dans Valeur qui spécifie un élément d’interface utilisateur dont la couleur est récupérée. Pour obtenir la liste des valeurs valides, consultez le paramètre *nIndex* de la méthode [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) .

### <a name="return-value"></a>Valeur de retour

Valeur de couleur RVB de l’élément d’interface utilisateur spécifié. Pour plus d'informations, consultez la section Notes.

### <a name="remarks"></a>Notes

Si le paramètre *nColor* est hors limites, la valeur de retour est zéro. Comme zéro est également une valeur RVB valide, vous ne pouvez pas utiliser cette méthode pour déterminer si une couleur système est prise en charge par le système d’exploitation actuel. Utilisez plutôt la méthode [GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) , qui retourne la valeur null si la couleur n’est pas prise en charge.

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA :: GetDirect2dFactory

Retourne un pointeur vers l’interface ID2D1Factory stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface ID2D1Factory si la création d’une fabrique réussit, ou NULL si la création échoue ou si le système d’exploitation actuel n’a pas de prise en charge D2D.

## <a name="gethandcursor"></a>AFX_GLOBAL_DATA :: GetHandCursor

Récupère le curseur prédéfini qui ressemble à une main et dont l’identificateur est IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Valeur de retour

Handle du curseur de la main.

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA :: GetNonClientMetrics

Récupère les mesures associées à la zone non cliente des fenêtres non réduites.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Paramètres

*info*<br/>
[in, out] Structure [NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) qui contient les métriques dimensionnables associées à la zone non cliente d’une fenêtre non réduite.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode est réussie ; Sinon, FALSe.

## <a name="gettextheight"></a>AFX_GLOBAL_DATA :: GetTextHeight

Récupère la hauteur des caractères de texte dans la police actuelle.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Paramètres

*bHorz*<br/>
dans TRUE pour récupérer la hauteur des caractères lorsque le texte s’exécute horizontalement ; FALSe pour récupérer la hauteur des caractères lorsque le texte s’exécute verticalement. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Hauteur de la police actuelle, qui est mesurée de son ascendeur à son descendant.

## <a name="getwicfactory"></a>AFX_GLOBAL_DATA :: GetWICFactory

Retourne un pointeur vers l’interface IWICImagingFactory stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface IWICImagingFactory si la création d’une fabrique réussit, ou NULL si la création échoue ou si le système d’exploitation actuel n’a pas de prise en charge de WIC.

## <a name="getwritefactory"></a>AFX_GLOBAL_DATA :: GetWriteFactory

Retourne un pointeur vers l’interface IDWriteFactory stockée dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface IDWriteFactory si la création d’une fabrique réussit, ou NULL si la création échoue ou si le système d’exploitation actuel n’a pas de prise en charge de DirectWrite.

## <a name="initd2d"></a>AFX_GLOBAL_DATA :: InitD2D

Initialise les fabriques D2D, DirectWrite et WIC. Appelez cette méthode avant que la fenêtre principale soit initialisée.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Paramètres

*d2dFactoryType*<br/>
Le modèle de thread de la fabrique D2D et les ressources qu’il crée.

*writeFactoryType*<br/>
Valeur qui spécifie si l’objet de fabrique d’écriture sera partagé ou isolé

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les fabriques étaient intilalizrd, FALSe dans le cas contraire

## <a name="is32biticons"></a>AFX_GLOBAL_DATA :: Is32BitIcons

Indique si les icônes 32 bits prédéfinies sont prises en charge.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si les icônes 32 bits prédéfinies sont prises en charge ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode retourne la valeur TRUE si le Framework prend en charge les icônes intégrées 32 bits et si le système d’exploitation prend en charge 16 bits par pixel ou plus et si les images ne sont pas affichées en contraste élevé.

## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA :: IsAccessibilitySupport

Indique si la prise en charge de Microsoft Active Accessibility est activée.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la prise en charge de l’accessibilité est activée ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Microsoft Active Accessibility était la solution précédente pour rendre les applications accessibles. Microsoft UI Automation est le nouveau modèle d’accessibilité de Microsoft Windows et est destiné à répondre aux besoins des produits de technologie d’assistance et des outils de test automatisés.

Utilisez la méthode [AFX_GLOBAL_DATA :: EnableAccessibilitySupport](#enableaccessibilitysupport) pour activer ou désactiver la prise en charge des Active Accessibility.

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA :: IsD2DInitialized

Détermine si le D2D a été initialisé

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si D2D a été initialisé ; Sinon, FALSe.

## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA :: IsDwmCompositionEnabled

Fournit un moyen simple d’appeler la méthode Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) .

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Valeur de retour

TRUE si la composition [Gestionnaire de fenêtrage](/windows/win32/dwm/dwm-overview) (DWM) est activée ; Sinon, FALSe.

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA :: IsHighContrastMode

Indique si les images sont actuellement affichées avec un contraste élevé.
```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si les images sont actuellement affichées en mode noir ou blanc à contraste élevé ; Sinon, FALSe.

### <a name="remarks"></a>Notes

En mode contraste élevé noir, les bords face à la lumière sont blancs et l’arrière-plan est noir. En mode contraste élevé blanc, les bords face à la lumière sont noirs et l’arrière-plan est blanc.

## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA :: IsWindowsLayerSupportAvailable

Indique si le système d’exploitation prend en charge les fenêtres superposées.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si les fenêtres superposées sont prises en charge ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si les fenêtres superposées sont prises en charge, les marqueurs d' *ancrage intelligent* utilisent des fenêtres superposées.

## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA :: m_bUseBuiltIn32BitIcons

Indique si l’infrastructure utilise des icônes de couleur 32 bits prédéfinies ou des icônes d’une résolution inférieure.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Notes

TRUE spécifie que l’infrastructure utilise des icônes de couleur 32 bits ; FALSe spécifie les icônes de résolution inférieure. Le constructeur `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Initialise ce membre à la valeur TRUE.

Ce membre doit être défini au démarrage de l’application.

## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA :: m_bUseSystemFont

Indique si une police système est utilisée pour les menus, les barres d’outils et les rubans.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Notes

TRUE spécifie l’utilisation d’une police système ; Sinon, FALSe. Le constructeur `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Initialise ce membre à FALSe.

Le test de ce membre n’est pas le seul moyen pour le Framework de déterminer la police à utiliser. La méthode `AFX_GLOBAL_DATA::UpdateFonts` teste également les polices par défaut et alternatives pour déterminer les styles visuels disponibles à appliquer aux menus, barres d’outils et rubans.

## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA :: m_hcurHand

Stocke le handle du curseur en forme de main.

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA :: m_hcurStretch

Stocke le handle du curseur d’étirement horizontal.

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA :: m_hcurStretchVert

Stocke le handle du curseur d’étirement vertical.

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a>AFX_GLOBAL_DATA :: m_hiconTool

Stocke le handle de l’icône d’outil.

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA :: m_nAutoHideToolBarMargin

Spécifie le décalage à partir de la barre d’outils de masquage automatique la plus à gauche sur le côté gauche de la barre d’ancrage.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Notes

Le constructeur `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Initialise ce membre à 4 pixels.

## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA :: m_nAutoHideToolBarSpacing

Spécifie l’intervalle entre les barres d’outils de masquage automatique.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Notes

Le constructeur `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Initialise ce membre à 14 pixels.

## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA :: m_nDragFrameThicknessDock

Spécifie l’épaisseur du cadre de glissement qui est utilisé pour indiquer l’état ancré.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Notes

Le constructeur `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Initialise ce membre à 3 pixels.

## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA :: m_nDragFrameThicknessFloat

Spécifie l’épaisseur du cadre de glissement qui est utilisé pour indiquer l’état flottant.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Notes

Le constructeur `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Initialise ce membre à 4 pixels.

## <a name="onsettingchange"></a>AFX_GLOBAL_DATA :: OnSettingChange

Détecte l’état actuel des fonctionnalités de masquage automatique de la barre des tâches et de l’animation des menus du Bureau.

```
void OnSettingChange();
```

### <a name="remarks"></a>Notes

Cette méthode définit les variables d’infrastructure à l’état de certains attributs du Bureau de l’utilisateur. Cette méthode détecte l’état actuel de l’animation de menu, de l’atténuation de menu et des fonctionnalités de masquage automatique de la barre des tâches.

## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA :: RegisterWindowClass

Inscrit la classe de fenêtre MFC spécifiée.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Paramètres

*lpszClassNamePrefix*<br/>
dans Nom de la classe de fenêtre à inscrire.

### <a name="return-value"></a>Valeur de retour

Nom qualifié de la classe inscrite si cette méthode est réussie ; Sinon, une [exception de ressource](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Notes

La valeur de retour est une liste délimitée par des deux-points de la chaîne de paramètre *lpszClassNamePrefix* et les représentations de texte hexadécimal des handles de l’instance d’application actuelle. le curseur de l’application, qui est le curseur en flèche dont l’identificateur est IDC_ARROW ; et le pinceau d’arrière-plan. Pour plus d’informations sur l’inscription des classes de fenêtre MFC, consultez [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="resume"></a>AFX_GLOBAL_DATA :: Resume

Réinitialise les pointeurs de fonction internes qui accèdent à des méthodes prenant en charge les thèmes et les styles visuels Windows.

```
BOOL Resume();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode est réussie ; Sinon, FALSe. En mode débogage, cette méthode déclare si cette méthode échoue.

### <a name="remarks"></a>Notes

Cette méthode est appelée lorsque le Framework reçoit le message de [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) .

## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA :: SetLayeredAttrib

Fournit un moyen simple d’appeler la méthode Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) .

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*HWND*<br/>
dans Handle vers la fenêtre superposée.

*crKey*<br/>
dans Clé de couleur de transparence que le [Gestionnaire de fenêtrage](/windows/win32/dwm/dwm-overview) utilise pour composer la fenêtre superposée.

*bAlpha*<br/>
dans Valeur alpha utilisée pour décrire l’opacité de la fenêtre superposée.

*dwFlags*<br/>
dans Combinaison de bits (OR) d’indicateurs qui spécifie les paramètres de méthode à utiliser. Spécifiez LWA_COLORKEY pour utiliser le paramètre *crKey* comme couleur de transparence. Spécifiez LWA_ALPHA pour utiliser le paramètre *bAlpha* pour déterminer l’opacité de la fenêtre superposée.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode est réussie ; Sinon, FALSe.

## <a name="setmenufont"></a>AFX_GLOBAL_DATA :: SetMenuFont

Crée la police logique spécifiée.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*lpLogFont*<br/>
dans Pointeur vers une structure qui contient les attributs d’une police.

*bHorz*<br/>
dans TRUE pour spécifier que le texte s’exécute horizontalement ; FALSe pour spécifier que le texte s’exécute verticalement.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode est réussie ; Sinon, FALSe. En mode débogage, cette méthode déclare si cette méthode échoue.

### <a name="remarks"></a>Notes

Cette méthode crée une police normale horizontale, une police soulignée et une police en gras qui est utilisée dans les éléments de menu par défaut. Cette méthode crée éventuellement une police verticale standard. Pour plus d’informations sur les polices logiques, consultez [CFont :: CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="updatefonts"></a>AFX_GLOBAL_DATA :: UpdateFonts

Réinitialise les polices logiques qui sont utilisées par l’infrastructure.

```
void UpdateFonts();
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les polices logiques, consultez `CFont::CreateFontIndirect`.

## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA :: UpdateSysColors

Initialise les couleurs, la profondeur de couleur, les pinceaux, les stylets et les images qui sont utilisés par l’infrastructure.

```
void UpdateSysColors();
```

## <a name="biswindows7"></a>AFX_GLOBAL_DATA :: bIsWindows7

Indique si l’application est exécutée sous Windows 7 ou version ultérieure.

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA :: clrActiveCaptionGradient

Spécifie la couleur de dégradé de la légende active. Généralement utilisé pour les volets d’ancrage.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA :: clrInactiveCaptionGradient

Spécifie la couleur de dégradé de la légende inactive. Généralement utilisé pour les volets d’ancrage.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA :: les

Crée et stocke dans les données globales un pointeur vers l’interface `ITaskBarList`.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface `ITaskbarList` si la création d’un objet de liste de barre de tâches est réussie ; NULL si la création échoue ou si le système d’exploitation actuel est inférieur à Windows 7.

## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA :: GetITaskbarList3

Crée et stocke dans les données globales un pointeur vers l’interface `ITaskBarList3`.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface `ITaskbarList3` si la création d’un objet de liste de barre de tâches est réussie ; NULL si la création échoue ou si le système d’exploitation actuel est inférieur à Windows 7.

## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA :: GetShellAutohideBars

Détermine les positions des barres de masquage automatique de l’interpréteur de commandes.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Valeur de retour

Valeur entière avec les indicateurs encodés qui spécifient les positions des barres de masquage automatique. Elle peut combiner les valeurs suivantes : AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA :: ReleaseTaskBarRefs

Libère les interfaces obtenues par l’intermédiaire des méthodes `GetITaskbarList` et `GetITaskbarList3`.

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA :: ShellCreateItemFromParsingName

Crée et initialise un objet élément d’interpréteur de commandes à partir d’un nom de l’analyse.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Paramètres

*pszPath*<br/>
dans Pointeur vers un nom complet.

*pbc*<br/>
Pointeur vers un contexte de liaison qui contrôle l’opération d’analyse.

*riid*<br/>
Référence à un ID d’interface.

*ppv*<br/>
à Lorsque cette fonction est retournée, contient le pointeur d’interface demandé dans *riid*. Il s’agit généralement de `IShellItem` ou `IShellItem2`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite ; valeur d’erreur dans le cas contraire.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../hierarchy-chart.md)<br/>
[Structures, styles, rappels et tables de messages](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Parties et États](/windows/win32/controls/parts-and-states)<br/>
[CDC ::D rawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Gestionnaire de fenêtrage](/windows/win32/dwm/dwm-overview)<br/>
[Activer et contrôler la composition DWM](/windows/win32/dwm/composition-ovw)<br/>
[UI Automation et Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor, fonction](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[NONCLIENTMETRICS, structure](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
