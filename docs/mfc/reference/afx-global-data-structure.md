---
title: Afx_global_data, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFX_GLOBAL_DATA
dev_langs:
- C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4885cf6e5ddbff939e3f8e6401bd23661f13e275
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337406"
---
# <a name="afxglobaldata-structure"></a>AFX_GLOBAL_DATA (structure)
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
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Initialise les fabriques `D2D`, `DirectWrite`et `WIC` . Appelez cette méthode avant que la fenêtre principale soit initialisée.|  
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Indique si les icônes 32 bits prédéfinies sont prises en charge.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Détermine si `D2D` a été initialisé.|  
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Fournit un moyen simple d’appeler la méthode Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) .|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Indique si les images sont actuellement affichées avec un contraste élevé.|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Détecte l’état actuel des fonctionnalités de masquage automatique de la barre des tâches et de l’animation des menus du Bureau.|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Inscrit la classe de fenêtre MFC spécifiée.|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Libère les interfaces obtenues par les méthodes GetITaskbarList et GetITaskbarList3.|  
|[AFX_GLOBAL_DATA::Resume](#resume)|Réinitialise les pointeurs de fonction internes qui accèdent à des méthodes prenant en charge [les thèmes et les styles visuels](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)Windows.|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Fournit un moyen simple d’appeler la méthode Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) .|  
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
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
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
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxglobals.h  
  
### <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


## <a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
Indique si le système d’exploitation prend en charge la fusion alpha.  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>Notes  
 TRUE indique que la fusion alpha est pris en charge ; Sinon, FALSE.  
  

## <a name="cleanup"></a> AFX_GLOBAL_DATA::CleanUp
Libère les ressources allouées par l’infrastructure, telles que les pinceaux, les polices et les DLL.  
  
  
```  
void CleanUp();
```  
## <a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
Crée une transformation de rotation qui pivote autour d’un point spécifié selon un angle spécifié.  
  
  
```  
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,  
    D2D1_POINT_2F center,  
    D2D1_MATRIX_3X2_F *matrix);
```  
  
### <a name="parameters"></a>Paramètres   
 *angle*  
 L’angle de rotation vers la droite, en degrés.  
  
 *Centre*  
 Le point autour duquel pivoter.  
  
 *matrice*  
 Lorsque cette méthode est retournée, contient la nouvelle transformation de rotation. Vous devez allouer le stockage pour ce paramètre.  
  
### <a name="return-value"></a>Valeur de retour  
 Sinon, retourne S_OK en cas de réussite, ou une valeur d’erreur.  
  
## <a name="drawparentbackground"></a> AFX_GLOBAL_DATA::DrawParentBackground
Dessine l’arrière-plan du parent d’un contrôle dans la zone spécifiée.  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Paramètres   
 [in] *pWnd*  
 Pointeur vers la fenêtre d’un contrôle.  
  
 [in] *pDC*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *lpRect*  
 Pointeur vers un rectangle qui délimite la zone dans laquelle dessiner. La valeur par défaut est NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
## <a name="drawtextonglass"></a> AFX_GLOBAL_DATA::DrawTextOnGlass
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
 [in] *hTheme*  
 Handle vers les données de thème d’une fenêtre, ou NULL. L’infrastructure utilise le thème spécifié pour dessiner le texte si ce paramètre n’est pas NULL et thèmes sont pris en charge. Sinon, l’infrastructure n’utilise pas de thème pour dessiner le texte.  
  
 Utilisez le [OpenThemeData](http://msdn.microsoft.com/library/windows/desktop/bb759821) méthode pour créer un HTHEME.  
  
 [in] *pDC*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *iPartId*  
 Composant du contrôle ayant l’apparence de texte désirée. Pour plus d’informations, consultez la colonne Composants de la table figurant dans [Composants et états](http://msdn.microsoft.com/library/windows/desktop/bb773210). Si cette valeur est égale à 0, le texte est dessiné avec la police par défaut ou une police sélectionnée dans le contexte de l’appareil.  
  
 [in] *iStateId*  
 État du contrôle ayant l’apparence de texte désirée. Pour plus d’informations, consultez la colonne États de la table figurant dans [Composants et états](http://msdn.microsoft.com/library/windows/desktop/bb773210).  
  
 [in] *strText*  
 Texte à dessiner.  
  
 [in] *rect*  
 Limite de la zone dans laquelle le texte spécifié est dessiné.  
  
 [in] *dwFlags*  
 Combinaison de bits (OR) d’indicateurs qui spécifient comment le texte spécifié est dessiné.  
  
 Si le *hTheme* paramètre est `NULL` ou si les thèmes ne sont pas pris en charge et activés, le *nFormat* paramètre de la [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) méthode décrit valides indicateurs. Si les thèmes sont pris en charge, le *dwFlags* paramètre de la [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) méthode décrit les indicateurs valides.  
  
 [in] *nGlowSize*  
 Taille d’un éclat dessiné à l’arrière-plan avant de dessiner le texte spécifié. La valeur par défaut est 0.  
  
 [in] *clrText*  
 Couleur utilisée pour dessiner le texte spécifié. La valeur par défaut est la couleur par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si un thème est utilisé pour dessiner le texte spécifié ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Un thème définit le style visuel d’une application. Un thème n’est pas utilisé pour dessiner le texte si le *hTheme* paramètre est NULL, ou si le [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) méthode n’est pas prise en charge, ou si [Gestionnaire de fenêtrage](http://msdn.microsoft.com/library/windows/desktop/aa969540) composition de (fenêtrage DWM) est désactivé.  
  
### <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [Composants et États](http://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317)   
 [Gestionnaire de fenêtrage](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [Activer et contrôler Composition DWM](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA::EnableAccessibilitySupport
Active ou désactive la prise en charge de Microsoft Active Accessibility.  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres   
 [in] *bActivez*  
 TRUE pour activer la prise en charge d’accessibilité ; FALSE pour désactiver la prise en charge de l’accessibilité. La valeur par défaut est TRUE.  
  
### <a name="remarks"></a>Notes  
 Active Accessibility est une technologie COM qui améliore les façon dont les programmes et le travail de système d’exploitation Windows ainsi que des produits de technologie d’assistance. Il fournit des méthodes fiables pour exposer des informations sur les éléments d’interface utilisateur. Toutefois, un modèle d’accessibilité plus récent appelé Microsoft UI Automation est maintenant disponible. Pour obtenir une comparaison des deux technologies, consultez [UI Automation et Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).  
  
 Utilisez le [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) méthode pour déterminer si la prise en charge de Microsoft Active Accessibility est activée.  
  
 
### <a name="see-also"></a>Voir aussi  
 [UI Automation et Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="excludetag"></a> AFX_GLOBAL_DATA::ExcludeTag
Supprime la paire de balises XML spécifiée dans une mémoire tampon spécifiée.  
  
  
```  
BOOL ExcludeTag(
    CString& strBuffer,  
    LPCTSTR lpszTag,  
    CString& strTag,  
    BOOL bIsCharsList = FALSE);
```  
  
### <a name="parameters"></a>Paramètres   
 [in] *strBuffer*  
 Une mémoire tampon de texte.  
  
 [in] *lpszTag*  
 Le nom d’une paire de balises de XML.  
  
 [out] *strTag*  
 Lorsque cette méthode est retournée, le *strTag* paramètre contient le texte entre les balises XML les balises qui sont nommés en fonction du *lpszTag* paramètre. Tout espace blanc au début ou de fin est tronqué à partir du résultat.  
  
 [in] *bIsCharsList*  
 True pour convertir les symboles pour les caractères d’échappement dans le *strTag* paramètre en caractères d’échappement réel ; Ne pas d’effectuer la conversion, la valeur est FALSE. La valeur par défaut est FALSE. Pour plus d'informations, consultez la section Notes.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Une paire de balises XML se compose de nommé balises qui indiquent le début et la fin d’une exécution de texte dans la mémoire tampon spécifiée. Le *strBuffer* paramètre spécifie la mémoire tampon et le *lpszTag* paramètre spécifie le nom des balises XML.  
  
 Utiliser les symboles dans le tableau suivant pour encoder un jeu de caractères d’échappement dans la mémoire tampon spécifiée. Spécifiez TRUE pour le *bIsCharsList* paramètre à convertir les symboles dans le *strTag* paramètre en caractères d’échappement réelle. Le tableau suivant utilise le [_T()](../../c-runtime-library/data-type-mappings.md) macro pour spécifier le symbole et de chaînes de caractères d’échappement.  
  
|Symbole|Caractère d'échappement|  
|------------|----------------------|  
|_T ("\\\t »)|_T("\t")|  
|_T ("\\\n »)|_T("\n")|  
|_T ("\\\r »)|_T("\r")|  
|_T ("\\\b »)|_T("\b")|  
|_T("LT")|_T («\<»)|  
|_T("GT")|_T("&GT;")|  
|_T("AMP")|_T("&AMP;")|  
  
## <a name="getcolor"></a> AFX_GLOBAL_DATA::GetColor
Récupère la couleur actuelle de l’élément d’interface utilisateur spécifié.  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>Paramètres   
 [in] *nColor*  
 Une valeur qui spécifie un élément d’interface utilisateur dont la couleur est récupérée. Pour obtenir la liste des valeurs valides, consultez la *nIndex* paramètre de la [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de couleur RVB de l’élément d’interface utilisateur spécifié. Pour plus d'informations, consultez la section Notes.  
  
### <a name="remarks"></a>Notes  
 Si le *nColor* paramètre est hors limites, la valeur de retour est égale à zéro. Étant donné que zéro est également une valeur valide RVB, vous ne pouvez pas utiliser cette méthode pour déterminer si une couleur système est pris en charge par le système d’exploitation actuel. Au lieu de cela, utilisez le [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927) (méthode), qui retourne la valeur NULL si la couleur n’est pas pris en charge.  
  
### <a name="see-also"></a>Voir aussi  

 [GetSysColor (fonction)](http://msdn.microsoft.com/library/windows/desktop/ms724371)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927)

## <a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA::GetDirect2dFactory
 Retourne un pointeur vers l’interface ID2D1Factory qui est stocké dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface ID2D1Factory si la création d’une fabrique réussit, ou NULL si la création échoue ou de système d’exploitation actuel ne prend pas prise en charge D2D.  
  
## <a name="gethandcursor"></a>  AFX_GLOBAL_DATA::GetHandCursor
Récupère le curseur prédéfini qui ressemble à une main et dont l’identificateur est IDC_HAND.  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du curseur main.  

## <a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA::GetNonClientMetrics
Récupère les mesures associées à la zone non cliente des fenêtres non réduites.  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>Paramètres   
 [in, out] *info*  
 Un [NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175) structure qui contient les mesures évolutives associées à la zone non cliente d’une fenêtre non réduite.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode réussit ; Sinon, FALSE.  
 
  
### <a name="see-also"></a>Voir aussi   
 [Structure NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a> AFX_GLOBAL_DATA::GetTextHeight
 Récupère la hauteur des caractères de texte dans la police actuelle.  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Paramètres   
 [in] *bHorz*  
 TRUE pour récupérer la hauteur des caractères lorsque le texte à l’horizontale ; FALSE pour récupérer la hauteur des caractères lorsque le texte verticalement. La valeur par défaut est TRUE.  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur de la police actuelle, qui est mesurée à partir de son ascender à son hampe.  
  
## <a name="getwicfactory"></a> AFX_GLOBAL_DATA::GetWICFactory
Retourne un pointeur vers l’interface IWICImagingFactory qui est stocké dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface IWICImagingFactory si la création d’une fabrique réussit, ou NULL si la création échoue ou système d’exploitation actuel ne prend pas prise en charge WIC.  
  
## <a name="getwritefactory"></a> AFX_GLOBAL_DATA::GetWriteFactory
Retourne un pointeur vers l’interface IDWriteFactory qui est stocké dans les données globales. Si l’interface n’est pas initialisée, elle est créée avec les paramètres par défaut.  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface IDWriteFactory si la création d’une fabrique réussit, ou NULL si la création échoue ou système d’exploitation actuel ne prend pas prise en charge de DirectWrite.  
 
## <a name="initd2d"></a> AFX_GLOBAL_DATA::InitD2D
Initialise les fabriques D2D, DirectWrite et WIC. Appelez cette méthode avant que la fenêtre principale soit initialisée.  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Paramètres   
 *d2dFactoryType*  
 Le modèle de thread de la fabrique D2D et des ressources qu’il crée.  
  
 *writeFactoryType*  
 Une valeur qui spécifie si l’objet de fabrique d’écriture sera partagé ou isolé  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE si les fabriques ont été initialisées, FALSE : sinon  
  
## <a name="is32biticons"></a> AFX_GLOBAL_DATA::Is32BitIcons
Indique si les icônes 32 bits prédéfinies sont prises en charge.  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si les icônes 32 bits prédéfinies sont prises en charge ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne la valeur TRUE si le framework prend en charge les icônes intégrés 32 bits, si le système d’exploitation prend en charge 16 bits par pixel ou plus et si les images ne sont pas affichées avec un contraste élevé.  
  
## <a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA::IsAccessibilitySupport
Indique si la prise en charge de Microsoft Active Accessibility est activée.  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la prise en charge de l’accessibilité est activée ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Microsoft Active Accessibility était la solution précédemment utilisée pour rendre les applications accessibles. Microsoft UI Automation est le nouveau modèle d’accessibilité pour Microsoft Windows et est conçue pour répondre aux besoins des produits de technologie d’assistance et outils de test automatisés.   
  
 Utilisez le [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) méthode pour activer ou désactiver la prise en charge Active Accessibility.  
  

### <a name="see-also"></a>Voir aussi  
 [UI Automation et Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)

## <a name="isd2dinitialized"></a> AFX_GLOBAL_DATA::IsD2DInitialized
 Détermine si le D2D a été initialisé.  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si D2D a été initialisé ; Sinon, FALSE.  
  
## <a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA::IsDwmCompositionEnabled
Fournit un moyen simple d’appeler la méthode Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) .  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si [Gestionnaire de fenêtrage](http://msdn.microsoft.com/library/windows/desktop/aa969540) composition de (fenêtrage DWM) est activée ; sinon, FALSE.  
  
### <a name="see-also"></a>Voir aussi    
 [Gestionnaire de fenêtrage](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [Activer et contrôler Composition DWM](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA::IsHighContrastMode
 Indique si les images sont actuellement affichées avec un contraste élevé.    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si les images sont affichées actuellement en mode de contraste élevé noir ou blanc. Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 En mode de contraste élevé noir, bords en face de la lumière sont le blancs et l’arrière-plan est noir. En mode de contraste élevé blanc, bords en face de la lumière sont affichent en noirs et l’arrière-plan est blanc.  
  
## <a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
Indique si le système d’exploitation prend en charge les fenêtres superposées.  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si les fenêtres superposées sont pris en charge ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Si les fenêtres superposées sont pris en charge, *ancrage actifs* marqueurs utilisent des fenêtres superposées.  
  
## <a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
Indique si l’infrastructure utilise des icônes de couleur 32 bits prédéfinies ou des icônes d’une résolution inférieure.  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>Notes  
 La valeur TRUE indique que le framework utilisent des icônes de couleur 32 bits ; La valeur FALSE indique les icônes de résolution inférieure. Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre sur TRUE.  
  
 Ce membre doit être défini au démarrage de l’application.  
  
## <a name="m_busesystemfont"></a> AFX_GLOBAL_DATA::m_bUseSystemFont
Indique si une police système est utilisée pour les menus, les barres d’outils et les rubans.  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>Notes  
 TRUE indique d’utiliser une police système ; Sinon, FALSE. Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre sur FALSE.  
  
 Test de ce membre n’est pas la seule façon de l’infrastructure pour déterminer la police à utiliser. Le `AFX_GLOBAL_DATA::UpdateFonts` méthode teste également des polices par défaut et de remplacement pour déterminer les styles visuels sont disponibles pour être appliqués à des menus, barres d’outils et les rubans.  
  
## <a name="m_hcurhand"></a> AFX_GLOBAL_DATA::m_hcurHand
Stocke le handle du curseur en forme de main.  
  
  
```  
HCURSOR m_hcurHand;  
```  
  
## <a name="m_hcurstretch"></a> AFX_GLOBAL_DATA::m_hcurStretch
Stocke le handle du curseur d’étirement horizontal.  
  
  
```  
HCURSOR m_hcurStretch;  
```  

## <a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA::m_hcurStretchVert
Stocke le handle du curseur d’étirement vertical.  
  
  
```  
HCURSOR m_hcurStretchVert;  
```  
  
## <a name="m_hicontool"></a> AFX_GLOBAL_DATA::m_hiconTool
Stocke le handle de l’icône d’outil.  
  
  
```  
HICON m_hiconTool;  
```  
## <a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
Spécifie l’offset à partir de la barre d’outils de masquage automatique à l’extrême gauche vers le côté gauche de la barre d’ancrage.  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>Notes  
 Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre de 4 pixels.  
  
## <a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
Spécifie l’intervalle entre les barres d’outils de masquage automatique.  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>Notes  
 Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre en 14 pixels.  
  
## <a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Spécifie l’épaisseur du cadre de glissement qui est utilisé pour indiquer l’état d’ancrage.  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>Notes  
 Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre de 3 pixels.  
  
## <a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
Spécifie l’épaisseur du cadre de glissement qui est utilisé pour indiquer l’état flottant.  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>Notes  
 Le `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructeur initialise ce membre de 4 pixels.  
  
## <a name="onsettingchange"></a> AFX_GLOBAL_DATA::OnSettingChange
Détecte l’état actuel des fonctionnalités de masquage automatique de la barre des tâches et de l’animation des menus du Bureau.  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode définit les variables de framework à l’état de certains attributs de bureau de l’utilisateur. Cette méthode détecte l’état actuel de l’animation de menu, une atténuation de menu et une tâche fonctionnalités de masquage automatique de la barre.  
  
## <a name="registerwindowclass"></a> AFX_GLOBAL_DATA::RegisterWindowClass
Inscrit la classe de fenêtre MFC spécifiée.  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>Paramètres   
 [in] *lpszClassNamePrefix*  
 Le nom de la classe de fenêtre à inscrire.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom qualifié de la classe inscrite si cette méthode réussit ; Sinon, un [exception de la ressource](http://msdn.microsoft.com/library/ddd99292-819b-4fa4-8371-b1954ed5856d).  
  
### <a name="remarks"></a>Notes  
 La valeur de retour est une liste délimitée par des deux-points de la *lpszClassNamePrefix* chaîne de paramètre et les représentations sous forme de texte hexadécimal des poignées de l’instance actuelle de l’application ; le curseur de l’application, c'est-à-dire la flèche curseur dont l’identificateur est IDC_ARROW ; et le pinceau d’arrière-plan. Pour plus d’informations sur l’inscription des classes de fenêtre MFC, consultez [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
### <a name="see-also"></a>Voir aussi    
 [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [AfxThrowResourceException](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a> AFX_GLOBAL_DATA::Resume
 Réinitialise les pointeurs de fonction internes qui accèdent à des méthodes qui prennent en charge des thèmes de Windows et les styles visuels. 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode réussit ; Sinon, FALSE. En mode débogage, cette méthode déclare si cette méthode est infructueuse.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsque l’infrastructure reçoit le [WM_POWERBROADCAST](http://msdn.microsoft.com/library/windows/desktop/aa373247) message.  
  
## <a name="setlayeredattrib"></a> AFX_GLOBAL_DATA::SetLayeredAttrib
Fournit un moyen simple d’appeler la méthode Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) .  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Paramètres   
 [in] *hwnd*  
 Handle de la fenêtre superposée.  
  
 [in] *crKey*  
 La couleur de transparence de clé qui le [Gestionnaire de fenêtrage](http://msdn.microsoft.com/library/windows/desktop/aa969540) utilise pour composer la fenêtre superposée.  
  
 [in] *bAlpha*  
 La valeur alpha est utilisée pour décrire l’opacité de la fenêtre superposée.  
  
 [in] *dwFlags*  
 Une combinaison (OR) au niveau du bit des indicateurs qui spécifient les paramètres de méthode à utiliser. Spécifiez LWA_COLORKEY à utiliser le *crKey* paramètre en tant que la couleur de transparence. Spécifiez LWA_ALPHA à utiliser le *bAlpha* paramètre pour déterminer l’opacité de la fenêtre superposée.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode réussit ; Sinon, FALSE.   
 
### <a name="see-also"></a>Voir aussi   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540)

## <a name="setmenufont"></a> AFX_GLOBAL_DATA::SetMenuFont
Crée la police logique spécifiée.  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres   
 [in] *lpLogFont*  
 Pointeur vers une structure qui contient les attributs d’une police.  
  
 [in] *bHorz*  
 TRUE pour spécifier que les séquences de texte horizontalement ; FALSE pour spécifier que les séquences de texte verticalement.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode réussit ; Sinon, FALSE. En mode débogage, cette méthode déclare si cette méthode est infructueuse.  
  
### <a name="remarks"></a>Notes  
 Cette méthode crée une police normale horizontale, une police soulignée, et une police en gras est utilisé par défaut des éléments de menu. Si vous le souhaitez, cette méthode crée une police verticale normale. Pour plus d’informations sur les polices logiques, consultez [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).  
  
## <a name="updatefonts"></a> AFX_GLOBAL_DATA::UpdateFonts
Réinitialise les polices logiques qui sont utilisées par l’infrastructure.  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les polices logiques, consultez `CFont::CreateFontIndirect`.  
  
## <a name="updatesyscolors"></a> AFX_GLOBAL_DATA::UpdateSysColors
Initialise les couleurs, la profondeur de couleur, les pinceaux, les stylets et les images qui sont utilisés par l’infrastructure.  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="biswindows7"></a> AFX_GLOBAL_DATA::bIsWindows7
Indique si l’application est en cours d’exécution sous Windows 7 ou version ultérieure.  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA::clrActiveCaptionGradient
Spécifie la couleur de dégradé de la légende active. Généralement utilisé pour les volets d’ancrage.  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA::clrInactiveCaptionGradient
Spécifie la couleur de la légende inactive. Généralement utilisé pour les volets d’ancrage.  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="getitaskbarlist"></a> AFX_GLOBAL_DATA::GetITaskbarList
Crée et stocke dans les données globales un pointeur vers le `ITaskBarList` interface.  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `ITaskbarList` interface si la création d’une tâche à l’objet de liste de la barre réussit ; NULL si la création échoue ou si le système d’exploitation actuel est inférieur à Windows 7.  
  
## <a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA::GetITaskbarList3
Crée et stocke dans les données globales un pointeur vers le `ITaskBarList3` interface.  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `ITaskbarList3` interface si la création d’une tâche à l’objet de liste de la barre réussit ; NULL si la création échoue ou si le système d’exploitation actuel est inférieur à Windows 7.  
  
## <a name="getshellautohidebars"></a> AFX_GLOBAL_DATA::GetShellAutohideBars
Détermine les positions des barres de masquage automatique de l’interpréteur de commandes.  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur entière avec des indicateurs encodées qui spécifient les positions d’auto masquer les barres. Il peut combiner les valeurs suivantes : AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.  
  
## <a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA::ReleaseTaskBarRefs
Libère les interfaces obtenues via le `GetITaskbarList` et `GetITaskbarList3` méthodes.  
  
  
```  
void ReleaseTaskBarRefs();
```  
  
## <a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
Crée et initialise un objet élément d’interpréteur de commandes à partir d’un nom de l’analyse.  
  
  
```  
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,  
    IBindCtx *pbc,  
    REFIID riid,  
    void **ppv);
```  
  
### <a name="parameters"></a>Paramètres   
 *pszPath*  
 [in] Pointeur vers un nom d’affichage.  
  
 *PBC*  
 Pointeur vers un contexte de liaison qui contrôle l’opération d’analyse.  
  
 *riid*  
 Une référence à un ID d’interface.  
  
 *PPV*  
 [out] Lorsque cette fonction est retournée, contient le pointeur d’interface demandé dans *riid*. Il s’agit généralement `IShellItem` ou `IShellItem2`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite ; une valeur d’erreur dans le cas contraire.  

