---
title: Classe CMFCDropDownFrame
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
ms.openlocfilehash: a5e95efe1880f1177490d55988ca1fe42c606b15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367551"
---
# <a name="cmfcdropdownframe-class"></a>Classe CMFCDropDownFrame

Fournit la fonctionnalité de fenêtre d’image de dépôt aux barres d’outils de dépôt vers le bas et les boutons de barre d’outils de dépôt.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|`CMFCDropDownFrame::CMFCDropDownFrame`|Constructeur par défaut.|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCDropDownFrame::Créer](#create)|Crée un objet `CMFCDropDownFrame` .|
|`CMFCDropDownFrame::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Récupère la barre de menu parent du cadre de dépôt.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Récupère le menu pop-up parent du cadre de décrochage.|
|`CMFCDropDownFrame::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Repositionne le cadre de descente.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Définit si la fenêtre de barre d’outils d’abandon de l’enfant est détruite automatiquement.|

### <a name="remarks"></a>Notes

Cette classe n'est pas destinée à être utilisée directement à partir de votre code.

Le cadre utilise cette classe pour `CMFCDropDownToolbar` `CMFCDropDownToolbarButton` fournir un comportement de cadre à la et les classes. Pour plus d’informations sur ces classes, voir [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md) et [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer `CMFCDropDownFrame` un pointeur à un objet d’une `CFrameWnd` classe, et comment définir la fenêtre de barre d’outils de dépôt de l’enfant pour être détruit automatiquement.

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a>CMFCDropDownFrame::Créer

Crée un objet `CMFCDropDownFrame` .

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pWndParent*|[dans] La fenêtre parente du cadre de descente.|
|*X*|[dans] La coordonnées horizontale de l’écran pour l’emplacement du cadre descendant.|
|*y*|[dans] La coordonnées de l’écran vertical pour l’emplacement du cadre descendant.|
|*pWndOriginToolbar*|[dans] La barre d’outils qui a les boutons de chute que cette méthode utilise pour peupler le nouvel objet de cadre de drop-down.|

### <a name="return-value"></a>Valeur de retour

VRAI si le cadre de décrochage a été créé avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode appelle la base [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) méthode pour créer la fenêtre de cadre de dépôt avec le style WS_POPUP. La fenêtre d’image de dépôt apparaît aux coordonnées d’écran spécifiées. Cette méthode échoue si la méthode [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) méthode retourne FALSE.

La `CMFCDropDownFrame` classe crée une `CMFCDropDownToolBar` copie du paramètre fourni. Cette méthode copie les images de `pWndOriginToolbar` bouton `m_pWndOriginToolbar` et les états de bouton du paramètre au membre de données.

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar

Récupère la barre de menu parent du cadre de dépôt.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la barre de menu parent du cadre de dépôt, ou NULL si le cadre n’a pas de parent.

### <a name="remarks"></a>Notes

Cette méthode récupère la barre de menu parent du bouton parent. Cette méthode renvoie NULL si le cadre de dépôt n’a pas de bouton parent ou le bouton parent n’a pas de barre de menu parent.

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

Récupère le menu pop-up parent du cadre de décrochage.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur pour le menu déroulant parent du cadre de décrochage, ou NULL si le cadre n’a pas de parent.

### <a name="remarks"></a>Notes

Cette méthode récupère le menu parent du bouton parent. Cette méthode renvoie NULL si le cadre de dépôt n’a pas de bouton parent ou le bouton parent n’a pas de menu parent.

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout

Repositionne le cadre de descente.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*bNotifier*|[in] Inutilisé.|

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsque le cadre de dépôt est créé ou que la fenêtre parente est redimensionné. Cette méthode calcule la position et la taille du cadre de dépôt en utilisant la position et la taille de la fenêtre parente.

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

Définit si la fenêtre de barre d’outils d’abandon de l’enfant est détruite automatiquement.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoDestroy*<br/>
[dans] VRAI pour détruire automatiquement la fenêtre de barre d’outils de dépôt associée; autrement, FALSE.

### <a name="remarks"></a>Notes

Si *bAutoDestroy* est VRAI, alors le `CMFCDropDownFrame` destructeur détruit la fenêtre de barre d’outils de chute associée. La valeur par défaut est TRUE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[Classe CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
