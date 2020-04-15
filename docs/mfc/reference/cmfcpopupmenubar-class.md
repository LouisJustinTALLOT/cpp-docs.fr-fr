---
title: CMFCPopupMenuBar, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: b4693e316fd78948cfae262433fee8ca8b6ab23c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375360"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar, classe

Barre de menus incorporée dans un menu contextuel.

## <a name="syntax"></a>Syntaxe

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Réacalcule immédiatement la disposition d’une vitre. (Overrides [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Charge les éléments du menu popup à partir d’une ressource de menu spécifiée.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Ferme un bouton de menu popup retardé.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Construit un menu à partir des boutons popup-menu.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Localise la barre d’outils où se trouve un point spécifié.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Indique la taille des images bouton-menu.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Retourne l’identifiant de l’élément de menu par défaut.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Obtient l’index de la commande de menu la plus récemment invoquée.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Obtient le décalage de ligne de la barre de menu popup.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importe les boutons du menu popup à partir d’un menu spécifié.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Indique si la barre de menu popup est en mode drop-down-list.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Indique si la barre de menu popup est en mode palette.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Indique s’il s’agit d’un panneau ruban (FALSE par défaut).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Indique s’il s’agit d’un panneau ruban en mode régulier (FALSE par défaut).|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Charge un menu archivé.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Restaure un bouton de menu retardé pour fermer la barre de menu popup.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Définit le style du bouton de la barre d’outils à l’index donné. (Overrides [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Définit le décalage de ligne de la barre de menu popup.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Démarre la minuterie pour un bouton de menu popup retardé spécifié.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCPopupMenuBar:m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Précise si la barre latérale grise sera affichée lorsque l’application a une apparence Windows XP.|

## <a name="remarks"></a>Notes

Le `CMFCPopupMenuBar` est créé en même temps qu’une [classe CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) et intégré à l’intérieur. Le `CMFCPopupMenuBar` couvre toute la `CMFCPopupMenu` zone client de l’objet. Il prend en charge l’entrée du clavier et de la souris. Il communique également cette `CMFCPopupMenu` entrée à la fenêtre de cadre de haut niveau et à celle du haut niveau.

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCPopupMenuBar` initialiser `CMFCPopupMenu` un objet à partir d’un objet. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpopupmenubar.h

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a>CMFCPopupMenuBar::AdjustSizeImmediate

Réacalcule immédiatement la disposition de la vitre du menu popup bar. (Overrides [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Paramètres

*bRecalcLayout (en)*<br/>
[dans] VRAI pour recalculer automatiquement la disposition de la vitre du menu popup barre; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a>CMFCPopupMenuBar::BuildOrigItems

Charge les éléments du menu popup à partir d’une ressource de menu spécifiée.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Paramètres

*uiMenuResID*<br/>
[dans] Spécifie l’ID du menu de la ressource du menu à charger.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI en cas de succès ou DE FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a>CMFCPopupMenuBar::CloseDelayedSubMenu

Ferme un bouton de menu popup qui a été retardé.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a>CMFCPopupMenuBar::ExportToMenu

Construit un menu à partir des boutons du menu popup.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne une poignée au nouveau menu.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a>CMFCPopupMenuBar::FindDestintationToolBar

Localise la barre d’outils où se trouve un point spécifié.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
[dans] Un point à l’écran.

### <a name="return-value"></a>Valeur de retour

Retourne une poignée à la barre d’outils où le point se trouve, s’il y en a un, ou NULL sinon.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a>CMFCPopupMenuBar::GetCurrentMenuImageSize

Indique la taille des images bouton-menu.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la taille des images bouton de menu dans la barre d’outils.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a>CMFCPopupMenuBar::GetDefaultMenuId

Retourne l’identifiant de l’élément de menu par défaut.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’identifiant de l’élément de menu par défaut dans la barre de menu popup.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a>CMFCPopupMenuBar::GetLastCommandIndex

Obtient l’index de la commande de menu la plus récemment invoquée.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’index de la dernière commande de menu qui a été invoquée.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a>CMFCPopupMenuBar::GetOffset

Obtient le décalage de ligne de la barre de menu popup.

```
int GetOffset() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le décalage de ligne de la barre de menu popup.

### <a name="remarks"></a>Notes

Cette valeur est définie à l’aide [de CMFCPopupMenuBar:SetOffset](#setoffset).

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a>CMFCPopupMenuBar::ImportDeMenu

Importe les boutons du menu popup à partir d’un menu spécifié.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
[dans] Le menu à partir duquel importer les boutons du menu popup.

*bShowAllCommands (en)*<br/>
[dans] VRAI si toutes les commandes sur le menu doivent être importées, ou FALSE si rarement utilisées peuvent être cachées.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si les boutons du menu ont été importés avec succès du menu, ou FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a>CMFCPopupMenuBar::IsDropDownListMode

Indique si la barre de menu popup est en mode drop-down-list.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la barre de menu popup est en mode drop-down-list, ou FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a>CMFCPopupMenuBar::IsPaletteMode

Indique si la barre de menu popup est en mode palette.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le mode palette est activé, ou FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

Lorsque la barre de menu est réglée en mode palette, les éléments du menu apparaissent dans plusieurs colonnes et un nombre limité de lignes.

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a>CMFCPopupMenuBar::IsRibbonPanel

Indique s’il s’agit d’un panneau ruban (FALSE par défaut).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne FALSE par défaut, indiquant qu’il ne s’agit pas d’un panneau ruban.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a>CMFCPopupMenuBar::IsRibbonPanelInRegularMode

Indique s’il s’agit d’un panneau ruban en mode régulier (FALSE par défaut).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne FALSE par défaut, indiquant qu’il ne s’agit pas d’un panneau ruban en mode régulier.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a>CMFCPopupMenuBar::LoadDeHash

Charge un menu archivé.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
[dans] Une poignée au menu archivé à charger.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le menu est chargé avec succès, ou FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a>CMFCPopupMenuBar:m_bDisableSideBarInXPMode

Un paramètre Boolean qui indique si votre application a une barre latérale grise lorsqu’elle a une apparence Windows XP.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Notes

Si cette variable de membre est définie à FALSE et que votre application a une apparence Windows XP, le cadre tire une barre latérale grise dans votre application.

La valeur par défaut est FALSE.

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a>CMFCPopupMenuBar::RestoreDelayedSubMenu

Restaure un bouton de menu retardé pour fermer la barre de menu popup.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFCPopupMenuBar::SetButtonStyle

Définit le style du bouton de la barre d’outils à l’index donné. (Overrides [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] L’index zéro du bouton de la barre d’outils dont le style doit être défini.

*nStyle*<br/>
[dans] Le style du bouton. Consultez [ToolBar Control Styles](../../mfc/reference/toolbar-control-styles.md) pour la liste des styles de boutons de barre d’outils disponibles.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a>CMFCPopupMenuBar::SetOffset

Définit le décalage de ligne de la barre de menu popup.

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Paramètres

*iOffset (en anglais)*<br/>
[dans] Le nombre de lignes que la barre de menu popup doit être compensée.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a>CMFCPopupMenuBar::StartPopupMenuTimer

Démarre la minuterie pour un bouton de menu popup retardé spécifié.

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Paramètres

*pMenuButton*<br/>
[dans] Pointeur sur le bouton menu pour lequel définir la minuterie de retard.

*nDelayFactor (en)*<br/>
[dans] Un facteur de retard, égal à au moins un, à multiplier par le temps de retard standard du menu (généralement entre une demi-seconde et cinq secondes).

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)
