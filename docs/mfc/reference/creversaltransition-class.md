---
title: CReversalTransition, classe
ms.date: 11/04/2016
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
ms.openlocfilehash: 73d12fb6bbaefcfac1437248ebe11f3a5c24c45b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368319"
---
# <a name="creversaltransition-class"></a>CReversalTransition, classe

Encapsule une transition inverse.

## <a name="syntax"></a>Syntaxe

```
class CReversalTransition : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CReversalTransition::CReversalTransition](#creversaltransition)|Construit un objet de transition d’inversion et initialise sa durée.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CReversalTransition::Créer](#create)|Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé. (Overrides [CBaseTransition::Créer](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CReversalTransition::m_duration](#m_duration)|La durée de la transition.|

## <a name="remarks"></a>Notes

Une transition d’inversion change en douceur de direction sur une durée donnée. La valeur finale sera la même que la valeur initiale et la vitesse finale sera la négative de la vitesse initiale. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les répartir à l’aide de l’opérateur nouveau. L’objet IUIAnimationTransition COM encapsulé est créé par CAnimationController::AnimateGroup, jusque-là c’est NULL. Changer les variables des membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CReversalTransition](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="creversaltransitioncreate"></a><a name="create"></a>CReversalTransition::Créer

Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibraire*<br/>
Un pointeur vers la bibliothèque de transition, qui est responsable de la création de transitions standard.

### <a name="return-value"></a>Valeur de retour

VRAI si la transition est créée avec succès; autrement FALSE.

## <a name="creversaltransitioncreversaltransition"></a><a name="creversaltransition"></a>CReversalTransition::CReversalTransition

Construit un objet de transition d’inversion et initialise sa durée.

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*Durée*<br/>
La durée de la transition.

## <a name="creversaltransitionm_duration"></a><a name="m_duration"></a>CReversalTransition::m_duration

La durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
