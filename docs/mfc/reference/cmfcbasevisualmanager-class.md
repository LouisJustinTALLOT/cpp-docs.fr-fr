---
title: Cmfcbasevisualmanager, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 0c26c0c9c9026f8312218b2ac15f83a50a67be79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403852"
---
# <a name="cmfcbasevisualmanager-class"></a>Cmfcbasevisualmanager, classe

Une couche entre dérivée gestionnaires visuels et de l’API de thème Windows.

`CMFCBaseVisualManager` charge UxTheme.dll, s’il est disponible et gère l’accès aux méthodes d’API de thème Windows.

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
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Dessine un contrôle de case à cocher à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Dessine une bordure de zone de liste déroulante à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Dessine un bouton de liste déroulante de zone de liste déroulante à l’aide du thème actuel de Windows.|
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Dessine un bouton de commande à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Dessine un contrôle case d’option à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Dessine une barre de progression sur un contrôle de barre d’état ( [cmfcstatusbar, classe](../../mfc/reference/cmfcstatusbar-class.md)) à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Remplit l’arrière-plan du contrôle rebar en utilisant le thème Windows actuel.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Obtient le thème Windows en cours.|

### <a name="protected-methods"></a>Méthodes protégées

|||
|-|-|
|Nom|Description|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Appels `CloseThemeData` pour tous les handles obtenu dans `UpdateSystemColors`.|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Appels `OpenThemeData` pour obtenir des handles pour divers contrôles de dessin : windows, des barres d’outils, des boutons et ainsi de suite.|

## <a name="remarks"></a>Notes

Il est inutile d’instancier directement des objets de cette classe.

S’agissant d’une classe de base pour tous les gestionnaires visuels, vous pouvez simplement appeler [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), obtenir un pointeur pour le Gestionnaire visuel actuel et accéder aux méthodes pour `CMFCBaseVisualManager` à l’aide de ce pointeur. Toutefois, si vous devez afficher un contrôle à l’aide du thème Windows actuel, il est préférable d’utiliser le `CMFCVisualManagerWindows` interface.

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

Dessine un contrôle de case à cocher à l’aide du thème Windows actuel.

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

*pDC*<br/>
[in] Un pointeur vers un contexte de périphérique

*rect*<br/>
[in] Le rectangle englobant de la case à cocher.

*bHighlighted*<br/>
[in] Spécifie si la case à cocher est mis en surbrillance.

*nState*<br/>
[in] 0 pour non coché, 1 pour normal activé,

2 pour mixte normal.

*bEnabled*<br/>
[in] Spécifie si la case à cocher est activée.

*bPressed*<br/>
[in] Spécifie si la case à cocher est activée.

### <a name="return-value"></a>Valeur de retour

TRUE si les API de thème est activé ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Les valeurs de *nState* correspondent aux styles de case à cocher suivantes.

|nState|Style de case à cocher|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

##  <a name="drawcomboborder"></a>  CMFCBaseVisualManager::DrawComboBorder

Dessine la bordure de zone de liste déroulante à l’aide du thème Windows actuel.

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*rect*<br/>
[in] Rectangle englobant de la bordure de zone de liste déroulante.

*bDisabled*<br/>
[in] Spécifie si la bordure de zone de liste déroulante est désactivée.

*bIsDropped*<br/>
[in] Spécifie si la bordure de zone de liste déroulante est déroulée.

*bIsHighlighted*<br/>
[in] Spécifie si la bordure de zone de liste déroulante est mis en surbrillance.

### <a name="return-value"></a>Valeur de retour

TRUE si les API de thème est activé ; Sinon, FALSE.

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
|*pDC*|[in] Pointeur vers un contexte de périphérique.|
|*rect*|[in] Le rectangle englobant de bouton de liste déroulante de zone de liste déroulante.|
|*bDisabled*|[in] Spécifie si le bouton de liste déroulante de zone de liste déroulante est désactivé.|
|*bIsDropped*|[in] Spécifie si le bouton de liste déroulante de zone de liste déroulante est déroulé.|
|*bIsHighlighted*|[in] Spécifie si le bouton de liste déroulante de zone de liste déroulante est mis en surbrillance.|

### <a name="return-value"></a>Valeur de retour

TRUE si les API de thème est activé ; Sinon, FALSE.

