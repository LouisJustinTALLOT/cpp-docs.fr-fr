---
description: 'En savoir plus sur : CRectTracker, classe'
title: CRectTracker (classe)
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
ms.openlocfilehash: 8406b6b45a99ca2e1816cb650f243fcea2db8ddc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343018"
---
# <a name="crecttracker-class"></a>CRectTracker (classe)

Permet d’afficher, de déplacer et de redimensionner un élément de différentes façons.

## <a name="syntax"></a>Syntaxe

```
class CRectTracker
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRectTracker :: CRectTracker](#crecttracker)|Construit un objet `CRectTracker`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRectTracker :: AdjustRect](#adjustrect)|Appelé lorsque le rectangle est redimensionné.|
|[CRectTracker ::D RAW](#draw)|Génère le rendu du rectangle.|
|[CRectTracker ::D rawTrackerRect](#drawtrackerrect)|Appelé lors du dessin de la bordure d’un `CRectTracker` objet.|
|[CRectTracker :: GetHandleMask](#gethandlemask)|Appelé pour obtenir le masque des `CRectTracker` poignées de redimensionnement d’un élément.|
|[CRectTracker :: GetTrueRect](#gettruerect)|Retourne la largeur et la hauteur du rectangle, y compris les poignées de redimensionnement.|
|[CRectTracker :: HitTest](#hittest)|Retourne la position actuelle du curseur associé à l' `CRectTracker` objet.|
|[CRectTracker :: NormalizeHit](#normalizehit)|Normalise un code de test de positionnement.|
|[CRectTracker :: OnChangedRect](#onchangedrect)|Appelé lorsque le rectangle a été redimensionné ou déplacé.|
|[CRectTracker :: SetCursor](#setcursor)|Définit le curseur, en fonction de sa position sur le rectangle.|
|[CRectTracker :: Track](#track)|Permet à l’utilisateur de manipuler le rectangle.|
|[CRectTracker :: TrackRubberBand](#trackrubberband)|Permet à l’utilisateur d’effectuer la sélection « caoutchouc ».|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRectTracker :: m_nHandleSize](#m_nhandlesize)|Détermine la taille des poignées de redimensionnement.|
|[CRectTracker :: m_nStyle](#m_nstyle)|Style (s) actuel (s) du dispositif de suivi.|
|[CRectTracker :: m_rect](#m_rect)|Position actuelle (en pixels) du rectangle.|
|[CRectTracker :: m_sizeMin](#m_sizemin)|Détermine la largeur et la hauteur minimales du rectangle.|

## <a name="remarks"></a>Notes

`CRectTracker` n’a pas de classe de base.

Bien que la `CRectTracker` classe soit conçue pour permettre à l’utilisateur d’interagir avec des éléments OLE à l’aide d’une interface graphique, son utilisation n’est pas limitée aux applications compatibles OLE. Elle peut être utilisée partout où une interface utilisateur est requise.

`CRectTracker` les bordures peuvent être des lignes pleines ou en pointillés. L’élément peut être associé à une bordure hachurée ou à un motif hachuré pour indiquer les différents États de l’élément. Vous pouvez placer huit poignées de redimensionnement à l’extérieur ou à la bordure intérieure de l’élément. (Pour obtenir une explication des poignées de redimensionnement, consultez [GetHandleMask](#gethandlemask).) Enfin, un `CRectTracker` vous permet de modifier l’orientation d’un élément pendant le redimensionnement.

Pour utiliser `CRectTracker` , construisez un `CRectTracker` objet et spécifiez les États d’affichage à initialiser. Vous pouvez ensuite utiliser cette interface pour fournir à l’utilisateur un commentaire visuel sur l’état actuel de l’élément OLE associé à l' `CRectTracker` objet.

Pour plus d’informations sur l’utilisation de `CRectTracker` , consultez l’article de [suivi](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CRectTracker`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a> CRectTracker :: AdjustRect

Appelé par le Framework lorsque le rectangle de suivi est redimensionné à l’aide d’une poignée de redimensionnement.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*nHandle*<br/>
Index du descripteur utilisé.

