---
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
ms.openlocfilehash: 0aa5831e2262602ee46bd69031e5927a86b978e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364087"
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
|[CParabolicTransitionDeAcceleration::CParabolicTransitionDeAcceleration](#cparabolictransitionfromacceleration)|Construit une transition parabolique-accélération et l’initialise avec des paramètres spécifiés.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CParabolicTransitionDeAcceleration::Créer](#create)|Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé. (Overrides [CBaseTransition::Créer](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CParabolicTransitionDeAcceleration::m_dblAcceleration](#m_dblacceleration)|L’accélération de la variable d’animation pendant la transition.|
|[CParabolicTransitionDeAcceleration::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable d’animation à la fin de la transition.|
|[CParabolicTransitionDeAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|La vitesse de la variable d’animation à la fin de la transition.|

## <a name="remarks"></a>Notes

Au cours d’une transition parabolique-accélération, la valeur de la variable d’animation passe de la valeur initiale à la valeur finale se terminant à une vitesse spécifiée. Vous pouvez contrôler la rapidité avec laquelle la variable atteint la valeur finale en spécifiant le taux d’accélération. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les répartir à l’aide de l’opérateur nouveau. L’objet IUIAnimationTransition COM encapsulé est créé par CAnimationController::AnimateGroup, jusque-là c’est NULL. Changer les variables des membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CParabolicTransitionDeAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cparabolictransitionfromaccelerationcparabolictransitionfromacceleration"></a><a name="cparabolictransitionfromacceleration"></a>CParabolicTransitionDeAcceleration::CParabolicTransitionDeAcceleration

Construit une transition parabolique-accélération et l’initialise avec des paramètres spécifiés.

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>Paramètres

*dblFinalValue (en)*<br/>
La valeur de la variable d’animation à la fin de la transition.

*dblFinalVelocity dblFinalVelocity dblFinalVelocity dbl*<br/>
La vitesse de la variable d’animation à la fin de la transition.

*dblAcceleration*<br/>
L’accélération de la variable d’animation pendant la transition.

## <a name="cparabolictransitionfromaccelerationcreate"></a><a name="create"></a>CParabolicTransitionDeAcceleration::Créer

Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>Paramètres

*pLibraire*<br/>
Un pointeur vers la bibliothèque de transition, qui est responsable de la création de transitions standard.

### <a name="return-value"></a>Valeur de retour

VRAI si la transition est créée avec succès; autrement FALSE.

## <a name="cparabolictransitionfromaccelerationm_dblacceleration"></a><a name="m_dblacceleration"></a>CParabolicTransitionDeAcceleration::m_dblAcceleration

L’accélération de la variable d’animation pendant la transition.

```
DOUBLE m_dblAcceleration;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CParabolicTransitionDeAcceleration::m_dblFinalValue

La valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalValue;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CParabolicTransitionDeAcceleration::m_dblFinalVelocity

La vitesse de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
