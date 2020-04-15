---
title: CInterpolatorBase, classe
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: e5294aabc42301e2f874d5b8328d648f4deeb3c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372354"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase, classe

Implémente un rappel, qui est appelé par l'API d'animation lorsqu'elle doit calculer la nouvelle valeur d'une variable de l'animation.

## <a name="syntax"></a>Syntaxe

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Construit l’objet. `CInterpolatorBase`|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInterpolatorBase::CréerInstance](#createinstance)|Crée une `CInterpolatorBase` instance et stocke un pointeur à l’interpolateur personnalisé, qui sera la manipulation des événements.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Obtient les dépendances de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::GetDependencies`.)|
|[CInterpolatorBase::GetDuration](#getduration)|La durée de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::GetDuration`.)|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Obtient la valeur finale à laquelle l’interpolateur conduit. (Substitue `CUIAnimationInterpolatorBase::GetFinalValue`.)|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpole la valeur à un décalage `CUIAnimationInterpolatorBase::InterpolateValue`donné (Overrides .)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpole la vitesse à un décalage `CUIAnimationInterpolatorBase::InterpolateVelocity`donné (Overrides .)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Stocke un pointeur à l’interpolateur personnalisé, qui sera la gestion des événements.|
|[CInterpolatorBase::SetDuration](#setduration)|Définit la durée de l’interpolateur (Overrides `CUIAnimationInterpolatorBase::SetDuration`.)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Définit la valeur et la vitesse initiales de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|

## <a name="remarks"></a>Notes

Ce gestionnaire est créé `IUIAnimationTransitionFactory::CreateTransition` et `CCustomTransition` transmis au moment où un objet est `CAnimationController::AnimateGroup`créé dans le cadre du processus d’initialisation d’animation (commencé par ). Habituellement, vous n’avez pas besoin d’utiliser cette classe `CCustomInterpolator`directement, il déroute juste tous `CCustomTransition`les événements à une classe dérivée, dont le pointeur est passé au constructeur de .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cinterpolatorbasecinterpolatorbase"></a><a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase

Construit l’objet CInterpolatorBase.

```
CInterpolatorBase();
```

## <a name="cinterpolatorbasecreateinstance"></a><a name="createinstance"></a>CInterpolatorBase::CréerInstance

Crée une instance de CInterpolatorBase et stocke un pointeur à l’interpolateur personnalisé, qui sera la manipulation des événements.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Paramètres

*pInterpolator (en)*<br/>
Un pointeur à l’interpolateur personnalisé.

*ppHandler (en)*<br/>
Sortie : Contient un pointeur à l’exemple de CInterpolatorBase lorsque la fonction revient.

### <a name="return-value"></a>Valeur de retour

## <a name="cinterpolatorbasegetdependencies"></a><a name="getdependencies"></a>CInterpolatorBase::GetDependencies

Obtient les dépendances de l’interpolateur.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Paramètres

*initialValueDependencies*<br/>
Sortie : Aspects de l’interpolateur qui dépendent de la valeur initiale passé à SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Sortie : Aspects de l’interpolateur qui dépendent de la vitesse initiale passé à SetInitialValueAndVelocity.

*duréeDependencies*<br/>
Sortie : Aspects de l’interpolateur qui dépendent de la durée passée à SetDuration.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Il renvoie E_FAIL si CCustomInterpolator n’est pas défini, ou la mise en œuvre personnalisée renvoie FALSE de la méthode GetDependencies.

## <a name="cinterpolatorbasegetduration"></a><a name="getduration"></a>CInterpolatorBase::GetDuration

La durée de l’interpolateur.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Paramètres

*Durée*<br/>
Sortie : La durée de la transition, en quelques secondes.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Il renvoie E_FAIL si CCustomInterpolator n’est pas défini, ou la mise en œuvre personnalisée renvoie FALSE de la méthode GetDuration.

## <a name="cinterpolatorbasegetfinalvalue"></a><a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue

Obtient la valeur finale à laquelle l’interpolateur conduit.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Sortie : La valeur finale d’une variable à la fin de la transition.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Il renvoie E_FAIL si CCustomInterpolator n’est pas défini, ou la mise en œuvre personnalisée renvoie FALSE de la méthode GetFinalValue.

## <a name="cinterpolatorbaseinterpolatevalue"></a><a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue

Interpole la valeur à un décalage donné

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
Le décalage depuis le début de la transition. Le décalage est toujours supérieur ou égal à zéro et inférieur à la durée de la transition. Cette méthode n’est pas appelée si la durée de la transition est nulle.

*value*<br/>
Sortie : La valeur interpolée.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Il renvoie E_FAIL si CCustomInterpolator n’est pas défini, ou la mise en œuvre personnalisée renvoie FALSE de la méthode InterpolateValue.

## <a name="cinterpolatorbaseinterpolatevelocity"></a><a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity

Interpole la vitesse à un décalage donné

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
Le décalage depuis le début de la transition. Le décalage est toujours supérieur ou égal à zéro et inférieur ou égal à la durée de la transition. Cette méthode n’est pas appelée si la durée de la transition est nulle.

*velocity*<br/>
Sortie : La vitesse de la variable à la compensation.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Il renvoie E_FAIL si CCustomInterpolator n’est pas défini, ou la mise en œuvre personnalisée renvoie FALSE de la méthode InterpolateVelocity.

## <a name="cinterpolatorbasesetcustominterpolator"></a><a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator

Stocke un pointeur à l’interpolateur personnalisé, qui sera la gestion des événements.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Paramètres

*pInterpolator (en)*<br/>
Un pointeur à l’interpolateur personnalisé.

## <a name="cinterpolatorbasesetduration"></a><a name="setduration"></a>CInterpolatorBase::SetDuration

Définit la durée de l’interpolateur

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*Durée*<br/>
La durée de la transition.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Il renvoie E_FAIL si CCustomInterpolator n’est pas défini, ou la mise en œuvre personnalisée renvoie FALSE de la méthode SetDuration.

## <a name="cinterpolatorbasesetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity

Définit la valeur et la vitesse initiales de l’interpolateur.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Paramètres

*initialValue*<br/>
La valeur de la variable au début de la transition.

*initialVelocity*<br/>
La vitesse de la variable au début de la transition.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Il renvoie E_FAIL si CCustomInterpolator n’est pas défini, ou la mise en œuvre personnalisée renvoie FALSE de la méthode SetInitialValueAndVelocity.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
