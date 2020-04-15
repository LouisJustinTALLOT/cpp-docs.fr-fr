---
title: Classe CMFCDropDownToolBar
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
ms.openlocfilehash: 68dd976471b39d7f50c2f0378b2fce99ad3feeca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367604"
---
# <a name="cmfcdropdowntoolbar-class"></a>Classe CMFCDropDownToolBar

Barre d'outils qui s'affiche lorsque l'utilisateur appuie sur un bouton de barre d'outils de niveau supérieur et le maintient enfoncé.

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Substitue `CPane::AllowShowOnPaneMenu`.)|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Overrides [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Overrides [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Substitue `CMFCToolBar::OnSendCommand`.)|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Overrides [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Notes

Un `CMFCDropDownToolBar` objet combine l’apparence visuelle d’une barre d’outils avec le comportement d’un menu popup. Lorsqu’un utilisateur appuie et tient un bouton de barre d’outils (voir [classe CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), une barre d’outils déroulante apparaît, et l’utilisateur peut sélectionner un bouton de la barre d’outils de dépôt en faisant défiler vers elle et en libérant le bouton de la souris. Une fois que l’utilisateur sélectionne un bouton dans la barre d’outils de dépôt, ce bouton s’affiche sous forme de bouton actuel sur la barre d’outils de haut niveau.

Une barre d’outils de dépôt ne peut pas être personnalisée ou amarré, et elle n’a pas d’état de déchirure.

L’illustration suivante `CMFCDropDownToolBar` montre un objet :

![Exemple de CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "Exemple de CMFCDropDownToolbar")

Vous créez `CMFCDropDownToolBar` un objet de la même façon que vous créez une barre d’outils ordinaire (voir [classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)).

Pour insérer la barre d’outils d’abandon dans une barre d’outils parent :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Créez `CMFCDropDownToolBarButton` un objet qui contient la barre d’outils de dépôt (pour plus d’informations, voir [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Remplacez le bouton factice par l’objet `CMFCDropDownToolBarButton` en utilisant [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations sur les boutons de la barre d’outils, voir [Procédure pas à pas: Mettre des contrôles sur les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md). Pour un exemple de barre d’outils d’abandon, voir l’exemple du projet VisualStudioDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment `Create` utiliser `CMFCDropDownToolBar` la méthode dans la classe. Cet extrait de code fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

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

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFCDropDownToolBar::LoadBitmap

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
[dans] L’ID de ressource de la bitmap qui se réfère aux images hot toolbar.

*uiColdResID*<br/>
[dans] L’ID de ressource de la bitmap qui se réfère aux images froides de barre d’outils.

*uiMenuResID*<br/>
[dans] L’ID de ressource de la bitmap qui se réfère aux images régulières de menu.

*Bloqué*<br/>
[dans] VRAI pour verrouiller la barre d’outils; autrement FALSE.

*uiDisabledResID*<br/>
[dans] L’ID de ressource de la bitmap qui se réfère aux images de barre d’outils désactivées.

*uiMenuDisabledResID*<br/>
[dans] L’ID de ressource de la bitmap qui se réfère aux images de menu désactivées.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode réussit ; sinon, 0.

### <a name="remarks"></a>Notes

La méthode [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) appelle cette méthode pour charger les images qui sont associées à la barre d’outils. Surchargez cette méthode pour effectuer un chargement personnalisé des ressources d’images.

Appelez la méthode `LoadBitmapEx` pour charger des images supplémentaires après avoir créé la barre d’outils.

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFCDropDownToolBar::LoadToolBar

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

[dans] *uiResID*<br/>

[dans] *uiColdResID*<br/>

[dans] *uiMenuResID*<br/>

[dans] *BOOL (en anglais)*<br/>

[dans] *uiDisabledResID*<br/>

[dans] *uiMenuDisabledResID*<br/>

[dans] *uiHotResID*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a>CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

[dans] *nFlags*<br/>

[dans] *point*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a>CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

[dans] *nFlags*<br/>

[dans] *point*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a>CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Paramètres

[dans] *pButton*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Paramètres

[dans] *pTarget*<br/>

[dans] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Créer](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::RemplacerButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Classe CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Procédure pas à pas : placement de contrôles dans les barres d'outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
