---
description: 'En savoir plus sur : CScrollView, classe'
title: CScrollView (classe)
ms.date: 11/04/2016
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
ms.openlocfilehash: 76045f640cf74b650fbbf48dead7ee44c57fbd87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342902"
---
# <a name="cscrollview-class"></a>CScrollView (classe)

[CView](../../mfc/reference/cview-class.md) avec fonctions de défilement.

## <a name="syntax"></a>Syntaxe

```
class CScrollView : public CView
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CScrollView :: CScrollView](#cscrollview)|Construit un objet `CScrollView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CScrollView :: CheckScrollBars](#checkscrollbars)|Indique si l’affichage de défilement a des barres de défilement horizontales et verticales.|
|[CScrollView :: FillOutsideRect](#filloutsiderect)|Remplit la zone d’une vue à l’extérieur de la zone de défilement.|
|[CScrollView :: GetDeviceScrollPosition](#getdevicescrollposition)|Obtient la position de défilement actuelle en unités de périphérique.|
|[CScrollView :: GetDeviceScrollSizes](#getdevicescrollsizes)|Obtient le mode de mappage actuel, la taille totale et les tailles de ligne et de page de l’affichage défilant. Les tailles sont exprimées en unités de périphérique.|
|[CScrollView :: GetScrollPosition](#getscrollposition)|Obtient la position de défilement actuelle en unités logiques.|
|[CScrollView :: GetTotalSize](#gettotalsize)|Obtient la taille totale de la vue de défilement en unités logiques.|
|[CScrollView :: ResizeParentToFit](#resizeparenttofit)|Fait en sorte que la taille de la vue dicte la taille de son frame.|
|[CScrollView :: ScrollToPosition](#scrolltoposition)|Fait défiler la vue jusqu’à un point donné, spécifié en unités logiques.|
|[CScrollView :: SetScaleToFitSize](#setscaletofitsize)|Place la vue de défilement en mode de mise à l’échelle adaptée.|
|[CScrollView :: SetScrollSizes](#setscrollsizes)|Définit le mode de mappage de la vue de défilement, la taille totale et les valeurs de défilement horizontales et verticales.|

## <a name="remarks"></a>Notes

Vous pouvez gérer vous-même le défilement standard dans toute classe dérivée de `CView` en substituant les fonctions membres [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) mappées par message. Mais `CScrollView` ajoute les fonctionnalités suivantes à ses `CView` fonctionnalités :

- Il gère les tailles des fenêtres et des Viewports et les modes de mappage.

- Elle défile automatiquement en réponse aux messages de la barre de défilement.

- Elle défile automatiquement en réponse aux messages du clavier, à une souris sans défilement ou à la roulette IntelliMouse.

Pour faire défiler automatiquement les messages du clavier, ajoutez un message WM_KEYDOWN et testez VK_DOWN, VK_PREV et appelez [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos).

Vous pouvez gérer vous-même le défilement de la roulette de la souris en remplaçant les fonctions membres mappées par le message [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) et [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) . Comme pour `CScrollView` , ces fonctions membres prennent en charge le comportement recommandé pour [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel), le message de rotation de la roulette.

Pour tirer parti du défilement automatique, dérivez votre classe d’affichage de `CScrollView` au lieu de `CView` . Lorsque la vue est créée pour la première fois, si vous souhaitez calculer la taille de l’affichage à défilement en fonction de la taille du document, appelez la `SetScrollSizes` fonction membre à partir de la substitution de [CView :: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) ou [CView :: OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Vous devez écrire votre propre code pour interroger la taille du document. Pour obtenir un exemple, consultez l' [exemple SCRIBBLE](../../overview/visual-cpp-samples.md).)

L’appel à la `SetScrollSizes` fonction membre définit le mode de mappage de la vue, les dimensions totales de l’affichage de défilement et les quantités à faire défiler horizontalement et verticalement. Toutes les tailles sont exprimées en unités logiques. La taille logique de la vue est généralement calculée à partir des données stockées dans le document, mais dans certains cas, vous souhaiterez peut-être spécifier une taille fixe. Pour obtenir des exemples des deux approches, consultez [CScrollView :: SetScrollSizes](#setscrollsizes).

Vous spécifiez les quantités à faire défiler horizontalement et verticalement en unités logiques. Par défaut, si l’utilisateur clique sur un arbre de barre de défilement en dehors de la case de défilement, `CScrollView` fait défiler une « page ». Si l’utilisateur clique sur une flèche de défilement à l’une des extrémités d’une barre de défilement, `CScrollView` fait défiler une « ligne ». Par défaut, une page est 1/10 de la taille totale de la vue. une ligne est 1/10 de la taille de la page. Remplacez ces valeurs par défaut en passant des tailles personnalisées dans la `SetScrollSizes` fonction membre. Par exemple, vous pouvez définir la taille horizontale à une fraction de la largeur de la taille totale et la taille verticale à la hauteur d’une ligne dans la police actuelle.

Au lieu de faire défiler, `CScrollView` peut automatiquement mettre à l’échelle la vue à la taille de fenêtre actuelle. Dans ce mode, la vue n’a pas de barres de défilement et la vue logique est étirée ou rétrécie pour correspondre exactement à la zone cliente de la fenêtre. Pour utiliser cette fonctionnalité de montée en puissance parallèle, appelez [CScrollView :: SetScaleToFitSize](#setscaletofitsize). (Appelez `SetScaleToFitSize` ou `SetScrollSizes` , mais pas les deux.)

Avant que la `OnDraw` fonction membre de votre classe de vue dérivée ne soit appelée, `CScrollView` ajuste automatiquement l’origine de la fenêtre d’affichage pour l' `CPaintDC` objet de contexte de périphérique auquel elle est transmise `OnDraw` .

Pour ajuster l’origine de la fenêtre de défilement, `CScrollView` remplace [CView :: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Cet ajustement est automatique pour le `CPaintDC` contexte de périphérique qui est `CScrollView` passé à `OnDraw` , mais vous devez vous appeler `CScrollView::OnPrepareDC` pour tous les contextes de périphérique que vous utilisez, par exemple, `CClientDC` . Vous pouvez substituer `CScrollView::OnPrepareDC` pour définir le stylet, la couleur d’arrière-plan et d’autres attributs de dessin, mais appeler la classe de base pour effectuer une mise à l’échelle.

Les barres de défilement peuvent apparaître à trois emplacements par rapport à une vue, comme indiqué dans les cas suivants :

- Les barres de défilement de style fenêtre standard peuvent être définies pour la vue à l’aide de la WS_HSCROLL et WS_VSCROLL[styles Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles).

- Les contrôles de barre de défilement peuvent également être ajoutés au frame contenant la vue, auquel cas l’infrastructure transfère les messages WM_HSCROLL et WM_VSCROLL de la fenêtre frame à la vue actuellement active.

- L’infrastructure transfère également les messages de défilement d’un `CSplitterWnd` contrôle Splitter vers le volet Splitter actuellement actif (une vue). Lorsqu’il est placé dans un [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) avec des barres de défilement partagées, un `CScrollView` objet utilise les éléments partagés au lieu de créer son propre.

Pour plus d’informations sur l’utilisation de `CScrollView` , consultez [architecture document/vue](../../mfc/document-view-architecture.md) et [classes de vue dérivée disponibles dans MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a> CScrollView :: CheckScrollBars

Appelez cette fonction membre pour déterminer si l’affichage de défilement a des barres verticales et horizontales.

```cpp
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Paramètres

*bHasHorzBar*<br/>
Indique que l’application a une barre de défilement horizontale.

*bHasVertBar*<br/>
Indique que l’application a une barre de défilement verticale.

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a> CScrollView :: CScrollView

Construit un objet `CScrollView`.

```
CScrollView();
```

### <a name="remarks"></a>Notes

Vous devez appeler `SetScrollSizes` ou `SetScaleToFitSize` avant que l’affichage de défilement soit utilisable.

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a> CScrollView :: FillOutsideRect

Appelez `FillOutsideRect` pour remplir la zone de la vue qui apparaît en dehors de la zone de défilement.

```cpp
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Contexte de périphérique dans lequel le remplissage doit être effectué.

*pBrush*<br/>
Pinceau avec lequel la zone doit être remplie.

### <a name="remarks"></a>Notes

Utilisez `FillOutsideRect` dans la fonction de gestionnaire de votre vue de défilement `OnEraseBkgnd` pour empêcher un redessin d’arrière-plan excessif.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a> CScrollView :: GetDeviceScrollPosition

Appelez `GetDeviceScrollPosition` lorsque vous avez besoin des positions horizontale et verticale actuelles des cases de défilement dans les barres de défilement.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Valeur renvoyée

Positions horizontales et verticales (en unités de périphérique) des cases de défilement comme un `CPoint` objet.

### <a name="remarks"></a>Notes

Cette paire de coordonnées correspond à l’emplacement dans le document dans lequel l’angle supérieur gauche de la vue a été défilé. Cela est utile pour décaler les positions des appareils de la souris sur les positions des appareils de défilement.

`GetDeviceScrollPosition` retourne des valeurs en unités de périphérique. Si vous souhaitez des unités logiques, utilisez à la `GetScrollPosition` place.

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a> CScrollView :: GetDeviceScrollSizes

`GetDeviceScrollSizes` Obtient le mode de mappage actuel, la taille totale et les tailles de ligne et de page de l’affichage défilant.

```cpp
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Paramètres

*nMapMode*<br/>
Retourne le mode de mappage actuel pour cette vue. Pour obtenir la liste des valeurs possibles, consultez `SetScrollSizes`.

*sizeTotal*<br/>
Retourne la taille totale actuelle de la vue de défilement dans les unités de périphérique.

*sizePage*<br/>
Retourne les quantités horizontales et verticales actuelles à faire défiler dans chaque direction en réponse à un clic de souris dans un arbre de barre de défilement. Le `cx` membre contient le montant horizontal. Le `cy` membre contient le montant vertical.

*sizeLine*<br/>
Retourne les quantités horizontales et verticales actuelles à faire défiler dans chaque direction en réponse à un clic de souris dans une flèche de défilement. Le `cx` membre contient le montant horizontal. Le `cy` membre contient le montant vertical.

### <a name="remarks"></a>Notes

Les tailles sont exprimées en unités de périphérique. Cette fonction membre est rarement appelée.

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a> CScrollView :: GetScrollPosition

Appelez `GetScrollPosition` lorsque vous avez besoin des positions horizontale et verticale actuelles des cases de défilement dans les barres de défilement.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Valeur renvoyée

Positions horizontales et verticales (en unités logiques) des zones de défilement comme un `CPoint` objet.

### <a name="remarks"></a>Notes

Cette paire de coordonnées correspond à l’emplacement dans le document dans lequel l’angle supérieur gauche de la vue a été défilé.

`GetScrollPosition` retourne des valeurs en unités logiques. Si vous souhaitez utiliser des unités de périphérique, utilisez à la `GetDeviceScrollPosition` place.

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a> CScrollView :: GetTotalSize

Appelez `GetTotalSize` pour récupérer les tailles horizontale et verticale actuelles de l’affichage de défilement.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille totale de l’affichage de défilement en unités logiques. La taille horizontale est dans le `cx` membre de la `CSize` valeur de retour. La taille verticale est dans le `cy` membre.

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a> CScrollView :: ResizeParentToFit

Appelez `ResizeParentToFit` pour permettre à la taille de votre vue de dicter la taille de sa fenêtre frame.

```cpp
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Paramètres

*bShrinkOnly*<br/>
Type de redimensionnement à effectuer. La valeur par défaut, TRUE, réduit la fenêtre frame, le cas échéant. Les barres de défilement s’affichent toujours pour les grandes vues ou les petites fenêtres Frame. Si la valeur est FALSe, la vue doit toujours redimensionner la fenêtre frame exactement. Cela peut être quelque peu dangereux dans la mesure où la fenêtre frame peut être trop grande pour s’ajuster à la fenêtre frame MDI (multiple document interface) ou à l’écran.

### <a name="remarks"></a>Notes

Cela est recommandé uniquement pour les vues dans les fenêtres frame MDI enfant. Utilisez `ResizeParentToFit` dans la `OnInitialUpdate` fonction de gestionnaire de votre `CScrollView` classe dérivée. Pour obtenir un exemple de cette fonction membre, consultez [CScrollView :: SetScrollSizes](#setscrollsizes).

`ResizeParentToFit` suppose que la taille de la fenêtre d’affichage a été définie. Si la taille de la fenêtre d’affichage n’a pas été définie lorsque `ResizeParentToFit` est appelé, vous obtiendrez une assertion. Pour vous assurer que cela ne se produit pas, effectuez l’appel suivant avant d’appeler `ResizeParentToFit` :

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a> CScrollView :: ScrollToPosition

Appelez `ScrollToPosition` pour faire défiler jusqu’à un point donné dans la vue.

```cpp
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Point vers lequel défiler, en unités logiques. Le `x` membre doit être une valeur positive (supérieure ou égale à 0, jusqu’à la taille totale de la vue). Il en va de même pour le `y` membre lorsque le mode de mappage est MM_TEXT. Le `y` membre est négatif dans les modes de mappage autres que MM_TEXT.

### <a name="remarks"></a>Notes

La vue défilera afin que ce point se trouve dans l’angle supérieur gauche de la fenêtre. Cette fonction membre ne doit pas être appelée si la vue est mise à l’échelle pour s’ajuster.

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a> CScrollView :: SetScaleToFitSize

Appelez `SetScaleToFitSize` lorsque vous souhaitez mettre à l’échelle automatiquement la taille de la fenêtre d’affichage avec la taille de fenêtre actuelle.

```cpp
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Paramètres

*sizeTotal*<br/>
Tailles horizontale et verticale auxquelles la vue doit être mise à l’échelle. La taille de l’affichage de défilement est mesurée en unités logiques. La taille horizontale est contenue dans le `cx` membre. La taille verticale est contenue dans le `cy` membre. `cx`Et `cy` doivent être supérieurs ou égaux à 0.

### <a name="remarks"></a>Notes

Avec les barres de défilement, seule une partie de la vue logique peut être visible à tout moment. Toutefois, avec la capacité de mise à l’échelle, la vue n’a pas de barres de défilement et la vue logique est étirée ou rétrécie pour correspondre exactement à la zone cliente de la fenêtre. Lorsque la fenêtre est redimensionnée, la vue dessine ses données à une nouvelle échelle en fonction de la taille de la fenêtre.

En général, vous placez l’appel à `SetScaleToFitSize` dans votre remplacement de la fonction membre de la vue `OnInitialUpdate` . Si vous ne souhaitez pas mettre à l’échelle automatiquement, appelez la `SetScrollSizes` fonction membre à la place.

`SetScaleToFitSize` peut être utilisé pour implémenter une opération « zoom pour ajuster ». Utilisez `SetScrollSizes` pour réinitialiser le défilement.

`SetScaleToFitSize` suppose que la taille de la fenêtre d’affichage a été définie. Si la taille de la fenêtre d’affichage n’a pas été définie lorsque `SetScaleToFitSize` est appelé, vous obtiendrez une assertion. Pour vous assurer que cela ne se produit pas, effectuez l’appel suivant avant d’appeler `SetScaleToFitSize` :

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a> CScrollView :: SetScrollSizes

Appelez `SetScrollSizes` lorsque la vue va être mise à jour.

```cpp
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Paramètres

*nMapMode*<br/>
Mode de mappage à définir pour cette vue. Les valeurs possibles incluent :

|Mode de mappage|Unité logique|L’axe des y positif s’étend...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 pixel|Diagonale|
|MM_HIMETRIC|0,01 mm|Supérieures|
|MM_TWIPS|1/1440 dans|Supérieures|
|MM_HIENGLISH|0,001 dans|Supérieures|
|MM_LOMETRIC|0,1 mm|Supérieures|
|MM_LOENGLISH|0,01 dans|Supérieures|

Tous ces modes sont définis par Windows. Deux modes de mappage standard, MM_ISOTROPIC et MM_ANISOTROPIC, ne sont pas utilisés pour `CScrollView` . La bibliothèque de classes fournit la `SetScaleToFitSize` fonction membre pour la mise à l’échelle de l’affichage à la taille de la fenêtre. La colonne trois du tableau ci-dessus décrit l’orientation des coordonnées.

*sizeTotal*<br/>
Taille totale de l’affichage de défilement. Le `cx` membre contient l’étendue horizontale. Le `cy` membre contient l’étendue verticale. Les tailles sont exprimées en unités logiques. `cx`Et `cy` doivent être supérieurs ou égaux à 0.

*sizePage*<br/>
Les valeurs horizontales et verticales à faire défiler dans chaque direction en réponse à un clic de souris dans un arbre de barre de défilement. Le `cx` membre contient le montant horizontal. Le `cy` membre contient le montant vertical.

*sizeLine*<br/>
Valeurs horizontales et verticales à faire défiler dans chaque direction en réponse à un clic de souris dans une flèche de défilement. Le `cx` membre contient le montant horizontal. Le `cy` membre contient le montant vertical.

### <a name="remarks"></a>Notes

Appelez-la dans votre remplacement de la `OnUpdate` fonction membre pour ajuster les caractéristiques de défilement lorsque, par exemple, le document est affiché initialement ou lorsqu’il change de taille.

Vous obtiendrez généralement des informations sur la taille à partir du document associé à la vue en appelant une fonction membre du document, éventuellement appelée `GetMyDocSize` , que vous fournissez avec votre classe de document dérivée. Le code suivant illustre cette approche :

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Vous pouvez également être amené à définir une taille fixe, comme dans le code suivant :

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Vous devez définir le mode de mappage sur l’un des modes de mappage Windows, à l’exception de MM_ISOTROPIC ou MM_ANISOTROPIC. Si vous souhaitez utiliser un mode de mappage sans contrainte, appelez la `SetScaleToFitSize` fonction membre à la place de `SetScrollSizes` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd, classe](../../mfc/reference/csplitterwnd-class.md)
