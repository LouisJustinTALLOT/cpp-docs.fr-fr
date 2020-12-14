---
description: 'En savoir plus sur : classe Cd2dgeometrysink,'
title: CD2DGeometrySink, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
ms.openlocfilehash: e7916cdb39272e924a9d6ef6c0a8322d8ce6fb1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193420"
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink, classe

Wrapper pour ID2D1GeometrySink.

## <a name="syntax"></a>Syntaxe

```
class CD2DGeometrySink;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dgeometrysink, :: Cd2dgeometrysink,](#cd2dgeometrysink)|Construit un objet Cd2dgeometrysink, à partir de l’objet Cd2dpathgeometry,.|
|[Cd2dgeometrysink, :: ~ Cd2dgeometrysink,](#_dtorcd2dgeometrysink)|Destructeur. Appelé lorsqu’un objet récepteur de géométrie D2D est en cours de destruction.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dgeometrysink, :: AddArc](#addarc)|Ajoute un seul arc à la géométrie du tracé|
|[Cd2dgeometrysink, :: AddBezier](#addbezier)|Crée une courbe de Bézier cubique lissée entre le point actuel et le point de fin spécifié.|
|[Cd2dgeometrysink, :: AddBeziers](#addbeziers)|Crée une séquence de courbes de Bézier cubiques et les ajoute au récepteur de géométrie.|
|[Cd2dgeometrysink, :: AddLine](#addline)|Crée un segment de ligne entre le point actuel et le point de terminaison spécifié et l’ajoute au récepteur de géométrie.|
|[Cd2dgeometrysink, :: AddLines](#addlines)|Crée une séquence de lignes à l’aide des points spécifiés et les ajoute au récepteur de géométrie.|
|[Cd2dgeometrysink, :: AddQuadraticBezier](#addquadraticbezier)|Crée une courbe de Bézier quadratique lissée entre le point actuel et le point de fin spécifié.|
|[Cd2dgeometrysink, :: AddQuadraticBeziers](#addquadraticbeziers)|Ajoute une séquence de segments de Bézier quadratiques sous la forme d’un tableau en un seul appel.|
|[Cd2dgeometrysink, :: BeginFigure](#beginfigure)|Démarre une nouvelle figure au point spécifié.|
|[Cd2dgeometrysink, :: Close](#close)|Ferme le récepteur de géométrie|
|[Cd2dgeometrysink, :: EndFigure](#endfigure)|Met fin à la figure en cours ; le cas échéant, la ferme.|
|[Cd2dgeometrysink, :: obtient](#get)|Retourne l’interface ID2D1GeometrySink|
|[Cd2dgeometrysink, :: IsValid](#isvalid)|Vérifie la validité du récepteur de géométrie|
|[Cd2dgeometrysink, :: SetFillMode](#setfillmode)|Spécifie la méthode utilisée pour déterminer les points situés à l’intérieur de la géométrie décrite par ce récepteur de géométrie et les points qui se trouvent à l’extérieur.|
|[Cd2dgeometrysink, :: SetSegmentFlags](#setsegmentflags)|Spécifie les options de trait et de jointure à appliquer aux nouveaux segments ajoutés au récepteur de géométrie.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dgeometrysink, :: Operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|Retourne l’interface ID2D1GeometrySink|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dgeometrysink, :: m_pSink](#m_psink)|Pointeur vers un ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CD2DGeometrySink`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a> Cd2dgeometrysink, :: ~ Cd2dgeometrysink,

Destructeur. Appelé lorsqu’un objet récepteur de géométrie D2D est en cours de destruction.

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a> Cd2dgeometrysink, :: AddArc

Ajoute un seul arc à la géométrie du tracé

```cpp
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Paramètres

*arc*<br/>
Segment d’arc à ajouter à la figure

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a> Cd2dgeometrysink, :: AddBezier

Crée une courbe de Bézier cubique lissée entre le point actuel et le point de fin spécifié.

```cpp
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Paramètres

*interpolation*<br/>
Structure qui décrit les points de contrôle et le point de terminaison de la courbe Bézier à ajouter.

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a> Cd2dgeometrysink, :: AddBeziers

Crée une séquence de courbes de Bézier cubiques et les ajoute au récepteur de géométrie.

