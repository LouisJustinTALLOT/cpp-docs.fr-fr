---
title: CScrollView, classe
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
ms.openlocfilehash: d60082092bd42fbe220eee08953ad5fda0ff0a85
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339583"
---
# <a name="cscrollview-class"></a>CScrollView, classe

Un [CView](../../mfc/reference/cview-class.md) avec les possibilités de défilement.

## <a name="syntax"></a>Syntaxe

```
class CScrollView : public CView
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Construit un objet `CScrollView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Indique si l’affichage du défilement possède des barres de défilement horizontale et verticale.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Remplit la zone d’une vue en dehors de la zone de défilement.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Obtient la position de défilement actuelle en unités de périphérique.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Obtient le mode de mappage actuel, la taille totale et les tailles de page et de ligne de la vue à défilement. Tailles sont exprimées en unités de périphérique.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Obtient la position de défilement actuelle en unités logiques.|
|[CScrollView::GetTotalSize](#gettotalsize)|Obtient la taille totale de l’affichage du défilement en unités logiques.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Provoque la taille de la vue pour déterminer la taille de son cadre.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Fait défiler la vue à un moment donné, spécifié en unités logiques.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Place l’affichage du défilement en mode de mise à l’échelle à ajuster.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Définit le mode de mappage de l’affichage du défilement, la taille totale et quantités de défilement horizontales et verticales.|

## <a name="remarks"></a>Notes

Vous pouvez gérer vous-même le défilement dans une classe dérivée à partir de standard `CView` en substituant le message mappé [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) fonctions membres. Mais `CScrollView` ajoute les fonctionnalités suivantes pour son `CView` fonctionnalités :

- Il gère les tailles de fenêtre et de la fenêtre d’affichage et les modes de mappage.

- Fait défiler automatiquement en réponse aux messages de la barre de défilement.

- Fait défiler automatiquement en réponse aux messages à partir du clavier, une souris sans défilement ou la roulette.

Pour faire défiler automatiquement en réponse aux messages à partir du clavier, ajoutez un message WM_KEYDOWN et de test pour VK_DOWN, VK_PREV et appeler [SetScrollPos](/windows/desktop/api/winuser/nf-winuser-setscrollpos).

Vous pouvez gérer la roulette de défilement vous-même en substituant le message mappé [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) et [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) fonctions membres. Comme pour les `CScrollView`, ces fonctions membres prennent en charge le comportement recommandé pour [WM_MOUSEWHEEL](/windows/desktop/inputdev/wm-mousewheel), le message de rotation de roulette.

Pour tirer parti du défilement automatique, dérivez votre classe de vue de `CScrollView` au lieu d’à partir de `CView`. Lorsque la vue est tout d’abord créée, si vous souhaitez calculer la taille de la vue à défilement selon la taille du document, appel le `SetScrollSizes` fonction membre à partir de votre substitution de soit [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) ou [ CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Vous devez écrire votre propre code pour interroger la taille du document. Pour obtenir un exemple, consultez le [exemple Scribble](../../overview/visual-cpp-samples.md).)

L’appel à la `SetScrollSizes` fonction membre définit le mode de mappage de la vue, le nombre total de dimensions de la vue de défilement et les quantités pour faire défiler horizontalement et verticalement. Toutes les tailles sont exprimées en unités logiques. La taille logique de la vue est généralement calculée à partir des données stockées dans le document, mais dans certains cas vous pouvez spécifier une taille fixe. Pour obtenir des exemples des deux approches, consultez [CScrollView::SetScrollSizes](#setscrollsizes).

Vous pouvez spécifier la faire défiler horizontalement et verticalement en unités logiques. Par défaut, si l’utilisateur clique sur un arbre de barre de défilement en dehors de la case de défilement, `CScrollView` fait défiler une « page ». Si l’utilisateur clique sur une flèche de défilement aux deux extrémités d’une barre de défilement, `CScrollView` fait défiler une « ligne ». Par défaut, une page est de 1/10 de la taille totale de la vue ; une ligne est de 1/10 de la taille de page. Remplacer ces valeurs par défaut en passant des tailles personnalisées dans le `SetScrollSizes` fonction membre. Par exemple, vous pouvez définir la taille horizontale à une fraction de la largeur de la taille totale et la taille verticale de la hauteur d’une ligne dans la police actuelle.

Au lieu du défilement, `CScrollView` dimensionne automatiquement la vue à la taille de fenêtre actuelle. Dans ce mode, la vue ne comporte aucune barre de défilement et la vue logique est étirée ou rétrécie pour correspondre exactement à la zone la fenêtre client. Pour utiliser cette fonctionnalité de mise à l’échelle pour ajuster, appelez [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Appelez `SetScaleToFitSize` ou `SetScrollSizes`, mais pas les deux.)

Avant du `OnDraw` fonction membre de votre classe d’affichage dérivée est appelée, `CScrollView` ajuste automatiquement l’origine de la fenêtre d’affichage pour le `CPaintDC` objet de contexte de périphérique qu’il transmet au `OnDraw`.

Pour ajuster l’origine de la fenêtre d’affichage de la fenêtre de défilement `CScrollView` substitue [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Cet ajustement est automatique pour le `CPaintDC` contexte de périphérique qui `CScrollView` transmet à `OnDraw`, mais vous devez appeler `CScrollView::OnPrepareDC` vous-même pour toutes les autres contextes de périphérique vous utilisez, comme un `CClientDC`. Vous pouvez remplacer `CScrollView::OnPrepareDC` pour définir le stylet, couleur d’arrière-plan et autres attributs de dessins, mais appelle la classe de base pour faire la mise à l’échelle.

Barres de défilement peuvent apparaître dans trois emplacements par rapport à une vue, comme indiqué dans les cas suivants :

- Les barres de défilement de style de fenêtre standard peuvent être définies pour la vue en utilisant le WS_HSCROLL et WS_VSCROLL[les Styles Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles).

- Contrôles de barre de défilement peuvent également être ajoutés pour le frame qui contient la vue, auquel cas le framework transfère les messages WM_HSCROLL et WM_VSCROLL à partir de la fenêtre frame à la vue actuellement active.

- Le framework transfère également faire défiler les messages à partir d’un `CSplitterWnd` contrôle splitter vers le volet de fractionnement actuellement actif (une vue). Lorsqu’elle est placée dans un [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) avec des barres de défilement partagé, un `CScrollView` objet utilisera ceux partagés, plutôt que de créer son propre.

Pour plus d’informations sur l’utilisation de `CScrollView`, consultez [Architecture Document/vue](../../mfc/document-view-architecture.md) et [dérivées les Classes d’affichage disponibles dans MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars

Appelez cette fonction membre pour déterminer si l’affichage du défilement possède des barres horizontales et verticales.

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Paramètres

*bHasHorzBar*<br/>
Indique que l’application a une barre de défilement horizontale.

*bHasVertBar*<br/>
Indique que l’application a une barre de défilement verticale.

##  <a name="cscrollview"></a>  CScrollView::CScrollView

Construit un objet `CScrollView`.

```
CScrollView();
```

### <a name="remarks"></a>Notes

Vous devez appeler `SetScrollSizes` ou `SetScaleToFitSize` avant le défilement vue est utilisable.

##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect

Appelez `FillOutsideRect` pour remplir la zone de la vue qui apparaît en dehors de la zone de défilement.

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Contexte de périphérique dans lequel le remplissage doit être effectuée.

*pBrush*<br/>
Pinceau avec lequel la zone doit être rempli.

### <a name="remarks"></a>Notes

Utilisez `FillOutsideRect` dans votre affichage défilement `OnEraseBkgnd` fonction de gestionnaire pour empêcher la mise à jour d’arrière-plan excessive.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition

Appelez `GetDeviceScrollPosition` lorsque vous avez besoin de la position horizontale et verticale actuelle des cases de défilement dans les barres de défilement.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Les positions horizontales et verticales (en unités de périphérique), les cases de défilement en tant qu’un `CPoint` objet.

### <a name="remarks"></a>Notes

Cette paire de coordonnées correspond à l’emplacement dans le document auquel le coin supérieur gauche de la vue a été défilé. Cela est utile pour la compensation de positions de périphérique de la souris à des positions de périphérique d’affichage du défilement.

`GetDeviceScrollPosition` Retourne les valeurs en unités de périphérique. Si vous souhaitez que les unités logiques, utilisez `GetScrollPosition` à la place.

##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes` Obtient le mode de mappage actuel, la taille totale et les tailles de page et de ligne de la vue à défilement.

```
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
Retourne la taille totale actuelle de l’affichage du défilement en unités de périphérique.

*sizePage*<br/>
Retourne les montants horizontales et verticales pour faire défiler dans chaque direction en réponse à une souris cliquez dans un arbre de la barre de défilement. Le `cx` membre contient la valeur horizontale. Le `cy` membre contient la valeur verticale.

*sizeLine*<br/>
Retourne les montants horizontales et verticales pour faire défiler dans chaque direction en réponse à une souris cliquez dans une flèche de défilement. Le `cx` membre contient la valeur horizontale. Le `cy` membre contient la valeur verticale.

### <a name="remarks"></a>Notes

Tailles sont exprimées en unités de périphérique. Cette fonction membre est rarement appelée.

##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition

Appelez `GetScrollPosition` lorsque vous avez besoin de la position horizontale et verticale actuelle des cases de défilement dans les barres de défilement.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Les positions horizontales et verticales (en unités logiques), les cases de défilement en tant qu’un `CPoint` objet.

### <a name="remarks"></a>Notes

Cette paire de coordonnées correspond à l’emplacement dans le document auquel le coin supérieur gauche de la vue a été défilé.

`GetScrollPosition` Retourne les valeurs en unités logiques. Si vous souhaitez des unités de périphérique, utilisez `GetDeviceScrollPosition` à la place.

##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize

Appelez `GetTotalSize` pour récupérer les tailles horizontales et verticales actuelles de l’affichage du défilement.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille totale de l’affichage du défilement en unités logiques. La taille horizontale est dans le `cx` membre de la `CSize` valeur de retour. La taille verticale est dans le `cy` membre.

##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit

Appelez `ResizeParentToFit` pour permettre à la taille de votre vue de déterminer la taille de sa fenêtre frame.

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Paramètres

*bShrinkOnly*<br/>
Le type de redimensionnement pour effectuer. La valeur par défaut, la valeur TRUE, réduit la fenêtre frame, le cas échéant. Barres de défilement apparaît toujours pour les vues volumineuses ou les fenêtres frame petit. La valeur FALSE, la vue toujours redimensionner la fenêtre frame exactement. Cela peut être quelque peu dangereux dans la mesure où la fenêtre frame deviendrait trop volumineux pour s’ajuster à la fenêtre frame multidocument MDI (interface) ou de l’écran.

### <a name="remarks"></a>Notes

Cela est recommandé uniquement pour les vues dans des fenêtres de frame enfant MDI. Utilisez `ResizeParentToFit` dans le `OnInitialUpdate` fonction de gestionnaire de votre dérivée `CScrollView` classe. Pour obtenir un exemple de cette fonction membre, consultez [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit` suppose que la taille de la fenêtre d’affichage a été définie. Si la taille de la fenêtre d’affichage n’a pas été définie lorsque `ResizeParentToFit` est appelée, vous obtiendrez une assertion. Pour vous assurer que cela ne se produit pas, effectuer l’appel suivant avant d’appeler `ResizeParentToFit`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition

Appelez `ScrollToPosition` pour accéder à un moment donné dans la vue.

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Le point de défilement, en unités logiques. Le `x` membre doit être une valeur positive (supérieure ou égale à 0, jusqu'à la taille totale de la vue). Vaut également pour le `y` membre quand le mode de mappage est MM_TEXT. Le `y` membre est négatif dans les modes de mappage autre que MM_TEXT.

### <a name="remarks"></a>Notes

L’affichage est défilé afin que ce point est dans l’angle supérieur gauche de la fenêtre. Cette fonction membre ne doit pas être appelée si la vue est étirée pour remplir.

##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize

Appelez `SetScaleToFitSize` lorsque vous souhaitez mettre à l’échelle automatiquement de la taille de fenêtre d’affichage à la taille de fenêtre actuelle.

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Paramètres

*sizeTotal*<br/>
Les tailles horizontales et verticales dans lequel la vue doit être mis à l’échelle. Taille de la vue défilement est mesurée en unités logiques. La taille horizontale est contenue dans le `cx` membre. La taille verticale est contenue dans le `cy` membre. Les deux `cx` et `cy` doit être supérieur ou égal à 0.

### <a name="remarks"></a>Notes

Avec les barres de défilement, seule une partie de la vue logique peut-être être visible à tout moment. Mais avec la fonctionnalité de mise à l’échelle pour ajuster la vue ne comporte aucune barre de défilement et la vue logique est étirée ou rétrécie pour correspondre exactement à la zone la fenêtre client. Lorsque la fenêtre est redimensionnée, la vue dessine ses données à une nouvelle mise à l’échelle selon la taille de la fenêtre.

Vous allez généralement placer l’appel à `SetScaleToFitSize` dans votre substitution de la vue `OnInitialUpdate` fonction membre. Si vous ne souhaitez pas que la mise à l’échelle automatique, appelez le `SetScrollSizes` membre de fonction à la place.

`SetScaleToFitSize` peut être utilisé pour implémenter une opération « Zoom Fit ». Utilisez `SetScrollSizes` pour réinitialiser le défilement.

`SetScaleToFitSize` suppose que la taille de la fenêtre d’affichage a été définie. Si la taille de la fenêtre d’affichage n’a pas été définie lorsque `SetScaleToFitSize` est appelée, vous obtiendrez une assertion. Pour vous assurer que cela ne se produit pas, effectuer l’appel suivant avant d’appeler `SetScaleToFitSize`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes

Appelez `SetScrollSizes` lorsque la vue est sur le point d’être mis à jour.

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Paramètres

*nMapMode*<br/>
Le mode de mappage à définir pour cette vue. Les valeurs possibles sont les suivantes :

|Mode de mappage|Unité logique|L’axe y positif étend...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 pixel|Vers le bas|
|MM_HIMETRIC|0,01 mm|Vers le haut|
|MM_TWIPS|1/1440 dans|Vers le haut|
|MM_HIENGLISH|0,001|Vers le haut|
|MM_LOMETRIC|0,1 mm|Vers le haut|
|MM_LOENGLISH|0,01 pouce|Vers le haut|

Chacun de ces modes sont définis par Windows. Deux modes de mappage standard, MM_ISOTROPIC et MM_ANISOTROPIC, ne sont pas utilisés pour `CScrollView`. La bibliothèque de classes fournit le `SetScaleToFitSize` fonction membre pour la mise à l’échelle de la vue à la taille de la fenêtre. Colonne trois dans le tableau ci-dessus décrit l’orientation de coordonnées.

*sizeTotal*<br/>
La taille totale de l’affichage du défilement. Le `cx` membre contient la mesure horizontale. Le `cy` membre contient l’étendue verticale. Tailles sont exprimées en unités logiques. Les deux `cx` et `cy` doit être supérieur ou égal à 0.

*sizePage*<br/>
Les taux horizontal et verticales pour faire défiler dans chaque direction en réponse à une souris cliquez dans un arbre de la barre de défilement. Le `cx` membre contient la valeur horizontale. Le `cy` membre contient la valeur verticale.

*sizeLine*<br/>
Les taux horizontal et verticales pour faire défiler dans chaque direction en réponse à une souris cliquez sur une flèche de défilement. Le `cx` membre contient la valeur horizontale. Le `cy` membre contient la valeur verticale.

### <a name="remarks"></a>Notes

Appeler dans votre substitution de la `OnUpdate` fonction membre pour ajuster les caractéristiques de défilement lorsque, par exemple, le document est initialement affiché ou quand il change de taille.

Vous obtiendrez généralement les informations de taille de document associé de la vue en appelant une fonction membre de document, peut-être appelée `GetMyDocSize`, que vous fournissez à votre classe de document dérivée. Le code suivant illustre cette approche :

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Ou bien, vous devrez peut-être parfois définir une taille fixe, comme dans le code suivant :

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Vous devez définir le mode de mappage à un des modes de mappage de Windows à l’exception de MM_ISOTROPIC ou MM_ANISOTROPIC. Si vous souhaitez utiliser un mode de mappage sans contrainte, appelez le `SetScaleToFitSize` fonction membre au lieu de `SetScrollSizes`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd, classe](../../mfc/reference/csplitterwnd-class.md)
