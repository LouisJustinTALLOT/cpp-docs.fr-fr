---
title: CMFCAutoHideButton, classe
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
ms.openlocfilehash: 3ea6ce13b8cca7e0130fe14459a832b476391b0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751674"
---
# <a name="cmfcautohidebutton-class"></a>CMFCAutoHideButton, classe

Bouton qui affiche ou masque une [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) configurée pour être masquée.

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)|Crée et initialise les bouton masquer automatiquement.|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Récupère l'alignement du bouton masquer automatiquement.|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Retourne l’objet [CDockablePane](../../mfc/reference/cdockablepane-class.md) associé au bouton de cache automatique.|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|Détermine la taille du bouton masquer automatiquement.|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Retourne la taille de l'étiquette de texte du bouton masquer automatiquement.|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Met en évidence le bouton masquer automatiquement.|
|[CMFCAutoHideButton::IsActive](#isactive)|Indique si le bouton masquer automatiquement est actif.|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Fait état de la mise en évidence du bouton masquer automatiquement.|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Détermine si le bouton masquer automatiquement est horizontal ou vertical.|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|Indique si le bouton est visible.|
|[CMFCAutoHideButton::Move](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|L'infrastructure appelle cette méthode au moment de dessiner le bouton masquer automatiquement.|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|L'infrastructure appelle cette méthode au moment de dessiner la bordure d'un bouton masquer automatiquement.|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|L'infrastructure appelle cette méthode au moment de remplir l'arrière-plan d'un bouton masquer automatiquement.|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Affiche ou cache la [classe CDockablePane](../../mfc/reference/cdockablepane-class.md)associée .|
|[CMFCAutoHideButton::ShowButton](#showbutton)|Affiche ou masque le bouton masquer automatiquement.|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>Notes

Sur la `CMFCAutoHideButton` création, l’objet est attaché à une [classe CDockablePane](../../mfc/reference/cdockablepane-class.md). L'objet `CDockablePane` est masqué ou affiché quand l'utilisateur interagit avec l'objet `CMFCAutoHideButton`.

Par défaut, l'infrastructure crée automatiquement un `CMFCAutoHideButton` quand l'utilisateur active le bouton masquer automatiquement. L'infrastructure peut créer un élément d'une classe d'interface utilisateur personnalisée à la place de la classe `CMFCAutoHideButton`. Pour spécifier la classe d'interface utilisateur personnalisée que l'infrastructure doit utiliser, attribuez à la variable de membre statique `CMFCAutoHideBar::m_pAutoHideButtonRTS` la même valeur que la classe d'interface utilisateur personnalisée. Par défaut, cette variable a la valeur `CMFCAutoHideButton`.

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet `CMFCAutoHideButton` et utiliser différentes méthodes de la classe `CMFCAutoHideButton`. L'exemple montre comment initialiser un objet `CMFCAutoHideButton` en utilisant sa méthode `Create`, afficher la classe `CDockablePane` associée et afficher le bouton masquer automatiquement.

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a>CMFCAutoHideButton::BringToTop

```cpp
void BringToTop();
```

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a>CMFCAutoHideButton::Créer

Crée et initialise un bouton de cache automatique.

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Paramètres

*pParentBar*<br/>
[dans] Un pointeur à la barre d’outils parent.

*pAutoHideWnd*<br/>
[dans] Un pointeur vers un objet [CDockablePane.](../../mfc/reference/cdockablepane-class.md) Ce bouton de cache automatique `CDockablePane`se cache et montre que .

*dwAlignment*<br/>
[dans] Une valeur qui spécifie l’alignement du bouton avec la fenêtre du cadre principal.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Lorsque vous `CMFCAutoHideButton` créez un objet, vous devez associer `CDockablePane`le bouton auto-cacher à un spécifique . L’utilisateur peut utiliser le bouton auto-cacher `CDockablePane`pour se cacher et afficher l’associé .

Le *paramètre dwAlignment* indique où se trouve le bouton de cache automatique dans l’application. Le paramètre peut avoir l’une des valeurs suivantes :

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a>CMFCAutoHideButton::GetAlignment

Récupère l'alignement du bouton masquer automatiquement.

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui contient l’alignement actuel du bouton de cache automatique.

### <a name="remarks"></a>Notes

L’alignement du bouton de cache automatique indique où se trouve le bouton sur l’application. Il peut s’agir de l’une des valeurs suivantes :

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a>CMFCAutoHideButton::GetAutoHideWindow

Retourne l’objet [CDockablePane](../../mfc/reference/cdockablepane-class.md) associé au bouton de cache automatique.

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CDockablePane` sur l’objet associé.

### <a name="remarks"></a>Notes

Pour associer un bouton de `CDockablePane`cache automatique `CDockablePane` à un , passez le comme paramètre à la [CMFCAutoHideButton::Créer la](#create) méthode.

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a>CMFCAutoHideButton::GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a>CMFCAutoHideButton::GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a>CMFCAutoHideButton::GetSize

Détermine la taille du bouton masquer automatiquement.

```
CSize GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CSize` objet qui contient la taille du bouton.

### <a name="remarks"></a>Notes

La taille calculée comprend la taille de la bordure du bouton de cache automatique.

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a>CMFCAutoHideButton::GetTextSize

Retourne la taille de l'étiquette de texte du bouton masquer automatiquement.

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>Valeur de retour

Un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) qui contient la taille du texte pour le bouton de cache automatique.

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a>CMFCAutoHideButton::IsActive

Indique si le bouton masquer automatiquement est actif.

```
BOOL IsActive() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton de cache automatique est actif; FALSE autrement.

### <a name="remarks"></a>Notes

Un bouton de cache automatique est actif lorsque la fenêtre [associée de la classe CDockablePane](../../mfc/reference/cdockablepane-class.md) est affichée.

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a>CMFCAutoHideButton::IsHorizontal

Détermine si le bouton masquer automatiquement est horizontal ou vertical.

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton est horizontal; 0 autrement.

### <a name="remarks"></a>Notes

Le cadre définit l’orientation d’un objet [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) lorsque vous le créez.  Vous pouvez contrôler l’orientation en utilisant le *paramètre dwAlignment* dans le [CMFCAutoHideButton::Créer la](#create) méthode.

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a>CMFCAutoHideButton::IsTop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a>CMFCAutoHideButton::IsVisible

Indique si le bouton de cache automatique est visible.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton est visible; FALSE autrement.

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a>CMFCAutoHideButton::OnDraw

L'infrastructure appelle cette méthode au moment de dessiner le bouton masquer automatiquement.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

### <a name="remarks"></a>Notes

Si vous souhaitez personnaliser l’apparence des boutons de cache automatique dans `CMFCAutoHideButton`votre application, créez une nouvelle classe dérivée de . Dans votre classe dérivée, remplacez cette méthode.

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a>CMFCAutoHideButton::OnDrawBorder

L'infrastructure appelle cette méthode au moment de dessiner la bordure d'un bouton masquer automatiquement.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*rectBounds (rectBounds)*<br/>
[dans] Le rectangle de délimitation du bouton auto-cacher.

*rectBorderSize*<br/>
[dans] L’épaisseur de la bordure de chaque côté du bouton de cache automatique.

### <a name="remarks"></a>Notes

Si vous souhaitez personnaliser la bordure de chaque bouton de cache automatique dans `CMFCAutoHideButton`votre application, créez une nouvelle classe dérivée de la . Dans votre classe dérivée, remplacez cette méthode.

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a>CMFCAutoHideButton::OnFillBackground

L'infrastructure appelle cette méthode au moment de remplir l'arrière-plan d'un bouton masquer automatiquement.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Le rectangle de délimitation du bouton auto-cacher.

### <a name="remarks"></a>Notes

Si vous souhaitez personnaliser l’arrière-plan pour les boutons de cache automatique `CMFCAutoHideButton`dans votre application, créez une nouvelle classe dérivée de la . Dans votre classe dérivée, remplacez cette méthode.

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a>CMFCAutoHideButton::ShowAttachedWindow

Affiche ou cache la [classe CDockablePane](../../mfc/reference/cdockablepane-class.md)associée .

```cpp
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
[dans] Un Boolean qui précise si cette `CDockablePane`méthode montre l’attaché .

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a>CMFCAutoHideButton::ShowButton

Affiche ou masque le bouton masquer automatiquement.

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
[dans] Un Boolean qui précise s’il faut afficher le bouton de cache automatique.

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a>CMFCAutoHideButton::Déplacer

```cpp
void Move(int nOffset);
```

### <a name="parameters"></a>Paramètres

[dans] *nOffset (en anglais)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a>CMFCAutoHideButton::ReplacePane

```cpp
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>Paramètres

[dans] *pNewBar (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideButton::UnSetAutoHideMode

Désactivez le mode de masquage automatique.

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>Paramètres

*pFirstBarInGroup*<br/>
[dans] Un pointeur à la première barre du groupe.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a>CMFCAutoHideButton::HighlightButton

Met en évidence le bouton de peau d’auto.

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>Paramètres

*bHighlight (en)*<br/>
Spécifie le nouvel état du bouton de cache automatique. TRUE indique que le bouton est surligné, FALSE indique que le bouton n’est pas surligné.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a>CMFCAutoHideButton::IsHighlighted

Retourne l’état de surbrillance du bouton de peau d’auto.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le bouton de cache automatique est mis en surbrillance; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar, classe](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[Classe CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)
