---
title: CReversalTransition, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 393c0ed7c9d1c5715528468e0c611ae399fbadf6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431500"
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
|[CReversalTransition::CReversalTransition](#creversaltransition)|Construit un objet de transition inverse et initialise sa durée.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CReversalTransition::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CReversalTransition::m_duration](#m_duration)|La durée de la transition.|

## <a name="remarks"></a>Notes

Une transition inverse change sans heurts de direction sur une durée donnée. La valeur finale doit être le même que la valeur initiale et la rapidité finale sera la valeur négative de la rapidité initiale. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouvel opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que puis sa valeur est NULL. La modification de variables membres après que la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CReversalTransition](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="create"></a>  CReversalTransition::Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers la bibliothèque de transitions qui est responsable de la création de transitions standards.

### <a name="return-value"></a>Valeur de retour

TRUE si la transition est créée avec succès ; Sinon, FALSE.

##  <a name="creversaltransition"></a>  CReversalTransition::CReversalTransition

Construit un objet de transition inverse et initialise sa durée.

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*durée*<br/>
La durée de la transition.

##  <a name="m_duration"></a>  CReversalTransition::m_duration

La durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