*lpRect*<br/>
Pointeur vers la taille actuelle du rectangle. (La taille d’un rectangle est donnée par sa hauteur et sa largeur).

### <a name="remarks"></a>Notes

Le comportement par défaut de cette fonction permet à l’orientation du rectangle de changer uniquement lorsque `Track` et `TrackRubberBand` sont appelés avec l’inversion autorisée.

Substituez cette fonction pour contrôler l’ajustement du rectangle de suivi pendant une opération de glissement. Une méthode consiste à ajuster les coordonnées spécifiées par *lpRect* avant de retourner.

Il est possible d’implémenter des fonctionnalités spéciales qui ne sont pas directement prises en charge par `CRectTracker` , telles que l’alignement sur la grille ou le ratio de conservation, en substituant cette fonction.

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a> CRectTracker :: CRectTracker

Crée et initialise un objet `CRectTracker`.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*lpSrcRect*<br/>
Coordonnées de l’objet Rectangle.

*nStyle*<br/>
Spécifie le style de l' `CRectTracker` objet. Les styles suivants sont pris en charge :

- `CRectTracker::solidLine` Utilisez une ligne pleine pour la bordure du rectangle.

- `CRectTracker::dottedLine` Utilisez une ligne en pointillés pour la bordure du rectangle.

- `CRectTracker::hatchedBorder` Utilisez un motif hachuré pour la bordure du rectangle.

- `CRectTracker::resizeInside` Poignées de redimensionnement situées à l’intérieur du rectangle.

- `CRectTracker::resizeOutside` Poignées de redimensionnement situées en dehors du rectangle.

- `CRectTracker::hatchInside` Le modèle hachuré couvre l’ensemble du rectangle.

### <a name="remarks"></a>Notes

Le constructeur par défaut initialise l' `CRectTracker` objet avec les valeurs de *lpSrcRect* et initialise d’autres tailles aux valeurs par défaut du système. Si l’objet est créé sans aucun paramètre, les `m_rect` `m_nStyle` membres de données et ne sont pas initialisés.

## <a name="crecttrackerdraw"></a><a name="draw"></a> CRectTracker ::D RAW

Appelez cette fonction pour dessiner les lignes externes et la région interne du rectangle.

```cpp
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers le contexte de périphérique sur lequel dessiner.

### <a name="remarks"></a>Notes

Le style du dispositif de suivi détermine la façon dont le dessin est effectué. Pour `CRectTracker` plus d’informations sur les styles disponibles, consultez le constructeur.

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a> CRectTracker ::D rawTrackerRect

Appelée par l’infrastructure chaque fois que la position du dispositif de suivi a changé pendant l’intérieur de la `Track` `TrackRubberBand` fonction membre ou.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointeur vers `RECT` qui contient le rectangle à dessiner.

*pWndClipTo*<br/>
Pointeur vers la fenêtre à utiliser pour découper le rectangle.

*Maîtres*<br/>
Pointeur vers le contexte de périphérique sur lequel dessiner.

*pWnd*<br/>
Pointeur vers la fenêtre sur laquelle le dessin doit se produire.

### <a name="remarks"></a>Notes

L’implémentation par défaut effectue un appel à `CDC::DrawFocusRect` , qui dessine un rectangle en pointillés.

Remplacez cette fonction pour fournir des commentaires différents au cours de l’opération de suivi.

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a> CRectTracker :: GetHandleMask

L’infrastructure appelle cette fonction membre pour récupérer le masque des poignées de redimensionnement d’un rectangle.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Valeur renvoyée

Masque des poignées de `CRectTracker` redimensionnement d’un élément.

### <a name="remarks"></a>Notes

Les poignées de redimensionnement apparaissent sur les côtés et les angles du rectangle et permettent à l’utilisateur de contrôler la forme et la taille du rectangle.

Un rectangle a 8 poignées de redimensionnement numérotées 0-7. Chaque poignée de redimensionnement est représentée par un bit dans le masque ; la valeur de ce bit est 2 ^ *n*, où *n* est le numéro de la poignée de redimensionnement. Bits 0-3 correspond aux poignées de redimensionnement d’angle, en commençant par l’angle supérieur gauche qui se déplace dans le sens des aiguilles d’une montre. Bits 4-7 correspond aux poignées de redimensionnement latérales en commençant par le haut qui se déplace dans le sens des aiguilles d’une montre. L’illustration suivante montre les poignées de redimensionnement d’un rectangle et leurs valeurs et nombres de poignées de redimensionnement correspondants :

![Redimensionner les valeurs de la poignée](../../mfc/reference/media/vc35dp1.gif "Redimensionner les valeurs de la poignée")

L’implémentation par défaut de `GetHandleMask` retourne le masque des bits afin que les poignées de redimensionnement apparaissent. Si le bit unique est activé, la poignée de redimensionnement correspondante est dessinée.

Substituez cette fonction membre pour masquer ou afficher les poignées de redimensionnement indiquées.

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a> CRectTracker :: GetTrueRect

Appelez cette fonction pour récupérer les coordonnées du rectangle.

```cpp
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Paramètres

