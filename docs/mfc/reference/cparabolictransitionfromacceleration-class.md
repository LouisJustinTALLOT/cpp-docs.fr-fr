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
ms.openlocfilehash: 3d4a073a0fd74f7564d9183779acfd66b41a9540
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372970"
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
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|Construit une transition d’accélération parabolique et l’initialise avec les paramètres spécifiés.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|L’accélération de la variable d’animation pendant la transition.|
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable à la fin de la transition de l’animation.|
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|Rapidité de la variable à la fin de la transition de l’animation.|

## <a name="remarks"></a>Notes

Pendant une transition d’accélération parabolique, la valeur de la variable de l’animation passe de la valeur initiale pour la valeur finale se terminant par une vitesse spécifiée. Vous pouvez contrôler la vitesse à laquelle la variable a atteint la valeur finale en spécifiant le taux d’accélération. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouvel opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que puis sa valeur est NULL. La modification de variables membres après que la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="cparabolictransitionfromacceleration"></a>  CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration

Construit une transition d’accélération parabolique et l’initialise avec les paramètres spécifiés.

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>Paramètres

*dblFinalValue*<br/>
La valeur de la variable à la fin de la transition de l’animation.

*dblFinalVelocity*<br/>
Rapidité de la variable à la fin de la transition de l’animation.

*dblAcceleration*<br/>
L’accélération de la variable d’animation pendant la transition.

##  <a name="create"></a>  CParabolicTransitionFromAcceleration::Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers la bibliothèque de transitions qui est responsable de la création de transitions standards.

### <a name="return-value"></a>Valeur de retour

TRUE si la transition est créée avec succès ; Sinon, FALSE.

##  <a name="m_dblacceleration"></a>  CParabolicTransitionFromAcceleration::m_dblAcceleration

L’accélération de la variable d’animation pendant la transition.

```
DOUBLE m_dblAcceleration;
```

##  <a name="m_dblfinalvalue"></a>  CParabolicTransitionFromAcceleration::m_dblFinalValue

La valeur de la variable à la fin de la transition de l’animation.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblfinalvelocity"></a>  CParabolicTransitionFromAcceleration::m_dblFinalVelocity

Rapidité de la variable à la fin de la transition de l’animation.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
