---
title: CRectTracker, classe
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: 4d262ab5f88481d56de1c236effb66fcbf6a706a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368381"
---
# <a name="crecttracker-class"></a>CRectTracker, classe

Permet d’afficher, de déplacer et de resized un objet de différentes manières.

## <a name="syntax"></a>Syntaxe

```
class CRectTracker
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|Construit un objet `CRectTracker`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|Appelé lorsque le rectangle est resized.|
|[CRectTracker::Draw](#draw)|Rend le rectangle.|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Appelé lors du dessin `CRectTracker` de la frontière d’un objet.|
|[CRectTracker::GetHandleMask](#gethandlemask)|Appelé pour obtenir le `CRectTracker` masque des poignées resize d’un élément.|
|[CRectTracker::GetTrueRect](#gettruerect)|Retourne la largeur et la hauteur du rectangle, y compris les poignées de resize.|
|[CRectTracker::HitTest](#hittest)|Retourne la position actuelle du curseur `CRectTracker` lié à l’objet.|
|[CRectTracker::NormalizeHit](#normalizehit)|Normalise un code de test à succès.|
|[CRectTracker::OnChangedRect](#onchangedrect)|Appelé lorsque le rectangle a été resized ou déplacé.|
|[CRectTracker::SetCursor](#setcursor)|Définit le curseur, en fonction de sa position sur le rectangle.|
|[CRectTracker::Track](#track)|Permet à l’utilisateur de manipuler le rectangle.|
|[CRectTracker::TrackRubberBand](#trackrubberband)|Permet à l’utilisateur de "rubber-band" la sélection.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Détermine la taille des poignées de resize.|
|[CRectTracker::m_nStyle](#m_nstyle)|Style actuel(s) du tracker.|
|[CRectTracker::m_rect](#m_rect)|Position actuelle (en pixels) du rectangle.|
|[CRectTracker::m_sizeMin](#m_sizemin)|Détermine la largeur et la hauteur minimales du rectangle.|

## <a name="remarks"></a>Notes

`CRectTracker`n’a pas de classe de base.

Bien `CRectTracker` que la classe soit conçue pour permettre à l’utilisateur d’interagir avec les éléments OLE en utilisant une interface graphique, son utilisation ne se limite pas aux applications compatibles OLE. Il peut être utilisé n’importe où une telle interface utilisateur est nécessaire.

`CRectTracker`les frontières peuvent être des lignes solides ou pointillées. L’élément peut être donné une bordure éclose ou recouvert d’un modèle éclos pour indiquer différents états de l’élément. Vous pouvez placer huit poignées de resize sur l’extérieur ou la bordure intérieure de l’élément. (Pour une explication des poignées de resize, voir [GetHandleMask](#gethandlemask).) Enfin, `CRectTracker` un vous permet de modifier l’orientation d’un élément lors de la resizing.

Pour `CRectTracker`utiliser, `CRectTracker` construire un objet et spécifier les états d’affichage qui sont parasés. Vous pouvez ensuite utiliser cette interface pour donner à l’utilisateur une `CRectTracker` rétroaction visuelle sur l’état actuel de l’élément OLE associé à l’objet.

Pour plus d’informations sur l’utilisation `CRectTracker`, voir l’article [Trackers](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CRectTracker`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a>CRectTracker::AdjustRect

Appelé par le cadre lorsque le rectangle de suivi est resized à l’aide d’une poignée de resize.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*nHandle (en)*<br/>
Index de poignée utilisé.

*lpRect*<br/>
Pointeur sur la taille actuelle du rectangle. (La taille d’un rectangle est donnée par sa hauteur et sa largeur.)

### <a name="remarks"></a>Notes

Le comportement par défaut de cette fonction permet `Track` à `TrackRubberBand` l’orientation du rectangle de changer seulement quand et sont appelés avec l’inversion autorisée.

Remplacer cette fonction pour contrôler l’ajustement du rectangle de suivi lors d’une opération de dragage. Une méthode consiste à ajuster les coordonnées spécifiées par *lpRect* avant de revenir.

Des fonctionnalités spéciales qui `CRectTracker`ne sont pas directement prises en charge par , telles que snap-to-grid ou keep-aspect-ratio, peuvent être mises en œuvre en l’emportent sur cette fonction.

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a>CRectTracker::CRectTracker

Crée et initialise un objet `CRectTracker`.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*lpSrcRect*<br/>
Les coordonnées de l’objet rectangle.

*nStyle*<br/>
Spécifie le `CRectTracker` style de l’objet. Les styles suivants sont pris en charge :

- `CRectTracker::solidLine`Utilisez une ligne solide pour la bordure du rectangle.

- `CRectTracker::dottedLine`Utilisez une ligne pointillée pour la bordure du rectangle.

- `CRectTracker::hatchedBorder`Utilisez un motif éclos pour la bordure du rectangle.

- `CRectTracker::resizeInside`Resize poignées situées à l’intérieur du rectangle.

- `CRectTracker::resizeOutside`Resize poignées situées à l’extérieur du rectangle.

- `CRectTracker::hatchInside`Le motif éclos couvre tout le rectangle.

