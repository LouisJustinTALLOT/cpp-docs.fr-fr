---
description: 'En savoir plus sur : classe CSinusoidalTransitionFromVelocity,'
title: CSinusoidalTransitionFromVelocity, classe
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_period
helpviewer_keywords:
- CSinusoidalTransitionFromVelocity [MFC], CSinusoidalTransitionFromVelocity
- CSinusoidalTransitionFromVelocity [MFC], Create
- CSinusoidalTransitionFromVelocity [MFC], m_duration
- CSinusoidalTransitionFromVelocity [MFC], m_period
ms.assetid: cc885f17-b84b-45ee-8f1f-36a8bbb7adad
ms.openlocfilehash: 96f4a4c6343f3635f3b60480f49c5af6e6f1e089
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342752"
---
# <a name="csinusoidaltransitionfromvelocity-class"></a>CSinusoidalTransitionFromVelocity, classe

Encapsule une transition de vitesse sinusoïdale dont l’amplitude est déterminée par la rapidité initiale de la variable de l’animation.

## <a name="syntax"></a>Syntaxe

```
class CSinusoidalTransitionFromVelocity : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSinusoidalTransitionFromVelocity, :: CSinusoidalTransitionFromVelocity,](#csinusoidaltransitionfromvelocity)|Construit un objet de transition.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSinusoidalTransitionFromVelocity, :: Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition :: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSinusoidalTransitionFromVelocity, :: m_duration](#m_duration)|Durée de la transition.|
|[CSinusoidalTransitionFromVelocity, :: m_period](#m_period)|Période d’oscillation de l’onde sinusoïdale en secondes.|

## <a name="remarks"></a>Notes

La valeur de la variable d’animation oscille autour de la valeur initiale pendant toute la durée d’une transition de plage sinusoïdale. L’amplitude de l’oscillation est déterminée par la rapidité de la variable d’animation au début de la transition. Étant donné que toutes les transitions sont automatiquement désactivées, il est recommandé de les allouer à l’aide de operator new. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController :: AnimateGroup, jusqu’à ce qu’il soit NULL. La modification des variables membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromVelocity,](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromvelocitycreate"></a><a name="create"></a> CSinusoidalTransitionFromVelocity, :: Create

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

## <a name="csinusoidaltransitionfromvelocitycsinusoidaltransitionfromvelocity"></a><a name="csinusoidaltransitionfromvelocity"></a> CSinusoidalTransitionFromVelocity, :: CSinusoidalTransitionFromVelocity,

Construit un objet de transition.

```
CSinusoidalTransitionFromVelocity(
    UI_ANIMATION_SECONDS duration,
    UI_ANIMATION_SECONDS period);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Durée de la transition.

*heures*<br/>
Période d’oscillation de l’onde sinusoïdale en secondes.

## <a name="csinusoidaltransitionfromvelocitym_duration"></a><a name="m_duration"></a> CSinusoidalTransitionFromVelocity, :: m_duration

Durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromvelocitym_period"></a><a name="m_period"></a> CSinusoidalTransitionFromVelocity, :: m_period

Période d’oscillation de l’onde sinusoïdale en secondes.

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
