---
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
ms.openlocfilehash: 00ce0661fa3fbde714a7299ecbbd54df7c9bcc36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749161"
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
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Surchargé. Construit un objet d’interpolateur personnalisé et initialise la durée et la vitesse à des valeurs spécifiées.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCustomInterpolator:GetDependencies](#getdependencies)|Obtient les dépendances de l’interpolateur.|
|[CCustomInterpolator::GetDuration](#getduration)|La durée de l’interpolateur.|
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Obtient la valeur finale à laquelle l’interpolateur conduit.|
|[CCustomInterpolator::Init](#init)|Initialise la durée et la valeur finale.|
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Interpole la valeur à un décalage donné.|
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Interpole la vitesse à un décalage donné|
|[CCustomInterpolator::SetDuration](#setduration)|Définit la durée de l’interpolateur.|
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Définit la valeur et la vitesse initiales de l’interpolateur.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|La valeur interpolée.|
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|La vitesse interpolée.|
|[CCustomInterpolator::m_duration](#m_duration)|La durée de la transition.|
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|La valeur finale d’une variable à la fin de la transition.|
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|La valeur de la variable au début de la transition.|
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|La vitesse de la variable au début de la transition.|

## <a name="remarks"></a>Notes

Dérivez une classe de CCustomInterpolator et remplacez toutes les méthodes nécessaires pour implémenter un algorithme d’interpolation personnalisé. Un pointeur de cette classe doit être passé comme paramètre à CCustomTransition.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CCustomInterpolator`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator

Construit un objet d’interpolateur personnalisé et définit toutes les valeurs par défaut 0.

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
La durée de la transition.

*finalValue*

### <a name="remarks"></a>Notes

Utilisez CCustomInterpolator::Init pour initialiser la durée et la valeur finale plus tard dans le code.

## <a name="ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustomInterpolator:GetDependencies

Obtient les dépendances de l’interpolateur.

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Paramètres

*initialValueDependencies*<br/>
Sortie : Aspects de l’interpolateur qui dépendent de la valeur initiale passé à SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Sortie : Aspects de l’interpolateur qui dépendent de la vitesse initiale passé à SetInitialValueAndVelocity.

*duréeDependencies*<br/>
Sortie : Aspects de l’interpolateur qui dépendent de la durée passée à SetDuration.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre de base renvoie toujours VRAI. Retournez FALSE de la mise en œuvre annulée si vous souhaitez échouer à l’événement.

## <a name="ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustomInterpolator::GetDuration

La durée de l’interpolateur.

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Sortie : La durée de la transition, en quelques secondes.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre de base renvoie toujours VRAI. Retournez FALSE de la mise en œuvre annulée si vous souhaitez échouer à l’événement.

## <a name="ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue

Obtient la valeur finale à laquelle l’interpolateur conduit.

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Sortie : La valeur finale d’une variable à la fin de la transition.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre de base renvoie toujours VRAI. Retournez FALSE de la mise en œuvre annulée si vous souhaitez échouer à l’événement.

## <a name="ccustominterpolatorinit"></a><a name="init"></a>CCustomInterpolator::Init

Initialise la durée et la valeur finale.

```cpp
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
La durée de la transition.

*finalValue*<br/>
La valeur finale d’une variable à la fin de la transition.

## <a name="ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue

Interpole la valeur à un décalage donné.

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Sortie : La valeur interpolée.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre de base renvoie toujours VRAI. Retournez FALSE de la mise en œuvre annulée si vous souhaitez échouer à l’événement.

## <a name="ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity

Interpole la vitesse à un décalage donné

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>Paramètres

*velocity*<br/>
Sortie : La vitesse de la variable à la compensation.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre de base renvoie toujours VRAI. Retournez FALSE de la mise en œuvre annulée si vous souhaitez échouer à l’événement.

## <a name="ccustominterpolatorm_currentvalue"></a><a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue

La valeur interpolée.

```
DOUBLE m_currentValue;
```

## <a name="ccustominterpolatorm_currentvelocity"></a><a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity

La vitesse interpolée.

```
DOUBLE m_currentVelocity;
```

## <a name="ccustominterpolatorm_duration"></a><a name="m_duration"></a>CCustomInterpolator::m_duration

La durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="ccustominterpolatorm_finalvalue"></a><a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue

La valeur finale d’une variable à la fin de la transition.

```
DOUBLE m_finalValue;
```

## <a name="ccustominterpolatorm_initialvalue"></a><a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue

La valeur de la variable au début de la transition.

```
DOUBLE m_initialValue;
```

## <a name="ccustominterpolatorm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity

La vitesse de la variable au début de la transition.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustominterpolatorsetduration"></a><a name="setduration"></a>CCustomInterpolator::SetDuration

Définit la durée de l’interpolateur.

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
La durée de la transition.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre de base renvoie toujours VRAI. Retournez FALSE de la mise en œuvre annulée si vous souhaitez échouer à l’événement.

## <a name="ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity

Définit la valeur et la vitesse initiales de l’interpolateur.

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>Paramètres

*initialValue*<br/>
La valeur de la variable au début de la transition.

*initialVelocity*<br/>
La vitesse de la variable au début de la transition.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre de base renvoie toujours VRAI. Retournez FALSE de la mise en œuvre annulée si vous souhaitez échouer à l’événement.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