### <a name="remarks"></a>Notes

Le constructeur par défaut `CRectTracker` initialise l’objet avec les valeurs de *lpSrcRect* et initialise d’autres tailles aux défauts du système. Si l’objet est créé sans `m_rect` `m_nStyle` paramètres, les membres et les données sont uninitialisés.

## <a name="crecttrackerdraw"></a><a name="draw"></a>CRectTracker::Draw

Appelez cette fonction pour dessiner les lignes extérieures du rectangle et la région intérieure.

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur sur le contexte de l’appareil sur lequel dessiner.

### <a name="remarks"></a>Notes

Le style du tracker détermine comment le dessin est fait. Consultez le constructeur `CRectTracker` pour plus d’informations sur les styles disponibles.

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker::DrawTrackerRect

Appelé par le cadre chaque fois que la `Track` `TrackRubberBand` position du tracker a changé à l’intérieur de la fonction ou membre.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointeur `RECT` vers le qui contient le rectangle à dessiner.

*pWndClipTo*<br/>
Pointeur vers la fenêtre à utiliser en coupant le rectangle.

*pDC*<br/>
Pointeur sur le contexte de l’appareil sur lequel dessiner.

*Pwnd*<br/>
Pointeur vers la fenêtre sur laquelle le dessin se produira.

### <a name="remarks"></a>Notes

L’implémentation `CDC::DrawFocusRect`par défaut fait un appel à , qui tire un rectangle pointillé.

Remplacer cette fonction pour fournir des commentaires différents pendant l’opération de suivi.

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRectTracker::GetHandleMask

Le cadre appelle cette fonction de membre pour récupérer le masque pour les poignées de resize d’un rectangle.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Valeur de retour

Le masque `CRectTracker` des poignées resize d’un élément.

### <a name="remarks"></a>Notes

Les poignées de resize apparaissent sur les côtés et les coins du rectangle et permettent à l’utilisateur de contrôler la forme et la taille du rectangle.

Un rectangle a 8 poignées de redimensionnement numérotées 0-7. Chaque poignée de resize est représentée par un peu dans le masque; la valeur de ce bit est de 2 *n*, où *n* est le numéro de poignée de resize. Bits 0-3 correspondent aux poignées de redimensionnement du coin, à partir du haut à gauche en mouvement dans le sens des aiguilles d’une montre. Les bits 4-7 correspondent aux poignées latérales de redimensionnement à partir du haut en mouvement dans le sens des aiguilles d’une montre. L’illustration suivante montre les poignées de resize d’un rectangle et leurs nombres et valeurs de poignée de resize correspondants :

![Redimensionner les valeurs de la poignée](../../mfc/reference/media/vc35dp1.gif "Redimensionner les valeurs de la poignée")

La mise `GetHandleMask` en œuvre par défaut des retours du masque des bits de sorte que les poignées de resize apparaissent. Si le bit unique est allumé, la poignée de resize correspondante sera tirée.

Remplacer cette fonction de membre pour cacher ou afficher les poignées de resize indiquées.

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a>CRectTracker::GetTrueRect

Appelez cette fonction pour récupérer les coordonnées du rectangle.

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Paramètres

*lpTrueRect*<br/>
Pointeur `RECT` vers la structure qui contiendra les coordonnées de l’appareil de l’objet. `CRectTracker`

### <a name="remarks"></a>Notes

Les dimensions du rectangle comprennent la hauteur et la largeur de toutes les poignées de resize situées sur la bordure extérieure. Au retour, *lpTrueRect* est toujours un rectangle normalisé dans les coordonnées de l’appareil.

## <a name="crecttrackerhittest"></a><a name="hittest"></a>CRectTracker::HitTest

Appelez cette fonction pour savoir si l’utilisateur a saisi une poignée de resize.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Le point, dans les coordonnées de l’appareil, de tester.

### <a name="return-value"></a>Valeur de retour

