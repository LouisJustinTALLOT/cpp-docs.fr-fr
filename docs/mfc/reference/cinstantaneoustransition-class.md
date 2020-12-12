---
description: 'En savoir plus sur : classe CInstantaneousTransition,'
title: CInstantaneousTransition, classe
ms.date: 11/04/2016
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
ms.openlocfilehash: 1152d7ed6317b5f1d0c30929cc908266594deb1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143570"
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
|[CInstantaneousTransition, :: CInstantaneousTransition,](#cinstantaneoustransition)|Construit un objet de transition et initialise sa valeur finale.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInstantaneousTransition, :: Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition :: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CInstantaneousTransition, :: m_dblFinalValue](#m_dblfinalvalue)|Valeur de la variable d’animation à la fin de la transition.|

## <a name="remarks"></a>Notes

Pendant une transition instantanée, la valeur de la variable d’animation change instantanément de sa valeur actuelle à une valeur finale spécifiée. La durée de cette transition est toujours égale à zéro. Étant donné que toutes les transitions sont automatiquement désactivées, il est recommandé de les allouer à l’aide de operator new. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController :: AnimateGroup, jusqu’à ce qu’il soit NULL. La modification des variables membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition,](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cinstantaneoustransitioncinstantaneoustransition"></a><a name="cinstantaneoustransition"></a> CInstantaneousTransition, :: CInstantaneousTransition,

Construit un objet de transition et initialise sa valeur finale.

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Paramètres

*dblFinalValue*<br/>
Valeur de la variable d’animation à la fin de la transition.

## <a name="cinstantaneoustransitioncreate"></a><a name="create"></a> CInstantaneousTransition, :: Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers une [interface IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), qui définit une bibliothèque de transitions standard.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la transition est créée avec succès ; Sinon, FALSe.

## <a name="cinstantaneoustransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a> CInstantaneousTransition, :: m_dblFinalValue

Valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
