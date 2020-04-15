---
title: CCubicTransition, classe
ms.date: 11/04/2016
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
ms.openlocfilehash: de376503111dab157ca34744863fb1d35a58785e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369345"
---
# <a name="ccubictransition-class"></a>CCubicTransition, classe

Encapsule une transition cubique.

## <a name="syntax"></a>Syntaxe

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCubicTransition::CCubicTransition](#ccubictransition)|Construit un objet de transition et initialise ses paramètres.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCubicTransition::Créer](#create)|Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé. (Overrides [CBaseTransition::Créer](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable d’animation à la fin de la transition.|
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|La vitesse de la variable à la fin de la transition.|
|[CCubicTransition::m_duration](#m_duration)|La durée de la transition.|

## <a name="remarks"></a>Notes

Au cours d’une transition cubique, la valeur de la variable d’animation passe de sa valeur initiale à une valeur finale spécifiée pendant toute la durée de la transition, se terminant à une vitesse spécifiée. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les répartir à l’aide de l’opérateur nouveau. L’objet IUIAnimationTransition COM encapsulé est créé par CAnimationController::AnimateGroup, jusque-là c’est NULL. Changer les variables des membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="ccubictransitionccubictransition"></a><a name="ccubictransition"></a>CCubicTransition::CCubicTransition

Construit un objet de transition et initialise ses paramètres.

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>Paramètres

*Durée*<br/>
La durée de la transition.

*finalValue*<br/>
La valeur de la variable d’animation à la fin de la transition.

*finalVelocity*<br/>
La vitesse de la variable à la fin de la transition.

## <a name="ccubictransitioncreate"></a><a name="create"></a>CCubicTransition::Créer

Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibraire*<br/>
Un pointeur à une [interface IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), qui définit une bibliothèque de transitions standard.

### <a name="return-value"></a>Valeur de retour

VRAI si la transition est créée avec succès; autrement FALSE.

## <a name="ccubictransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue

La valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalValue;
```

## <a name="ccubictransitionm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity

La vitesse de la variable à la fin de la transition.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="ccubictransitionm_duration"></a><a name="m_duration"></a>CCubicTransition::m_duration

La durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
