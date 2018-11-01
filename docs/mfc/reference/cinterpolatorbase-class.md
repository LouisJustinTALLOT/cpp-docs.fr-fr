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
ms.openlocfilehash: e428478f2f437654ea2f0890993245afc53c01f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541464"
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
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Construit le `CInterpolatorBase` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Crée une instance de `CInterpolatorBase` et stocke un pointeur à un interpolateur personnalisé, ce qui doit gérer les événements.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Obtient les dépendances de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::GetDependencies`.)|
|[CInterpolatorBase::GetDuration](#getduration)|Obtient la durée de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::GetDuration`.)|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Obtient la valeur finale à laquelle l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::GetFinalValue`.)|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpole la valeur à un offset donné (substitue `CUIAnimationInterpolatorBase::InterpolateValue`.)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpole la rapidité à un offset donné (substitue `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Stocke un pointeur à un interpolateur personnalisé, ce qui doit gérer les événements.|
|[CInterpolatorBase::SetDuration](#setduration)|Définit la durée de l’interpolateur (substitue `CUIAnimationInterpolatorBase::SetDuration`.)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Définit la valeur initiale et la rapidité de l’interpolateur. (Substitue `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|

## <a name="remarks"></a>Notes

Ce gestionnaire est créé et transmis à `IUIAnimationTransitionFactory::CreateTransition` lorsqu’un `CCustomTransition` objet est créé dans le cadre du processus d’initialisation de l’animation (démarré par `CAnimationController::AnimateGroup`). En général vous n’avez pas besoin d’utiliser cette classe directement, elle achemine simplement tous les événements dans un `CCustomInterpolator`-dont le pointeur est passé au constructeur de classe dérivée `CCustomTransition`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>  CInterpolatorBase::CInterpolatorBase

Construit l’objet CInterpolatorBase.

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>  CInterpolatorBase::CreateInstance

Crée une instance de CInterpolatorBase et stocke un pointeur à un interpolateur personnalisé, ce qui doit gérer les événements.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Paramètres

*pInterpolator*<br/>
Pointeur vers l’interpolateur personnalisé.

*ppHandler*<br/>
Sortie. Contient un pointeur vers une instance de CInterpolatorBase lorsque la fonction retourne.

### <a name="return-value"></a>Valeur de retour

##  <a name="getdependencies"></a>  CInterpolatorBase::GetDependencies

Obtient les dépendances de l’interpolateur.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Paramètres

*initialValueDependencies*<br/>
Sortie. Aspects de l’interpolateur qui dépendent de la valeur initiale est transmise à SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Sortie. Aspects de l’interpolateur qui dépendent de la rapidité initiale transmise à SetInitialValueAndVelocity.

*durationDependencies*<br/>
Sortie. Aspects de l’interpolateur qui dépendent de la durée transmise à SetDuration.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Retourne E_FAIL si CCustomInterpolator n’est pas défini, ou l’implémentation personnalisée retourne FALSE de la méthode GetDependencies.

##  <a name="getduration"></a>  CInterpolatorBase::GetDuration

Obtient la durée de l’interpolateur.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Paramètres

*durée*<br/>
Sortie. La durée de la transition, en secondes.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Retourne E_FAIL si CCustomInterpolator n’est pas défini, ou l’implémentation personnalisée retourne FALSE de la méthode GetDuration.

##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue

Obtient la valeur finale à laquelle l’interpolateur.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*valeur*<br/>
Sortie. La valeur finale d’une variable à la fin de la transition.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Retourne E_FAIL si CCustomInterpolator n’est pas défini, ou l’implémentation personnalisée retourne FALSE de la méthode GetFinalValue.

##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue

Interpole la valeur à un offset donné

```
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* value);
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
Le décalage à partir du début de la transition. Le décalage est toujours supérieure ou égale à zéro et inférieur à la durée de la transition. Cette méthode n’est pas appelée si la durée de la transition est égal à zéro.

*valeur*<br/>
Sortie. La valeur interpolée.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Retourne E_FAIL si CCustomInterpolator n’est pas défini, ou l’implémentation personnalisée retourne FALSE de la méthode InterpolateValue.

##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity

Interpole la rapidité à un offset donné

```
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```

### <a name="parameters"></a>Paramètres

*offset*<br/>
Le décalage à partir du début de la transition. Le décalage est toujours supérieure ou égale à zéro et inférieure ou égale à la durée de la transition. Cette méthode n’est pas appelée si la durée de la transition est égal à zéro.

*Rapidité*<br/>
Sortie. La rapidité de la variable à l’offset.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Retourne E_FAIL si CCustomInterpolator n’est pas défini, ou l’implémentation personnalisée retourne FALSE de la méthode InterpolateVelocity.

##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator

Stocke un pointeur à un interpolateur personnalisé, ce qui doit gérer les événements.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Paramètres

*pInterpolator*<br/>
Pointeur vers l’interpolateur personnalisé.

##  <a name="setduration"></a>  CInterpolatorBase::SetDuration

Définit la durée de l’interpolateur

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*durée*<br/>
La durée de la transition.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Retourne E_FAIL si CCustomInterpolator n’est pas défini, ou l’implémentation personnalisée retourne FALSE de la méthode SetDuration.

##  <a name="setinitialvalueandvelocity"></a>  CInterpolatorBase::SetInitialValueAndVelocity

Définit la valeur initiale et la rapidité de l’interpolateur.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue,
  __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Paramètres

*initialValue*<br/>
La valeur de la variable au début de la transition.

*initialVelocity*<br/>
La rapidité de la variable au début de la transition.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Retourne E_FAIL si CCustomInterpolator n’est pas défini, ou l’implémentation personnalisée retourne FALSE de la méthode SetInitialValueAndVelocity.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
