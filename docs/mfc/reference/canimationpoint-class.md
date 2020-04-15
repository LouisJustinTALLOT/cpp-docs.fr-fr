---
title: CAnimationPoint, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: 19f02010b6b73573a4800152e40c592fd1736ad5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369734"
---
# <a name="canimationpoint-class"></a>CAnimationPoint, classe

Implémente les fonctionnalités d'un point dont les coordonnées peuvent être animées.

## <a name="syntax"></a>Syntaxe

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Surchargé. Construit l’objet CAnimationPoint.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|Ajoute des transitions pour les coordonnées X et Y.|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour les coordonnées X et Y.|
|[CAnimationPoint::GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationPoint::GetX](#getx)|Donne accès à CAnimationVariable pour la coordonnées X.|
|[CAnimationPoint::Gety](#gety)|Donne accès à CAnimationVariable pour la coordonnées Y.|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Place les variables d’animation encapsulées dans une liste. (Overrides [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint::opérateur CPoint](#operator_cpoint)|Convertit un CAnimationPoint en CPoint.|
|[CAnimationPoint::opérateur](#operator_eq)|Assigne ptSrc à CAnimationPoint.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|La variable d’animation encapsulée qui représente la coordination X du point d’animation.|
|[CAnimationPoint::m_yValue](#m_yvalue)|La variable d’animation encapsulée qui représente la coordination Y du point d’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationPoint résume deux objets CAnimationVariable et peut représenter dans les applications un point. Par exemple, vous pouvez utiliser cette classe pour animer une position de n’importe quel objet à l’écran (comme la chaîne de texte, le cercle, le point, etc.). Pour utiliser cette classe en application, il suffit d’instantané d’un objet de cette classe, ajoutez-le au contrôleur d’animation à l’aide de CAnimationController::AddAnimationObject et appelez AddTransition pour chaque transition à appliquer aux coordonnées X et/ou Y.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a>CAnimationPoint::AddTransition

Ajoute des transitions pour les coordonnées X et Y.

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Paramètres

*pXTransition (en)*<br/>
Un pointeur à la transition pour les coordonnées X.

*pYTransition (traduction)*<br/>
Un pointeur à la transition pour la coordonnées Y.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation pour les coordonnées X et Y. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à un storyboard pour une valeur particulière) lorsque vous appelez CAnimationController::AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition vers l’une des coordonnées, vous pouvez passer NULL.

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a>CAnimationPoint::CAnimationPoint

Construit l’objet CAnimationPoint.

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*ptDefault*<br/>
Spécifie les coordonnées par défaut des points.

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

*nObjectID (nObjectID)*<br/>
Spécifie l’id d’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

### <a name="remarks"></a>Notes

Construit l’objet CAnimationPoint avec propriétés par défaut : les coordonnées par défaut, l’ID de groupe et l’ID d’objet sont réglés à 0.

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationPoint::GetAnimationVariableList

Place les variables d’animation encapsulées dans une liste.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*Lst*<br/>
Lorsque la fonction revient, il contient des indications à deux objets CAnimationVariable représentant les coordonnées X et Y.

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationPoint::GetDefaultValue

Retourne les valeurs par défaut pour les coordonnées X et Y.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Valeur de retour

Un point contenant la valeur par défaut.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, qui a déjà été définie par le constructeur ou SetDefaultValue.

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a>CAnimationPoint::GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Paramètres

*ptValue*<br/>
Sortie : Contient la valeur actuelle lorsque cette méthode revient.

### <a name="return-value"></a>Valeur de retour

VRAI, si la valeur actuelle a été récupérée avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle du point d’animation. Si cette méthode échoue ou que les objets COM sous-jacents pour les coordonnées X et Y n’ont pas été parasés, ptValue contient une valeur par défaut, qui a déjà été définie en constructeur ou par SetDefaultValue.

## <a name="canimationpointgetx"></a><a name="getx"></a>CAnimationPoint::GetX

Donne accès à CAnimationVariable pour la coordonnées X.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant la coordonnées X.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à la CAnimationVariable sous-jacente représentant la coordonnées X.

## <a name="canimationpointgety"></a><a name="gety"></a>CAnimationPoint::Gety

Donne accès à CAnimationVariable pour la coordonnées Y.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Valeur de retour

Une référence à CAnimationVariable encapsulé représentant Y coordonnées.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour obtenir un accès direct à la CAnimationVariable sous-jacente représentant Y coordonnées.

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a>CAnimationPoint::m_xValue

La variable d’animation encapsulée qui représente la coordination X du point d’animation.

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a>CAnimationPoint::m_yValue

La variable d’animation encapsulée qui représente la coordination Y du point d’animation.

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a>CAnimationPoint::opérateur CPoint

Convertit un CAnimationPoint en CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de CAnimationPoint en CPoint.

### <a name="remarks"></a>Notes

Cette fonction appelle en interne GetValue. Si GetValue échoue pour une raison quelconque, le point de retour contiendra des valeurs par défaut pour les coordonnées X et Y.

## <a name="canimationpointoperator"></a><a name="operator_eq"></a>CAnimationPoint::opérateur

Assigne ptSrc à CAnimationPoint.

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Paramètres

*ptSrc*<br/>
Se réfère à CPoint ou POINT.

### <a name="remarks"></a>Notes

Assigne ptSrc à CAnimationPoint. Il est recommandé de le faire avant le début de l’animation, car cet opérateur appelle SetDefaultValue, qui recrée les objets COM sous-jacents pour les coordonnées X et Y s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationPoint::SetDefaultValue

Définit la valeur par défaut.

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Paramètres

*ptDefault*<br/>
Spécifie la valeur de point par défaut.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut à l’objet d’animation. Ces méthodes attribuent des valeurs par défaut aux coordonnées X et Y du point d’animation. Il recrée également des objets COM sous-jacents s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
