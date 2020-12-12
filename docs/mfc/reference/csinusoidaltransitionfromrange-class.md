---
description: 'En savoir plus sur : classe CSinusoidalTransitionFromRange,'
title: CSinusoidalTransitionFromRange, classe
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
ms.openlocfilehash: 5d00b1cbfb8fe9b76a5a69bd1c9f10316ddf8141
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264568"
---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange, classe

Encapsule une transition de plage sinusoïdale comportant une plage d'oscillation donnée.

## <a name="syntax"></a>Syntaxe

```
class CSinusoidalTransitionFromRange : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSinusoidalTransitionFromRange, :: CSinusoidalTransitionFromRange,](#csinusoidaltransitionfromrange)|Construit un objet de transition.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSinusoidalTransitionFromRange, :: Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition :: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSinusoidalTransitionFromRange, :: m_dblMaximumValue](#m_dblmaximumvalue)|Valeur de la variable d’animation à un pic de l’onde sinusoïdale.|
|[CSinusoidalTransitionFromRange, :: m_dblMinimumValue](#m_dblminimumvalue)|Valeur de la variable d’animation à un creux de l’onde sinusoïdale.|
|[CSinusoidalTransitionFromRange, :: m_duration](#m_duration)|Durée de la transition.|
|[CSinusoidalTransitionFromRange, :: m_period](#m_period)|Période d’oscillation de l’onde sinusoïdale en secondes.|
|[CSinusoidalTransitionFromRange, :: m_slope](#m_slope)|Pente au début de la transition.|

## <a name="remarks"></a>Notes

La valeur de la variable d’animation fluctue entre les valeurs minimale et maximale spécifiées sur toute la durée d’une transition de plage sinusoïdale. Le paramètre Slope est utilisé pour lever l’ambiguïté entre les deux ondes sinusoïdales possibles spécifiées par les autres paramètres. Étant donné que toutes les transitions sont automatiquement désactivées, il est recommandé de les allouer à l’aide de operator new. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController :: AnimateGroup, jusqu’à ce qu’il soit NULL. La modification des variables membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromRange,](../../mfc/reference/csinusoidaltransitionfromrange-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromrangecreate"></a><a name="create"></a> CSinusoidalTransitionFromRange, :: Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers la bibliothèque de transitions, qui est responsable de la création de transitions standard.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la transition est créée avec succès ; Sinon, FALSe.

## <a name="csinusoidaltransitionfromrangecsinusoidaltransitionfromrange"></a><a name="csinusoidaltransitionfromrange"></a> CSinusoidalTransitionFromRange, :: CSinusoidalTransitionFromRange,

Construit un objet de transition.

```
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblMinimumValue,
    DOUBLE dblMaximumValue,
    UI_ANIMATION_SECONDS period,
    UI_ANIMATION_SLOPE slope);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Durée de la transition.

*dblMinimumValue*<br/>
Valeur de la variable d’animation à un creux de l’onde sinusoïdale.

*dblMaximumValue*<br/>
Valeur de la variable d’animation à un pic de l’onde sinusoïdale.

*heures*<br/>
Période d’oscillation de l’onde sinusoïdale en secondes.

*ascendant*<br/>
Pente au début de la transition.

## <a name="csinusoidaltransitionfromrangem_dblmaximumvalue"></a><a name="m_dblmaximumvalue"></a> CSinusoidalTransitionFromRange, :: m_dblMaximumValue

Valeur de la variable d’animation à un pic de l’onde sinusoïdale.

```
DOUBLE m_dblMaximumValue;
```

## <a name="csinusoidaltransitionfromrangem_dblminimumvalue"></a><a name="m_dblminimumvalue"></a> CSinusoidalTransitionFromRange, :: m_dblMinimumValue

Valeur de la variable d’animation à un creux de l’onde sinusoïdale.

```
DOUBLE m_dblMinimumValue;
```

## <a name="csinusoidaltransitionfromrangem_duration"></a><a name="m_duration"></a> CSinusoidalTransitionFromRange, :: m_duration

Durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromrangem_period"></a><a name="m_period"></a> CSinusoidalTransitionFromRange, :: m_period

Période d’oscillation de l’onde sinusoïdale en secondes.

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="csinusoidaltransitionfromrangem_slope"></a><a name="m_slope"></a> CSinusoidalTransitionFromRange, :: m_slope

Pente au début de la transition.

```
UI_ANIMATION_SLOPE m_slope;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
