---
title: Classe CMFCBaseVisualManager
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
ms.openlocfilehash: ac64a3feac5d124c2bfa67fc857dad5045c2dd28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754888"
---
# <a name="cmfcbasevisualmanager-class"></a>Classe CMFCBaseVisualManager

Une couche entre les gestionnaires visuels dérivés et l’API thème Windows.

`CMFCBaseVisualManager`charge UxTheme.dll, si disponible, et gère l’accès aux méthodes d’API thème Windows.

Cette classe est pour un usage interne seulement.

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
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Dessine un contrôle de la case à cocher en utilisant le thème Windows actuel.|
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Dessine une bordure de boîte combo en utilisant le thème Windows actuel.|
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Dessine un bouton de dépose de boîte combo à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Dessine un bouton poussoir à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Dessine un contrôle de bouton radio en utilisant le thème Windows actuel.|
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Dessine une barre de progression sur un contrôle de barre d’état ( [classe CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) en utilisant le thème Windows actuel.|
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Remplit l’arrière-plan du contrôle des barres d’armature en utilisant le thème Windows actuel.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Obtient le thème Windows actuel.|

### <a name="protected-methods"></a>Méthodes protégées

|||
|-|-|
|Nom|Description|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Appels `CloseThemeData` pour toutes les `UpdateSystemColors`poignées obtenues en .|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Appels `OpenThemeData` pour obtenir des poignées pour dessiner différents contrôles: fenêtres, barres d’outils, boutons, et ainsi de suite.|

## <a name="remarks"></a>Notes

Vous n’avez pas à instantané les objets de cette classe directement.

Parce qu’il s’agit d’une classe de base pour tous les gestionnaires visuels, vous pouvez simplement appeler [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), obtenir un pointeur à l’actuel Visual Manager, et accéder aux méthodes pour `CMFCBaseVisualManager` l’utilisation de ce pointeur. Toutefois, si vous devez afficher un contrôle en utilisant le thème `CMFCVisualManagerWindows` Windows actuel, il est préférable d’utiliser l’interface.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxvisualmanager.h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes

Appels `CloseThemeData` pour toutes les `UpdateSystemColors`poignées obtenues en .

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>Notes

À usage interne uniquement.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager

Construit et initialise un objet `CMFCBaseVisualManager`.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox

Dessine un contrôle de la case à cocher en utilisant le thème Windows actuel.

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
[dans] Un pointeur vers un contexte d’appareil

*Rect*<br/>
[dans] Le rectangle de délimitation de la case à cocher.

*bHighlighted*<br/>
[dans] Précise si la case à cocher est mise en surbrillance.

*nState (États-Unis)*<br/>
[en] 0 pour non contrôlé, 1 pour vérifié normal,

2 pour la normale mixte.

*bEnabled*<br/>
[dans] Précise si la case à cocher est activée.

*bPressed (en)*<br/>
[dans] Précise si la case à cocher est pressée.

### <a name="return-value"></a>Valeur de retour

VRAI si l’API thème est activé; autrement FALSE.

### <a name="remarks"></a>Notes

Les valeurs de *nState* correspondent aux styles de case à cocher suivants.

|nState (États-Unis)|Style de boîte à cocher|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder

Dessine la bordure de la boîte combo en utilisant le thème Windows actuel.

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
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Rectangle de délimitation de la bordure de boîte de combo.

*bDissabled*<br/>
[dans] Précise si la bordure de la boîte combo est désactivée.

*bIsDropped*<br/>
[dans] Précise si la bordure de la boîte combo est tombée vers le bas.

*bIsHighlighted*<br/>
[dans] Précise si la bordure de la boîte combo est mise en évidence.

### <a name="return-value"></a>Valeur de retour

VRAI si l’API thème est activé; autrement FALSE.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton

Dessine un bouton de dépose de boîte combo à l’aide du thème Windows actuel.

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
|*pDC*|[dans] Un pointeur vers un contexte d’appareil.|
|*Rect*|[dans] Le rectangle de délimitation du bouton de chute de la boîte combo.|
|*bDissabled*|[dans] Précise si le bouton de drop-down de la boîte combo est désactivé.|
|*bIsDropped*|[dans] Précise si le bouton de chute de la boîte combo est tombé vers le bas.|
|*bIsHighlighted*|[dans] Précise si le bouton de drop-down de la boîte combo est mis en surbrillance.|

### <a name="return-value"></a>Valeur de retour

VRAI si l’API thème est activé; autrement FALSE.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton

Dessine un bouton poussoir à l’aide du thème Windows actuel.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Le rectangle de délimitation du bouton poussoir.

*pButton*<br/>
[dans] Un pointeur à l’objet [cmFCButton Classe](../../mfc/reference/cmfcbutton-class.md) à dessiner.

*uiState (uiState)*<br/>
[dans] Ignoré. L’état est pris de *pButton*.

### <a name="return-value"></a>Valeur de retour

VRAI si l’API thème est activé; autrement FALSE.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton

Dessine un contrôle de bouton radio en utilisant le thème Windows actuel.

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
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Le rectangle de délimitation du bouton radio.

*bHighlighted*<br/>
[dans] Précise si le bouton radio est mis en surbrillance.

*bChecked*<br/>
[dans] Précise si le bouton radio est vérifié.

*bEnabled*<br/>
[dans] Précise si le bouton radio est activé.

*bPressed (en)*<br/>
[dans] Précise si le bouton radio est appuyé.

### <a name="return-value"></a>Valeur de retour

VRAI si l’API thème est activé; autrement FALSE.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress

Dessine la barre de progression sur le contrôle des barres d’état ( [classe CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) en utilisant le thème Windows actuel.

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
[dans] Un pointeur vers un contexte d’appareil.

*pStatusBar*<br/>
[dans] Un pointeur à la barre de statut. Cette valeur est ignorée.

*rectProgresse*<br/>
[dans] Le rectangle de délimitation de la barre de progression dans les coordonnées *pDC.*

*nProgressTotal*<br/>
[dans] La valeur totale de progression.

*nProgressCurr*<br/>
[dans] La valeur actuelle des progrès.

*clrBar*<br/>
[dans] La couleur de départ. `CMFCBaseVisualManager`ignore cela. Les classes dérivées peuvent l’utiliser pour les gradients de couleur.

*clrProgressBarDest*<br/>
[dans] La couleur de fin. `CMFCBaseVisualManager`ignore cela. Les classes dérivées peuvent l’utiliser pour les gradients de couleur.

*clrProgressText*<br/>
[dans] Progrès de la couleur du texte. `CMFCBaseVisualManager`ignore cela. La couleur du `afxGlobalData.clrBtnText`texte est définie par .

*bProgressText*<br/>
[dans] Précise s’il faut afficher le texte de progression.

### <a name="return-value"></a>Valeur de retour

VRAI si l’API thème est activé; autrement FALSE.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBaseVisualManager::FillReBarPane

Remplit l’arrière-plan du contrôle des barres d’armature en utilisant le thème Windows actuel.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*pBar (pBar)*<br/>
[dans] Un pointeur à une vitre dont l’arrière-plan doit être dessiné.

*rectClient*<br/>
[dans] Le rectangle de délimitation de la zone à remplir.

### <a name="return-value"></a>Valeur de retour

VRAI si l’API thème est activé; autrement FALSE.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme

Obtient le thème Windows actuel.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Valeur de retour

La couleur Windows Theme actuellement sélectionnée. Peut être l’une des valeurs énumérées suivantes :

- `WinXpTheme_None`- il n’y a pas de thème activé.

- `WinXpTheme_NonStandard`- le thème non standard est choisi (ce qui signifie qu’un thème est choisi, mais aucun de la liste ci-dessous).

- `WinXpTheme_Blue`- thème bleu (Luna).

- `WinXpTheme_Olive`- thème olive.

- `WinXpTheme_Silver`- thème argenté.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors

Appels `OpenThemeData` pour obtenir des poignées pour dessiner différents contrôles: fenêtres, barres d’outils, boutons, et ainsi de suite.

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>Notes

À usage interne uniquement.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
