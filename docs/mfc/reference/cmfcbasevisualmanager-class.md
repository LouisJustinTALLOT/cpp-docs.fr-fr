---
title: CMFCBaseVisualManager, classe
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
ms.openlocfilehash: 28efe75c3c825c04c88f9f2263a3db2d83d4f3af
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561321"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager, classe

Couche entre les gestionnaires visuels dérivés et l’API de thème Windows.

`CMFCBaseVisualManager` charge UxTheme.dll, le cas échéant, et gère l’accès aux méthodes de l’API de thème Windows.

Cette classe est destinée à un usage interne uniquement.

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
|[CMFCBaseVisualManager ::D rawCheckBox](#drawcheckbox)|Dessine un contrôle de case à cocher en utilisant le thème Windows actuel.|
|[CMFCBaseVisualManager ::D rawComboBorder](#drawcomboborder)|Dessine une bordure de zone de liste déroulante à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager ::D rawComboDropButton](#drawcombodropbutton)|Dessine un bouton déroulant de zone de liste déroulante à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager ::D rawPushButton](#drawpushbutton)|Dessine un bouton de commande à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager ::D rawRadioButton](#drawradiobutton)|Dessine un contrôle de case d’option à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager ::D rawStatusBarProgress](#drawstatusbarprogress)|Dessine une barre de progression sur un contrôle de barre d’État ( [classe CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Remplit l’arrière-plan du contrôle rebar à l’aide du thème Windows actuel.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Obtient le thème Windows actuel.|

### <a name="protected-methods"></a>Méthodes protégées

|||
|-|-|
|Nom|Description|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Appelle `CloseThemeData` pour tous les handles obtenus dans `UpdateSystemColors` .|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Appelle `OpenThemeData` pour obtenir des handles pour le dessin de différents contrôles : fenêtres, barres d’outils, boutons, etc.|

## <a name="remarks"></a>Notes

Vous n’avez pas besoin d’instancier directement des objets de cette classe.

Étant donné qu’il s’agit d’une classe de base pour tous les gestionnaires visuels, vous pouvez simplement appeler [CMFCVisualManager :: GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), obtenir un pointeur vers le gestionnaire visuel actuel et accéder aux méthodes pour `CMFCBaseVisualManager` utiliser ce pointeur. Toutefois, si vous devez afficher un contrôle à l’aide du thème Windows actuel, il est préférable d’utiliser l' `CMFCVisualManagerWindows` interface.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxvisualmanager. h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a> CMFCBaseVisualManager::CleanUpThemes

Appelle `CloseThemeData` pour tous les handles obtenus dans `UpdateSystemColors` .

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>Notes

Uniquement réservé à un usage interne.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a> CMFCBaseVisualManager::CMFCBaseVisualManager

Construit et initialise un objet `CMFCBaseVisualManager`.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a> CMFCBaseVisualManager ::D rawCheckBox

Dessine un contrôle de case à cocher en utilisant le thème Windows actuel.

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

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context)

*rectangulaire*<br/>
dans Rectangle englobant de la case à cocher.

*bHighlighted*<br/>
dans Spécifie si la case à cocher est mise en surbrillance.

*nState*<br/>
[in] 0 pour désactivé, 1 pour vérifié normal,

2 pour la normale mixte.

*bEnabled*<br/>
dans Spécifie si la case à cocher est activée.

*bPressed*<br/>
dans Spécifie si la case à cocher est activée.

### <a name="return-value"></a>Valeur de retour

TRUE si l’API de thème est activée ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Les valeurs de *nState* correspondent aux styles de case à cocher suivants.

|nState|Style de case à cocher|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a> CMFCBaseVisualManager ::D rawComboBorder

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

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectangulaire*<br/>
dans Rectangle englobant de la bordure de zone de liste déroulante.

*bDisabled*<br/>
dans Spécifie si la bordure de zone de liste déroulante est désactivée.

*bIsDropped*<br/>
dans Spécifie si la bordure de zone de liste déroulante est déroulée.

*bIsHighlighted*<br/>
dans Spécifie si la bordure de zone de liste déroulante est mise en surbrillance.

### <a name="return-value"></a>Valeur de retour

TRUE si l’API de thème est activée ; Sinon, FALSe.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a> CMFCBaseVisualManager ::D rawComboDropButton

Dessine un bouton déroulant de zone de liste déroulante à l’aide du thème Windows actuel.

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Paramètres

*Maîtres*\
dans Pointeur vers un contexte de périphérique (Device Context).

*rectangulaire*\
dans Rectangle englobant du bouton déroulant de la zone de liste déroulante.

*bDisabled*\
dans Spécifie si le bouton de liste déroulante de la zone de liste déroulante est désactivé.

*bIsDropped*\
dans Spécifie si le bouton déroulant de la zone de liste déroulante est supprimé.

*bIsHighlighted*\
dans Spécifie si le bouton déroulant de la zone de liste déroulante est mis en surbrillance.

### <a name="return-value"></a>Valeur de retour

TRUE si l’API de thème est activée ; Sinon, FALSe.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a> CMFCBaseVisualManager ::D rawPushButton

Dessine un bouton de commande à l’aide du thème Windows actuel.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectangulaire*<br/>
dans Rectangle englobant du bouton de commande.

*pButton*<br/>
dans Pointeur vers l’objet de [classe CMFCButton](../../mfc/reference/cmfcbutton-class.md) à dessiner.

*uiState*<br/>
dans Pas. L’État est extrait de *pButton*.

### <a name="return-value"></a>Valeur de retour

TRUE si l’API de thème est activée ; Sinon, FALSe.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a> CMFCBaseVisualManager ::D rawRadioButton

Dessine un contrôle de case d’option à l’aide du thème Windows actuel.

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

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectangulaire*<br/>
dans Rectangle englobant de la case d’option.

*bHighlighted*<br/>
dans Spécifie si la case d’option est mise en surbrillance.

*bChecked*<br/>
dans Spécifie si la case d’option est activée.

*bEnabled*<br/>
dans Spécifie si la case d’option est activée.

*bPressed*<br/>
dans Spécifie si la case d’option est activée.

### <a name="return-value"></a>Valeur de retour

TRUE si l’API de thème est activée ; Sinon, FALSe.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a> CMFCBaseVisualManager ::D rawStatusBarProgress

Dessine la barre de progression sur le contrôle de barre d’État ( [classe CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) à l’aide du thème Windows actuel.

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

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*pStatusBar*<br/>
dans Pointeur vers la barre d’État. Cette valeur est ignorée.

*rectProgress*<br/>
dans Rectangle englobant de la barre de progression dans les coordonnées *PDC* .

*nProgressTotal*<br/>
dans Valeur de progression totale.

*nProgressCurr*<br/>
dans Valeur de progression actuelle.

*clrBar*<br/>
dans Couleur de début. `CMFCBaseVisualManager` ignore ce. Les classes dérivées peuvent l’utiliser pour les dégradés de couleur.

*clrProgressBarDest*<br/>
dans Couleur de fin. `CMFCBaseVisualManager` ignore ce. Les classes dérivées peuvent l’utiliser pour les dégradés de couleur.

*clrProgressText*<br/>
dans Couleur du texte de progression. `CMFCBaseVisualManager` ignore ce. La couleur du texte est définie par `afxGlobalData.clrBtnText` .

*bProgressText*<br/>
dans Spécifie s’il faut afficher le texte de progression.

### <a name="return-value"></a>Valeur de retour

TRUE si l’API de thème est activée ; Sinon, FALSe.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a> CMFCBaseVisualManager::FillReBarPane

Remplit l’arrière-plan du contrôle rebar à l’aide du thème Windows actuel.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*pBar*<br/>
dans Pointeur vers un volet dont l’arrière-plan doit être dessiné.

*rectClient*<br/>
dans Rectangle englobant de la zone à remplir.

### <a name="return-value"></a>Valeur de retour

TRUE si l’API de thème est activée ; Sinon, FALSe.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a> CMFCBaseVisualManager::GetStandardWindowsTheme

Obtient le thème Windows actuel.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Valeur de retour

Couleur de thème Windows actuellement sélectionnée. Il peut s’agir de l’une des valeurs énumérées suivantes :

- `WinXpTheme_None` -aucun thème n’est activé.

- `WinXpTheme_NonStandard` -le thème non standard est sélectionné (ce qui signifie qu’un thème est sélectionné, mais aucun n’est répertorié dans la liste ci-dessous).

- `WinXpTheme_Blue` -thème bleu (Luna).

- `WinXpTheme_Olive` -Thème olive.

- `WinXpTheme_Silver` -Thème Silver.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a> CMFCBaseVisualManager::UpdateSystemColors

Appelle `OpenThemeData` pour obtenir des handles pour le dessin de différents contrôles : fenêtres, barres d’outils, boutons, etc.

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>Notes

Uniquement réservé à un usage interne.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
