---
title: CMFCDropDownToolbar, classe
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
ms.openlocfilehash: 704d48cc546943d818ae8b898060fe0f7e203c53
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303551"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolbar, classe

Barre d'outils qui s'affiche lorsque l'utilisateur appuie sur un bouton de barre d'outils de niveau supérieur et le maintient enfoncé.

   Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Substitue `CPane::AllowShowOnPaneMenu`.)|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Substitue [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Substitue [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Substitue `CMFCToolBar::OnSendCommand`.)|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Substitue [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Notes

Un `CMFCDropDownToolBar` objet combine l’apparence visuelle d’une barre d’outils avec le comportement d’un menu contextuel. Lorsqu’un utilisateur appuie sur et contient un bouton de barre d’outils déroulante (consultez [cmfcdropdowntoolbarbutton, classe](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), une barre d’outils de la liste déroulante s’affiche, et l’utilisateur peut sélectionner un bouton à partir de la barre d’outils de la liste déroulante en le défilement vers elle et en libérant de la souris bouton. Une fois que l’utilisateur sélectionne un bouton dans la barre d’outils de la liste déroulante, ce bouton s’affiche en tant que bouton dans la barre d’outils de niveau supérieur en cours.

Une barre d’outils de la liste déroulante ne peut pas être personnalisé ou ancré, et il n’a pas un état détachable.

L’illustration suivante montre un `CMFCDropDownToolBar` objet :

![Exemple de CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "exemple de CMFCDropDownToolbar")

Vous créez un `CMFCDropDownToolBar` objet de la même façon que vous créez une barre d’outils ordinaire (consultez [cmfctoolbar, classe](../../mfc/reference/cmfctoolbar-class.md)).

Pour insérer la barre d’outils de la liste déroulante dans une barre d’outils parent :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Créer un `CMFCDropDownToolBarButton` objet qui contient la barre d’outils déroulante (pour plus d’informations, consultez [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Remplacez le bouton fictif avec le `CMFCDropDownToolBarButton` objet à l’aide de [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations sur les boutons de barre d’outils, consultez [procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md). Pour obtenir un exemple d’une barre d’outils de la liste déroulante, consultez l’exemple de projet VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `Create` méthode dans la `CMFCDropDownToolBar` classe. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).

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

##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap

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
[in] L’ID de ressource de la bitmap qui fait référence aux images de barre d’outils Accès rapide.

*uiColdResID*<br/>
[in] L’ID de ressource de la bitmap qui fait référence aux images de barre d’outils à froid.

*uiMenuResID*<br/>
[in] L’ID de ressource de la bitmap qui fait référence aux images de menu standard.

*bLocked*<br/>
[in] TRUE pour verrouiller la barre d’outils ; Sinon, FALSE.

*uiDisabledResID*<br/>
[in] L’ID de ressource de la bitmap qui fait référence aux images de barre d’outils désactivées.

*uiMenuDisabledResID*<br/>
[in] L’ID de ressource de la bitmap qui fait référence aux images de menu désactivé.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode réussit ; sinon, 0.

### <a name="remarks"></a>Notes

La méthode [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) appelle cette méthode pour charger les images qui sont associées à la barre d’outils. Surchargez cette méthode pour effectuer un chargement personnalisé des ressources d’images.

Appelez la méthode `LoadBitmapEx` pour charger des images supplémentaires après avoir créé la barre d’outils.

##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar

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

[in] *uiResID*<br/>

[in] *uiColdResID*<br/>

[in] *uiMenuResID*<br/>

[in] *BOOL*<br/>

[in] *uiDisabledResID*<br/>

[in] *uiMenuDisabledResID*<br/>

[in] *uiHotResID*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

[in] *nFlags*<br/>

[in] *point*<br/>

### <a name="remarks"></a>Notes

##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

[in] *nFlags*<br/>

[in] *point*<br/>

### <a name="remarks"></a>Notes

##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Paramètres

[in] *pButton*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Paramètres

[in] *pTarget*<br/>

[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton, classe](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
