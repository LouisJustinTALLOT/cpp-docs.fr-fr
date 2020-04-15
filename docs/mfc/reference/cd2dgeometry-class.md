---
title: CD2DGeometry, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
ms.openlocfilehash: 2631005fcedfb8d5db69667e22c375f585b4f044
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369244"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry, classe

Un emballage pour ID2D1Geometry.

## <a name="syntax"></a>Syntaxe

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Construit un objet CD2DGeometry.|
|[CD2DGeometry::CD2DGeometry](#_dtorcd2dgeometry)|Destructeur. Appelé quand un objet de géométrie D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DGeometry::Attach](#attach)|Attache l’interface de ressources existante à l’objet|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Combine cette géométrie avec la géométrie spécifiée et stocke le résultat dans un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Décrit l’intersection entre cette géométrie et la géométrie spécifiée. La comparaison est effectuée à l’aide de la tolérance à l’aplatissement spécifiée.|
|[CD2DGeometry::ComputeArea](#computearea)|Calcule la zone de la géométrie après qu’elle a été transformée par la matrice spécifiée et aplatie à l’aide de la tolérance spécifiée.|
|[CD2DGeometry::ComputeLength](#computelength)|Calcule la longueur de la géométrie comme si chaque segment était déroulé dans une ligne.|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Calcule le point et le vecteur tangent à la distance spécifiée le long de la géométrie après qu’il a été transformé par la matrice spécifiée et aplati en utilisant la tolérance spécifiée.|
|[CD2DGeometry::Destroy](#destroy)|Détruit un objet CD2DGeometry. (Overrides [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DGeometry::Detach](#detach)|Détache l’interface des ressources de l’objet|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Indique si la zone remplie par la géométrie contiendrait le point spécifié étant donné la tolérance à l’aplatissement spécifiée.|
|[CD2DGeometry::Get](#get)|Retourne l’interface ID2D1Geometry|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Obtient les limites de la géométrie après qu’il a été élargi par la largeur et le style spécifiés de course et transformé par la matrice spécifiée.|
|[CD2DGeometry::IsValid](#isvalid)|Vérifie la validité des ressources (Overrides [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DGeometry::Outline](#outline)|Calcule le contour de la géométrie et écrit le résultat à un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::Simplifier](#simplify)|Crée une version simplifiée de la géométrie qui ne contient que des lignes et (optionnellement) des courbes bœères cubiques et écrit le résultat à un ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Détermine si le trait de la géométrie contient le point spécifié compte tenu de l’épaisseur, du style et de la transformation spécifiés.|
|[CD2DGeometry::Tessellate](#tessellate)|Crée un ensemble de triangles enroulés dans le sens horaire qui couvrent la géométrie après avoir été transformés à l'aide de la matrice spécifiée et aplatis à l'aide de la tolérance spécifiée.|
|[CD2DGeometry::Widen](#widen)|Élargit la géométrie par le trait spécifié et écrit le résultat à un ID2D1SimplifiedGeometrySink après qu’il a été transformé par la matrice spécifiée et aplati en utilisant la tolérance spécifiée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DGeometry::opérateur ID2D1Geometry](#operator_id2d1geometry_star)|Retourne l’interface ID2D1Geometry|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Un pointeur à un ID2D1Geometry.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource (en anglais)](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a>CD2DGeometry::CD2DGeometry

Destructeur. Appelé quand un objet de géométrie D2D est détruit.

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a>CD2DGeometry::Attach

Attache l’interface de ressources existante à l’objet

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Paramètres

*pResource (en)*<br/>
Interface de ressources existante. Impossible d’être NULL

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry

Construit un objet CD2DGeometry.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Un pointeur à la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry

Combine cette géométrie avec la géométrie spécifiée et stocke le résultat dans un ID2D1SimplifiedGeometrySink.

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*inputGeometry (en)*<br/>
La géométrie à combiner avec cette instance.

*combineMode*<br/>
Le type d’opération de combiner pour effectuer.

*inputGeometryTransform*<br/>
La transformation à appliquer à l’entréeGeometry avant de combiner.

*géométrieSink*<br/>
Le résultat de l’opération de moissonneuse-batteuse.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale des géométries. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry

Décrit l’intersection entre cette géométrie et la géométrie spécifiée. La comparaison est effectuée à l’aide de la tolérance à l’aplatissement spécifiée.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*inputGeometry (en)*<br/>
La géométrie à tester.

*inputGeometryTransform*<br/>
La transformation à appliquer à l’entréeGeometry.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale des géométries. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a>CD2DGeometry::ComputeArea

Calcule la zone de la géométrie après qu’elle a été transformée par la matrice spécifiée et aplatie à l’aide de la tolérance spécifiée.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*mondeTransforme*<br/>
La transformation pour s’appliquer à cette géométrie avant de calculer sa zone.

*Zone*<br/>
Lorsque cette méthode revient, contient un pointeur à la zone de la version transformée et aplatie de cette géométrie. Vous devez allouer le stockage pour ce paramètre.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a>CD2DGeometry::ComputeLength

Calcule la longueur de la géométrie comme si chaque segment était déroulé dans une ligne.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*mondeTransforme*<br/>
La transformation pour s’appliquer à la géométrie avant de calculer sa longueur.

*length*<br/>
Lorsque cette méthode revient, contient un pointeur sur la longueur de la géométrie. Pour les géométries fermées, la longueur comprend un segment de clôture implicite. Vous devez allouer le stockage pour ce paramètre.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength

Calcule le point et le vecteur tangent à la distance spécifiée le long de la géométrie après qu’il a été transformé par la matrice spécifiée et aplati en utilisant la tolérance spécifiée.

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*length*<br/>
La distance le long de la géométrie du point et tangente à trouver. Si cette distance est inférieure à 0, cette méthode calcule le premier point de la géométrie. Si cette distance est supérieure à la longueur de la géométrie, cette méthode calcule le dernier point de la géométrie.

*mondeTransforme*<br/>
La transformation pour s’appliquer à la géométrie avant de calculer le point spécifié et la tangente.

*Point*<br/>
L’emplacement à la distance spécifiée le long de la géométrie. Si la géométrie est vide, ce point contient NaN comme ses valeurs x et y.

*unitéTangentVector*<br/>
Lorsque cette méthode revient, contient un pointeur sur le vecteur tangent à la distance spécifiée le long de la géométrie. Si la géométrie est vide, ce vecteur contient NaN comme valeurs x et y. Vous devez allouer le stockage pour ce paramètre.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a>CD2DGeometry::Destroy

Détruit un objet CD2DGeometry.

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a>CD2DGeometry::Detach

Détache l’interface des ressources de l’objet

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface de ressource détachée.

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint

Indique si la zone remplie par la géométrie contiendrait le point spécifié étant donné la tolérance à l’aplatissement spécifiée.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Point à tester.

*mondeTransforme*<br/>
La transformation pour s’appliquer à la géométrie avant l’essai pour le confinement.

*Contient*<br/>
Lorsque cette méthode revient, contient une valeur bool qui est VRAI si la zone remplie par la géométrie contient point; autrement, FALSE. Vous devez allouer le stockage pour ce paramètre.

*aplatissementTolerance*<br/>
La précision numérique avec laquelle le chemin géométrique précis et l’intersection du chemin est calculé. Les points manquant le remplissage par moins que la tolérance sont toujours considérés à l’intérieur. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometryget"></a><a name="get"></a>CD2DGeometry::Get

Retourne l’interface ID2D1Geometry

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Geometry ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a>CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>Paramètres

*mondeTransforme*<br/>
*Limites*

### <a name="return-value"></a>Valeur de retour

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds

Obtient les limites de la géométrie après qu’il a été élargi par la largeur et le style spécifiés de course et transformé par la matrice spécifiée.

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*strokeWidth*<br/>
La quantité par laquelle élargir la géométrie en caressant son contour.

*strokeStyle (en)*<br/>
Le style du trait qui élargit la géométrie.

*mondeTransforme*<br/>
Une transformation à appliquer à la géométrie après la transformation de la géométrie et après la géométrie a été caressée.

*Limites*<br/>
Lorsque cette méthode revient, contient les limites de la géométrie élargie. Vous devez allouer le stockage pour ce paramètre.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale des géométries. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a>CD2DGeometry::IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la ressource est valide; autrement FALSE.

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry

Un pointeur à un ID2D1Geometry.

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a>CD2DGeometry::opérateur ID2D1Geometry

Retourne l’interface ID2D1Geometry

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface ID2D1Geometry ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dgeometryoutline"></a><a name="outline"></a>CD2DGeometry::Outline

Calcule le contour de la géométrie et écrit le résultat à un ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*mondeTransforme*<br/>
La transformation à appliquer à la géométrie.

*géométrieSink*<br/>
Le ID2D1SimplifiéGeometrySink auquel le contour transformé par la géométrie est annexé.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a>CD2DGeometry::Simplifier

Crée une version simplifiée de la géométrie qui ne contient que des lignes et (optionnellement) des courbes bœères cubiques et écrit le résultat à un ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*simplificationOption*<br/>
Une valeur qui précise si la géométrie simplifiée doit contenir des courbes.

*mondeTransforme*<br/>
La transformation pour s’appliquer à la géométrie simplifiée.

*géométrieSink*<br/>
L’ID2D1SimplifiéGeometrySink auquel la géométrie simplifiée est annexée.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint

Détermine si le trait de la géométrie contient le point spécifié compte tenu de l’épaisseur, du style et de la transformation spécifiés.

```
BOOL StrokeContainsPoint(
    CD2DPointF point,
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
Point dont la relation contenant-contenu doit être testée.

*strokeWidth*<br/>
L’épaisseur du trait à appliquer.

*strokeStyle (en)*<br/>
Le style de l’AVC à appliquer.

*mondeTransforme*<br/>
La transformation pour s’appliquer à la géométrie caressée.

*Contient*<br/>
Lorsque cette méthode revient, contient une valeur boolean définie à VRAI si le trait de la géométrie contient le point spécifié; autrement, FALSE. Vous devez allouer le stockage pour ce paramètre.

*aplatissementTolerance*<br/>
La précision numérique avec laquelle le chemin géométrique précis et l’intersection du chemin est calculé. Les points manquants de l’AVC par moins que la tolérance sont toujours considérés à l’intérieur. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a>CD2DGeometry::Tessellate

Crée un ensemble de triangles enroulés dans le sens horaire qui couvrent la géométrie après avoir été transformés à l'aide de la matrice spécifiée et aplatis à l'aide de la tolérance spécifiée.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*mondeTransforme*<br/>
La transformation à appliquer à cette géométrie, ou NULL.

*tessellationSink*<br/>
L’ID2D1TessellationSink auquel le tessellated est annexé.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="cd2dgeometrywiden"></a><a name="widen"></a>CD2DGeometry::Widen

Élargit la géométrie par le trait spécifié et écrit le résultat à un ID2D1SimplifiedGeometrySink après qu’il a été transformé par la matrice spécifiée et aplati en utilisant la tolérance spécifiée.

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*strokeWidth*<br/>
La quantité par laquelle élargir la géométrie.

*strokeStyle (en)*<br/>
Le style d’AVC à appliquer à la géométrie, ou NULL.

*mondeTransforme*<br/>
La transformation pour s’appliquer à la géométrie après l’avoir élargie.

*géométrieSink*<br/>
L’ID2D1SimplifiéGeometrySink auquel la géométrie élargie est annexée.

*aplatissementTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle revient VRAI. Sinon, il retourne FALSE.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
