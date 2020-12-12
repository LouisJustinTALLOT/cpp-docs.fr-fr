---
description: 'En savoir plus sur : classe CMFCDropDownToolBar'
title: CMFCDropDownToolBar, classe
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: 158562829cb5bbebfb9a858d34751c56bdf46ed8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293987"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar, classe

Barre d'outils qui s'affiche lorsque l'utilisateur appuie sur un bouton de barre d'outils de niveau supérieur et le maintient enfoncé.

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDropDownToolBar :: AllowShowOnPaneMenu](#allowshowonpanemenu)|(Substitue `CPane::AllowShowOnPaneMenu`.)|
|[CMFCDropDownToolBar :: LoadBitmap](#loadbitmap)|(Substitue [CMFCToolBar :: LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar :: LoadToolBar](#loadtoolbar)|(Substitue [CMFCToolBar :: LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar :: OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar :: OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar :: OnSendCommand](#onsendcommand)|(Substitue `CMFCToolBar::OnSendCommand`.)|
|[CMFCDropDownToolBar :: OnUpdateCmdUI](#onupdatecmdui)|(Substitue [CMFCToolBar :: OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Notes

Un `CMFCDropDownToolBar` objet combine l’apparence visuelle d’une barre d’outils avec le comportement d’un menu contextuel. Lorsqu’un utilisateur appuie sur un bouton de barre d’outils déroulante (voir la [classe CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), une barre d’outils déroulante s’affiche, et l’utilisateur peut sélectionner un bouton dans la barre d’outils déroulante en y faisant défiler et en relâchant le bouton de la souris. Une fois que l’utilisateur a sélectionné un bouton dans la barre d’outils déroulante, ce bouton est affiché en tant que bouton actuel dans la barre d’outils de niveau supérieur.

Une barre d’outils déroulante ne peut pas être personnalisée ou ancrée et n’a pas d’état de destruction.

L’illustration suivante montre un `CMFCDropDownToolBar` objet :

![Exemple de CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "Exemple de CMFCDropDownToolbar")

Vous créez un `CMFCDropDownToolBar` objet de la même façon que vous créez une barre d’outils ordinaire (consultez [CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)).

Pour insérer la barre d’outils déroulante dans une barre d’outils parente :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Créer un `CMFCDropDownToolBarButton` objet qui contient la barre d’outils déroulante (pour plus d’informations, consultez [CMFCDropDownToolbarButton :: CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Remplacez le bouton factice par l' `CMFCDropDownToolBarButton` objet à l’aide de [CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations sur les boutons de la barre d’outils, consultez [procédure pas à pas : ajout de contrôles sur des barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md). Pour obtenir un exemple de barre d’outils déroulante, consultez l’exemple de projet VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `Create` méthode dans la `CMFCDropDownToolBar` classe. Cet extrait de code fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a> CMFCDropDownToolBar :: AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a> CMFCDropDownToolBar :: LoadBitmap

Charge les images de barre d’outils à partir des ressources de l’application.

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>Paramètres

*uiResID*<br/>
dans ID de ressource de la bitmap qui fait référence aux images de barre d’outils actives.

*uiColdResID*<br/>
dans ID de ressource de la bitmap qui fait référence aux images de barre d’outils froides.

*uiMenuResID*<br/>
dans ID de ressource de la bitmap qui fait référence aux images de menu normales.

*Obstrué*<br/>
dans TRUE pour verrouiller la barre d’outils ; Sinon, FALSe.

*uiDisabledResID*<br/>
dans ID de ressource de la bitmap qui fait référence aux images de barre d’outils désactivées.

*uiMenuDisabledResID*<br/>
dans ID de ressource de la bitmap qui fait référence aux images de menu désactivées.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la méthode réussit ; sinon, 0.

### <a name="remarks"></a>Notes

La méthode [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) appelle cette méthode pour charger les images qui sont associées à la barre d’outils. Surchargez cette méthode pour effectuer un chargement personnalisé des ressources d’images.

Appelez la méthode `LoadBitmapEx` pour charger des images supplémentaires après avoir créé la barre d’outils.

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a> CMFCDropDownToolBar :: LoadToolBar

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>Paramètres

dans *uiResID*<br/>

dans *uiColdResID*<br/>

dans *uiMenuResID*<br/>

dans Valeur *booléenne*<br/>

dans *uiDisabledResID*<br/>

dans *uiMenuDisabledResID*<br/>

dans *uiHotResID*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a> CMFCDropDownToolBar :: OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

dans *nFlags*<br/>

dans *point*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a> CMFCDropDownToolBar :: OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

dans *nFlags*<br/>

dans *point*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a> CMFCDropDownToolBar :: OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Paramètres

dans *pButton*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a> CMFCDropDownToolBar :: OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Paramètres

dans *pTarget*<br/>

dans *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar :: Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton, classe](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Procédure pas à pas : ajout de contrôles aux barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
