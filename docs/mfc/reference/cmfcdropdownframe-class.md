---
title: CMFCDropDownFrame, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: 62bab0fbde364406f35edb959abb6e55a9125504
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840737"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame, classe

Fournit des fonctionnalités de fenêtres frames déroulantes à des barres d’outils déroulantes et des boutons de barre d’outils déroulants.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Constructeur par défaut.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[CMFCDropDownFrame :: Create](#create)|Crée un objet `CMFCDropDownFrame`.|
|`CMFCDropDownFrame::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Récupère la barre de menus parente du frame de liste déroulante.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Récupère le menu contextuel parent du frame de liste déroulante.|
|`CMFCDropDownFrame::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCDropDownFrame :: RecalcLayout](#recalclayout)|Repositionne le frame de liste déroulante.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Définit si la fenêtre de la barre d’outils déroulante enfant est détruite automatiquement.|

### <a name="remarks"></a>Notes

Cette classe n'est pas destinée à être utilisée directement à partir de votre code.

L’infrastructure utilise cette classe pour fournir le comportement de frame `CMFCDropDownToolbar` aux `CMFCDropDownToolbarButton` classes et. Pour plus d’informations sur ces classes, consultez [CMFCDropDownToolBar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md) et CMFCDropDownToolbarButton, [classe](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer un pointeur vers un `CMFCDropDownFrame` objet à partir d’une `CFrameWnd` classe et comment définir la destruction automatique de la fenêtre de la barre d’outils déroulante enfant.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a> CMFCDropDownFrame :: Create

Crée un objet `CMFCDropDownFrame`.

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>Paramètres

*pWndParent*\
dans Fenêtre parente du frame de liste déroulante.

*x*\
dans Coordonnée d’écran horizontale pour l’emplacement du cadre vers le dessous.

*y*\
dans Coordonnée d’écran verticale pour l’emplacement du cadre vers le dessous.

*pWndOriginToolbar*\
dans La barre d’outils qui contient les boutons déroulants que cette méthode utilise pour remplir le nouvel objet de frame de liste déroulante.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le frame de liste déroulante a été créé avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode appelle la méthode [CMiniFrameWnd :: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) de base pour créer la fenêtre frame déroulante avec le style WS_POPUP. La fenêtre frame déroulante apparaît aux coordonnées d’écran spécifiées. Cette méthode échoue si la méthode [CMiniFrameWnd :: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) retourne false.

La `CMFCDropDownFrame` classe crée une copie du paramètre fourni `CMFCDropDownToolBar` . Cette méthode copie les images de bouton et les États de bouton du `pWndOriginToolbar` paramètre vers le `m_pWndOriginToolbar` membre de données.

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a> CMFCDropDownFrame::GetParentMenuBar

Récupère la barre de menus parente du frame de liste déroulante.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la barre de menus parente du frame déroulant, ou NULL si le frame n’a pas de parent.

### <a name="remarks"></a>Notes

Cette méthode récupère la barre de menus parente à partir du bouton parent. Cette méthode retourne la valeur NULL si le frame de liste déroulant n’a pas de bouton parent ou si le bouton parent n’a pas de barre de menus parente.

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a> CMFCDropDownFrame::GetParentPopupMenu

Récupère le menu contextuel parent du frame de liste déroulante.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le menu déroulant parent du frame de liste déroulante, ou NULL si le frame n’a pas de parent.

### <a name="remarks"></a>Notes

Cette méthode récupère le menu parent du bouton parent. Cette méthode retourne la valeur NULL si le frame de liste déroulant n’a pas de bouton parent ou si le bouton parent n’a pas de menu parent.

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a> CMFCDropDownFrame :: RecalcLayout

Repositionne le frame de liste déroulante.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Paramètres

*bNotify*\
[in] Inutilisé.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsque le frame de liste déroulante est créé ou que la fenêtre parente est redimensionnée. Cette méthode calcule la position et la taille du frame de liste déroulante à l’aide de la position et de la taille de la fenêtre parente.

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a> CMFCDropDownFrame::SetAutoDestroy

Définit si la fenêtre de la barre d’outils déroulante enfant est détruite automatiquement.

```cpp
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoDestroy*<br/>
dans TRUE pour détruire automatiquement la fenêtre de la barre d’outils déroulante associée ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si *bAutoDestroy* a la valeur true, le `CMFCDropDownFrame` destructeur détruit la fenêtre de barre d’outils déroulante associée. La valeur par défaut est TRUE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton, classe](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
