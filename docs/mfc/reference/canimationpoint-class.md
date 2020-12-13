---
description: 'En savoir plus sur : classe CAnimationPoint,'
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
ms.openlocfilehash: ddefb93950f0ff1109478f3574413faf9f60a22a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336789"
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
|[CAnimationPoint, :: CAnimationPoint,](#canimationpoint)|Surchargé. Construit l’objet CAnimationPoint,.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint, :: AddTransition](#addtransition)|Ajoute des transitions pour les coordonnées X et Y.|
|[CAnimationPoint, :: GetDefaultValue](#getdefaultvalue)|Retourne les valeurs par défaut pour les coordonnées X et Y.|
|[CAnimationPoint, :: GetValue](#getvalue)|Retourne la valeur actuelle.|
|[CAnimationPoint, :: GetX](#getx)|Fournit l’accès à CAnimationVariable pour la coordonnée X.|
|[CAnimationPoint, :: GetY](#gety)|Fournit l’accès à CAnimationVariable pour la coordonnée Y.|
|[CAnimationPoint, :: SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint, :: GetAnimationVariableList](#getanimationvariablelist)|Place les variables d’animation encapsulées dans une liste. (Substitue [CAnimationBaseObject, :: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint, :: Operator CPoint](#operator_cpoint)|Convertit un CAnimationPoint, en CPoint.|
|[CAnimationPoint, :: Operator =](#operator_eq)|Affecte ptSrc à CAnimationPoint,.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationPoint, :: m_xValue](#m_xvalue)|Variable d’animation encapsulée qui représente la coordonnée X du point d’animation.|
|[CAnimationPoint, :: m_yValue](#m_yvalue)|Variable d’animation encapsulée qui représente la coordonnée Y du point d’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationPoint, encapsule deux objets CAnimationVariable et peut représenter dans des applications un point. Par exemple, vous pouvez utiliser cette classe pour animer une position de tout objet sur l’écran (comme chaîne de texte, cercle, point, etc.). Pour utiliser cette classe dans l’application, il vous suffit d’instancier un objet de cette classe, de l’ajouter au contrôleur d’animation à l’aide de CAnimationController :: AddAnimationObject et d’appeler AddTransition pour chaque transition à appliquer aux coordonnées X et/ou Y.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject,](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a> CAnimationPoint, :: AddTransition

Ajoute des transitions pour les coordonnées X et Y.

```cpp
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Paramètres

*pXTransition*<br/>
Pointeur vers la transition pour les coordonnées X.

*pYTransition*<br/>
Pointeur vers la transition pour la coordonnée Y.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter les transitions spécifiées à la liste interne des transitions à appliquer aux variables d’animation pour les coordonnées X et Y. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à une table de montage séquentiel pour une valeur particulière) quand vous appelez CAnimationController :: AnimateGroup. Si vous n’avez pas besoin d’appliquer une transition à l’une des coordonnées, vous pouvez passer la valeur NULL.

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a> CAnimationPoint, :: CAnimationPoint,

Construit l’objet CAnimationPoint,.

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
Spécifie les coordonnées de point par défaut.

*nGroupID*<br/>
Spécifie l’ID de groupe.

*nObjectID*<br/>
Spécifie l’ID de l’objet.

*dwUserData*<br/>
Spécifie les données définies par l’utilisateur.

### <a name="remarks"></a>Notes

Construit l’objet CAnimationPoint, avec les propriétés par défaut : les coordonnées de point par défaut, l’ID de groupe et l’ID d’objet ont la valeur 0.

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationPoint, :: GetAnimationVariableList

Place les variables d’animation encapsulées dans une liste.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*LST*<br/>
Quand la fonction retourne, elle contient des pointeurs vers deux objets CAnimationVariable représentant les coordonnées X et Y.

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationPoint, :: GetDefaultValue

Retourne les valeurs par défaut pour les coordonnées X et Y.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Valeur renvoyée

Point contenant la valeur par défaut.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur par défaut, qui a été précédemment définie par le constructeur ou SetDefaultValue.

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a> CAnimationPoint, :: GetValue

Retourne la valeur actuelle.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Paramètres

*ptValue*<br/>
Sortie : Contient la valeur actuelle lorsque cette méthode est retournée.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la valeur actuelle a été récupérée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle du point d’animation. Si cette méthode échoue ou si les objets COM sous-jacents pour les coordonnées X et Y n’ont pas été initialisés, ptValue contient la valeur par défaut, qui a été précédemment définie dans le constructeur ou par SetDefaultValue.

## <a name="canimationpointgetx"></a><a name="getx"></a> CAnimationPoint, :: GetX

Fournit l’accès à CAnimationVariable pour la coordonnée X.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à l’CAnimationVariable encapsulé représentant la coordonnée X.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour accéder directement à l’CAnimationVariable sous-jacent représentant la coordonnée X.

## <a name="canimationpointgety"></a><a name="gety"></a> CAnimationPoint, :: GetY

Fournit l’accès à CAnimationVariable pour la coordonnée Y.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à CAnimationVariable encapsulé représentant la coordonnée Y.

### <a name="remarks"></a>Notes

Vous pouvez appeler cette méthode pour accéder directement à l’CAnimationVariable sous-jacent représentant la coordonnée Y.

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a> CAnimationPoint, :: m_xValue

Variable d’animation encapsulée qui représente la coordonnée X du point d’animation.

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a> CAnimationPoint, :: m_yValue

Variable d’animation encapsulée qui représente la coordonnée Y du point d’animation.

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a> CAnimationPoint, :: Operator CPoint

Convertit un CAnimationPoint, en CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle de CAnimationPoint, en tant que CPoint.

### <a name="remarks"></a>Notes

Cette fonction appelle GetValue en interne. Si GetValue échoue pour une raison quelconque, le point retourné contient des valeurs par défaut pour les coordonnées X et Y.

## <a name="canimationpointoperator"></a><a name="operator_eq"></a> CAnimationPoint, :: Operator =

Affecte ptSrc à CAnimationPoint,.

```cpp
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Paramètres

*ptSrc*<br/>
Fait référence à CPoint ou POINT.

### <a name="remarks"></a>Notes

Affecte ptSrc à CAnimationPoint,. Il est recommandé de le faire avant le démarrage de l’animation, car cet opérateur appelle SetDefaultValue, qui recrée les objets COM sous-jacents pour les coordonnées X et Y si elles ont été créées. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationPoint, :: SetDefaultValue

Définit la valeur par défaut.

```cpp
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Paramètres

*ptDefault*<br/>
Spécifie la valeur de point par défaut.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir une valeur par défaut pour l’objet d’animation. Cette méthode affecte des valeurs par défaut aux coordonnées X et Y du point d’animation. Il recrée également les objets COM sous-jacents s’ils ont été créés. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
