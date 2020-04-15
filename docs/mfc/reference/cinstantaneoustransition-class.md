---
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
ms.openlocfilehash: 15c471d64309cc1358c9c5b0b33577261dd877f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372441"
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
|[CInstantaneousTransition::Créer](#create)|Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé. (Overrides [CBaseTransition::Créer](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable d’animation à la fin de la transition.|

## <a name="remarks"></a>Notes

Au cours d’une transition instantanée, la valeur de la variable d’animation change instantanément de sa valeur actuelle à une valeur finale spécifiée. La durée de cette transition est toujours nulle. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les répartir à l’aide de l’opérateur nouveau. L’objet IUIAnimationTransition COM encapsulé est créé par CAnimationController::AnimateGroup, jusque-là c’est NULL. Changer les variables des membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cinstantaneoustransitioncinstantaneoustransition"></a><a name="cinstantaneoustransition"></a>CInstantaneousTransition::CInstantaneousTransition

Construit un objet de transition et initialise sa valeur finale.

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Paramètres

*dblFinalValue (en)*<br/>
La valeur de la variable d’animation à la fin de la transition.

## <a name="cinstantaneoustransitioncreate"></a><a name="create"></a>CInstantaneousTransition::Créer

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

## <a name="cinstantaneoustransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CInstantaneousTransition::m_dblFinalValue

La valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
