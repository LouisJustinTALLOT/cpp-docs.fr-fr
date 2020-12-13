---
description: 'En savoir plus sur : classe Cmfcpopupmenubar,'
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
ms.openlocfilehash: 4db8c02ed92aec5243f9a2c7800c6fd1f9747751
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334747"
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
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Recalcule immédiatement la disposition d’un volet. (Substitue [CPane :: AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Charge les éléments de menu contextuel d’une ressource de menu spécifiée.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Ferme un bouton de menu contextuel retardé.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Génère un menu à partir des boutons de menu contextuel.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Localise la barre d’outils là où se trouve un point spécifié.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Indique la taille des images de bouton de menu.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Retourne l’identificateur de l’élément de menu par défaut.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Obtient l’index de la commande de menu appelée le plus récemment.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Obtient l’offset de ligne de la barre de menus contextuel.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importe des boutons de menu contextuel à partir d’un menu spécifié.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Indique si la barre de menus contextuel est en mode liste déroulante.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Indique si la barre de menus contextuel est en mode palette.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Indique s’il s’agit d’un panneau de ruban (FALSe par défaut).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Indique s’il s’agit d’un panneau du ruban en mode normal (FALSe par défaut).|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Charge un menu archivé.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Restaure un bouton de menu retardé pour fermer la barre de menus contextuel.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Définit le style du bouton de barre d’outils à l’index donné. (Substitue [CMFCToolBar :: SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Définit l’offset de ligne de la barre de menus contextuel.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Démarre le minuteur pour un bouton de menu contextuel retardé spécifié.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[Cmfcpopupmenubar, :: m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Spécifie si la barre latérale grise s’affiche lorsque l’application a une apparence Windows XP.|

## <a name="remarks"></a>Notes

Le `CMFCPopupMenuBar` est créé en même temps qu’une [classe CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) et incorporé à l’intérieur de celui-ci. Le `CMFCPopupMenuBar` couvre la totalité de la zone cliente de l' `CMFCPopupMenu` objet. Il prend en charge l’entrée au clavier et à la souris. Il communique également cette entrée à `CMFCPopupMenu` et à la fenêtre frame de niveau supérieur.

## <a name="example"></a>Exemple

L’exemple suivant montre comment initialiser un `CMFCPopupMenuBar` objet à partir d’un `CMFCPopupMenu` objet. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

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

**En-tête :** afxpopupmenubar. h

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a> Cmfcpopupmenubar, :: AdjustSizeImmediate

Recalcule immédiatement la disposition du volet de barre de menus contextuel. (Substitue [CPane :: AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Paramètres

*bRecalcLayout*<br/>
dans TRUE pour recalculer automatiquement la disposition du volet de barre de menus contextuel ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a> Cmfcpopupmenubar, :: BuildOrigItems

Charge les éléments de menu contextuel d’une ressource de menu spécifiée.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Paramètres

*uiMenuResID*<br/>
dans Spécifie l’ID de menu de la ressource de menu à charger.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a> Cmfcpopupmenubar, :: CloseDelayedSubMenu

Ferme un bouton de menu contextuel qui a été retardé.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a> Cmfcpopupmenubar, :: ExportToMenu

Génère un menu à partir des boutons de menu contextuel.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle vers le nouveau menu.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a> Cmfcpopupmenubar, :: FindDestintationToolBar

Localise la barre d’outils là où se trouve un point spécifié.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
dans Point sur l’écran.

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle vers la barre d’outils où le point se trouve, s’il y en a un, ou NULL dans le cas contraire.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a> Cmfcpopupmenubar, :: GetCurrentMenuImageSize

Indique la taille des images de bouton de menu.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la taille des images de bouton de menu dans la barre d’outils.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a> Cmfcpopupmenubar, :: GetDefaultMenuId

Retourne l’identificateur de l’élément de menu par défaut.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’identificateur de l’élément de menu par défaut dans la barre de menus contextuel.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a> Cmfcpopupmenubar, :: GetLastCommandIndex

Obtient l’index de la commande de menu appelée le plus récemment.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’index de la dernière commande de menu appelée.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a> Cmfcpopupmenubar, :: GetOffset,

Obtient l’offset de ligne de la barre de menus contextuel.

```
int GetOffset() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’offset de ligne de la barre de menus contextuel.

### <a name="remarks"></a>Notes

Cette valeur est définie à l’aide de [cmfcpopupmenubar, :: SetOffset](#setoffset).

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a> Cmfcpopupmenubar, :: ImportFromMenu

Importe des boutons de menu contextuel à partir d’un menu spécifié.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
dans Menu à partir duquel importer les boutons de menu contextuel.

*bShowAllCommands*<br/>
dans TRUE si toutes les commandes du menu doivent être importées, ou FALSe si elles sont rarement utilisées.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si les boutons de menu ont été correctement importés à partir du menu, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a> Cmfcpopupmenubar, :: IsDropDownListMode

Indique si la barre de menus contextuel est en mode liste déroulante.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la barre de menus contextuel est en mode liste déroulante, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a> Cmfcpopupmenubar, :: IsPaletteMode

Indique si la barre de menus contextuel est en mode palette.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le mode de palette est activé, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Quand la barre de menus est définie sur le mode palette, les éléments de menu s’affichent dans plusieurs colonnes et un nombre limité de lignes.

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a> Cmfcpopupmenubar, :: IsRibbonPanel

Indique s’il s’agit d’un panneau de ruban (FALSe par défaut).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur FALSe par défaut, ce qui indique qu’il ne s’agit pas d’un panneau de ruban.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a> Cmfcpopupmenubar, :: IsRibbonPanelInRegularMode

Indique s’il s’agit d’un panneau du ruban en mode normal (FALSe par défaut).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur FALSe par défaut, ce qui indique qu’il ne s’agit pas d’un panneau du ruban en mode normal.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a> Cmfcpopupmenubar, :: LoadFromHash

Charge un menu archivé.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
dans Handle vers le menu archivé à charger.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le menu est chargé avec succès, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a> Cmfcpopupmenubar, :: m_bDisableSideBarInXPMode

Paramètre booléen qui indique si votre application a un encadré gris lorsqu’elle a une apparence Windows XP.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Notes

Si cette variable membre est définie sur FALSe et que votre application a une apparence Windows XP, l’infrastructure dessine un encadré gris dans votre application.

La valeur par défaut est FALSE.

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a> Cmfcpopupmenubar, :: RestoreDelayedSubMenu

Restaure un bouton de menu retardé pour fermer la barre de menus contextuel.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a> Cmfcpopupmenubar, :: SetButtonStyle

Définit le style du bouton de barre d’outils à l’index donné. (Substitue [CMFCToolBar :: SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Index de base zéro du bouton de barre d’outils dont le style doit être défini.

*nStyle*<br/>
dans Style du bouton. Consultez [styles de contrôle de barre d’outils](../../mfc/reference/toolbar-control-styles.md) pour obtenir la liste des styles de boutons de barre d’outils disponibles.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a> Cmfcpopupmenubar, :: SetOffset

Définit l’offset de ligne de la barre de menus contextuel.

```cpp
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Paramètres

*iOffset*<br/>
dans Nombre de lignes que la barre de menus contextuelles doit décaler.

### <a name="remarks"></a>Notes

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a> Cmfcpopupmenubar, :: StartPopupMenuTimer

Démarre le minuteur pour un bouton de menu contextuel retardé spécifié.

```cpp
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Paramètres

*pMenuButton*<br/>
dans Pointeur vers le bouton de menu pour lequel définir le minuteur de délai.

*nDelayFactor*<br/>
dans Facteur de délai, égal à au moins un, à multiplier par le délai de menu standard (généralement entre une demi-seconde et cinq secondes).

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)
