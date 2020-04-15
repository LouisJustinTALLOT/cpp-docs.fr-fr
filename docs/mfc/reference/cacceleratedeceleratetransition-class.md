---
title: Classe CAccelerateDecelerateTransition
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 356ba30e6d9a638672d2c356676735ebfaed8f3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371147"
---
# <a name="cacceleratedeceleratetransition-class"></a>Classe CAccelerateDecelerateTransition

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
|[CAccelerateDecelerateTransition::Créer](#create)|Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé. (Overrides [CBaseTransition::Créer](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|Le rapport entre le temps passé à accélérer et la durée.|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|Le rapport entre le temps passé à décélérer et la durée.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|La durée de la transition.|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|La valeur de la variable d’animation à la fin de la transition.|

## <a name="remarks"></a>Notes

Au cours d’une transition accélérée, la variable d’animation accélère puis ralentit pendant toute la durée de la transition, se terminant à une valeur spécifiée. Vous pouvez contrôler la rapidité avec laquelle la variable accélère et décélère indépendamment, en spécifiant différents rapports d’accélération et de décélération. Lorsque la vitesse initiale est nulle, le rapport d’accélération est la fraction de la durée que la variable passera à accélérer; de même avec le rapport de décélération. Si la vitesse initiale n’est pas nulle, c’est la fraction du temps entre la vitesse atteignant zéro et la fin de la transition. Le ratio d’accélération et le ratio de décélération devraient s’établir à un maximum de 1,0. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les répartir à l’aide de l’opérateur nouveau. L’objet IUIAnimationTransition COM encapsulé est créé par CAnimationController::AnimateGroup, jusque-là c’est NULL. Changer les variables des membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

Construit un objet de transition.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>Paramètres

*Durée*<br/>
La durée de la transition.

*finalValue*<br/>
La valeur de la variable d’animation à la fin de la transition.

*accélérationRatio*<br/>
Le rapport entre le temps passé à accélérer et la durée.

*décélérationRatio*<br/>
Le rapport entre le temps passé à décélérer et la durée.

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a>CAccelerateDecelerateTransition::Créer

Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibraire*<br/>
Un pointeur à une [interface IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), qui définit une bibliothèque de transitions standard.

### <a name="return-value"></a>Valeur de retour

VRAI si la transition est créée avec succès; autrement FALSE.

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a>CAccelerateDecelerateTransition::m_accelerationRatio

Le rapport entre le temps passé à accélérer et la durée.

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio

Le rapport entre le temps passé à décélérer et la durée.

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration

La durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue

La valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
