---
title: CBaseTransition, classe
ms.date: 03/27/2019
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
ms.openlocfilehash: 9abe4ae55d9d84ea435cd5d82925ff8b8a544480
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752960"
---
# <a name="cbasetransition-class"></a>CBaseTransition, classe

Représente une transition de base.

## <a name="syntax"></a>Syntaxe

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>Membres

### <a name="public-enumerations"></a>Énumérations publiques

|Nom|Description|
|----------|-----------------|
|[CBaseTransition::TRANSITION_TYPE Énumération](#transition_type_enumeration)|Définit les types de transition actuellement pris en charge par la mise en œuvre MFC de Windows Animation API.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|Construit un objet de transition de base.|
|[CBaseTransition::CBaseTransition](#_dtorcbasetransition)|Destructeur. Appelé quand un objet de transition est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Ajoute une transition à un storyboard.|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Ajoute une transition à un storyboard.|
|[CBaseTransition::Clair](#clear)|Communiqués encapsulé IUIAnimationTransition COM objet.|
|[CBaseTransition::Créer](#create)|Crée une transition COM.|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Les retours commencent le cadre clé.|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Retourne un pointeur à la variable connexe.|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Les retours commencent le cadre clé.|
|[CBaseTransition::GetTransition](#gettransition)|Surchargé. Retourne un pointeur vers un objet de transition COM sous-jacent.|
|[CBaseTransition::GetType](#gettype)|Retourne le type de transition.|
|[CBaseTransition::IsAdded](#isadded)|Raconte si une transition a été ajoutée à un storyboard.|
|[CBaseTransition::SetKeyframes](#setkeyframes)|Définit les cadres clés pour une transition.|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Établit une relation entre la variable d’animation et la transition.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|Précise si une transition a été ajoutée à un storyboard.|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Stocke un pointeur sur le cadre clé qui spécifie la fin de la transition.|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Un pointeur vers une variable d’animation, qui est animée par la transition stockée dans m_transition.|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Stocke un pointeur sur le cadre clé qui spécifie le début de la transition.|
|[CBaseTransition::m_transition](#m_transition)|Stocke un pointeur à IUIAnimationTransition. NULL si un objet de transition COM n’a pas été créé.|
|[CBaseTransition::m_type](#m_type)|Stocke le type de transition.|

## <a name="remarks"></a>Notes

Cette classe résume l’interface IUIAnimationTransition et sert de classe de base pour toutes les transitions.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a>CBaseTransition::CBaseTransition

Destructeur. Appelé quand un objet de transition est détruit.

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseTransition::AddToStoryboard

Ajoute une transition à un storyboard.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur à storyboard, qui animera la variable connexe.

### <a name="return-value"></a>Valeur de retour

VRAI, si la transition a été ajoutée avec succès à un storyboard.

### <a name="remarks"></a>Notes

Applique la transition à la variable connexe dans le storyboard. S’il s’agit de la première transition appliquée à cette variable dans ce storyboard, la transition commence au début du storyboard. Dans le cas contraire, la transition est annexée à la transition ajoutée plus récemment à la variable.

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes

Ajoute une transition à un storyboard.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*pStoryboard (en)*<br/>
Un pointeur à storyboard, qui animera la variable connexe.

### <a name="return-value"></a>Valeur de retour

VRAI, si la transition a été ajoutée avec succès à un storyboard.

### <a name="remarks"></a>Notes

Applique la transition à la variable connexe dans le storyboard. Si le cadre de départ a été spécifié, la transition commence à ce cadre clé. Si le cadre de la clé de fin a été spécifié, la transition commence à la clé de départ et s’arrête à la clé de fin. Si la transition a été créée avec un paramètre de durée spécifié, cette durée est dépassée avec la durée entre les cadres clés de départ et de fin. Si aucun cadre clé n’a été spécifié, la transition est annexée à la transition ajoutée plus récemment à la variable.

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a>CBaseTransition::CBaseTransition

Construit un objet de transition de base.

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a>CBaseTransition::Clair

Communiqués encapsulé IUIAnimationTransition COM objet.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

Cette méthode doit être appelée à partir de la méthode Créer d’une classe dérivée afin d’éviter la fuite d’interface IUITransition.

## <a name="cbasetransitioncreate"></a><a name="create"></a>CBaseTransition::Créer

Crée une transition COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Paramètres

*pLibraire*<br/>
Un pointeur vers la bibliothèque de transition, qui crée des transitions standard. Il peut être NULL pour les transitions personnalisées.

*pFactory*<br/>
Un pointeur à l’usine de transition, qui crée des transitions personnalisées. Il peut être NULL pour les transitions standard.

### <a name="return-value"></a>Valeur de retour

VRAI si un objet COM de transition a été créé avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Il s’agit d’une fonction virtuelle pure qui doit être remplacée dans une classe dérivée. Il est appelé par le cadre pour instantanéer l’objet de transition COM sous-jacent.

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe

Les retours commencent le cadre clé.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide à un cadre clé, ou NULL si une transition ne doit pas être insérée entre les cadres clés.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour accéder à un objet keyframe qui a été précédemment défini par SetKeyframes. C’est ce qu’on appelle le code de haut niveau lorsque des transitions sont ajoutées au storyboard.

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable

Retourne un pointeur à la variable connexe.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide à la variable d’animation, ou NULL si une variable d’animation n’a pas été définie par SetRelatedVariable.

### <a name="remarks"></a>Notes

Il s’agit d’un accessoir-accédant à la variable d’animation connexe.

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe

Les retours commencent le cadre clé.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide à un cadre clé, ou NULL si une transition ne doit pas commencer après un cadre clé.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour accéder à un objet keyframe qui a été précédemment défini par SetKeyframes. C’est ce qu’on appelle le code de haut niveau lorsque des transitions sont ajoutées au storyboard.

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a>CBaseTransition::GetTransition

Retourne un pointeur vers un objet de transition COM sous-jacent.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Paramètres

*pLibraire*<br/>
Un pointeur vers la bibliothèque de transition, qui crée des transitions standard. Il peut être NULL pour les transitions personnalisées.

*pFactory*<br/>
Un pointeur à l’usine de transition, qui crée des transitions personnalisées. Il peut être NULL pour les transitions standard.

### <a name="return-value"></a>Valeur de retour

Un pointeur valide à IUIAnimationTransition ou NULL si la transition sous-jacente ne peut pas être créée.

### <a name="remarks"></a>Notes

Cette méthode renvoie un pointeur à l’objet de transition COM sous-jacent et le crée si nécessaire.

## <a name="cbasetransitiongettype"></a><a name="gettype"></a>CBaseTransition::GetType

Retourne le type de transition.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Valeur de retour

Une des valeurs TRANSITION_TYPE énumérées.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour identifier un objet de transition par son type. Le type est placé dans un constructeur dans une classe dérivée.

## <a name="cbasetransitionisadded"></a><a name="isadded"></a>CBaseTransition::IsAdded

Raconte si une transition a été ajoutée à un storyboard.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si une transition a été ajoutée à un storyboard, sinon FALSE.

### <a name="remarks"></a>Notes

Ce drapeau est défini en interne lorsque le code de haut niveau ajoute des transitions au storyboard.

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a>CBaseTransition::m_bAdded

Précise si une transition a été ajoutée à un storyboard.

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe

Stocke un pointeur sur le cadre clé qui spécifie la fin de la transition.

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable

Un pointeur vers une variable d’animation, qui est animée par la transition stockée dans m_transition.

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe

Stocke un pointeur sur le cadre clé qui spécifie le début de la transition.

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a>CBaseTransition::m_transition

Stocke un pointeur à IUIAnimationTransition. NULL si un objet de transition COM n’a pas été créé.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a>CBaseTransition::m_type

Stocke le type de transition.

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a>CBaseTransition::SetKeyframes

Définit les cadres clés pour une transition.

```cpp
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Paramètres

*Pstart*<br/>
Un cadre clé qui spécifie le début de la transition.

*pEnd (en)*<br/>
Un cadre clé qui spécifie la fin de la transition.

### <a name="remarks"></a>Notes

Cette méthode indique que la transition commence après un cadre clé spécifié et, en option, si le pEnd n’est pas NULL, se termine avant le cadre de clé spécifié. Si la transition a été créée avec un paramètre de durée spécifié, cette durée est dépassée avec la durée entre les cadres clés de départ et de fin.

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable

Établit une relation entre la variable d’animation et la transition.

```cpp
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Un pointeur à la variable d’animation connexe.

### <a name="remarks"></a>Notes

Établit une relation entre la variable d’animation et la transition. Une transition ne peut être appliquée qu’à une seule variable.

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE Énumération

Définit les types de transition actuellement pris en charge par la mise en œuvre MFC de Windows Animation API.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Notes

Un type de transition est placé dans le constructeur d’une transition spécifique. Par exemple, CSinusoidalTransitionFromRange définit son type pour SINUSOIDAL_FROM_RANGE.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
