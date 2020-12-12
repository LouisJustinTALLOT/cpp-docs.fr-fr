---
description: 'En savoir plus sur : classe CAccelerateDecelerateTransition'
title: CAccelerateDecelerateTransition, classe
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 5981c6f57acaf2507410acbb6c792f77b96f75c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322757"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition, classe

Implémente une transition accélérer-ralentir.

## <a name="syntax"></a>Syntaxe

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Construit un objet de transition.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAccelerateDecelerateTransition :: Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition :: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAccelerateDecelerateTransition :: m_accelerationRatio](#m_accelerationratio)|Rapport entre le temps consacré à l’accélération de la durée.|
|[CAccelerateDecelerateTransition :: m_decelerationRatio](#m_decelerationratio)|Rapport entre le temps consacré à la décélération et la durée.|
|[CAccelerateDecelerateTransition :: m_duration](#m_duration)|Durée de la transition.|
|[CAccelerateDecelerateTransition :: m_finalValue](#m_finalvalue)|Valeur de la variable d’animation à la fin de la transition.|

## <a name="remarks"></a>Notes

Pendant une transition accélére-décélération, la variable d’animation accélère, puis ralentit sur la durée de la transition, en se terminant à une valeur spécifiée. Vous pouvez contrôler la vitesse à laquelle la variable accélère et décélère indépendamment, en spécifiant des ratios d’accélération et de décélération différents. Lorsque la rapidité initiale est égale à zéro, le taux d’accélération est la fraction de la durée que la variable passera en accélération. de même que le rapport de décélération. Si la rapidité initiale est différente de zéro, il s’agit de la fraction du temps entre la vélocité qui atteint zéro et la fin de la transition. Le taux d’accélération et le rapport de décélération doivent être additionnés à un maximum de 1,0. Étant donné que toutes les transitions sont automatiquement désactivées, il est recommandé de les allouer à l’aide de operator new. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController :: AnimateGroup, jusqu’à ce qu’il soit NULL. La modification des variables membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a> CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

Construit un objet de transition.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Durée de la transition.

*finalValue*<br/>
Valeur de la variable d’animation à la fin de la transition.

*accelerationRatio*<br/>
Rapport entre le temps consacré à l’accélération de la durée.

*decelerationRatio*<br/>
Rapport entre le temps consacré à la décélération et la durée.

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a> CAccelerateDecelerateTransition :: Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers une [interface IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), qui définit une bibliothèque de transitions standard.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la transition est créée avec succès ; Sinon, FALSe.

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a> CAccelerateDecelerateTransition :: m_accelerationRatio

Rapport entre le temps consacré à l’accélération de la durée.

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a> CAccelerateDecelerateTransition :: m_decelerationRatio

Rapport entre le temps consacré à la décélération et la durée.

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a> CAccelerateDecelerateTransition :: m_duration

Durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a> CAccelerateDecelerateTransition :: m_finalValue

Valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