##  <a name="drawpushbutton"></a>  CMFCBaseVisualManager::DrawPushButton

Dessine un bouton de commande à l’aide du thème Windows actuel.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*rect*<br/>
[in] Le rectangle englobant du bouton push.

*pButton*<br/>
[in] Un pointeur vers le [cmfcbutton, classe](../../mfc/reference/cmfcbutton-class.md) objet sur lequel dessiner.

*uiState*<br/>
[in] Ignoré. L’état est extraite *pButton*.

### <a name="return-value"></a>Valeur de retour

TRUE si les API de thème est activé ; Sinon, FALSE.

##  <a name="drawradiobutton"></a>  CMFCBaseVisualManager::DrawRadioButton

Dessine un contrôle case d’option à l’aide du thème Windows actuel.

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

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*rect*<br/>
[in] Le rectangle englobant de la case.

*bHighlighted*<br/>
[in] Spécifie si la case d’option est mis en surbrillance.

*bChecked*<br/>
[in] Spécifie si la case d’option est activée.

*bEnabled*<br/>
[in] Spécifie si la case d’option est activée.

*bPressed*<br/>
[in] Spécifie si la case d’option est enfoncée.

### <a name="return-value"></a>Valeur de retour

TRUE si les API de thème est activé ; Sinon, FALSE.

##  <a name="drawstatusbarprogress"></a>  CMFCBaseVisualManager::DrawStatusBarProgress

Dessine la barre de progression sur le contrôle de barre d’état ( [cmfcstatusbar, classe](../../mfc/reference/cmfcstatusbar-class.md)) à l’aide du thème Windows actuel.

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

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*pStatusBar*<br/>
[in] Pointeur vers la barre d’état. Cette valeur est ignorée.

*rectProgress*<br/>
[in] Le rectangle englobant de la barre de progression dans *pDC* coordonnées.

*nProgressTotal*<br/>
[in] La valeur de progression totale.

*nProgressCurr*<br/>
[in] La valeur de progression actuel.

*clrBar*<br/>
[in] La couleur de début. `CMFCBaseVisualManager` il ignore. Les classes dérivées peuvent utiliser pour les dégradés de couleur.

*clrProgressBarDest*<br/>
[in] Couleur de fin. `CMFCBaseVisualManager` il ignore. Les classes dérivées peuvent utiliser pour les dégradés de couleur.

*clrProgressText*<br/>
[in] Couleur du texte de progression. `CMFCBaseVisualManager` il ignore. La couleur du texte est définie par `afxGlobalData.clrBtnText`.

*bProgressText*<br/>
[in] Spécifie s’il faut afficher le texte de progression.

### <a name="return-value"></a>Valeur de retour

TRUE si les API de thème est activé ; Sinon, FALSE.

##  <a name="fillrebarpane"></a>  CMFCBaseVisualManager::FillReBarPane

Remplit l’arrière-plan du contrôle rebar en utilisant le thème Windows actuel.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique.

*pBar*<br/>
[in] Pointeur vers un volet dont l’arrière-plan doit être dessiné.

*rectClient*<br/>
[in] Le rectangle englobant de la zone à remplir.

### <a name="return-value"></a>Valeur de retour

TRUE si les API de thème est activé ; Sinon, FALSE.

##  <a name="getstandardwindowstheme"></a>  CMFCBaseVisualManager::GetStandardWindowsTheme

Obtient le thème Windows en cours.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Valeur de retour

La couleur de thème de Windows actuellement sélectionnée. Peut être une des valeurs énumérées suivantes :

- `WinXpTheme_None` -Il n’existe aucun thème activé.

- `WinXpTheme_NonStandard` -thème non standard est sélectionné (ce qui signifie qu’un thème est sélectionné, mais aucun dans la liste ci-dessous).

- `WinXpTheme_Blue` -le thème bleu (Luna).

- `WinXpTheme_Olive` -thème olive.

- `WinXpTheme_Silver` -Thème argent.

##  <a name="updatesystemcolors"></a>  CMFCBaseVisualManager::UpdateSystemColors

Appels `OpenThemeData` pour obtenir des handles pour divers contrôles de dessin : windows, des barres d’outils, des boutons et ainsi de suite.

```
void UpdateSystemColors();
```

### <a name="remarks"></a>Notes

Uniquement réservé à un usage interne.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
