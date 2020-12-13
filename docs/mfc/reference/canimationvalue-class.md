---
description: 'En savoir plus sur : classe CAnimationValue,'
title: CAnimationValue, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: d704e83d286b4078af90d09edef35e8445d149d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336747"
---
# <a name="canimationvalue-class"></a>CAnimationValue, classe

Implémente les fonctionnalités d'un objet d'animation qui a une valeur.

## <a name="syntax"></a>Syntaxe

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationValue, :: CAnimationValue,](#canimationvalue)|Surchargé. Construit un objet CAnimationValue,.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationValue, :: AddTransition](#addtransition)|Ajoute une transition à appliquer à une valeur.|
|[CAnimationValue, :: GetValue](#getvalue)|Surchargé. Récupère la valeur actuelle.|
|[CAnimationValue, :: GetVariable](#getvariable)|Fournit l’accès à la variable d’animation encapsulée.|
|[CAnimationValue, :: SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationValue, :: GetAnimationVariableList](#getanimationvariablelist)|Place la variable d’animation encapsulée dans une liste. (Substitue [CAnimationBaseObject, :: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationValue, :: Operator DOUBLE](#operator_double)|Fournit la conversion entre CAnimationValue, et DOUBLE.|
|[CAnimationValue, :: Operator INT32](#operator_int32)|Fournit la conversion entre CAnimationValue, et INT32.|
|[CAnimationValue, :: Operator =](#operator_eq)|Surchargé. Assigne une valeur INT32 à CAnimationValue,.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationValue, :: m_value](#m_value)|Variable d’animation encapsulée qui représente la valeur d’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationValue, encapsule un objet CAnimationVariable unique et peut représenter dans les applications une valeur animée unique. Par exemple, vous pouvez utiliser cette classe pour la transparence animée (effet de fondu), l’angle (pour faire pivoter des objets) ou pour tout autre cas lorsque vous devez créer une animation en fonction d’une valeur animée unique. Pour utiliser cette classe dans l’application, il vous suffit d’instancier un objet de cette classe, de l’ajouter au contrôleur d’animation à l’aide de CAnimationController :: AddAnimationObject et d’appeler AddTransition pour chaque transition à appliquer à la valeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject,](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a> CAnimationValue, :: AddTransition

Ajoute une transition à appliquer à une valeur.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Paramètres

*pTransition*<br/>
Pointeur vers un objet de transition.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter une transition à la liste interne des transitions à appliquer à une variable d’animation. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à une table de montage séquentiel pour une valeur particulière) quand vous appelez CAnimationController :: AnimateGroup.

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a> CAnimationValue, :: CAnimationValue,

Construit un objet CAnimationValue,.

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*dblDefaultValue*<br/>
Spécifie la valeur par défaut.

*nGroupID*<br/>
Spécifie l’ID de groupe.

*nObjectID*<br/>
Spécifie l’ID de l’objet.

*dwUserData*<br/>
spécifie les données définies par l’utilisateur.

### <a name="remarks"></a>Notes

Construit l’objet CAnimationValue, avec les propriétés par défaut : la valeur par défaut, l’ID de groupe et l’ID d’objet sont définis sur 0.

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationValue, :: GetAnimationVariableList

Place la variable d’animation encapsulée dans une liste.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*LST*<br/>
Quand la fonction retourne, elle contient un pointeur vers CAnimationVariable représentant la valeur animée.

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a> CAnimationValue, :: GetValue

Récupère la valeur actuelle.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Paramètres

*dblValue*<br/>
Sortie : Quand la fonction retourne, elle contient une valeur actuelle de variable d’animation.

*nValeur*<br/>
Sortie : Quand la fonction retourne, elle contient une valeur actuelle de variable d’animation.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la valeur actuelle a été récupérée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle. Cette implémentation appelle l’objet COM encapsulé et, si l’appel échoue, cette méthode retourne la valeur par défaut précédemment définie dans le constructeur ou avec SetDefaultValue.

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a> CAnimationValue, :: GetVariable

Fournit l’accès à la variable d’animation encapsulée.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Valeur renvoyée

Référence à une variable d’animation encapsulée.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour accéder à la variable d’animation encapsulée. À partir de CAnimationVariable, vous accédez à l’objet IUIAnimationVariable sous-jacent, dont le pointeur peut être NULL si la variable d’animation n’a pas été créée.

## <a name="canimationvaluem_value"></a><a name="m_value"></a> CAnimationValue, :: m_value

Variable d’animation encapsulée qui représente la valeur d’animation.

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a> CAnimationValue, :: Operator DOUBLE

Fournit la conversion entre CAnimationValue, et DOUBLE.

```
operator DOUBLE();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle de la valeur d’animation.

### <a name="remarks"></a>Notes

Fournit la conversion entre CAnimationValue, et DOUBLE. Cette méthode appelle GetValue en interne et ne vérifie pas les erreurs. Si GetValue échoue, la valeur retournée contient une valeur par défaut précédemment définie dans le constructeur ou avec SetDefaultValue.

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a> CAnimationValue, :: Operator INT32

Fournit la conversion entre CAnimationValue, et INT32.

```
operator INT32();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle de la valeur d’animation en tant qu’entier.

### <a name="remarks"></a>Notes

Fournit la conversion entre CAnimationValue, et INT32. Cette méthode appelle GetValue en interne et ne vérifie pas les erreurs. Si GetValue échoue, la valeur retournée contient une valeur par défaut précédemment définie dans le constructeur ou avec SetDefaultValue.

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a> CAnimationValue, :: Operator =

Affecte une valeur DOUBLE à CAnimationValue,.

```cpp
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Paramètres

*dblVal*<br/>
Spécifie la valeur à assigner à la valeur d’animation.

*nVal*<br/>
Spécifie la valeur à assigner à la valeur d’animation.

### <a name="remarks"></a>Notes

Affecte une valeur DOUBLE à CAnimationValue,. Cette valeur est définie en tant que valeur par défaut pour la variable d’animation encapsulée. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationValue, :: SetDefaultValue

Définit la valeur par défaut.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Paramètres

*dblDefaultValue*<br/>
Spécifie la valeur par défaut.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une valeur par défaut. Une valeur par défaut est retournée à l’application lorsque l’animation n’a pas été démarrée et/ou que l’objet COM sous-jacent n’a pas été créé. Si l’objet COM sous-jacent encapsulé dans CAnimationVarible a déjà été créé, cette méthode le recrée. par conséquent, vous devrez peut-être appeler de nouveau les méthodes EnableValueChanged/EnableIntegerValueChanged.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
