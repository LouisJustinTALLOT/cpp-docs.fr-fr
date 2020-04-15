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
ms.openlocfilehash: 31c04c303e7e253ec4de41bf076130d19232aac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372269"
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
|[CLinearTransitionDeSpeed::CLinearTransitionDeSpeed](#clineartransitionfromspeed)|Construit un objet de transition à vitesse linéaire et l’initialise avec rapidité et valeur finale.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CLinearTransitionDeSpeed::Créer](#create)|Appelle la bibliothèque de transition pour créer un objet COM de transition encapsulé. (Overrides [CBaseTransition::Créer](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CLinearTransitionDeSpeed::m_dblFinalValue](#m_dblfinalvalue)|La valeur de la variable d’animation à la fin de la transition.|
|[CLinearTransitionDeSpeed::m_dblSpeed](#m_dblspeed)|La valeur absolue de la vitesse de la variable.|

## <a name="remarks"></a>Notes

Lors d’une transition linéaire, la valeur de la variable d’animation change à un rythme spécifié. La durée de la transition est déterminée par la différence entre la valeur initiale et la valeur finale spécifiée. Étant donné que toutes les transitions sont effacées automatiquement, il est recommandé de les répartir à l’aide de l’opérateur nouveau. L’objet IUIAnimationTransition COM encapsulé est créé par CAnimationController::AnimateGroup, jusque-là c’est NULL. Changer les variables des membres après la création de cet objet COM n’a aucun effet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionDeSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="clineartransitionfromspeedclineartransitionfromspeed"></a><a name="clineartransitionfromspeed"></a>CLinearTransitionDeSpeed::CLinearTransitionDeSpeed

Construit un objet de transition à vitesse linéaire et l’initialise avec rapidité et valeur finale.

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Paramètres

*dblSpeed*<br/>
La valeur absolue de la vitesse de la variable.

*dblFinalValue (en)*<br/>
La valeur de la variable d’animation à la fin de la transition.

## <a name="clineartransitionfromspeedcreate"></a><a name="create"></a>CLinearTransitionDeSpeed::Créer

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

## <a name="clineartransitionfromspeedm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CLinearTransitionDeSpeed::m_dblFinalValue

La valeur de la variable d’animation à la fin de la transition.

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionfromspeedm_dblspeed"></a><a name="m_dblspeed"></a>CLinearTransitionDeSpeed::m_dblSpeed

La valeur absolue de la vitesse de la variable.

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
