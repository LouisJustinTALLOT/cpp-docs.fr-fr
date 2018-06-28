---
title: Classe de CMFCBaseVisualManager | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b18eef5b828577f6d77846a5e9e231dcf828332
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040725"
---
# <a name="cmfcbasevisualmanager-class"></a>Classe de CMFCBaseVisualManager
Une couche entre dérivée gestionnaires visuels et de l’API de thème Windows.  
  
 `CMFCBaseVisualManager` charge UxTheme.dll, s’il est disponible et gère l’accès aux méthodes de l’API de thème Windows.  
  
 Cette classe est à usage interne uniquement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Construit et initialise un objet `CMFCBaseVisualManager`.|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Dessine un contrôle de case à cocher à l’aide du thème actuel de Windows.|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Dessine une bordure de zone de liste déroulante à l’aide du thème actuel de Windows.|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Dessine un bouton de liste déroulante de zone de liste déroulante à l’aide du thème actuel de Windows.|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Dessine un bouton de commande à l’aide du thème actuel de Windows.|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Dessine un contrôle case d’option à l’aide du thème actuel de Windows.|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Dessine une barre de progression sur un contrôle de barre d’état ( [CMFCStatusBar classe](../../mfc/reference/cmfcstatusbar-class.md)) à l’aide du thème actuel de Windows.|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Remplit l’arrière-plan du contrôle rebar à l’aide du thème actuel de Windows.|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Obtient le thème actuel de Windows.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Appels `CloseThemeData` pour tous les handles obtenu dans `UpdateSystemColors`.|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Appels `OpenThemeData` pour obtenir des handles pour les différents contrôles de dessin : windows, des barres d’outils, des boutons et ainsi de suite.|  
  
## <a name="remarks"></a>Notes  
 Vous n’avez pas instancier directement des objets de cette classe.  
  
 S’agissant d’une classe de base pour tous les gestionnaires visuels, vous pouvez simplement appeler [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), obtenir un pointeur vers le gestionnaire Visual actuel et accéder aux méthodes de `CMFCBaseVisualManager` à l’aide de ce pointeur. Toutefois, si vous disposez d’un contrôle à l’aide du thème actuel de Windows, il est préférable d’utiliser le `CMFCVisualManagerWindows` interface.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxvisualmanager.h  
  
##  <a name="cleanupthemes"></a>  CMFCBaseVisualManager::CleanUpThemes  
 Appels `CloseThemeData` pour tous les handles obtenu dans `UpdateSystemColors`.  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>Notes  
 Uniquement réservé à un usage interne.  
  
##  <a name="cmfcbasevisualmanager"></a>  CMFCBaseVisualManager::CMFCBaseVisualManager  
 Construit et initialise un objet `CMFCBaseVisualManager`.  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="drawcheckbox"></a>  CMFCBaseVisualManager::DrawCheckBox  
 Dessine un contrôle de case à cocher à l’aide du thème actuel de Windows.  
  
```  
virtual BOOL DrawCheckBox(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    int nState,   
    BOOL bEnabled,   
    BOOL bPressed);

);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Un pointeur vers un contexte de périphérique  
  
 [in] *rect*  
 Le rectangle englobant de la case à cocher.  
  
 [in] *bHighlighted*  
 Spécifie si la case à cocher est mis en surbrillance.  
  
 [in] *nState*  
 0 pour est désactivé, 1 pour activé normal,  
  
 2 pour mixte normal.  
  
 [in] *case d’option bActivé*  
 Spécifie si la case à cocher est activée.  
  
 [in] *bPressed*  
 Spécifie si la case à cocher est activée.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le thème API est activée ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Les valeurs de *nState* correspondent aux styles de case à cocher suivante.  
  
|nState|Style de la case à cocher|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="drawcomboborder"></a>  CMFCBaseVisualManager::DrawComboBorder  
 Dessine la bordure de zone de liste déroulante à l’aide du thème actuel de Windows.  
  
```  
virtual BOOL DrawComboBorder(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *rect*  
 Rectangle englobant de la bordure de zone de liste déroulante.  
  
 [in] *bDésactiver*  
 Spécifie si la bordure de zone de liste déroulante est désactivée.  
  
 [in] *bIsDropped*  
 Spécifie si la bordure de zone de liste déroulante est déroulée.  
  
 [in] *bIsHighlighted*  
 Spécifie si la bordure de zone de liste déroulante est mis en surbrillance.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le thème API est activée ; dans le cas contraire `FALSE`.  
  
##  <a name="drawcombodropbutton"></a>  CMFCBaseVisualManager::DrawComboDropButton  
 Dessine un bouton de liste déroulante de zone de liste déroulante à l’aide du thème actuel de Windows.  
  
```  
virtual BOOL DrawComboDropButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *contrôleur de domaine principal*|Pointeur vers un contexte de périphérique.|  
|[in] *rect*|Le rectangle englobant du bouton de liste déroulante de zone de liste déroulante.|  
|[in] *bDésactiver*|Spécifie si le bouton de liste déroulante de zone de liste déroulante est désactivé.|  
|[in] *bIsDropped*|Spécifie si le bouton de liste déroulante de zone de liste déroulante est déroulé.|  
|[in] *bIsHighlighted*|Spécifie si le bouton de liste déroulante de zone de liste déroulante est mis en surbrillance.|  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le thème API est activée ; dans le cas contraire `FALSE`.  
  
##  <a name="drawpushbutton"></a>  CMFCBaseVisualManager::DrawPushButton  
 Dessine un bouton de commande à l’aide du thème actuel de Windows.  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *rect*  
 Le rectangle englobant du bouton push.  
  
 [in] *pButton*  
 Un pointeur vers le [CMFCButton classe](../../mfc/reference/cmfcbutton-class.md) objet à dessiner.  
  
 [in] *uiState*  
 Ignoré. L’état est extraite *pButton*.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le thème API est activée ; dans le cas contraire `FALSE`.  
  
##  <a name="drawradiobutton"></a>  CMFCBaseVisualManager::DrawRadioButton  
 Dessine un contrôle case d’option à l’aide du thème actuel de Windows.  
  
```  
virtual BOOL DrawRadioButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    BOOL bChecked,   
    BOOL bEnabled,   
    BOOL bPressed);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *rect*  
 Le rectangle englobant de la case d’option.  
  
 [in] *bHighlighted*  
 Spécifie si la case d’option est mis en surbrillance.  
  
 [in] *bChecked*  
 Spécifie si la case d’option est activée.  
  
 [in] *case d’option bActivé*  
 Spécifie si la case d’option est activée.  
  
 [in] *bPressed*  
 Spécifie si la case d’option est activée.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le thème API est activée ; dans le cas contraire `FALSE`.  
  
