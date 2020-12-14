---
description: 'En savoir plus sur : classe Cd2dgeometry,'
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
ms.openlocfilehash: 2c902554ba5377ce9f7a4a481d4001a9ef7a47f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193446"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry, classe

Wrapper pour ID2D1Geometry.

## <a name="syntax"></a>Syntaxe

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dgeometry, :: Cd2dgeometry,](#cd2dgeometry)|Construit un objet Cd2dgeometry,.|
|[Cd2dgeometry, :: ~ Cd2dgeometry,](#_dtorcd2dgeometry)|Destructeur. Appelée lorsqu’un objet Geometry D2D est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dgeometry, :: Attach](#attach)|Attache une interface de ressource existante à l’objet.|
|[Cd2dgeometry, :: CombineWithGeometry](#combinewithgeometry)|Combine cette géométrie à la géométrie spécifiée et stocke le résultat dans un ID2D1SimplifiedGeometrySink.|
|[Cd2dgeometry, :: CompareWithGeometry](#comparewithgeometry)|Décrit l’intersection entre cette géométrie et la géométrie spécifiée. La comparaison est effectuée à l’aide de la tolérance d’aplatissement spécifiée.|
|[Cd2dgeometry, :: ComputeArea](#computearea)|Calcule la zone de la géométrie après qu’elle a été transformée par la matrice spécifiée et aplatie à l’aide de la tolérance spécifiée.|
|[Cd2dgeometry, :: ComputeLength](#computelength)|Calcule la longueur de la géométrie comme si chaque segment était déroulé dans une ligne.|
|[Cd2dgeometry, :: ComputePointAtLength](#computepointatlength)|Calcule le vecteur point et tangent à la distance spécifiée le long de la géométrie après qu’il a été transformé par la matrice spécifiée et aplati à l’aide de la tolérance spécifiée.|
|[Cd2dgeometry, ::D estroy](#destroy)|Détruit un objet Cd2dgeometry,. (Substitue [CD2DResource, ::D estroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[Cd2dgeometry, ::D Etach](#detach)|Détache l’interface de ressource de l’objet|
|[Cd2dgeometry, :: FillContainsPoint](#fillcontainspoint)|Indique si la zone remplie par la géométrie contient le point spécifié en fonction de la tolérance de aplatissement spécifiée.|
|[Cd2dgeometry, :: obtient](#get)|Retourne l’interface ID2D1Geometry|
|[Cd2dgeometry, :: GetBounds](#getbounds)||
|[Cd2dgeometry, :: GetWidenedBounds](#getwidenedbounds)|Obtient les limites de la géométrie après qu’elle a été élargie par la largeur et le style de trait spécifiés et transformée par la matrice spécifiée.|
|[Cd2dgeometry, :: IsValid](#isvalid)|Vérifie la validité des ressources (Substitue [CD2DResource, :: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[Cd2dgeometry, :: Outline](#outline)|Calcule le contour de la géométrie et écrit le résultat dans un ID2D1SimplifiedGeometrySink.|
|[Cd2dgeometry, :: simplifier](#simplify)|Crée une version simplifiée de la géométrie qui contient uniquement des lignes et (éventuellement) des courbes de Bézier cubiques et écrit le résultat dans un ID2D1SimplifiedGeometrySink.|
|[Cd2dgeometry, :: StrokeContainsPoint](#strokecontainspoint)|Détermine si le trait de la géométrie contient le point spécifié en fonction de l’épaisseur du trait, du style et de la transformation spécifiés.|
|[Cd2dgeometry, :: paver](#tessellate)|Crée un ensemble de triangles enroulés dans le sens horaire qui couvrent la géométrie après avoir été transformés à l'aide de la matrice spécifiée et aplatis à l'aide de la tolérance spécifiée.|
|[Cd2dgeometry, :: Widening](#widen)|Élargit la géométrie par le trait spécifié et écrit le résultat dans un ID2D1SimplifiedGeometrySink après qu’il a été transformé par la matrice spécifiée et aplati à l’aide de la tolérance spécifiée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dgeometry, :: Operator ID2D1Geometry *](#operator_id2d1geometry_star)|Retourne l’interface ID2D1Geometry|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[Cd2dgeometry, :: m_pGeometry](#m_pgeometry)|Pointeur vers un ID2D1Geometry.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource,](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a> Cd2dgeometry, :: ~ Cd2dgeometry,

Destructeur. Appelée lorsqu’un objet Geometry D2D est détruit.

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a> Cd2dgeometry, :: Attach

Attache une interface de ressource existante à l’objet.

```cpp
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Paramètres

*Préversion*<br/>
Interface de ressource existante. Ne peut pas être NULL

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a> Cd2dgeometry, :: Cd2dgeometry,

Construit un objet Cd2dgeometry,.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*pParentTarget*<br/>
Pointeur vers la cible de rendu.

*bAutoDestroy*<br/>
Indique que l’objet sera détruit par le propriétaire (pParentTarget).

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a> Cd2dgeometry, :: CombineWithGeometry

Combine cette géométrie à la géométrie spécifiée et stocke le résultat dans un ID2D1SimplifiedGeometrySink.

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*inputGeometry*<br/>
Géométrie à combiner à cette instance.

*combineMode*<br/>
Type d’opération de combinaison à effectuer.

*inputGeometryTransform*<br/>
Transformation à appliquer à inputGeometry avant la combinaison.

*geometrySink*<br/>
Résultat de l’opération de combinaison.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale des géométries. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a> Cd2dgeometry, :: CompareWithGeometry

Décrit l’intersection entre cette géométrie et la géométrie spécifiée. La comparaison est effectuée à l’aide de la tolérance d’aplatissement spécifiée.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*inputGeometry*<br/>
Géométrie à tester.

*inputGeometryTransform*<br/>
Transformation à appliquer à inputGeometry.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale des géométries. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a> Cd2dgeometry, :: ComputeArea

Calcule la zone de la géométrie après qu’elle a été transformée par la matrice spécifiée et aplatie à l’aide de la tolérance spécifiée.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*worldTransform*<br/>
Transformation à appliquer à cette géométrie avant de calculer sa zone.

*partie*<br/>
Lorsque cette méthode est retournée, contient un pointeur vers la zone de la version transformée et aplatie de cette géométrie. Vous devez allouer du stockage pour ce paramètre.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a> Cd2dgeometry, :: ComputeLength

Calcule la longueur de la géométrie comme si chaque segment était déroulé dans une ligne.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*worldTransform*<br/>
Transformation à appliquer à la géométrie avant de calculer sa longueur.

*length*<br/>
Lorsque cette méthode est retournée, contient un pointeur vers la longueur de la géométrie. Pour les géométries fermées, la longueur comprend un segment de fermeture implicite. Vous devez allouer du stockage pour ce paramètre.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a> Cd2dgeometry, :: ComputePointAtLength

Calcule le vecteur point et tangent à la distance spécifiée le long de la géométrie après qu’il a été transformé par la matrice spécifiée et aplati à l’aide de la tolérance spécifiée.

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
Distance le long de la géométrie du point et de la tangente à rechercher. Si cette distance est inférieure à 0, cette méthode calcule le premier point de la géométrie. Si cette distance est supérieure à la longueur de la géométrie, cette méthode calcule le dernier point de la géométrie.

*worldTransform*<br/>
Transformation à appliquer à la géométrie avant de calculer le point et la tangente spécifiés.

*point*<br/>
Emplacement à la distance spécifiée le long de la géométrie. Si la géométrie est vide, ce point contient NaN comme valeurs x et y.

*unitTangentVector*<br/>
Lorsque cette méthode est retournée, contient un pointeur vers le vecteur tangent à la distance spécifiée le long de la géométrie. Si la géométrie est vide, ce vecteur contient NaN comme valeurs x et y. Vous devez allouer du stockage pour ce paramètre.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a> Cd2dgeometry, ::D estroy

Détruit un objet Cd2dgeometry,.

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a> Cd2dgeometry, ::D Etach

Détache l’interface de ressource de l’objet

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface de ressource détachée.

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a> Cd2dgeometry, :: FillContainsPoint

Indique si la zone remplie par la géométrie contient le point spécifié en fonction de la tolérance de aplatissement spécifiée.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*point*<br/>
Point à tester.

*worldTransform*<br/>
Transformation à appliquer à la géométrie avant le test de la relation contenant-contenu.

*contains*<br/>
Lorsque cette méthode est retournée, contient une valeur booléenne qui est TRUE si la zone remplie par la géométrie contient un point ; Sinon, FALSe. Vous devez allouer du stockage pour ce paramètre.

*flatteningTolerance*<br/>
Précision numérique avec laquelle le tracé géométrique et l’intersection de tracés précis sont calculés. Les points qui manquent le remplissage de moins que la tolérance sont toujours considérés dans. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometryget"></a><a name="get"></a> Cd2dgeometry, :: obtient

Retourne l’interface ID2D1Geometry

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Geometry ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a> Cd2dgeometry, :: GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>Paramètres

*worldTransform*<br/>
*limites*

### <a name="return-value"></a>Valeur renvoyée

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a> Cd2dgeometry, :: GetWidenedBounds

Obtient les limites de la géométrie après qu’elle a été élargie par la largeur et le style de trait spécifiés et transformée par la matrice spécifiée.

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
Valeur d’élargissement de la géométrie en traçant son contour.

*strokeStyle*<br/>
Style du trait qui élargit la géométrie.

*worldTransform*<br/>
Transformation à appliquer à la géométrie après la transformation de la géométrie et une fois que la géométrie a été rayée.

*limites*<br/>
Lorsque cette méthode est retournée, contient les limites de la géométrie étendue. Vous devez allouer du stockage pour ce paramètre.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale des géométries. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a> Cd2dgeometry, :: IsValid

Vérifie la validité des ressources

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la ressource est valide ; Sinon, FALSe.

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a> Cd2dgeometry, :: m_pGeometry

Pointeur vers un ID2D1Geometry.

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a> Cd2dgeometry, :: Operator ID2D1Geometry *

Retourne l’interface ID2D1Geometry

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une interface ID2D1Geometry ou NULL si l’objet n’est pas encore initialisé.

## <a name="cd2dgeometryoutline"></a><a name="outline"></a> Cd2dgeometry, :: Outline

Calcule le contour de la géométrie et écrit le résultat dans un ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*worldTransform*<br/>
Transformation à appliquer au contour de la géométrie.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink auquel le contour de la géométrie transformée est ajouté.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a> Cd2dgeometry, :: simplifier

Crée une version simplifiée de la géométrie qui contient uniquement des lignes et (éventuellement) des courbes de Bézier cubiques et écrit le résultat dans un ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*simplificationOption*<br/>
Valeur qui spécifie si la géométrie simplifiée doit contenir des courbes.

*worldTransform*<br/>
Transformation à appliquer à la géométrie simplifiée.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink auquel la géométrie simplifiée est ajoutée.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a> Cd2dgeometry, :: StrokeContainsPoint

Détermine si le trait de la géométrie contient le point spécifié en fonction de l’épaisseur du trait, du style et de la transformation spécifiés.

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

*point*<br/>
Point dont la relation contenant-contenu doit être testée.

*strokeWidth*<br/>
Épaisseur du trait à appliquer.

*strokeStyle*<br/>
Style du trait à appliquer.

*worldTransform*<br/>
Transformation à appliquer à la géométrie rayée.

*contains*<br/>
Lorsque cette méthode est retournée, contient une valeur booléenne définie sur TRUE si le trait de la géométrie contient le point spécifié ; Sinon, FALSe. Vous devez allouer du stockage pour ce paramètre.

*flatteningTolerance*<br/>
Précision numérique avec laquelle le tracé géométrique et l’intersection de tracés précis sont calculés. Les points qui manquent le trait de moins que la tolérance sont toujours considérés dans. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a> Cd2dgeometry, :: paver

Crée un ensemble de triangles enroulés dans le sens horaire qui couvrent la géométrie après avoir été transformés à l'aide de la matrice spécifiée et aplatis à l'aide de la tolérance spécifiée.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Paramètres

*worldTransform*<br/>
Transformation à appliquer à cette géométrie, ou NULL.

*tessellationSink*<br/>
ID2D1TessellationSink auquel le fractionné est ajouté.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="cd2dgeometrywiden"></a><a name="widen"></a> Cd2dgeometry, :: Widening

Élargit la géométrie par le trait spécifié et écrit le résultat dans un ID2D1SimplifiedGeometrySink après qu’il a été transformé par la matrice spécifiée et aplati à l’aide de la tolérance spécifiée.

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
Valeur d’élargissement de la géométrie.

*strokeStyle*<br/>
Style de trait à appliquer à la géométrie, ou NULL.

*worldTransform*<br/>
Transformation à appliquer à la géométrie après l’avoir étendue.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink auquel la géométrie étendue est ajoutée.

*flatteningTolerance*<br/>
Limites maximales de la distance entre les points de l'approximation polygonale de la géométrie. Des valeurs plus faibles permettent de générer des résultats plus précis mais ralentissent l'exécution.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne TRUE. Sinon, elle retourne FALSe.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
