---
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
ms.openlocfilehash: bb5d2b53fa5899ac84608dc4ace6a84a3e5a7575
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754763"
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink, classe

Un emballage pour ID2D1GeometrySink.

## <a name="syntax"></a>Syntaxe

```
class CD2DGeometrySink;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Construit un objet CD2DGeometrySink à partir de l’objet CD2DPathGeometry.|
|[CD2DGeometrySink::CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destructeur. Appelé quand un objet d’évier de géométrie D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Ajoute un seul arc à la géométrie du chemin|
|[CD2DGeometrySink::AddBezier](#addbezier)|Crée une courbe de Bézier cubique lissée entre le point actuel et le point de fin spécifié.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Crée une séquence de courbes cubiques de Bézier et les ajoute à l’évier de géométrie.|
|[CD2DGeometrySink::AddLine](#addline)|Crée un segment de ligne entre le point actuel et le point final spécifié et l’ajoute à l’évier de géométrie.|
|[CD2DGeometrySink::AddLines](#addlines)|Crée une séquence de lignes à l’aide des points spécifiés et les ajoute à l’évier de géométrie.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Crée une courbe de Bézier quadratique lissée entre le point actuel et le point de fin spécifié.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Ajoute une séquence de segments quadratic Bezier comme un tableau en un seul appel.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Démarre un nouveau chiffre au point spécifié.|
|[CD2DGeometrySink::Close](#close)|Ferme l’évier de géométrie|
|[CD2DGeometrySink::EndFigure](#endfigure)|Termine le chiffre actuel; optionnellement, ferme-le.|
|[CD2DGeometrySink::Get](#get)|Retourne l’interface ID2D1GeometrySink|
|[CD2DGeometrySink::IsValid](#isvalid)|Vérifie la validité de l’évier de géométrie|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Précise la méthode utilisée pour déterminer quels points sont à l’intérieur de la géométrie décrite par cet évier de géométrie et quels points sont à l’extérieur.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Spécifie les options d’AVC et de jointure à appliquer à de nouveaux segments ajoutés à l’évier de géométrie.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DGeometrySink::opérateur ID2D1GeometrySink](#operator_id2d1geometrysink_star)|Retourne l’interface ID2D1GeometrySink|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Un pointeur à un ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CD2DGeometrySink`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink

Destructeur. Appelé quand un objet d’évier de géométrie D2D est détruit.

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a>CD2DGeometrySink::AddArc

Ajoute un seul arc à la géométrie du chemin

```cpp
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Paramètres

*Arc*<br/>
Le segment d’arc à ajouter à la figure

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a>CD2DGeometrySink::AddBezier

Crée une courbe de Bézier cubique lissée entre le point actuel et le point de fin spécifié.

```cpp
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Paramètres

*Bézier*<br/>
Une structure qui décrit les points de contrôle et le point final de la courbe de Bézier à ajouter.

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a>CD2DGeometrySink::AddBeziers

Crée une séquence de courbes cubiques de Bézier et les ajoute à l’évier de géométrie.

```cpp
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Paramètres

*Béziers*<br/>
Un éventail de segments bézier qui décrit les courbes bézieres à créer. Une courbe est tirée du point actuel de l’évier de géométrie (le point final du dernier segment dessiné ou l’emplacement spécifié par BeginFigure) jusqu’au point final du premier segment bézier dans le tableau. si le tableau contient d’autres segments bézier, chaque segment bezier ultérieur utilise le point final du segment précédent de Bézier comme point de départ.

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a>CD2DGeometrySink::AddLine

Crée un segment de ligne entre le point actuel et le point final spécifié et l’ajoute à l’évier de géométrie.

```cpp
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Le point final de la ligne à dessiner.

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a>CD2DGeometrySink::AddLines

Crée une séquence de lignes à l’aide des points spécifiés et les ajoute à l’évier de géométrie.

```cpp
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Paramètres

*Points*<br/>
Un tableau d’un ou plusieurs points qui décrivent les lignes à dessiner. Une ligne est tracée à partir du point actuel de l’évier de géométrie (le point final du dernier segment dessiné ou l’emplacement spécifié par BeginFigure) au premier point du tableau. si le tableau contient des points supplémentaires, une ligne est tracée du premier point au deuxième point du tableau, du deuxième point au troisième point, et ainsi de suite. Un tableau d’une séquence des points de fin des lignes à dessiner.

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier

Crée une courbe de Bézier quadratique lissée entre le point actuel et le point de fin spécifié.

```cpp
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Paramètres

*Bézier*<br/>
Une structure qui décrit le point de contrôle et le point final de la courbe quadratique bézier à ajouter.

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers

Ajoute une séquence de segments quadratic Bezier comme un tableau en un seul appel.

```cpp
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Paramètres

*Béziers*<br/>
Une série d’une séquence de segments quadratic Bézier.

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a>CD2DGeometrySink::BeginFigure

Démarre un nouveau chiffre au point spécifié.

```cpp
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Paramètres

*startPoint*<br/>
Le moment où commencer le nouveau chiffre.

*figureBegin*<br/>
Si le nouveau chiffre doit être creux ou rempli.

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink

Construit un objet CD2DGeometrySink à partir de l’objet CD2DPathGeometry.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Paramètres

*Pathgeometry*<br/>
Un objet CD2DPathGeometry existant.

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a>CD2DGeometrySink::Close

Ferme l’évier de géométrie

```
BOOL Close();
```

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; autrement FALSE.

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a>CD2DGeometrySink::EndFigure

Termine le chiffre actuel; optionnellement, ferme-le.

```cpp
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Paramètres

*figureEnd*<br/>
Une valeur qui indique si le chiffre actuel est fermé. Si le chiffre est fermé, une ligne est tracée entre le point actuel et le point de départ spécifié par BeginFigure.

## <a name="cd2dgeometrysinkget"></a><a name="get"></a>CD2DGeometrySink::Get

Retourne l’interface ID2D1GeometrySink

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1GeometrySink ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a>CD2DGeometrySink::IsValid

Vérifie la validité de l’évier de géométrie

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si l’évier de géométrie est valide; autrement FALSE.

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a>CD2DGeometrySink::m_pSink

Un pointeur à un ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::opérateur ID2D1GeometrySink

Retourne l’interface ID2D1GeometrySink

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1GeometrySink ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a>CD2DGeometrySink::SetFillMode

Précise la méthode utilisée pour déterminer quels points sont à l’intérieur de la géométrie décrite par cet évier de géométrie et quels points sont à l’extérieur.

```cpp
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Paramètres

*fillMode*<br/>
La méthode utilisée pour déterminer si un point donné fait partie de la géométrie.

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags

Spécifie les options d’AVC et de jointure à appliquer à de nouveaux segments ajoutés à l’évier de géométrie.

```cpp
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Paramètres

*vertexFlags (en)*<br/>
Options d’AVC et de jointure à appliquer à de nouveaux segments ajoutés à l’évier de géométrie.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
