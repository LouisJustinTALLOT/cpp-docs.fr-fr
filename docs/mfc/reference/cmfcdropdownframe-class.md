---
title: Cmfcdropdownframe, classe
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
ms.openlocfilehash: 534dc90443371c8440e0cb317540f2cf80f6eacc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237371"
---
# <a name="cmfcdropdownframe-class"></a>Cmfcdropdownframe, classe

Fournit des fonctionnalités de fenêtre frame de la liste déroulante pour les barres d’outils de la liste déroulante et les boutons de barre d’outils de la liste déroulante.

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
|[CMFCDropDownFrame::Create](#create)|Crée un objet `CMFCDropDownFrame`.|
|`CMFCDropDownFrame::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Récupère la barre de menu parent de l’image de la liste déroulante.|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Récupère le menu contextuel du parent de l’image de la liste déroulante.|
|`CMFCDropDownFrame::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Repositionne le frame de la liste déroulante.|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Définit si la fenêtre de la barre d’outils déroulante enfant est supprimée automatiquement.|

### <a name="remarks"></a>Notes

Cette classe n’est pas destinée à être utilisée directement à partir de votre code.

L’infrastructure utilise cette classe pour fournir un comportement frame le `CMFCDropDownToolbar` et `CMFCDropDownToolbarButton` classes. Pour plus d’informations sur ces classes, consultez [CMFCDropDownToolbar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md) et [cmfcdropdowntoolbarbutton, classe](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer un pointeur vers un `CMFCDropDownFrame` de l’objet à partir d’un `CFrameWnd` classe et comment définir l’enfant de fenêtre de la barre d’outils de la liste déroulante d’être détruit automatiquement.

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

##  <a name="create"></a>  CMFCDropDownFrame::Create

Crée un objet `CMFCDropDownFrame`.

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
|*pWndParent*|[in] La fenêtre parente de l’image de la liste déroulante.|
|*x*|[in] Coordonnée d’écran horizontale pour l’emplacement de l’image du bas vers le bas.|
|*y*|[in] Coordonnée d’écran verticale pour l’emplacement de l’image du bas vers le bas.|
|*pWndOriginToolbar*|[in] La barre d’outils qui affiche les boutons de liste déroulante que cette méthode utilise pour remplir le nouvel objet de frame de la liste déroulante.|

### <a name="return-value"></a>Valeur de retour

TRUE si le frame de la liste déroulante a été créé avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode appelle la base de [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) pour créer la fenêtre frame de la liste déroulante avec le style WS_POPUP (méthode). La fenêtre frame de la liste déroulante apparaît en coordonnées d’écran spécifiées. Cette méthode échoue si le [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) méthode retourne FALSE.

Le `CMFCDropDownFrame` classe crée une copie de la liste fournie `CMFCDropDownToolBar` paramètre. Cette méthode copie les images des boutons et les États de bouton à partir de la `pWndOriginToolbar` paramètre à la `m_pWndOriginToolbar` membre de données.

##  <a name="getparentmenubar"></a>  CMFCDropDownFrame::GetParentMenuBar

Récupère la barre de menu parent de l’image de la liste déroulante.

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la barre de menu parent du cadre de la liste déroulante, ou NULL si le frame n’a aucun parent.

### <a name="remarks"></a>Notes

Cette méthode récupère la barre de menus du parent à partir du bouton parent. Cette méthode retourne NULL si le frame de la liste déroulante n’a pas de bouton parent ou le bouton parent aucune barre de menu parent.

##  <a name="getparentpopupmenu"></a>  CMFCDropDownFrame::GetParentPopupMenu

Récupère le menu contextuel du parent de l’image de la liste déroulante.

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le menu déroulant parent du cadre de la liste déroulante, ou NULL si le frame n’a aucun parent.

### <a name="remarks"></a>Notes

Cette méthode récupère le menu parent à partir du bouton parent. Cette méthode retourne NULL si le frame de la liste déroulante n’a pas de bouton parent ou le bouton parent aucun menu parent.

##  <a name="recalclayout"></a>  CMFCDropDownFrame::RecalcLayout

Repositionne le frame de la liste déroulante.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*bNotify*|[in] Inutilisé.|

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsque le frame de la liste déroulante est créé, ou la fenêtre parent est redimensionnée. Cette méthode calcule la position et la taille de l’image de la liste déroulante à l’aide de la position et la taille de la fenêtre parente.

##  <a name="setautodestroy"></a>  CMFCDropDownFrame::SetAutoDestroy

Définit si la fenêtre de la barre d’outils déroulante enfant est supprimée automatiquement.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoDestroy*<br/>
[in] TRUE pour détruire automatiquement la fenêtre de la barre d’outils de liste déroulante associée. Sinon, FALSE.

### <a name="remarks"></a>Notes

Si *bAutoDestroy* a la valeur TRUE, le `CMFCDropDownFrame` destructeur détruit la fenêtre de la barre d’outils de liste déroulante associée. La valeur par défaut est TRUE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton, classe](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
