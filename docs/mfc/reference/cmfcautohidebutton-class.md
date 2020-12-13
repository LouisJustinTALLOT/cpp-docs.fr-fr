---
description: 'En savoir plus sur : classe Cmfcautohidebutton,'
title: Cmfcautohidebutton,, classe
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
ms.openlocfilehash: 9d100417193ea8a757b02b9cc8fad0cdedf668f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336573"
---
# <a name="cmfcautohidebutton-class"></a>Cmfcautohidebutton,, classe

Bouton qui affiche ou masque une [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) configurée pour être masquée.

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

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
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Retourne l’objet [CDockablePane](../../mfc/reference/cdockablepane-class.md) associé au bouton de masquage automatique.|
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
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Affiche ou masque la [classe CDockablePane](../../mfc/reference/cdockablepane-class.md)associée.|
|[CMFCAutoHideButton::ShowButton](#showbutton)|Affiche ou masque le bouton masquer automatiquement.|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>Notes

À la création, l' `CMFCAutoHideButton` objet est attaché à une [classe CDockablePane](../../mfc/reference/cdockablepane-class.md). L'objet `CDockablePane` est masqué ou affiché quand l'utilisateur interagit avec l'objet `CMFCAutoHideButton`.

Par défaut, l'infrastructure crée automatiquement un `CMFCAutoHideButton` quand l'utilisateur active le bouton masquer automatiquement. L'infrastructure peut créer un élément d'une classe d'interface utilisateur personnalisée à la place de la classe `CMFCAutoHideButton`. Pour spécifier la classe d'interface utilisateur personnalisée que l'infrastructure doit utiliser, attribuez à la variable de membre statique `CMFCAutoHideBar::m_pAutoHideButtonRTS` la même valeur que la classe d'interface utilisateur personnalisée. Par défaut, cette valeur est définie sur `CMFCAutoHideButton`.

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet `CMFCAutoHideButton` et utiliser différentes méthodes de la classe `CMFCAutoHideButton`. L'exemple montre comment initialiser un objet `CMFCAutoHideButton` en utilisant sa méthode `Create`, afficher la classe `CDockablePane` associée et afficher le bouton masquer automatiquement.

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a> Cmfcautohidebutton, :: BringToTop

```cpp
void BringToTop();
```

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a> Cmfcautohidebutton, :: Create

Crée et initialise un bouton de masquage automatique.

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Paramètres

*pParentBar*<br/>
dans Pointeur vers la barre d’outils parente.

*pAutoHideWnd*<br/>
dans Pointeur vers un objet [CDockablePane](../../mfc/reference/cdockablepane-class.md) . Ce bouton de masquage automatique le masque et l’affiche `CDockablePane` .

*dwAlignment*<br/>
dans Valeur qui spécifie l’alignement du bouton avec la fenêtre frame principale.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Lorsque vous créez un `CMFCAutoHideButton` objet, vous devez associer le bouton Masquer automatiquement à un spécifique `CDockablePane` . L’utilisateur peut utiliser le bouton Masquer automatiquement pour masquer et afficher le associé `CDockablePane` .

Le paramètre *dwAlignment* indique où le bouton de masquage automatique réside dans l’application. Le paramètre peut avoir l’une des valeurs suivantes :

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a> Cmfcautohidebutton, :: GetAlignment

Récupère l'alignement du bouton masquer automatiquement.

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur DWORD qui contient l’alignement actuel du bouton Masquer automatiquement.

### <a name="remarks"></a>Notes

L’alignement du bouton Masquer automatiquement indique où le bouton réside sur l’application. Il peut s’agir de l’une des valeurs suivantes :

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a> Cmfcautohidebutton, :: GetAutoHideWindow

Retourne l’objet [CDockablePane](../../mfc/reference/cdockablepane-class.md) associé au bouton de masquage automatique.

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet associé `CDockablePane` .

### <a name="remarks"></a>Notes

Pour associer un bouton de masquage automatique à un `CDockablePane` , transmettez le `CDockablePane` en tant que paramètre à la méthode [Cmfcautohidebutton, :: Create](#create) .

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a> Cmfcautohidebutton, :: GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a> Cmfcautohidebutton, :: GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a> Cmfcautohidebutton, :: est à obtenir

Détermine la taille du bouton masquer automatiquement.

```
CSize GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

`CSize`Objet qui contient la taille du bouton.

### <a name="remarks"></a>Notes

La taille calculée comprend la taille de la bordure du bouton Masquer automatiquement.

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a> Cmfcautohidebutton, :: GetTextSize

Retourne la taille de l'étiquette de texte du bouton masquer automatiquement.

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet [CSize](../../atl-mfc-shared/reference/csize-class.md) qui contient la taille du texte pour le bouton Masquer automatiquement.

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a> Cmfcautohidebutton, :: IsActive

Indique si le bouton masquer automatiquement est actif.

```
BOOL IsActive() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton Masquer automatiquement est actif ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Un bouton Masquer automatiquement est actif lorsque la fenêtre de la [classe CDockablePane](../../mfc/reference/cdockablepane-class.md) associée est affichée.

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a> Cmfcautohidebutton, :: IsHorizontal

Détermine si le bouton masquer automatiquement est horizontal ou vertical.

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le bouton est horizontal ; Sinon, 0.

### <a name="remarks"></a>Notes

L’infrastructure définit l’orientation d’un objet [cmfcautohidebutton,](../../mfc/reference/cmfcautohidebutton-class.md) lorsque vous le créez.  Vous pouvez contrôler l’orientation à l’aide du paramètre *dwAlignment* dans la méthode [Cmfcautohidebutton, :: Create](#create) .

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a> Cmfcautohidebutton, :: IsTop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a> Cmfcautohidebutton, :: IsVisible

Indique si le bouton Masquer automatiquement est visible.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton est visible ; FALSe dans le cas contraire.

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a> Cmfcautohidebutton, :: OnDraw

L'infrastructure appelle cette méthode au moment de dessiner le bouton masquer automatiquement.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

### <a name="remarks"></a>Notes

Si vous souhaitez personnaliser l’apparence des boutons Masquer automatiquement dans votre application, créez une nouvelle classe dérivée de `CMFCAutoHideButton` . Dans votre classe dérivée, substituez cette méthode.

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a> Cmfcautohidebutton, :: OnDrawBorder

L'infrastructure appelle cette méthode au moment de dessiner la bordure d'un bouton masquer automatiquement.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectBounds*<br/>
dans Rectangle englobant du bouton Masquer automatiquement.

*rectBorderSize*<br/>
dans Épaisseur de la bordure de chaque côté du bouton Masquer automatiquement.

### <a name="remarks"></a>Notes

Si vous souhaitez personnaliser la bordure de chaque bouton Masquer automatiquement dans votre application, créez une nouvelle classe dérivée de `CMFCAutoHideButton` . Dans votre classe dérivée, substituez cette méthode.

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a> Cmfcautohidebutton, :: OnFillBackground

L'infrastructure appelle cette méthode au moment de remplir l'arrière-plan d'un bouton masquer automatiquement.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectangulaire*<br/>
dans Rectangle englobant du bouton Masquer automatiquement.

### <a name="remarks"></a>Notes

Si vous souhaitez personnaliser l’arrière-plan des boutons de masquage automatique dans votre application, créez une classe dérivée de `CMFCAutoHideButton` . Dans votre classe dérivée, substituez cette méthode.

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a> Cmfcautohidebutton, :: ShowAttachedWindow

Affiche ou masque la [classe CDockablePane](../../mfc/reference/cdockablepane-class.md)associée.

```cpp
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
dans Valeur booléenne qui spécifie si cette méthode affiche le attaché `CDockablePane` .

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a> Cmfcautohidebutton, :: ShowButton

Affiche ou masque le bouton masquer automatiquement.

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
dans Valeur booléenne qui spécifie s’il faut afficher le bouton Masquer automatiquement.

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a> Cmfcautohidebutton, :: Move

```cpp
void Move(int nOffset);
```

### <a name="parameters"></a>Paramètres

dans *nOffset*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a> Cmfcautohidebutton, :: ReplacePane

```cpp
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>Paramètres

dans *pNewBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a> Cmfcautohidebutton, :: UnSetAutoHideMode

Désactivez le mode de masquage automatique.

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>Paramètres

*pFirstBarInGroup*<br/>
dans Pointeur vers la première barre du groupe.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a> Cmfcautohidebutton, :: HighlightButton

Met en surbrillance le bouton Masquer automatiquement.

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>Paramètres

*bHighlight*<br/>
Spécifie le nouvel État du bouton Masquer automatiquement. TRUE indique que le bouton est mis en surbrillance, FALSe indique que le bouton n’est pas mis en surbrillance.

### <a name="remarks"></a>Notes

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a> Cmfcautohidebutton, :: IsHighlighted

Retourne l’état de mise en surbrillance du bouton Masquer automatiquement.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le bouton Masquer automatiquement est mis en surbrillance ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar, classe](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite, classe](../../mfc/reference/cautohidedocksite-class.md)
