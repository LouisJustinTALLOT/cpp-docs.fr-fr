---
description: 'En savoir plus sur : classe CParabolicTransitionFromAcceleration,'
title: CParabolicTransitionFromAcceleration, classe
ms.date: 11/04/2016
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
helpviewer_keywords:
- CParabolicTransitionFromAcceleration [MFC], CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration [MFC], Create
- CParabolicTransitionFromAcceleration [MFC], m_dblAcceleration
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalValue
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalVelocity
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
ms.openlocfilehash: 037c2ff8391b655c556339547966b14ee094fee0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301488"
---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration, classe

Encapsule une transition d'accélération parabolique.

## <a name="syntax"></a>Syntaxe

```
class CParabolicTransitionFromAcceleration : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration, :: CParabolicTransitionFromAcceleration,](#cparabolictransitionfromacceleration)|Construit une transition d’accélération parabolique et l’initialise avec les paramètres spécifiés.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration, :: Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition :: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration, :: m_dblAcceleration](#m_dblacceleration)|Accélération de la variable d’animation pendant la transition.|
|[CParabolicTransitionFromAcceleration, :: m_dblFinalValue](#m_dblfinalvalue)|Valeur de la variable d’animation à la fin de la transition.|
|[CParabolicTransitionFromAcceleration, :: m_dblFinalVelocity](#m_dblfinalvelocity)|Rapidité de la variable d’animation à la fin de la transition.|

## <a name="remarks"></a>Notes

Pendant une transition d’accélération parabolique, la valeur de la variable d’animation passe de la valeur initiale à la valeur finale se terminant à une vélocité spécifiée. Vous pouvez contrôler la vitesse à laquelle la variable atteint la valeur finale en spécifiant le taux d’accélération. Étant donné que toutes les transitions sont automatiquement désactivées, il est recommandé de les allouer à l’aide de operator new. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController :: AnimateGroup, jusqu’à ce qu’il soit NULL. La modification des variables membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CParabolicTransitionFromAcceleration,](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cparabolictransitionfromaccelerationcparabolictransitionfromacceleration"></a><a name="cparabolictransitionfromacceleration"></a> CParabolicTransitionFromAcceleration, :: CParabolicTransitionFromAcceleration,

Construit une transition d’accélération parabolique et l’initialise avec les paramètres spécifiés.

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>Paramètres

*dblFinalValue*<br/>
Valeur de la variable d’animation à la fin de la transition.

*dblFinalVelocity*<br/>
Rapidité de la variable d’animation à la fin de la transition.

*dblAcceleration*<br/>
Accélération de la variable d’animation pendant la transition.

## <a name="cparabolictransitionfromaccelerationcreate"></a><a name="create"></a> CParabolicTransitionFromAcceleration, :: Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers la bibliothèque de transitions, qui est responsable de la création de transitions standard.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la transition est créée avec succès ; Sinon, FALSe.

## <a name="cparabolictransitionfromaccelerationm_dblacceleration"></a><a name="m_dblacceleration"></a> CParabolicTransitionFromAcceleration, :: m_dblAcceleration

Accélération de la variable d’animation pendant la transition.

```
DOUBLE m_dblAcceleration;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a> CParabolicTransitionFromAcceleration, :: m_dblFinalValue

Valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalValue;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a> CParabolicTransitionFromAcceleration, :: m_dblFinalVelocity

Rapidité de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
