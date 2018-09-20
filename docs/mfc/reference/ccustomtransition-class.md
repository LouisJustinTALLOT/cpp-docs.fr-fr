---
title: CCustomTransition, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94590b5f14fe8f8be072a1db751129045aaa08e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434854"
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
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Construit un objet de transition personnalisée.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCustomTransition::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Définit une valeur initiale, qui est appliquée à une variable de l’animation associée à cette transition.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Définit une rapidité initiale, qui sera appliquée à une variable d’animation associée à cette transition.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Spécifie si la valeur initiale a été spécifiée avec SetInitialValue.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Spécifie si la rapidité initiale a été spécifiée avec SetInitialVelocity.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Stocke la valeur initiale.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Stocke la rapidité initiale.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Stocke un pointeur à un interpolateur personnalisé.|

## <a name="remarks"></a>Notes

La classe CCustomTransitions permet aux développeurs d’implémenter des transitions personnalisées. Il est créé et utilisé comme une transition standard, mais son constructeur accepte comme paramètre un pointeur vers un interpolateur personnalisé. Procédez comme suit pour utiliser les transitions personnalisées : 1. Dérivez une classe de CCustomInterpolator et implémenter au moins InterpolateValue (méthode). 2. Assurez-vous que la durée de vie d’objet de l’interpolateur personnalisé doit être plus longue que la durée d’animation où il est utilisé. 3. Instancier (utilisation de l’opérateur new) un objet CCustomTransition et passer un pointeur vers l’interpolateur personnalisé dans le constructeur. 4. Appelez CCustomTransition::SetInitialValue et CCustomTransition::SetInitialVelocity si ces paramètres sont requis pour l’interpolation personnalisée. 5. Passer le pointeur à une transition personnalisée à la méthode AddTransition de l’objet d’animation, dont la valeur doit être animée qu’avec l’algorithme personnalisé. 6. Lorsque la valeur de l’objet d’animation doit changer l’API Windows Animation appelle InterpolateValue (et autres méthodes pertinentes) dans CCustomInterpolator.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition

Construit un objet de transition personnalisée.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Paramètres

*pInterpolator*<br/>
Pointeur vers l’interpolateur personnalisé.

##  <a name="create"></a>  CCustomTransition::Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Paramètres

*pFactory*<br/>
Pointeur vers la fabrique de transitions qui est responsable de la création de transitions personnalisées.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Cette méthode peut également définir une valeur initiale et la rapidité initiale à appliquer à une variable de l’animation, qui est associée à cette transition. Pour cela, vous devez appeler SetInitialValue et SetInitialVelocity avant que l’infrastructure crée l’objet COM encapsulé de transition (il se produit lorsque vous appelez CAnimationController::AnimateGroup).

##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified

Spécifie si la valeur initiale a été spécifiée avec SetInitialValue.

```
BOOL m_bInitialValueSpecified;
```

##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified

Spécifie si la rapidité initiale a été spécifiée avec SetInitialVelocity.

```
BOOL m_bInitialVelocitySpecified;
```

##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue

Stocke la valeur initiale.

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity

Stocke la rapidité initiale.

```
DOUBLE m_initialVelocity;
```

##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator

Stocke un pointeur à un interpolateur personnalisé.

```
CCustomInterpolator* m_pInterpolator;
```

##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue

Définit une valeur initiale, qui est appliquée à une variable de l’animation associée à cette transition.

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Paramètres

*initialValue*

##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity

Définit une rapidité initiale, qui sera appliquée à une variable d’animation associée à cette transition.

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Paramètres

*initialVelocity*

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
