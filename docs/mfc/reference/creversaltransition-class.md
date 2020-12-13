---
description: 'En savoir plus sur : classe CReversalTransition,'
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
ms.openlocfilehash: f1d16562751e93ccf6df7ca3f70dac08bda8423d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343005"
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
|[CReversalTransition, :: CReversalTransition,](#creversaltransition)|Construit un objet de transition inverse et initialise sa durée.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CReversalTransition, :: Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition :: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CReversalTransition, :: m_duration](#m_duration)|Durée de la transition.|

## <a name="remarks"></a>Notes

Une transition de contrepassation change en douceur le sens sur une durée donnée. La valeur finale sera la même que la valeur initiale et la vélocité finale sera la valeur négative de la rapidité initiale. Étant donné que toutes les transitions sont automatiquement désactivées, il est recommandé de les allouer à l’aide de operator new. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController :: AnimateGroup, jusqu’à ce qu’il soit NULL. La modification des variables membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CReversalTransition,](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="creversaltransitioncreate"></a><a name="create"></a> CReversalTransition, :: Create

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

## <a name="creversaltransitioncreversaltransition"></a><a name="creversaltransition"></a> CReversalTransition, :: CReversalTransition,

Construit un objet de transition inverse et initialise sa durée.

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*duration*<br/>
Durée de la transition.

## <a name="creversaltransitionm_duration"></a><a name="m_duration"></a> CReversalTransition, :: m_duration

Durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
