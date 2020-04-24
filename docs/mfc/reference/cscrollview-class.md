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
ms.openlocfilehash: 5d0eb163fae2aa5fc63470e1c499311ab1a402a6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754422"
---
# <a name="cscrollview-class"></a>CScrollView, classe

Un [CView](../../mfc/reference/cview-class.md) avec des capacités de défilement.

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
|[CScrollView::CheckScrollBars](#checkscrollbars)|Indique si la vue de défilement a des barres de défilement horizontales et verticales.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Remplit la zone d’une vue à l’extérieur de la zone de défilement.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Obtient la position de défilement actuelle dans les unités de périphérique.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Obtient le mode de cartographie actuel, la taille totale, et la ligne et la taille des pages de la vue défilementable. Les tailles sont dans les unités d’appareil.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Obtient la position de défilement actuelle dans les unités logiques.|
|[CScrollView::GetTotalSize](#gettotalsize)|Obtient la taille totale de la vue de défilement dans les unités logiques.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|La taille de la vue dicte la taille de son cadre.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Faites défiler la vue à un point donné, spécifié dans les unités logiques.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Place la vue de défilement en mode échelle à ajustement.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Définit le mode de cartographie, la taille totale et les quantités de défilement horizontal et vertical de la vue de défilement.|

## <a name="remarks"></a>Notes

Vous pouvez gérer le défilement `CView` standard vous-même dans n’importe quelle classe dérivée en remplaçant les fonctions des membres [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) cartographiées par message. Mais `CScrollView` ajoute les caractéristiques suivantes à ses `CView` capacités:

- Il gère les tailles de fenêtre et de viewport et les modes de cartographie.

- Il fait défiler automatiquement en réponse aux messages à barres de défilement.

- Il fait défiler automatiquement en réponse aux messages du clavier, d’une souris qui ne fait pas défiler ou de la roue IntelliMouse.

Pour faire défiler automatiquement en réponse aux messages du clavier, ajoutez un message WM_KEYDOWN et testez pour VK_DOWN, VK_PREV et appelez [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos).

Vous pouvez gérer la roue de la souris en vous faisant défiler en suppliant les fonctions des membres [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) et [OnRegisteredMouseWheel cartographiées](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) par message. Comme ils `CScrollView`le sont pour, ces fonctions membres soutiennent le comportement recommandé pour [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel), le message de rotation de roue.

Pour profiter du défilement automatique, `CScrollView` dérivez `CView`votre classe de vue au lieu de . Lorsque la vue est créée pour la première fois, si vous souhaitez calculer la `SetScrollSizes` taille de la vue défilementable en fonction de la taille du document, appelez la fonction membre à partir de votre remplacement de [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) ou [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Vous devez écrire votre propre code pour demander la taille du document. Par exemple, voir [l’échantillon Scribble](../../overview/visual-cpp-samples.md).)

L’appel `SetScrollSizes` à la fonction membre définit le mode de cartographie de la vue, les dimensions totales de la vue de défilement et les montants à faire défiler horizontalement et verticalement. Toutes les tailles sont dans des unités logiques. La taille logique de la vue est généralement calculée à partir des données stockées dans le document, mais dans certains cas, vous pouvez spécifier une taille fixe. Pour des exemples des deux approches, voir [CScrollView::SetScrollSizes](#setscrollsizes).

Vous spécifiez les montants à faire défiler horizontalement et verticalement dans les unités logiques. Par défaut, si l’utilisateur clique sur un arbre `CScrollView` de barre de défilement à l’extérieur de la boîte de défilement, fait défiler une « page ». Si l’utilisateur clique sur une flèche de `CScrollView` défilement à chaque extrémité d’une barre de défilement, fait défiler une « ligne ». Par défaut, une page est 1/10 de la taille totale de la vue; une ligne est 1/10 de la taille de la page. Remplacez ces valeurs par défaut en `SetScrollSizes` passant des tailles personnalisées dans la fonction membre. Par exemple, vous pouvez définir la taille horizontale à une fraction de la largeur de la taille totale et la taille verticale à la hauteur d’une ligne dans la police actuelle.

Au lieu de `CScrollView` faire défiler, peut automatiquement mettre la vue à l’échelle actuelle de la fenêtre. Dans ce mode, la vue n’a pas de barres de défilement et la vue logique est étirée ou réduite pour s’adapter exactement à la zone client de la fenêtre. Pour utiliser cette capacité d’échelle à ajustement, appelez [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Appelez `SetScaleToFitSize` l’un ou l’autre ou `SetScrollSizes`, mais pas les deux.)

Avant `OnDraw` que la fonction de membre `CScrollView` de votre classe de vue `CPaintDC` dérivée soit appelée, `OnDraw`ajuste automatiquement l’origine du viewport pour l’objet de contexte de l’appareil qu’il passe à .

Pour ajuster l’origine du port `CScrollView` de vue pour la fenêtre de défilement, remplace [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Cet ajustement est `CPaintDC` automatique pour `CScrollView` le `OnDraw`contexte de `CScrollView::OnPrepareDC` l’appareil qui passe à , mais `CClientDC`vous devez vous appeler pour tous les autres contextes de périphérique que vous utilisez, tels que un . Vous pouvez `CScrollView::OnPrepareDC` remplacer pour définir le stylo, la couleur de fond, et d’autres attributs de dessin, mais appelez la classe de base pour faire la mise à l’échelle.

Les barres de défilement peuvent apparaître en trois endroits par rapport à une vue, comme indiqué dans les cas suivants :

- Des barres de défilement standard de style fenêtre peuvent être définies pour la vue à l’aide des WS_HSCROLL et WS_VSCROLL[Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles).

- Des commandes de barre de défilement peuvent également être ajoutées au cadre contenant la vue, auquel cas le cadre transmet WM_HSCROLL et WM_VSCROLL messages de la fenêtre du cadre à la vue actuellement active.

- Le cadre transmet également les `CSplitterWnd` messages défilants d’un contrôle de splitter à la vitre de splitter actuellement active (une vue). Lorsqu’il est placé dans un [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) avec des barres de défilement partagées, un `CScrollView` objet utilisera les barres partagées plutôt que de créer son propre.

Pour plus d’informations sur l’utilisation `CScrollView`, voir Document / Afficher [l’architecture](../../mfc/document-view-architecture.md) et les classes de vue [dérivée disponibles dans MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScrollView::CheckScrollBars

Appelez cette fonction de membre pour déterminer si la vue de défilement a des barres horizontales et verticales.

```cpp
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Paramètres

*bHasHorzBar*<br/>
Indique que l’application a une barre de défilement horizontal.

*bHasVertBar (en anglais seulement)*<br/>
Indique que l’application a une barre de défilement vertical.

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a>CScrollView::CScrollView

Construit un objet `CScrollView`.

```
CScrollView();
```

### <a name="remarks"></a>Notes

Vous devez `SetScrollSizes` appeler `SetScaleToFitSize` l’un ou l’autre ou avant que la vue de défilement soit utilisable.

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScrollView::FillOutsideRect

Appelez `FillOutsideRect` pour remplir la zone de la vue qui apparaît à l’extérieur de la zone de défilement.

```cpp
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Contexte de l’appareil dans lequel le remplissage doit être fait.

*pBrush*<br/>
Badigeonner la zone à remplir.

### <a name="remarks"></a>Notes

Utilisez `FillOutsideRect` dans la fonction `OnEraseBkgnd` de gestionnaire de votre vue de défilement pour éviter le repeindre de fond excessif.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition

Appelez `GetDeviceScrollPosition` lorsque vous avez besoin des positions horizontales et verticales actuelles des boîtes de défilement dans les barres de défilement.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Les positions horizontales et verticales (dans les `CPoint` unités de périphérique) des boîtes de défilement comme objet.

### <a name="remarks"></a>Notes

Cette paire de coordonnées correspond à l’emplacement dans le document auquel le coin supérieur gauche de la vue a été défilé. Ceci est utile pour compenser les positions de la souris-appareil pour faire défiler les positions de l’appareil.

`GetDeviceScrollPosition`retourne les valeurs dans les unités d’appareils. Si vous voulez des `GetScrollPosition` unités logiques, utilisez plutôt.

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes`obtient le mode de cartographie actuel, la taille totale, et la taille de la ligne et des pages de la vue défilementable.

```cpp
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Paramètres

*nMapMode*<br/>
Retourne le mode de cartographie actuel pour cette vue. Pour obtenir la liste des valeurs possibles, consultez `SetScrollSizes`.

*tailleTotal*<br/>
Retourne la taille totale actuelle de la vue de défilement dans les unités de périphérique.

*sizePage*<br/>
Retourne les quantités horizontales et verticales actuelles pour faire défiler dans chaque direction en réponse à un clic de souris dans un arbre à barres de défilement. Le `cx` membre contient la quantité horizontale. Le `cy` membre contient le montant vertical.

*sizeLine (en)*<br/>
Retourne les montants horizontaux et verticaux actuels pour faire défiler dans chaque direction en réponse à un clic de souris dans une flèche de défilement. Le `cx` membre contient la quantité horizontale. Le `cy` membre contient le montant vertical.

### <a name="remarks"></a>Notes

Les tailles sont dans les unités d’appareil. Cette fonction de membre est rarement appelée.

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScrollView::GetScrollPosition

Appelez `GetScrollPosition` lorsque vous avez besoin des positions horizontales et verticales actuelles des boîtes de défilement dans les barres de défilement.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Les positions horizontales et verticales (en unités `CPoint` logiques) des boîtes de défilement comme objet.

### <a name="remarks"></a>Notes

Cette paire de coordonnées correspond à l’emplacement dans le document auquel le coin supérieur gauche de la vue a été défilé.

`GetScrollPosition`retourne des valeurs dans des unités logiques. Si vous voulez des `GetDeviceScrollPosition` unités d’appareil, utilisez plutôt.

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScrollView::GetTotalSize

Appelez `GetTotalSize` pour récupérer les tailles horizontales et verticales actuelles de la vue de défilement.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille totale de la vue de défilement dans les unités logiques. La taille horizontale `cx` est `CSize` dans le membre de la valeur de retour. La taille verticale `cy` est dans le membre.

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView::ResizeParentToFit

Appelez `ResizeParentToFit` pour laisser la taille de votre vue dicter la taille de sa fenêtre de cadre.

```cpp
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Paramètres

*bShrinkOnly*<br/>
Le genre de resizing pour effectuer. La valeur par défaut, TRUE, rétrécit la fenêtre de cadre si nécessaire. Les barres de défilement apparaîtront toujours pour de grandes vues ou de petites fenêtres à cadre. Une valeur de FALSE provoque la vue toujours de resize la fenêtre de cadre exactement. Cela peut être un peu dangereux puisque la fenêtre de cadre pourrait devenir trop grande pour s’adapter à l’intérieur de la fenêtre de cadre de l’interface documentaire multiple (MDI) ou de l’écran.

### <a name="remarks"></a>Notes

Ceci est recommandé uniquement pour les vues dans les fenêtres de cadre pour enfants MDI. `ResizeParentToFit` Utilisez-le `OnInitialUpdate` dans la `CScrollView` fonction de gestionnaire de votre classe dérivée. Pour un exemple de cette fonction de membre, voir [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit`suppose que la taille de la fenêtre de vue a été définie. Si la taille de la `ResizeParentToFit` fenêtre de vue n’a pas été définie lorsqu’elle est appelée, vous obtiendrez une affirmation. Pour vous assurer que cela ne se `ResizeParentToFit`produise pas, faites l’appel suivant avant d’appeler :

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScrollView::ScrollToPosition

Appelez `ScrollToPosition` pour faire défiler un point donné dans la vue.

```cpp
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Le point à faire défiler, dans les unités logiques. Le `x` membre doit être une valeur positive (supérieure ou égale à 0, jusqu’à la taille totale de la vue). Il en va `y` de même pour le membre lorsque le mode de cartographie est MM_TEXT. Le `y` membre est négatif dans les modes de cartographie autres que MM_TEXT.

### <a name="remarks"></a>Notes

La vue sera défichée de sorte que ce point est au coin supérieur gauche de la fenêtre. Cette fonction de membre ne doit pas être appelée si la vue est mise à l’échelle pour s’adapter.

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize

Appelez `SetScaleToFitSize` lorsque vous souhaitez mettre à l’échelle la taille du viewport à la taille actuelle de la fenêtre automatiquement.

```cpp
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Paramètres

*tailleTotal*<br/>
Les tailles horizontales et verticales auxquelles la vue doit être échelle. La taille de la vue de défilement est mesurée en unités logiques. La taille horizontale `cx` est contenue dans le membre. La taille verticale est `cy` contenue dans le membre. Les `cx` `cy` deux et doivent être plus ou égal à 0.

### <a name="remarks"></a>Notes

Avec les barres de défilement, seule une partie de la vue logique peut être visible à tout moment. Mais avec la capacité de l’échelle à l’ajustement, la vue n’a pas de barres de défilement et la vue logique est étirée ou réduite pour s’adapter exactement à la zone client de la fenêtre. Lorsque la fenêtre est resized, la vue tire ses données à une nouvelle échelle en fonction de la taille de la fenêtre.

Vous placez généralement l’appel `SetScaleToFitSize` dans votre remplacement `OnInitialUpdate` de la fonction de membre de la vue. Si vous ne voulez pas la `SetScrollSizes` mise à l’échelle automatique, appelez la fonction membre à la place.

`SetScaleToFitSize`peut être utilisé pour implémenter une opération "Zoom to Fit". Utilisez `SetScrollSizes` pour réinitialiser le défilement.

`SetScaleToFitSize`suppose que la taille de la fenêtre de vue a été définie. Si la taille de la `SetScaleToFitSize` fenêtre de vue n’a pas été définie lorsqu’elle est appelée, vous obtiendrez une affirmation. Pour vous assurer que cela ne se `SetScaleToFitSize`produise pas, faites l’appel suivant avant d’appeler :

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScrollView::SetScrollSizes

Appelez `SetScrollSizes` lorsque la vue est sur le point d’être mise à jour.

```cpp
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Paramètres

*nMapMode*<br/>
Le mode de cartographie à définir pour cette vue. Les valeurs possibles incluent :

|Mode de cartographie|Unité logique|L’axe y positif s’étend...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 pixel|Baisse|
|MM_HIMETRIC|0,01 mm|Hausse|
|MM_TWIPS|1/1440 en|Hausse|
|MM_HIENGLISH|0,001 en|Hausse|
|MM_LOMETRIC|0,1 mm|Hausse|
|MM_LOENGLISH|0,01 en|Hausse|

Tous ces modes sont définis par Windows. Deux modes de cartographie standard, MM_ISOTROPIC et MM_ANISOTROPIC, `CScrollView`ne sont pas utilisés pour . La bibliothèque de `SetScaleToFitSize` classe fournit la fonction de membre pour l’échelle de la vue à la taille de fenêtre. La colonne trois dans le tableau ci-dessus décrit l’orientation de coordonnées.

*tailleTotal*<br/>
La taille totale de la vue de défilement. Le `cx` membre contient l’étendue horizontale. Le `cy` membre contient l’étendue verticale. Les tailles sont dans les unités logiques. Les `cx` `cy` deux et doivent être plus ou égal à 0.

*sizePage*<br/>
L’horizontale et verticale s’élève à faire défiler dans chaque direction en réponse à un clic de souris dans un arbre de barre de défilement. Le `cx` membre contient la quantité horizontale. Le `cy` membre contient le montant vertical.

*sizeLine (en)*<br/>
L’horizontale et verticale s’élève à faire défiler dans chaque direction en réponse à un clic de souris dans une flèche de défilement. Le `cx` membre contient la quantité horizontale. Le `cy` membre contient le montant vertical.

### <a name="remarks"></a>Notes

Appelez-le dans votre `OnUpdate` remplacement de la fonction membre pour ajuster les caractéristiques de défilement lorsque, par exemple, le document est initialement affiché ou quand il change de taille.

Vous obtiendrez généralement des informations de taille à partir du document `GetMyDocSize`associé de la vue en appelant une fonction de membre de document, peut-être appelée, que vous fournissez avec votre classe de documents dérivée. Le code suivant montre cette approche :

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Alternativement, vous pouvez parfois avoir besoin de définir une taille fixe, comme dans le code suivant:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Vous devez définir le mode de cartographie à l’un des modes de cartographie Windows, sauf MM_ISOTROPIC ou MM_ANISOTROPIC. Si vous souhaitez utiliser un mode de `SetScaleToFitSize` cartographie sans `SetScrollSizes`contrainte, appelez la fonction membre au lieu de .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[Classe CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)
