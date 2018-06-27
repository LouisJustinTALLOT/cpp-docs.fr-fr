---
title: Classe de CD2DGeometry | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51e3c24464ff74ab262cd241dcdce68037d530f9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955100"
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
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Construit un objet CD2DGeometry.|  
|[CD2DGeometry :: ~ CD2DGeometry](#_dtorcd2dgeometry)|Destructeur. Appelé lorsqu’un objet de géométrie D2D est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DGeometry::Attach](#attach)|Attache existant à l’objet interface de la ressource|  
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Associe ce geometry avec la géométrie spécifiée et stocke le résultat dans un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Décrit l’intersection entre cette géométrie et la géométrie spécifiée. La comparaison est effectuée à l’aide de la tolérance d’aplatissement spécifiée.|  
|[CD2DGeometry::ComputeArea](#computearea)|Calcule la surface de la géométrie après avoir été transformés par la matrice spécifiée et aplatis à l’aide de la tolérance spécifiée.|  
|[CD2DGeometry::ComputeLength](#computelength)|Calcule la longueur de la géométrie comme si chaque segment étaient déroulées dans une ligne.|  
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Calcule le vecteur de point et la tangente à la distance spécifiée le long de la géométrie après avoir été transformés par la matrice spécifiée et aplatis à l’aide de la tolérance spécifiée.|  
|[CD2DGeometry::Destroy](#destroy)|Détruit un objet CD2DGeometry. (Substitue [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DGeometry::Detach](#detach)|Détache l’interface de la ressource à partir de l’objet|  
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Indique si la zone remplie par la géométrie contient le point spécifié selon la tolérance d’aplatissement spécifiée.|  
|[CD2DGeometry::Get](#get)|Renvoie l’interface ID2D1Geometry|  
|[CD2DGeometry::GetBounds](#getbounds)||  
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Obtient les limites de la géométrie après que qu’il a été élargie par la largeur de trait spécifié et le style et transformé par la matrice spécifiée.|  
|[CD2DGeometry::IsValid](#isvalid)|Vérifie la validité des ressources (remplace [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DGeometry::Outline](#outline)|Calcule le plan de la géométrie et écrit le résultat dans un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::Simplify](#simplify)|Crée une version simplifiée de la géométrie qui contient uniquement des lignes et des courbes de Bézier cubiques (éventuellement) et écrit le résultat dans un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Détermine si le trait de la géométrie contient le point spécifié selon l’épaisseur de trait spécifié, le style et la transformation.|  
|[CD2DGeometry::Tessellate](#tessellate)|Crée un ensemble de triangles enroulés dans le sens horaire qui couvrent la géométrie après avoir été transformés à l’aide de la matrice spécifiée et aplatis à l’aide de la tolérance spécifiée.|  
|[CD2DGeometry::widen](#widen)|Élargit la géométrie par le trait spécifié et écrit le résultat à un ID2D1SimplifiedGeometrySink après avoir été transformés par la matrice spécifiée et aplatis à l’aide de la tolérance spécifiée.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|Renvoie l’interface ID2D1Geometry|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Pointeur vers un ID2D1Geometry.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DGeometry`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometry"></a>  CD2DGeometry :: ~ CD2DGeometry  
 Destructeur. Appelé lorsqu’un objet de géométrie D2D est détruit.  
  
```  
virtual ~CD2DGeometry();
```  
  
##  <a name="attach"></a>  CD2DGeometry::Attach  
 Attache existant à l’objet interface de la ressource  
  
```  
void Attach(ID2D1Geometry* pResource);
```  
  
### <a name="parameters"></a>Paramètres  
 *pResource*  
 Interface de la ressource existante. Ne peut pas être NULL  
  
##  <a name="cd2dgeometry"></a>  CD2DGeometry::CD2DGeometry  
 Construit un objet CD2DGeometry.  
  
```  
CD2DGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParentTarget*  
 Pointeur vers la cible de rendu.  
  
 *bAutoDestroy*  
 Indique que l’objet sera détruit par le propriétaire (pParentTarget).  
  
##  <a name="combinewithgeometry"></a>  CD2DGeometry::CombineWithGeometry  
 Associe ce geometry avec la géométrie spécifiée et stocke le résultat dans un ID2D1SimplifiedGeometrySink.  
  
```  
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,  
    D2D1_COMBINE_MODE combineMode,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *inputGeometry*  
 Géométrie à combiner avec cette instance.  
  
 *combineMode*  
 Type d’opération d’association à effectuer.  
  
 *inputGeometryTransform*  
 La transformation à appliquer à inputGeometry avant la combinaison.  
  
 *geometrySink*  
 Le résultat de l’opération d’association.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale des géométries. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="comparewithgeometry"></a>  CD2DGeometry::CompareWithGeometry  
 Décrit l’intersection entre cette géométrie et la géométrie spécifiée. La comparaison est effectuée à l’aide de la tolérance d’aplatissement spécifiée.  
  
```  
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *inputGeometry*  
 Géométrie à tester.  
  
 *inputGeometryTransform*  
 La transformation à appliquer à inputGeometry.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale des géométries. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="computearea"></a>  CD2DGeometry::ComputeArea  
 Calcule la surface de la géométrie après avoir été transformés par la matrice spécifiée et aplatis à l’aide de la tolérance spécifiée.  
  
```  
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& area,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *worldTransform*  
 La transformation à appliquer à cette géométrie avant de calculer sa zone.  
  
 *Zone*  
 Lorsque cette méthode est retournée, contient un pointeur vers la zone de la version transformée et aplatie de cette géométrie. Vous devez allouer le stockage pour ce paramètre.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale de la géométrie. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="computelength"></a>  CD2DGeometry::ComputeLength  
 Calcule la longueur de la géométrie comme si chaque segment étaient déroulées dans une ligne.  
  
```  
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& length,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *worldTransform*  
 La transformation à appliquer à la géométrie avant de calculer sa longueur.  
  
 *length*  
 Lorsque cette méthode est retournée, contient un pointeur vers la longueur de la géométrie. Pour les géométries fermées, la longueur inclut un segment de fermeture implicite. Vous devez allouer le stockage pour ce paramètre.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale de la géométrie. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="computepointatlength"></a>  CD2DGeometry::ComputePointAtLength  
 Calcule le vecteur de point et la tangente à la distance spécifiée le long de la géométrie après avoir été transformés par la matrice spécifiée et aplatis à l’aide de la tolérance spécifiée.  
  
```  
BOOL ComputePointAtLength(
    FLOAT length,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DPointF& point,  
    CD2DPointF& unitTangentVector,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *length*  
 La distance le long de la géométrie du point et la tangente à rechercher. Si cette distance est inférieure à 0, cette méthode calcule le premier point dans la géométrie. Si cette distance est supérieure à la longueur de la géométrie, cette méthode calcule le dernier point dans la géométrie.  
  
 *worldTransform*  
 La transformation à appliquer à la géométrie avant de calculer le point spécifié et la tangente.  
  
 *Point*  
 L’emplacement à la distance spécifiée le long de la géométrie. Si la géométrie est vide, ce point contient NaN x et y valeurs.  
  
 *unitTangentVector*  
 Lorsque cette méthode est retournée, contient un pointeur vers le vecteur de tangente à la distance spécifiée le long de la géométrie. Si la géométrie est vide, ce vecteur contient NaN x et y valeurs. Vous devez allouer le stockage pour ce paramètre.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale de la géométrie. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="destroy"></a>  CD2DGeometry::Destroy  
 Détruit un objet CD2DGeometry.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DGeometry::Detach  
 Détache l’interface de la ressource à partir de l’objet  
  
```  
ID2D1Geometry* Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface de la ressource détaché.  
  
##  <a name="fillcontainspoint"></a>  CD2DGeometry::FillContainsPoint  
 Indique si la zone remplie par la géométrie contient le point spécifié selon la tolérance d’aplatissement spécifiée.  
  
```  
BOOL FillContainsPoint(
    CD2DPointF point,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *Point*  
 Point à tester.  
  
 *worldTransform*  
 La transformation à appliquer à la géométrie avant le test de la relation contenant-contenu.  
  
 *Contient*  
 Lorsque cette méthode est retournée, contient une valeur booléenne qui est TRUE si la zone remplie par la géométrie contient le point ; Sinon, FALSE. Vous devez allouer le stockage pour ce paramètre.  
  
 *flatteningTolerance*  
 La précision numérique avec lequel l’intersection de chemin d’accès et le chemin d’accès géométrique précis est calculée. Points manquant du remplissage inférieur à la tolérance sont toujours considérés à l’intérieur. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="get"></a>  CD2DGeometry::Get  
 Renvoie l’interface ID2D1Geometry  
  
```  
ID2D1Geometry* Get();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de ID2D1Geometry ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="getbounds"></a>  CD2DGeometry::GetBounds  
  
```   
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,  
CD2DRectF& bounds) const; 
```  
  
### <a name="parameters"></a>Paramètres  
 *worldTransform*  
 *limites*  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="getwidenedbounds"></a>  CD2DGeometry::GetWidenedBounds  
 Obtient les limites de la géométrie après que qu’il a été élargie par la largeur de trait spécifié et le style et transformé par la matrice spécifiée.  
  
```  
BOOL GetWidenedBounds(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DRectF& bounds,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *strokeWidth*  
 Le montant par lequel élargir la géométrie en traçant le contour.  
  
 *strokeStyle*  
 Le style du trait qui s’étend de la géométrie.  
  
 *worldTransform*  
 Une transformation à appliquer à la géométrie après la transformation de la géométrie et une fois que la géométrie a été tracée.  
  
 *limites*  
 Lorsque cette méthode est retournée, contient les limites de la géométrie élargie. Vous devez allouer le stockage pour ce paramètre.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale des géométries. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="isvalid"></a>  CD2DGeometry::IsValid  
 Vérifications de validité des ressources  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la ressource est valide ; Sinon, FALSE.  
  
##  <a name="m_pgeometry"></a>  CD2DGeometry::m_pGeometry  
 Pointeur vers un ID2D1Geometry.  
  
```  
ID2D1Geometry* m_pGeometry;  
```  
  
##  <a name="operator_id2d1geometry_star"></a>  CD2DGeometry::operator ID2D1Geometry *  
 Renvoie l’interface ID2D1Geometry  
  
```  
operator ID2D1Geometry*();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de ID2D1Geometry ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="outline"></a>  CD2DGeometry::Outline  
 Calcule le plan de la géométrie et écrit le résultat dans un ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *worldTransform*  
 La transformation à appliquer au contour de la géométrie.  
  
 *geometrySink*  
 Le ID2D1SimplifiedGeometrySink auquel la géométrie transformé le plan est ajouté.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale de la géométrie. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="simplify"></a>  CD2DGeometry::Simplify  
 Crée une version simplifiée de la géométrie qui contient uniquement des lignes et des courbes de Bézier cubiques (éventuellement) et écrit le résultat dans un ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *simplificationOption*  
 Une valeur qui spécifie si la géométrie simplifiée doit contenir des courbes.  
  
 *worldTransform*  
 La transformation à appliquer à la géométrie simplifiée.  
  
 *geometrySink*  
 Le ID2D1SimplifiedGeometrySink auquel la géométrie simplifiée est ajoutée.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale de la géométrie. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="strokecontainspoint"></a>  CD2DGeometry::StrokeContainsPoint  
 Détermine si le trait de la géométrie contient le point spécifié selon l’épaisseur de trait spécifié, le style et la transformation.  
  
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
 *Point*  
 Point à tester pour la relation contenant-contenu.  
  
 *strokeWidth*  
 L’épaisseur de trait à appliquer.  
  
 *strokeStyle*  
 Style de trait à appliquer.  
  
 *worldTransform*  
 La transformation à appliquer à la géométrie de tracé.  
  
 *Contient*  
 Lorsque cette méthode est retournée, contient une valeur booléenne définie sur TRUE si le trait de la géométrie contient le point spécifié ; Sinon, FALSE. Vous devez allouer le stockage pour ce paramètre.  
  
 *flatteningTolerance*  
 La précision numérique avec lequel l’intersection de chemin d’accès et le chemin d’accès géométrique précis est calculée. Points manquant le contour inférieur à la tolérance sont toujours considérés à l’intérieur. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="tessellate"></a>  CD2DGeometry::Tessellate  
 Crée un ensemble de triangles enroulés dans le sens horaire qui couvrent la géométrie après avoir été transformés à l’aide de la matrice spécifiée et aplatis à l’aide de la tolérance spécifiée.  
  
```  
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1TessellationSink* tessellationSink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *worldTransform*  
 La transformation à appliquer à cette géométrie, ou NULL.  
  
 *tessellationSink*  
 Le ID2D1TessellationSink auquel est ajouté.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale de la géométrie. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
##  <a name="widen"></a>  CD2DGeometry::widen  
 Élargit la géométrie par le trait spécifié et écrit le résultat à un ID2D1SimplifiedGeometrySink après avoir été transformés par la matrice spécifiée et aplatis à l’aide de la tolérance spécifiée.  
  
```  
BOOL Widen(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *strokeWidth*  
 Le montant par lequel élargir la géométrie.  
  
 *strokeStyle*  
 Le style de trait à appliquer à la géométrie, ou NULL.  
  
 *worldTransform*  
 La transformation à appliquer à la géométrie après son élargissement.  
  
 *geometrySink*  
 Le ID2D1SimplifiedGeometrySink auquel la géométrie élargie est ajoutée.  
  
 *flatteningTolerance*  
 Limites maximales de la distance entre les points de l’approximation polygonale de la géométrie. Plus petites valeurs produisent des résultats plus précis mais ralentissent l’exécution.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
