---
description: 'En savoir plus sur : classe CCustomInterpolator,'
title: CCustomInterpolator, classe
ms.date: 11/04/2016
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
ms.openlocfilehash: 84fcdc20ce1a90441a508f1469d498095980af83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227752"
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator, classe

Implémente un interpolateur de base.

## <a name="syntax"></a>Syntaxe

```
class CCustomInterpolator;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCustomInterpolator, :: CCustomInterpolator,](#ccustominterpolator)|Surchargé. Construit un objet de l’interpolateur personnalisé et initialise la durée et la vélocité aux valeurs spécifiées.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCustomInterpolator, :: GetDependencies](#getdependencies)|Obtient les dépendances de l’interpolateur.|
|[CCustomInterpolator, :: GetDuration](#getduration)|Obtient la durée de l’interpolateur.|
|[CCustomInterpolator, :: GetFinalValue](#getfinalvalue)|Obtient la valeur finale vers laquelle l’interpolateur dirige.|
|[CCustomInterpolator, :: init](#init)|Initialise la durée et la valeur finale.|
|[CCustomInterpolator, :: InterpolateValue](#interpolatevalue)|Interpole la valeur à un offset donné.|
|[CCustomInterpolator, :: InterpolateVelocity](#interpolatevelocity)|Interpole la vélocité à un décalage donné.|
|[CCustomInterpolator, :: SetDuration](#setduration)|Définit la durée de l’interpolateur.|
|[CCustomInterpolator, :: SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Définit la valeur initiale et la vélocité de l’interpolateur.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CCustomInterpolator, :: m_currentValue](#m_currentvalue)|Valeur interpolée.|
|[CCustomInterpolator, :: m_currentVelocity](#m_currentvelocity)|Vélocité interpolée.|
|[CCustomInterpolator, :: m_duration](#m_duration)|Durée de la transition.|
|[CCustomInterpolator, :: m_finalValue](#m_finalvalue)|Valeur finale d’une variable à la fin de la transition.|
|[CCustomInterpolator, :: m_initialValue](#m_initialvalue)|Valeur de la variable au début de la transition.|
|[CCustomInterpolator, :: m_initialVelocity](#m_initialvelocity)|Rapidité de la variable au début de la transition.|

## <a name="remarks"></a>Notes

Dérivez une classe de CCustomInterpolator, et substituez toutes les méthodes nécessaires pour implémenter un algorithme d’interpolation personnalisé. Un pointeur vers cette classe doit être passé en tant que paramètre à CCustomTransition,.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CCustomInterpolator`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a> CCustomInterpolator, :: CCustomInterpolator,

Construit un objet interpolateur personnalisé et affecte à toutes les valeurs la valeur par défaut 0.

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Durée de la transition.

*finalValue*

### <a name="remarks"></a>Notes

Utilisez CCustomInterpolator, :: init pour initialiser la durée et la valeur finale ultérieurement dans le code.

## <a name="ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a> CCustomInterpolator, :: GetDependencies

Obtient les dépendances de l’interpolateur.

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Paramètres

*initialValueDependencies*<br/>
Sortie : Aspects de l’interpolation qui dépendent de la valeur initiale passée à SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Sortie : Aspects de l’interpolation qui dépendent de la rapidité initiale passée à SetInitialValueAndVelocity.

*durationDependencies*<br/>
Sortie : Aspects de l’interpolation qui dépendent de la durée passée à SetDuration.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation de base retourne toujours la valeur TRUE. Retournez la valeur FALSe à partir de l’implémentation remplacée si vous souhaitez faire échouer l’événement.

## <a name="ccustominterpolatorgetduration"></a><a name="getduration"></a> CCustomInterpolator, :: GetDuration

Obtient la durée de l’interpolateur.

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Sortie : Durée de la transition, en secondes.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation de base retourne toujours la valeur TRUE. Retournez la valeur FALSe à partir de l’implémentation remplacée si vous souhaitez faire échouer l’événement.

## <a name="ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a> CCustomInterpolator, :: GetFinalValue

Obtient la valeur finale vers laquelle l’interpolateur dirige.

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Sortie : Valeur finale d’une variable à la fin de la transition.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation de base retourne toujours la valeur TRUE. Retournez la valeur FALSe à partir de l’implémentation remplacée si vous souhaitez faire échouer l’événement.

## <a name="ccustominterpolatorinit"></a><a name="init"></a> CCustomInterpolator, :: init

Initialise la durée et la valeur finale.

```cpp
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Durée de la transition.

*finalValue*<br/>
Valeur finale d’une variable à la fin de la transition.

## <a name="ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a> CCustomInterpolator, :: InterpolateValue

Interpole la valeur à un offset donné.

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Sortie : Valeur interpolée.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation de base retourne toujours la valeur TRUE. Retournez la valeur FALSe à partir de l’implémentation remplacée si vous souhaitez faire échouer l’événement.

## <a name="ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a> CCustomInterpolator, :: InterpolateVelocity

Interpole la vélocité à un décalage donné.

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>Paramètres

*vélocité*<br/>
Sortie : Vélocité de la variable à l’offset.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation de base retourne toujours la valeur TRUE. Retournez la valeur FALSe à partir de l’implémentation remplacée si vous souhaitez faire échouer l’événement.

## <a name="ccustominterpolatorm_currentvalue"></a><a name="m_currentvalue"></a> CCustomInterpolator, :: m_currentValue

Valeur interpolée.

```
DOUBLE m_currentValue;
```

## <a name="ccustominterpolatorm_currentvelocity"></a><a name="m_currentvelocity"></a> CCustomInterpolator, :: m_currentVelocity

Vélocité interpolée.

```
DOUBLE m_currentVelocity;
```

## <a name="ccustominterpolatorm_duration"></a><a name="m_duration"></a> CCustomInterpolator, :: m_duration

Durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="ccustominterpolatorm_finalvalue"></a><a name="m_finalvalue"></a> CCustomInterpolator, :: m_finalValue

Valeur finale d’une variable à la fin de la transition.

```
DOUBLE m_finalValue;
```

## <a name="ccustominterpolatorm_initialvalue"></a><a name="m_initialvalue"></a> CCustomInterpolator, :: m_initialValue

Valeur de la variable au début de la transition.

```
DOUBLE m_initialValue;
```

## <a name="ccustominterpolatorm_initialvelocity"></a><a name="m_initialvelocity"></a> CCustomInterpolator, :: m_initialVelocity

Rapidité de la variable au début de la transition.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustominterpolatorsetduration"></a><a name="setduration"></a> CCustomInterpolator, :: SetDuration

Définit la durée de l’interpolateur.

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Durée de la transition.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation de base retourne toujours la valeur TRUE. Retournez la valeur FALSe à partir de l’implémentation remplacée si vous souhaitez faire échouer l’événement.

## <a name="ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a> CCustomInterpolator, :: SetInitialValueAndVelocity

Définit la valeur initiale et la vélocité de l’interpolateur.

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>Paramètres

*initialValue*<br/>
Valeur de la variable au début de la transition.

*initialVelocity*<br/>
Rapidité de la variable au début de la transition.

### <a name="return-value"></a>Valeur renvoyée

L’implémentation de base retourne toujours la valeur TRUE. Retournez la valeur FALSe à partir de l’implémentation remplacée si vous souhaitez faire échouer l’événement.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