```cpp
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Paramètres

*éléments Bézier*<br/>
Tableau de segments de Bézier qui décrit les courbes de Bézier à créer. Une courbe est dessinée à partir du point actuel du récepteur de géométrie (point de terminaison du dernier segment dessiné ou de l’emplacement spécifié par BeginFigure) vers le point de terminaison du premier segment de Bézier dans le tableau. Si le tableau contient des segments de Bézier supplémentaires, chaque segment de Bézier suivant utilise le point de terminaison du segment de Bézier précédent comme point de départ.

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a> Cd2dgeometrysink, :: AddLine

Crée un segment de ligne entre le point actuel et le point de terminaison spécifié et l’ajoute au récepteur de géométrie.

```cpp
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Point de terminaison de la ligne à dessiner.

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a> Cd2dgeometrysink, :: AddLines

Crée une séquence de lignes à l’aide des points spécifiés et les ajoute au récepteur de géométrie.

```cpp
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Paramètres

*moments*<br/>
Tableau d’un ou plusieurs points qui décrivent les lignes à dessiner. Une ligne est dessinée à partir du point actuel du récepteur de géométrie (point de terminaison du dernier segment dessiné ou de l’emplacement spécifié par BeginFigure) au premier point du tableau. Si le tableau contient des points supplémentaires, une ligne est dessinée à partir du premier point jusqu’au deuxième point du tableau, du deuxième point au troisième point, et ainsi de suite. Tableau d’une séquence des points de terminaison des lignes à dessiner.

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a> Cd2dgeometrysink, :: AddQuadraticBezier

Crée une courbe de Bézier quadratique lissée entre le point actuel et le point de fin spécifié.

```cpp
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Paramètres

*interpolation*<br/>
Structure qui décrit le point de contrôle et le point de terminaison de la courbe de Bézier quadratique à ajouter.

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a> Cd2dgeometrysink, :: AddQuadraticBeziers

Ajoute une séquence de segments de Bézier quadratiques sous la forme d’un tableau en un seul appel.

```cpp
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Paramètres

*éléments Bézier*<br/>
Tableau d’une séquence de segments de Bézier quadratiques.

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a> Cd2dgeometrysink, :: BeginFigure

Démarre une nouvelle figure au point spécifié.

```cpp
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Paramètres

*PathFigure*<br/>
Point à partir duquel commencer la nouvelle figure.

*figureBegin*<br/>
Indique si la nouvelle figure doit être vide ou remplie.

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a> Cd2dgeometrysink, :: Cd2dgeometrysink,

Construit un objet Cd2dgeometrysink, à partir de l’objet Cd2dpathgeometry,.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Paramètres

*pathGeometry*<br/>
Objet Cd2dpathgeometry, existant.

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a> Cd2dgeometrysink, :: Close

Ferme le récepteur de géométrie

```
BOOL Close();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; Sinon, FALSe.

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a> Cd2dgeometrysink, :: EndFigure

Met fin à la figure en cours ; le cas échéant, la ferme.

```cpp
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Paramètres

*figureEnd*<br/>
Valeur qui indique si la figure en cours est fermée. Si la figure est fermée, une ligne est dessinée entre le point actuel et le point de départ spécifié par BeginFigure.

## <a name="cd2dgeometrysinkget"></a><a name="get"></a> Cd2dgeometrysink, :: obtient

Retourne l’interface ID2D1GeometrySink

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1GeometrySink ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a> Cd2dgeometrysink, :: IsValid

Vérifie la validité du récepteur de géométrie

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le récepteur de géométrie est valide ; Sinon, FALSe.

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a> Cd2dgeometrysink, :: m_pSink

Pointeur vers un ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a> Cd2dgeometrysink, :: Operator ID2D1GeometrySink *

Retourne l’interface ID2D1GeometrySink

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1GeometrySink ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a> Cd2dgeometrysink, :: SetFillMode

Spécifie la méthode utilisée pour déterminer les points situés à l’intérieur de la géométrie décrite par ce récepteur de géométrie et les points qui se trouvent à l’extérieur.

```cpp
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Paramètres

*fillMode*<br/>
Méthode utilisée pour déterminer si un point donné fait partie de la géométrie.

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a> Cd2dgeometrysink, :: SetSegmentFlags

Spécifie les options de trait et de jointure à appliquer aux nouveaux segments ajoutés au récepteur de géométrie.

```cpp
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Paramètres

*vertexFlags*<br/>
Options de trait et de jointure à appliquer aux nouveaux segments ajoutés au récepteur de géométrie.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
