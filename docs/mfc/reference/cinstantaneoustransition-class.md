---
title: CInstantaneousTransition, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
dev_langs:
- C++
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e984bb3d616596d0e6c9439fa3096ba23059caae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428133"
---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition, classe

Encapsule une transition instantanée.

## <a name="syntax"></a>Syntaxe

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|Construit un objet de transition et initialise sa valeur finale.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInstantaneousTransition::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable à la fin de la transition de l’animation.|

## <a name="remarks"></a>Notes

Pendant une transition instantanée, la valeur de la variable d’animation change instantanément à partir de sa valeur actuelle à une valeur finale spécifiée. La durée de cette transition est toujours zéro. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les allouer à l’aide de nouvel opérateur. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController::AnimateGroup, jusqu'à ce que puis sa valeur est NULL. La modification de variables membres après que la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="cinstantaneoustransition"></a>  CInstantaneousTransition::CInstantaneousTransition

Construit un objet de transition et initialise sa valeur finale.

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Paramètres

*dblFinalValue*<br/>
La valeur de la variable à la fin de la transition de l’animation.

##  <a name="create"></a>  CInstantaneousTransition::Create

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

##  <a name="m_dblfinalvalue"></a>  CInstantaneousTransition::m_dblFinalValue

La valeur de la variable à la fin de la transition de l’animation.

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
