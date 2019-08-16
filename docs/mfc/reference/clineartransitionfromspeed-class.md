---
title: CLinearTransitionFromSpeed, classe
ms.date: 11/04/2016
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
ms.openlocfilehash: 50c958a092478f4b9ec4e94f9e5e973a74c334c2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505714"
---
# <a name="clineartransitionfromspeed-class"></a>CLinearTransitionFromSpeed, classe

Encapsule une transition de vitesse linéaire.

## <a name="syntax"></a>Syntaxe

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|Construit un objet de transition à vitesse linéaire et l’initialise avec la vitesse et la valeur finale.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CLinearTransitionFromSpeed::Create](#create)|Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé. (Substitue [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|Valeur de la variable d’animation à la fin de la transition.|
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|Valeur absolue de la rapidité de la variable.|

## <a name="remarks"></a>Notes

Pendant une transition à vitesse linéaire, la valeur de la variable d’animation change à une vitesse spécifiée. La durée de la transition est déterminée par la différence entre la valeur initiale et la valeur finale spécifiée. Étant donné que toutes les transitions sont automatiquement désactivées, il est recommandé de les allouer à l’aide de operator new. L’objet COM IUIAnimationTransition encapsulé est créé par CAnimationController:: AnimateGroup, jusqu’à ce qu’il soit NULL. La modification des variables membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="clineartransitionfromspeed"></a>  CLinearTransitionFromSpeed::CLinearTransitionFromSpeed

Construit un objet de transition à vitesse linéaire et l’initialise avec la vitesse et la valeur finale.

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Paramètres

*dblSpeed*<br/>
Valeur absolue de la rapidité de la variable.

*dblFinalValue*<br/>
Valeur de la variable d’animation à la fin de la transition.

##  <a name="create"></a>  CLinearTransitionFromSpeed::Create

Appelle la bibliothèque de transition pour créer l’objet COM de transition encapsulé.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers une [interface IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), qui définit une bibliothèque de transitions standard.

### <a name="return-value"></a>Valeur de retour

TRUE si la transition est créée avec succès; Sinon, FALSe.

##  <a name="m_dblfinalvalue"></a>  CLinearTransitionFromSpeed::m_dblFinalValue

Valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblspeed"></a>  CLinearTransitionFromSpeed::m_dblSpeed

Valeur absolue de la rapidité de la variable.

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
