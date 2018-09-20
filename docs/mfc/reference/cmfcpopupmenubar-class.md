---
title: Cmfcpopupmenubar, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed0c8bdc50dd1033d89ae2dd87fdc925c05328b3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436180"
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
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Immédiatement recalcule la disposition d’un volet. (Substitue [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Charge les éléments de menu contextuel à partir d’une ressource de menu spécifié.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Ferme un bouton de menu contextuel retardée.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Génère un menu à partir des boutons de menu contextuel.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Localise la barre d’outils dans laquelle se trouve un point spécifié.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Indique la taille des images de bouton de menu.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Retourne l’identificateur de l’élément de menu par défaut.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Obtient l’index de la commande de menu dernier appelée.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Obtient l’offset de ligne de la barre de menu contextuel.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importe des boutons de menu contextuel à partir d’un menu spécifié.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Indique si la barre de menus de fenêtre contextuelle est en mode de liste déroulante vers le bas.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Indique si la barre de menus de fenêtre contextuelle est en mode de palette.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Indique s’il s’agit d’un panneau de ruban (FALSE par défaut).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Indique s’il s’agit d’un panneau de ruban en mode normal (FALSE par défaut).|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Charge un menu archivé.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Restaure un bouton de menu retardée pour la fermeture de la barre de menu contextuel.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Définit le style du bouton de barre d’outils à l’index donné. (Substitue [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Définit le décalage de ligne de la barre de menu contextuel.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Démarre la minuterie pour un bouton de menu contextuel retardée spécifié.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Spécifie si la barre latérale grise s’affichera lorsque l’application a une apparence de Windows XP.|

## <a name="remarks"></a>Notes

Le `CMFCPopupMenuBar` est créé en même temps comme un [cmfcpopupmenu, classe](../../mfc/reference/cmfcpopupmenu-class.md) et incorporé à l’intérieur. Le `CMFCPopupMenuBar` couvre toute la zone cliente de la `CMFCPopupMenu` objet. Il prend en charge l’entrée clavier et souris. Il communique également que l’entrée de la `CMFCPopupMenu` et à la fenêtre frame de niveau supérieur.

## <a name="example"></a>Exemple

L’exemple suivant montre comment initialiser un `CMFCPopupMenuBar` de l’objet à partir d’un `CMFCPopupMenu` objet. Cet extrait de code fait partie de l’ [exemple Draw Client](../../visual-cpp-samples.md).

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

## <a name="requirements"></a>Configuration requise

**En-tête :** afxpopupmenubar.h

##  <a name="adjustsizeimmediate"></a>  CMFCPopupMenuBar::AdjustSizeImmediate

Immédiatement recalcule la disposition du volet de barre de menu contextuel. (Substitue [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Paramètres

*bRecalcLayout*<br/>
[in] TRUE pour recalculer automatiquement la disposition du volet de barre de menu contextuel ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="buildorigitems"></a>  CMFCPopupMenuBar::BuildOrigItems

Charge les éléments de menu contextuel à partir d’une ressource de menu spécifié.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Paramètres

*uiMenuResID*<br/>
[in] Spécifie l’ID de menu de la ressource de menu à charger.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE si l’opération réussit ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

##  <a name="closedelayedsubmenu"></a>  CMFCPopupMenuBar::CloseDelayedSubMenu

Ferme un bouton de menu contextuel qui a été différé.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Notes

##  <a name="exporttomenu"></a>  CMFCPopupMenuBar::ExportToMenu

Génère un menu à partir des boutons de menu contextuel.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un handle vers le nouveau menu.

### <a name="remarks"></a>Notes

##  <a name="finddestintationtoolbar"></a>  CMFCPopupMenuBar::FindDestintationToolBar

Localise la barre d’outils dans laquelle se trouve un point spécifié.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
[in] Un point sur l’écran.

### <a name="return-value"></a>Valeur de retour

Retourne un handle vers la barre d’outils où se trouve le point, le cas échéant, ou NULL dans le cas contraire.

### <a name="remarks"></a>Notes

##  <a name="getcurrentmenuimagesize"></a>  CMFCPopupMenuBar::GetCurrentMenuImageSize

Indique la taille des images de bouton de menu.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la taille des images de bouton de menu dans la barre d’outils.

### <a name="remarks"></a>Notes

##  <a name="getdefaultmenuid"></a>  CMFCPopupMenuBar::GetDefaultMenuId

Retourne l’identificateur de l’élément de menu par défaut.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’identificateur de l’élément de menu par défaut dans la barre de menu contextuel.

### <a name="remarks"></a>Notes

##  <a name="getlastcommandindex"></a>  CMFCPopupMenuBar::GetLastCommandIndex

Obtient l’index de la commande de menu dernier appelée.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’index de la dernière commande de menu qui a été appelée.

### <a name="remarks"></a>Notes

##  <a name="getoffset"></a>  CMFCPopupMenuBar::GetOffset

Obtient l’offset de ligne de la barre de menu contextuel.

```
int GetOffset() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’offset de ligne de la barre de menu contextuel.

### <a name="remarks"></a>Notes

Cette valeur est définie à l’aide de [CMFCPopupMenuBar::SetOffset](#setoffset).

##  <a name="importfrommenu"></a>  CMFCPopupMenuBar::ImportFromMenu

Importe des boutons de menu contextuel à partir d’un menu spécifié.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
[in] Le menu à partir duquel importer les boutons de menu contextuel.

*bShowAllCommands*<br/>
[in] TRUE si toutes les commandes du menu doivent être importés, ou FALSE si rarement utilisés peuvent être masqués.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les boutons de menu ont été correctement importés dans le menu, ou FALSE si pas.

### <a name="remarks"></a>Notes

##  <a name="isdropdownlistmode"></a>  CMFCPopupMenuBar::IsDropDownListMode

Indique si la barre de menus de fenêtre contextuelle est en mode de liste déroulante vers le bas.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la barre de menus de fenêtre contextuelle n’est pas en mode de liste déroulante vers le bas, ou FALSE si.

### <a name="remarks"></a>Notes

##  <a name="ispalettemode"></a>  CMFCPopupMenuBar::IsPaletteMode

Indique si la barre de menus de fenêtre contextuelle est en mode de palette.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE si le mode de palette est activé, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Lors de la barre de menus est définie en mode de palette, éléments de menu apparaissent dans plusieurs colonnes et un nombre limité de lignes.

##  <a name="isribbonpanel"></a>  CMFCPopupMenuBar::IsRibbonPanel

Indique s’il s’agit d’un panneau de ruban (FALSE par défaut).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Valeur de retour

Renvoie la valeur FALSE par défaut, indiquant qu’il ne s’agit pas d’un panneau de ruban.

### <a name="remarks"></a>Notes

##  <a name="isribbonpanelinregularmode"></a>  CMFCPopupMenuBar::IsRibbonPanelInRegularMode

Indique s’il s’agit d’un panneau de ruban en mode normal (FALSE par défaut).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Valeur de retour

Renvoie la valeur FALSE par défaut, indiquant qu’il s’agit pas un panneau de ruban en mode normal.

### <a name="remarks"></a>Notes

##  <a name="loadfromhash"></a>  CMFCPopupMenuBar::LoadFromHash

Charge un menu archivé.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
[in] Handle vers le menu archivé à charger.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le menu est chargé avec succès, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

##  <a name="m_bdisablesidebarinxpmode"></a>  CMFCPopupMenuBar::m_bDisableSideBarInXPMode

Un paramètre booléen qui indique si votre application a une barre latérale grise lorsqu’il a une apparence de Windows XP.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Notes

Si cette variable de membre est définie sur FALSE et que votre application a une apparence de Windows XP, le framework Dessine une barre latérale grise dans votre application.

La valeur par défaut est FALSE.

##  <a name="restoredelayedsubmenu"></a>  CMFCPopupMenuBar::RestoreDelayedSubMenu

Restaure un bouton de menu retardée pour la fermeture de la barre de menu contextuel.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Notes

##  <a name="setbuttonstyle"></a>  CMFCPopupMenuBar::SetButtonStyle

Définit le style du bouton de barre d’outils à l’index donné. (Substitue [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[in] Index de base zéro du bouton de barre d’outils dont le style doit être défini.

*nStyle*<br/>
[in] Le style du bouton. Consultez [Styles de contrôle de barre d’outils](../../mfc/reference/toolbar-control-styles.md) pour obtenir la liste des styles de bouton de barre d’outils disponibles.

### <a name="remarks"></a>Notes

##  <a name="setoffset"></a>  CMFCPopupMenuBar::SetOffset

Définit le décalage de ligne de la barre de menu contextuel.

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Paramètres

*iOffset*<br/>
[in] Le nombre de lignes que la barre de menu contextuel doit être décalée.

### <a name="remarks"></a>Notes

##  <a name="startpopupmenutimer"></a>  CMFCPopupMenuBar::StartPopupMenuTimer

Démarre la minuterie pour un bouton de menu contextuel retardée spécifié.

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Paramètres

*pMenuButton*<br/>
[in] Pointeur vers le bouton de menu pour lequel définir le minuteur de délai.

*nDelayFactor*<br/>
[in] Délai facteur, égal au moins un, multiplier par le temps de retard de menu standard (généralement entre une demi-seconde et cinq secondes).

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)
