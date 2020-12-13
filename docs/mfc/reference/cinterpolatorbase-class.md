---
description: 'En savoir plus sur : classe CInterpolatorBase,'
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
ms.openlocfilehash: 73204e8b81db862fe30058d1b2451ea468d332e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340955"
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
|[CInterpolatorBase, :: CInterpolatorBase,](#cinterpolatorbase)|Construit l' `CInterpolatorBase` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInterpolatorBase, :: CreateInstance](#createinstance)|Crée une instance de `CInterpolatorBase` et stocke un pointeur vers l’interpolateur personnalisé, qui gère les événements.|
|[CInterpolatorBase, :: GetDependencies](#getdependencies)|Obtient les dépendances de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::GetDependencies`.)|
|[CInterpolatorBase, :: GetDuration](#getduration)|Obtient la durée de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::GetDuration`.)|
|[CInterpolatorBase, :: GetFinalValue](#getfinalvalue)|Obtient la valeur finale vers laquelle l’interpolateur dirige. (Substitue `CUIAnimationInterpolatorBase::GetFinalValue`.)|
|[CInterpolatorBase, :: InterpolateValue](#interpolatevalue)|Interpole la valeur à un offset donné (substitutions `CUIAnimationInterpolatorBase::InterpolateValue` ).|
|[CInterpolatorBase, :: InterpolateVelocity](#interpolatevelocity)|Interpole la vélocité à un décalage donné (substitutions `CUIAnimationInterpolatorBase::InterpolateVelocity` ).|
|[CInterpolatorBase, :: SetCustomInterpolator](#setcustominterpolator)|Stocke un pointeur vers l’interpolateur personnalisé, qui gère les événements.|
|[CInterpolatorBase, :: SetDuration](#setduration)|Définit la durée de l’interpolateur (substitutions `CUIAnimationInterpolatorBase::SetDuration` ).|
|[CInterpolatorBase, :: SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Définit la valeur initiale et la vélocité de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|

## <a name="remarks"></a>Notes

Ce gestionnaire est créé et passé à `IUIAnimationTransitionFactory::CreateTransition` lorsqu’un `CCustomTransition` objet est créé dans le cadre du processus d’initialisation d’animation (démarré par `CAnimationController::AnimateGroup` ). En règle générale, vous n’avez pas besoin d’utiliser cette classe directement, elle achemine simplement tous les événements vers une `CCustomInterpolator` classe dérivée de, dont le pointeur est passé au constructeur de `CCustomTransition` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cinterpolatorbasecinterpolatorbase"></a><a name="cinterpolatorbase"></a> CInterpolatorBase, :: CInterpolatorBase,

Construit l’objet CInterpolatorBase,.

```
CInterpolatorBase();
```

## <a name="cinterpolatorbasecreateinstance"></a><a name="createinstance"></a> CInterpolatorBase, :: CreateInstance

Crée une instance de CInterpolatorBase, et stocke un pointeur vers l’interpolateur personnalisé qui gère les événements.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Paramètres

*pInterpolator*<br/>
Pointeur vers l’interpolateur personnalisé.

*ppHandler*<br/>
Sortie : Contient un pointeur vers l’instance de CInterpolatorBase, lorsque la fonction retourne.

### <a name="return-value"></a>Valeur renvoyée

## <a name="cinterpolatorbasegetdependencies"></a><a name="getdependencies"></a> CInterpolatorBase, :: GetDependencies

Obtient les dépendances de l’interpolateur.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Paramètres

*initialValueDependencies*<br/>
Sortie : Aspects de l’interpolation qui dépendent de la valeur initiale passée à SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Sortie : Aspects de l’interpolation qui dépendent de la rapidité initiale passée à SetInitialValueAndVelocity.

*durationDependencies*<br/>
Sortie : Aspects de l’interpolation qui dépendent de la durée passée à SetDuration.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Elle retourne E_FAIL si CCustomInterpolator, n’est pas défini, ou si l’implémentation personnalisée retourne la valeur FALSe à partir de la méthode GetDependencies.

## <a name="cinterpolatorbasegetduration"></a><a name="getduration"></a> CInterpolatorBase, :: GetDuration

Obtient la durée de l’interpolateur.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Sortie : Durée de la transition, en secondes.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Elle retourne E_FAIL si CCustomInterpolator, n’est pas défini, ou si l’implémentation personnalisée retourne la valeur FALSe à partir de la méthode GetDuration.

## <a name="cinterpolatorbasegetfinalvalue"></a><a name="getfinalvalue"></a> CInterpolatorBase, :: GetFinalValue

Obtient la valeur finale vers laquelle l’interpolateur dirige.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Sortie : Valeur finale d’une variable à la fin de la transition.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Elle retourne E_FAIL si CCustomInterpolator, n’est pas défini, ou si l’implémentation personnalisée retourne la valeur FALSe à partir de la méthode GetFinalValue.

## <a name="cinterpolatorbaseinterpolatevalue"></a><a name="interpolatevalue"></a> CInterpolatorBase, :: InterpolateValue

Interpole la valeur à un offset donné.

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
Offset à partir du début de la transition. Le décalage est toujours supérieur ou égal à zéro et inférieur à la durée de la transition. Cette méthode n’est pas appelée si la durée de la transition est égale à zéro.

*value*<br/>
Sortie : Valeur interpolée.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Elle retourne E_FAIL si CCustomInterpolator, n’est pas défini, ou si l’implémentation personnalisée retourne la valeur FALSe à partir de la méthode InterpolateValue.

## <a name="cinterpolatorbaseinterpolatevelocity"></a><a name="interpolatevelocity"></a> CInterpolatorBase, :: InterpolateVelocity

Interpole la vélocité à un décalage donné.

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
Offset à partir du début de la transition. Le décalage est toujours supérieur ou égal à zéro et inférieur ou égal à la durée de la transition. Cette méthode n’est pas appelée si la durée de la transition est égale à zéro.

*vélocité*<br/>
Sortie : Vélocité de la variable à l’offset.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Elle retourne E_FAIL si CCustomInterpolator, n’est pas défini, ou si l’implémentation personnalisée retourne la valeur FALSe à partir de la méthode InterpolateVelocity.

## <a name="cinterpolatorbasesetcustominterpolator"></a><a name="setcustominterpolator"></a> CInterpolatorBase, :: SetCustomInterpolator

Stocke un pointeur vers l’interpolateur personnalisé, qui gère les événements.

```cpp
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Paramètres

*pInterpolator*<br/>
Pointeur vers l’interpolateur personnalisé.

## <a name="cinterpolatorbasesetduration"></a><a name="setduration"></a> CInterpolatorBase, :: SetDuration

Définit la durée de l’interpolateur

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Durée de la transition.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Elle retourne E_FAIL si CCustomInterpolator, n’est pas défini, ou si l’implémentation personnalisée retourne la valeur FALSe à partir de la méthode SetDuration.

## <a name="cinterpolatorbasesetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a> CInterpolatorBase, :: SetInitialValueAndVelocity

Définit la valeur initiale et la vélocité de l’interpolateur.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Paramètres

*initialValue*<br/>
Valeur de la variable au début de la transition.

*initialVelocity*<br/>
Rapidité de la variable au début de la transition.

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Elle retourne E_FAIL si CCustomInterpolator, n’est pas défini, ou si l’implémentation personnalisée retourne la valeur FALSe à partir de la méthode SetInitialValueAndVelocity.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
