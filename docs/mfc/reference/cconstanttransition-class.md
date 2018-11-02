---
title: CConstantTransition, classe
ms.date: 11/04/2016
f1_keywords:
- CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::Create
- AFXANIMATIONCONTROLLER/CConstantTransition::m_duration
helpviewer_keywords:
- CConstantTransition [MFC], CConstantTransition
- CConstantTransition [MFC], Create
- CConstantTransition [MFC], m_duration
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
ms.openlocfilehash: 2ec8ec36e59a0d4dc0e00f5e379bfbef492ce4db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662018"
---
# <a name="cconstanttransition-class"></a>CConstantTransition, classe

Encapsule une transition constante.

## <a name="syntax"></a>Syntaxe

```
class CConstantTransition : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CConstantTransition::CConstantTransition](#cconstanttransition)|Construit un objet de transition et initialise sa durée.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CConstantTransition::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CConstantTransition::m_duration](#m_duration)|La durée de la transition.|

## <a name="remarks"></a>Notes

Pendant une transition constante, la valeur d’une variable d’animation conserve la valeur initiale pendant la durée de la transition. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouvel opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que puis sa valeur est NULL. La modification de variables membres après que la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CConstantTransition`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="cconstanttransition"></a>  CConstantTransition::CConstantTransition

Construit un objet de transition et initialise sa durée.

```
CConstantTransition (UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Paramètres

*durée*<br/>
La durée de la transition.

##  <a name="create"></a>  CConstantTransition::Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Un pointeur vers un [interface IUIAnimationTransitionLibrary](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), qui définit une bibliothèque de transitions standards.

### <a name="return-value"></a>Valeur de retour

TRUE si la transition est créée avec succès ; Sinon, FALSE.

##  <a name="m_duration"></a>  CConstantTransition::m_duration

La durée de la transition.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