##  <a name="drawstatusbarprogress"></a>  CMFCBaseVisualManager::DrawStatusBarProgress  
 Dessine la barre de progression sur le contrôle de barre d’état ( [CMFCStatusBar classe](../../mfc/reference/cmfcstatusbar-class.md)) à l’aide du thème actuel de Windows.  
  
```  
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,   
    CMFCStatusBar* pStatusBar,   
    CRect rectProgress,   
    int nProgressTotal,   
    int nProgressCurr,  
    COLORREF clrBar,   
    COLORREF clrProgressBarDest,   
    COLORREF clrProgressText,   
    BOOL bProgressText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *pStatusBar*  
 Pointeur vers la barre d’état. Cette valeur est ignorée.  
  
 [in] *rectProgress*  
 Le rectangle englobant de la barre de progression dans *pDC* coordonnées.  
  
 [in] *nProgressTotal*  
 La valeur de l’avancement total.  
  
 [in] *nProgressCurr*  
 La valeur de progression actuel.  
  
 [in] *clrBar*  
 La couleur de début. `CMFCBaseVisualManager` il ignore. Les classes dérivées peuvent utiliser pour les dégradés de couleur.  
  
 [in] *clrProgressBarDest*  
 Couleur de fin. `CMFCBaseVisualManager` il ignore. Les classes dérivées peuvent utiliser pour les dégradés de couleur.  
  
 [in] *clrProgressText*  
 Couleur du texte de progression. `CMFCBaseVisualManager` il ignore. La couleur du texte est définie par `afxGlobalData.clrBtnText`.  
  
 [in] *bProgressText*  
 Spécifie s’il faut afficher le texte de progression.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le thème API est activée ; dans le cas contraire `FALSE`.  
  
##  <a name="fillrebarpane"></a>  CMFCBaseVisualManager::FillReBarPane  
 Remplit l’arrière-plan du contrôle rebar à l’aide du thème actuel de Windows.  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *pBar*  
 Pointeur vers un volet dont en arrière-plan doit être dessiné.  
  
 [in] *rectClient*  
 Le rectangle englobant de la zone à remplir.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le thème API est activée ; dans le cas contraire `FALSE`.  
  
##  <a name="getstandardwindowstheme"></a>  CMFCBaseVisualManager::GetStandardWindowsTheme  
 Obtient le thème actuel de Windows.  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur de thème Windows actuellement sélectionnée. Peut être une des valeurs énumérées suivantes :  
  
- `WinXpTheme_None` -Il n’existe aucun thème activée.  
  
- `WinXpTheme_NonStandard` -thème non standard est sélectionné (ce qui signifie un thème est sélectionné, mais aucun dans la liste ci-dessous).  
  
- `WinXpTheme_Blue` -le thème bleu (Luna).  
  
- `WinXpTheme_Olive` -olive thème.  
  
- `WinXpTheme_Silver` -Thème argent.  
  
##  <a name="updatesystemcolors"></a>  CMFCBaseVisualManager::UpdateSystemColors  
 Appels `OpenThemeData` pour obtenir des handles pour les différents contrôles de dessin : windows, des barres d’outils, des boutons et ainsi de suite.  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>Notes  
 Uniquement réservé à un usage interne.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