La valeur retournée est basée sur `CRectTracker::TrackerHit` le type énuméré et peut avoir l’une des valeurs suivantes :

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight`1

- `CRectTracker::hitBottomRight`2

- `CRectTracker::hitBottomLeft`3

- `CRectTracker::hitTop`4

- `CRectTracker::hitRight`5

- `CRectTracker::hitBottom`6

- `CRectTracker::hitLeft`7

- `CRectTracker::hitMiddle`8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a>CRectTracker::m_nHandleSize

La taille, en pixels, des poignées `CRectTracker` de resize.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Notes

Initialisé avec la valeur du système par défaut.

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a>CRectTracker::m_rect

La position actuelle du rectangle dans les coordonnées des clients (pixels).

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a>CRectTracker::m_sizeMin

La taille minimale du rectangle.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Notes

Les deux `cx` valeurs `cy`par défaut, et , sont calculées à partir de la valeur du système par défaut pour la largeur de la frontière. Ce membre de données `AdjustRect` n’est utilisé que par la fonction membre.

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a>CRectTracker::m_nStyle

Style actuel du rectangle.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Notes

Voir [CRectTracker::CRectTracker](#crecttracker) pour une liste de styles possibles.

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a>CRectTracker::NormalizeHit

Appelez cette fonction pour convertir une poignée potentiellement inversée.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Paramètres

*nHandle (en)*<br/>
Poignée sélectionnée par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

L’index de la poignée normalisée.

### <a name="remarks"></a>Notes

Quand `CRectTracker::Track` `CRectTracker::TrackRubberBand` ou est appelé avec l’inverse autorisé, il est possible pour le rectangle d’être inversé sur l’axe x, l’axe y, ou les deux. Lorsque cela `HitTest` se produit, retourner les poignées qui sont également inversées par rapport au rectangle. Ceci est inapproprié pour dessiner la rétroaction de curseur parce que la rétroaction dépend de la position d’écran du rectangle, pas la partie de la structure de données de rectangle qui sera modifiée.

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CRectTracker::OnChangedRect

Appelé par le cadre chaque fois que `Track`le rectangle tracker a changé lors d’un appel à .

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Paramètres

*rectOld*<br/>
Contient les anciennes coordonnées `CRectTracker` de l’appareil de l’objet.

### <a name="remarks"></a>Notes

Au moment où cette fonction est `DrawTrackerRect` appelée, toutes les rétroactions tirées avec a été supprimée. L’implémentation par défaut de cette fonction est sans effet.

Remplacez cette fonction lorsque vous souhaitez effectuer des actions après la resized du rectangle.

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a>CRectTracker::SetCursor

Appelez cette fonction pour changer la forme du `CRectTracker` curseur pendant qu’elle est au-dessus de la région de l’objet.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre qui contient actuellement le curseur.

*nHitTest (en)*<br/>
Résultats du test de frappe précédent, du WM_SETCURSOR message.

### <a name="return-value"></a>Valeur de retour

Nonzero si le coup précédent était au-dessus du rectangle tracker; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction de l’intérieur de la fonction de votre `OnSetCursor`fenêtre qui gère le message WM_SETCURSOR (généralement ).

## <a name="crecttrackertrack"></a><a name="track"></a>CRectTracker::Track

Appelez cette fonction pour afficher l’interface utilisateur pour resizing le rectangle.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
L’objet de fenêtre qui contient le rectangle.

*Point*<br/>
Coordonnées de l’appareil de la position actuelle de la souris par rapport à la zone client.

*bAllowInvert*<br/>
Si VRAI, le rectangle peut être inversé le long de l’axe x ou y-axe; autrement FALSE.

*pWndClipTo*<br/>
La fenêtre à laquelle les opérations de dessin seront coupées. Si NULL, *pWnd* est utilisé comme rectangle de tonte.

### <a name="return-value"></a>Valeur de retour

Si la clé ESC est pressée, le processus de suivi est arrêté, le rectangle stocké dans le tracker n’est pas modifié et 0 est retourné. Si la modification est commise, en déplaçant la souris et en libérant le bouton de la souris gauche, la nouvelle position et/ou la nouvelle taille sont enregistrées dans le rectangle du tracker et le nonzero est retourné.

### <a name="remarks"></a>Notes

Cela est généralement appelé de l’intérieur de `WM_LBUTTONDOWN` la `OnLButtonDown`fonction de votre application qui gère le message (généralement ).

Cette fonction captera la souris jusqu’à ce que l’utilisateur libère le bouton de la souris gauche, appuie sur la clé ESC ou appuie sur le bouton de la souris droite. Comme l’utilisateur déplace le curseur de la `DrawTrackerRect` `OnChangedRect`souris, la rétroaction est mise à jour par appel et .

Si *bAllowInvert* est VRAI, le rectangle de suivi peut être inversé sur l’axe x ou y-axe.

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a>CRectTracker::TrackRubberBand

Appelez cette fonction pour faire la sélection des élastiques.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
L’objet de fenêtre qui contient le rectangle.

*Point*<br/>
Coordonnées de l’appareil de la position actuelle de la souris par rapport à la zone client.

*bAllowInvert*<br/>
Si VRAI, le rectangle peut être inversé le long de l’axe x ou y-axe; autrement FALSE.

### <a name="return-value"></a>Valeur de retour

Nonzero si la souris a bougé et le rectangle n’est pas vide; sinon 0.

### <a name="remarks"></a>Notes

Il est généralement appelé de l’intérieur de la fonction de `OnLButtonDown`votre application qui gère le message WM_LBUTTONDOWN (généralement ).

Cette fonction captera la souris jusqu’à ce que l’utilisateur libère le bouton de la souris gauche, appuie sur la clé ESC ou appuie sur le bouton de la souris droite. Comme l’utilisateur déplace le curseur de la `DrawTrackerRect` `OnChangedRect`souris, la rétroaction est mise à jour par appel et .

Le suivi est effectué avec une sélection de type bande de caoutchouc à partir de la poignée inférieure à droite. Si l’inversion est permise, le rectangle peut être dimensionné en traînant vers le haut et vers la gauche ou vers le bas et vers la droite.

## <a name="see-also"></a>Voir aussi

[MFC Sample TRACKER](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe COleResizeBar](../../mfc/reference/coleresizebar-class.md)<br/>
[Classe CRect](../../atl-mfc-shared/reference/crect-class.md)
