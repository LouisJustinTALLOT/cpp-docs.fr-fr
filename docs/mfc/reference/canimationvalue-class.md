---
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
ms.openlocfilehash: e020e3e123bb5dc96a623e7a41896d75c611b81e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755075"
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
|[CAnimationValue::CAnimationValue](#canimationvalue)|Surchargé. Construit un objet CAnimationValue.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|Ajoute une transition à appliquer à une valeur.|
|[CAnimationValue::GetValue](#getvalue)|Surchargé. Récupère la valeur actuelle.|
|[CAnimationValue::GetVariable](#getvariable)|Donne accès à une variable d’animation encapsulée.|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Met la variable d’animation encapsulée dans une liste. (Overrides [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationValue::opérateur DOUBLE](#operator_double)|Fournit la conversion entre CAnimationValue et DOUBLE.|
|[CAnimationValue::opérateur INT32](#operator_int32)|Fournit la conversion entre CAnimationValue et INT32.|
|[CAnimationValue::opérateur](#operator_eq)|Surchargé. Attribue une valeur INT32 à CAnimationValue.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|La variable d’animation encapsulée qui représente la valeur d’animation.|

## <a name="remarks"></a>Notes

La classe CAnimationValue résume un seul objet CAnimationVariable et peut représenter dans des applications une seule valeur animée. Par exemple, vous pouvez utiliser cette classe pour la transparence animée (effet fade), l’angle (pour faire pivoter les objets), ou pour tout autre cas lorsque vous avez besoin de créer une animation en fonction d’une seule valeur animée. Pour utiliser cette classe en application, il suffit d’instantanéiser un objet de cette classe, ajoutez-le au contrôleur d’animation à l’aide de CAnimationController::AddAnimationObject et appelez AddTransition pour chaque transition à appliquer à la valeur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a>CAnimationValue::AddTransition

Ajoute une transition à appliquer à une valeur.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Paramètres

*pTransition*<br/>
Un pointeur à l’objet de transition.

### <a name="remarks"></a>Notes

Appelez cette fonction pour ajouter une transition à la liste interne des transitions à appliquer à une variable d’animation. Lorsque vous ajoutez des transitions, elles ne sont pas appliquées immédiatement et stockées dans une liste interne. Les transitions sont appliquées (ajoutées à un storyboard pour une valeur particulière) lorsque vous appelez CAnimationController::AnimateGroup.

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>CAnimationValue::CAnimationValue

Construit un objet CAnimationValue.

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

*nGroupID (en anglais)*<br/>
Spécifie l’ID du groupe.

*nObjectID (nObjectID)*<br/>
Spécifie l’id d’objet.

*dwUserData*<br/>
spécifie les données définies par l’utilisateur.

### <a name="remarks"></a>Notes

Construit l’objet CAnimationValue avec propriétés par défaut : valeur par défaut, ID de groupe et ID d’objet sont réglés à 0.

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationValue::GetAnimationVariableList

Met la variable d’animation encapsulée dans une liste.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Paramètres

*Lst*<br/>
Lorsque la fonction revient, il contient un pointeur à CAnimationVariable représentant la valeur animée.

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a>CAnimationValue::GetValue

Récupère la valeur actuelle.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Paramètres

*dblValue (en)*<br/>
Sortie : Lorsque la fonction retourne, elle contient une valeur actuelle de variable d’animation.

*nValue (en)*<br/>
Sortie : Lorsque la fonction retourne, elle contient une valeur actuelle de variable d’animation.

### <a name="return-value"></a>Valeur de retour

VRAI si la valeur actuelle a été récupérée avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer la valeur actuelle. Cette implémentation appelle l’objet COM encapsulé, et si l’appel échoue, cette méthode renvoie la valeur par défaut qui a été précédemment définie dans le constructeur ou avec SetDefaultValue.

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a>CAnimationValue::GetVariable

Donne accès à une variable d’animation encapsulée.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Valeur de retour

Une référence à la variable d’animation encapsulée.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour accéder à la variable d’animation encapsulée. De CAnimationVariable vous avez accès à l’objet sous-jacent IUIAnimationVariable, dont le pointeur peut être NULL si la variable d’animation n’a pas été créée.

## <a name="canimationvaluem_value"></a><a name="m_value"></a>CAnimationValue::m_value

La variable d’animation encapsulée qui représente la valeur d’animation.

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a>CAnimationValue::opérateur DOUBLE

Fournit la conversion entre CAnimationValue et DOUBLE.

```
operator DOUBLE();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de la valeur d’animation.

### <a name="remarks"></a>Notes

Fournit la conversion entre CAnimationValue et DOUBLE. Cette méthode appelle en interne GetValue et ne vérifie pas les erreurs. Si GetValue échoue, la valeur retournée contiendra une valeur par défaut précédemment fixée dans le constructeur ou avec SetDefaultValue.

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a>CAnimationValue::opérateur INT32

Fournit la conversion entre CAnimationValue et INT32.

```
operator INT32();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de la valeur d’animation en tant qu’intégrant.

### <a name="remarks"></a>Notes

Fournit la conversion entre CAnimationValue et INT32. Cette méthode appelle en interne GetValue et ne vérifie pas les erreurs. Si GetValue échoue, la valeur retournée contiendra une valeur par défaut précédemment fixée dans le constructeur ou avec SetDefaultValue.

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a>CAnimationValue::opérateur

Attribue une valeur DOUBLE à CAnimationValue.

```cpp
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Paramètres

*dblVal (en)*<br/>
Spécifie la valeur à attribuer à la valeur d’animation.

*nVal (en)*<br/>
Spécifie la valeur à attribuer à la valeur d’animation.

### <a name="remarks"></a>Notes

Attribue une valeur DOUBLE à CAnimationValue. Cette valeur est définie comme une valeur par défaut pour la variable d’animation encapsulée. Si vous avez souscrit cet objet d’animation à des événements (ValueChanged ou IntegerValueChanged), vous devez réactiver ces événements.

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationValue::SetDefaultValue

Définit la valeur par défaut.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Paramètres

*dblDefaultValue*<br/>
Spécifie la valeur par défaut.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une valeur par défaut. Une valeur par défaut est retournée à l’application lorsque l’animation n’a pas été lancée et/ou que l’objet COM sous-jacent n’a pas été créé. Si l’objet COM sous-jacent encapsulé dans CAnimationVarible a déjà été créé, cette méthode le recrée, donc vous pourriez avoir besoin d’appeler les méthodes EnableValueChanged/EnableIntegerValueChanged à nouveau.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