*lpTrueRect*<br/>
Pointeur vers la `RECT` structure qui contient les coordonnées de l’appareil de l' `CRectTracker` objet.

### <a name="remarks"></a>Notes

Les dimensions du rectangle incluent la hauteur et la largeur de toutes les poignées de redimensionnement situées sur la bordure externe. Lors du retour de, *lpTrueRect* est toujours un rectangle normalisé dans les coordonnées de l’appareil.

## <a name="crecttrackerhittest"></a><a name="hittest"></a> CRectTracker :: HitTest

Appelez cette fonction pour déterminer si l’utilisateur a retiré une poignée de redimensionnement.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Point, en coordonnées de périphérique, à tester.

### <a name="return-value"></a>Valeur renvoyée

La valeur retournée est basée sur le type énuméré `CRectTracker::TrackerHit` et peut avoir l’une des valeurs suivantes :

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight` 1,0

- `CRectTracker::hitBottomRight` 2

- `CRectTracker::hitBottomLeft` 1,3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight` 5,5

- `CRectTracker::hitBottom` 6,3

- `CRectTracker::hitLeft` Commission(7

- `CRectTracker::hitMiddle` version8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a> CRectTracker :: m_nHandleSize

Taille, en pixels, des poignées de `CRectTracker` redimensionnement.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Notes

Initialisée avec la valeur système par défaut.

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a> CRectTracker :: m_rect

Position actuelle du rectangle en coordonnées clientes (pixels).

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a> CRectTracker :: m_sizeMin

Taille minimale du rectangle.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Notes

Les valeurs par défaut, `cx` et `cy` , sont calculées à partir de la valeur système par défaut pour la largeur de la bordure. Ce membre de données est utilisé uniquement par la `AdjustRect` fonction membre.

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a> CRectTracker :: m_nStyle

Style actuel du rectangle.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Notes

Pour obtenir la liste des styles possibles, consultez [CRectTracker :: CRectTracker](#crecttracker) .

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a> CRectTracker :: NormalizeHit

Appelez cette fonction pour convertir une poignée potentiellement inversée.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Paramètres

*nHandle*<br/>
Handle sélectionné par l’utilisateur.

### <a name="return-value"></a>Valeur renvoyée

Index du handle normalisé.

### <a name="remarks"></a>Notes

Lorsque `CRectTracker::Track` ou `CRectTracker::TrackRubberBand` est appelé avec l’inversion autorisée, il est possible que le rectangle soit inversé sur l’axe x, l’axe y ou les deux. Dans ce cas, `HitTest` retourne des handles qui sont également inversés par rapport au rectangle. Cela n’est pas approprié pour le dessin des commentaires des curseurs, car les commentaires dépendent de la position de l’écran du rectangle, et non pas de la partie de la structure de données du rectangle qui sera modifiée.

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a> CRectTracker :: OnChangedRect

Appelée par l’infrastructure chaque fois que le rectangle de suivi a changé pendant un appel à `Track` .

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Paramètres

*rectOld*<br/>
Contient les coordonnées d’appareil anciennes de l' `CRectTracker` objet.

### <a name="remarks"></a>Notes

Au moment où cette fonction est appelée, tous les commentaires qui `DrawTrackerRect` ont été dessinés avec ont été supprimés. L’implémentation par défaut de cette fonction est sans effet.

Substituez cette fonction lorsque vous souhaitez effectuer des actions après le redimensionnement du rectangle.

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a> CRectTracker :: SetCursor

Appelez cette fonction pour modifier la forme de curseur alors qu’elle se trouve sur la `CRectTracker` région de l’objet.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre qui contient actuellement le curseur.

*nHitTest*<br/>
Résultats du test de positionnement précédent, à partir du message de WM_SETCURSOR.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’accès précédent était sur le rectangle de suivi ; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction à partir de la fonction de votre fenêtre qui gère le message d’WM_SETCURSOR (en général `OnSetCursor` ).

## <a name="crecttrackertrack"></a><a name="track"></a> CRectTracker :: Track

Appelez cette fonction pour afficher l’interface utilisateur pour le redimensionnement du rectangle.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Objet de fenêtre qui contient le rectangle.

*point*<br/>
Coordonnées de l’appareil de la position actuelle de la souris par rapport à la zone cliente.

*bAllowInvert*<br/>
Si la valeur est TRUE, le rectangle peut être inversé le long de l’axe x ou de l’axe y ; Sinon, FALSe.

*pWndClipTo*<br/>
Fenêtre dans laquelle les opérations de dessin seront découpées. Si la valeur est NULL, *pwnd* est utilisé comme rectangle de découpage.

### <a name="return-value"></a>Valeur renvoyée

Si la touche Échap est enfoncée, le processus de suivi est interrompu, le rectangle stocké dans le dispositif de suivi n’est pas modifié et la valeur 0 est retournée. Si la modification est validée, en déplaçant la souris et en relâchant le bouton gauche de la souris, la nouvelle position et/ou taille est enregistrée dans le rectangle du dispositif de suivi et la valeur différente de zéro est retournée.

### <a name="remarks"></a>Notes

Cette méthode est généralement appelée depuis l’intérieur de la fonction de votre application qui gère le `WM_LBUTTONDOWN` message (en général `OnLButtonDown` ).

Cette fonction capture la souris jusqu’à ce que l’utilisateur relâche le bouton gauche de la souris, appuie sur la touche Échap ou appuie sur le bouton droit de la souris. Lorsque l’utilisateur déplace le curseur de la souris, les commentaires sont mis à jour en appelant `DrawTrackerRect` et `OnChangedRect` .

Si *bAllowInvert* a la valeur true, le rectangle de suivi peut être inversé sur l’axe des x ou l’axe des y.

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a> CRectTracker :: TrackRubberBand

Appelez cette fonction pour effectuer une sélection de bandes en caoutchouc.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Objet de fenêtre qui contient le rectangle.

*point*<br/>
Coordonnées de l’appareil de la position actuelle de la souris par rapport à la zone cliente.

*bAllowInvert*<br/>
Si la valeur est TRUE, le rectangle peut être inversé le long de l’axe x ou de l’axe y ; Sinon, FALSe.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la souris a été déplacée et que le rectangle n’est pas vide. Sinon, 0.

### <a name="remarks"></a>Notes

Elle est généralement appelée depuis l’intérieur de la fonction de votre application qui gère le message WM_LBUTTONDOWN (en général `OnLButtonDown` ).

Cette fonction capture la souris jusqu’à ce que l’utilisateur relâche le bouton gauche de la souris, appuie sur la touche Échap ou appuie sur le bouton droit de la souris. Lorsque l’utilisateur déplace le curseur de la souris, les commentaires sont mis à jour en appelant `DrawTrackerRect` et `OnChangedRect` .

Le suivi est effectué avec une sélection de type bande en caoutchouc à partir du handle inférieur droit. Si l’inversion est autorisée, le rectangle peut être dimensionné en faisant glisser vers le haut et vers la gauche ou vers la droite et vers la droite.

## <a name="see-also"></a>Voir aussi

[Exemple de suivi MFC](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar, classe](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect, classe](../../atl-mfc-shared/reference/crect-class.md)
