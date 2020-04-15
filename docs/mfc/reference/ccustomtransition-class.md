---
title: CCustomTransition, classe
ms.date: 11/04/2016
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
ms.openlocfilehash: 8bdd0ebab0a6e4138e24edff38da9b444745f83a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369329"
---
# <a name="ccustomtransition-class"></a>CCustomTransition, classe

Implémente une transition personnalisée.

## <a name="syntax"></a>Syntaxe

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Construit un objet de transition personnalisé.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCustomTransition::Créer](#create)|Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé. (Overrides [CBaseTransition::Créer](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Définit une valeur initiale, qui sera appliquée à une variable d’animation associée à cette transition.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Définit une vitesse initiale, qui sera appliquée à une variable d’animation associée à cette transition.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Précise si la valeur initiale a été spécifiée avec SetInitialValue.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Précise si la vitesse initiale a été spécifiée avec SetInitialVelocity.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Stocke la valeur initiale.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Stocke la vitesse initiale.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Stocke un pointeur vers un interpolateur personnalisé.|

## <a name="remarks"></a>Notes

La classe CCustomTransitions permet aux développeurs de mettre en œuvre des transitions personnalisées. Il est créé et utilisé comme une transition standard, mais son constructeur accepte comme paramètre un pointeur à un interpolateur personnalisé. Effectuez les étapes suivantes pour utiliser les transitions personnalisées : 1. Dérivez une classe de CCustomInterpolator et implémenter au moins la méthode InterpolateValue. 2. Assurez-vous que la durée de vie de l’objet d’interpolateur personnalisé doit être plus longue que la durée de l’animation où il est utilisé. 3. Instantané (à l’aide de l’opérateur nouveau) un objet CCustomTransition et passez un pointeur à l’interpolateur personnalisé dans le constructeur. 4. Appelez CCustomTransition::SetInitialValue et CCustomTransition::SetInitialVelocity si ces paramètres sont nécessaires pour l’interpolation personnalisée. 5. Passez le pointeur à la transition personnalisée vers la méthode AddTransition de l’objet d’animation, dont la valeur doit être animée avec l’algorithme personnalisé. 6. Lorsque la valeur de l’objet d’animation doit changer Windows Animation API appelle InterpolateValue (et d’autres méthodes pertinentes) dans CCustomInterpolator.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a>CCustomTransition::CCustomTransition

Construit un objet de transition personnalisé.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Paramètres

*pInterpolator (en)*<br/>
Un pointeur à l’interpolateur personnalisé.

## <a name="ccustomtransitioncreate"></a><a name="create"></a>CCustomTransition::Créer

Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Paramètres

*pFactory*<br/>
Un pointeur à l’usine de transition, qui est responsable de la création de transitions personnalisées.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Cette méthode peut également définir la valeur initiale et la vitesse initiale à appliquer à une variable d’animation, qui est associée à cette transition. À cette fin, vous devez appeler SetInitialValue et SetInitialVelocity avant que le cadre ne crée l’objet COM de transition encapsulé (il arrive lorsque vous appelez CAnimationController::AnimateGroup).

## <a name="ccustomtransitionm_binitialvaluespecified"></a><a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified

Précise si la valeur initiale a été spécifiée avec SetInitialValue.

```
BOOL m_bInitialValueSpecified;
```

## <a name="ccustomtransitionm_binitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified

Précise si la vitesse initiale a été spécifiée avec SetInitialVelocity.

```
BOOL m_bInitialVelocitySpecified;
```

## <a name="ccustomtransitionm_initialvalue"></a><a name="m_initialvalue"></a>CCustomTransition::m_initialValue

Stocke la valeur initiale.

```
DOUBLE m_initialValue;
```

## <a name="ccustomtransitionm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity

Stocke la vitesse initiale.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustomtransitionm_pinterpolator"></a><a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator

Stocke un pointeur vers un interpolateur personnalisé.

```
CCustomInterpolator* m_pInterpolator;
```

## <a name="ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a>CCustomTransition::SetInitialValue

Définit une valeur initiale, qui sera appliquée à une variable d’animation associée à cette transition.

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Paramètres

*initialValue*

## <a name="ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity

Définit une vitesse initiale, qui sera appliquée à une variable d’animation associée à cette transition.

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Paramètres

*initialVelocity*

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
