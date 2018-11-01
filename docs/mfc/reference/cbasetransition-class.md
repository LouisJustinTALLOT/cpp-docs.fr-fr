---
title: CBaseTransition, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: b4c15be574700730e847bce06aaa4a6f82aed4b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539124"
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
|[Énumération CBaseTransition::TRANSITION_TYPE](#transition_type_enumeration)|Définit les types de transition actuellement pris en charge par l’implémentation MFC de l’API Windows Animation.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|Construit un objet de base de la transition.|
|[CBaseTransition :: ~ CBaseTransition](#cbasetransition__~cbasetransition)|Destructeur. Appelé lorsqu’un objet de transition est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Ajoute une transition à une table de montage séquentiel.|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Ajoute une transition à une table de montage séquentiel.|
|[CBaseTransition::Clear](#clear)|Les versions d’objet COM IUIAnimationTransition encapsulé.|
|[CBaseTransition::Create](#create)|Crée une transition COM.|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Retourne la première image clé.|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Retourne un pointeur vers la variable connexe.|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Retourne la première image clé.|
|[CBaseTransition::GetTransition](#gettransition)|Surchargé. Retourne un pointeur vers l’objet de transition COM sous-jacent.|
|[CBaseTransition::GetType](#gettype)|Retourne le type de transition.|
|[CBaseTransition::IsAdded](#isadded)|Indique si une transition a été ajoutée à une table de montage séquentiel.|
|[CBaseTransition::SetKeyframes](#setkeyframes)|Définit des images clés pour une transition.|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Établit une relation entre la variable de l’animation et de transition.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|Spécifie si une transition a été ajoutée à une table de montage séquentiel.|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Stocke un pointeur vers l’image clé qui spécifie la fin de la transition.|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Pointeur vers une variable de l’animation, qui est animée avec la transition stockée dans m_transition.|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Stocke un pointeur vers l’image clé qui spécifie le début de la transition.|
|[CBaseTransition::m_transition](#m_transition)|Stocke un pointeur à IUIAnimationTransition. NULL si un objet de transition COM n’a pas été créé.|
|[CBaseTransition::m_type](#m_type)|Stocke le type de transition.|

## <a name="remarks"></a>Notes

Cette classe encapsule l’interface IUIAnimationTransition et sert de classe de base pour toutes les transitions.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="_dtorcbasetransition"></a>  CBaseTransition :: ~ CBaseTransition

Destructeur. Appelé lorsqu’un objet de transition est détruit.

```
virtual ~CBaseTransition();
```

##  <a name="addtostoryboard"></a>  CBaseTransition::AddToStoryboard

Ajoute une transition à une table de montage séquentiel.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers le storyboard qui animera la variable connexe.

### <a name="return-value"></a>Valeur de retour

TRUE si la transition a été ajoutée à une table de montage séquentiel.

### <a name="remarks"></a>Notes

S’applique à la transition à la variable connexe dans le storyboard. S’il s’agit de la première transition appliquée à cette variable dans ce plan conceptuel, la transition commence au début de la table de montage séquentiel. Sinon, la transition est ajoutée à la dernière transition ajoutée à la variable.

##  <a name="addtostoryboardatkeyframes"></a>  CBaseTransition::AddToStoryboardAtKeyframes

Ajoute une transition à une table de montage séquentiel.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers le storyboard qui animera la variable connexe.

### <a name="return-value"></a>Valeur de retour

TRUE si la transition a été ajoutée à une table de montage séquentiel.

### <a name="remarks"></a>Notes

S’applique à la transition à la variable connexe dans le storyboard. Si l’image clé de démarrage a été spécifiée, la transition commence à cette image clé. Si l’image clé de fin a été spécifiée, la transition commence au niveau de l’image clé de démarrage et s’arrête à l’image clé de fin. Si la transition a été créée avec un paramètre de durée spécifié, cette durée est remplacée par la durée écoulée entre les images clés de début et de fin. Si aucune image clé n’a été spécifiée, la transition est ajoutée à la dernière transition ajoutée à la variable.

##  <a name="cbasetransition"></a>  CBaseTransition::CBaseTransition

Construit un objet de base de la transition.

```
CBaseTransition();
```

##  <a name="clear"></a>  CBaseTransition::Clear

Les versions d’objet COM IUIAnimationTransition encapsulé.

```
void Clear();
```

### <a name="remarks"></a>Notes

Cette méthode doit être appelée à partir de la méthode de création d’une classe dérivée afin d’éviter la fuite de l’interface IUITransition.

##  <a name="create"></a>  CBaseTransition::Create

Crée une transition COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers la bibliothèque de transition, ce qui crée des transitions standards. Il peut être NULL pour les transitions personnalisées.

*pFactory*<br/>
Pointeur vers la fabrique de transition, ce qui crée des transitions personnalisées. Il peut être NULL pour les transitions standard.

### <a name="return-value"></a>Valeur de retour

TRUE si un objet COM de la transition a été créé avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Il s’agit d’une fonction virtuelle pure qui doit être substituée dans une classe dérivée. Elle est appelée par l’infrastructure pour instancier l’objet de transition COM sous-jacent.

##  <a name="getendkeyframe"></a>  CBaseTransition::GetEndKeyframe

Retourne la première image clé.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide vers une image clé, ou NULL si une transition ne doit pas être insérée entre les images clés.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour accéder à un objet d’image clé qui a été précédemment défini par SetKeyframes. Elle est appelée par le code de niveau supérieur lorsque les transitions sont ajoutées au storyboard.

##  <a name="getrelatedvariable"></a>  CBaseTransition::GetRelatedVariable

Retourne un pointeur vers la variable connexe.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide à la variable de l’animation, ou NULL si une variable d’animation n’a pas été définie par SetRelatedVariable.

### <a name="remarks"></a>Notes

Il s’agit d’un accesseur à la variable d’animation connexe.

##  <a name="getstartkeyframe"></a>  CBaseTransition::GetStartKeyframe

Retourne la première image clé.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur valide vers une image clé, ou NULL si une transition ne doit pas démarrer après une image clé.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour accéder à un objet d’image clé qui a été précédemment défini par SetKeyframes. Elle est appelée par le code de niveau supérieur lorsque les transitions sont ajoutées au storyboard.

##  <a name="gettransition"></a>  CBaseTransition::GetTransition

Retourne un pointeur vers l’objet de transition COM sous-jacent.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers la bibliothèque de transition, ce qui crée des transitions standards. Il peut être NULL pour les transitions personnalisées.

*pFactory*<br/>
Pointeur vers la fabrique de transition, ce qui crée des transitions personnalisées. Il peut être NULL pour les transitions standard.

### <a name="return-value"></a>Valeur de retour

Un pointeur valide vers IUIAnimationTransition ou NULL si la transition sous-jacente ne peut pas être créé.

### <a name="remarks"></a>Notes

Cette méthode retourne un pointeur vers l’objet de transition COM sous-jacent et il crée si nécessaire.

##  <a name="gettype"></a>  CBaseTransition::GetType

Retourne le type de transition.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Valeur de retour

Un des TRANSITION_TYPE valeurs énumérées.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour identifier un objet de transition par son type. Le type est défini dans un constructeur dans une classe dérivée.

##  <a name="isadded"></a>  CBaseTransition::IsAdded

Indique si une transition a été ajoutée à une table de montage séquentiel.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si une transition a été ajoutée à une table de montage séquentiel, sinon, FALSE.

### <a name="remarks"></a>Notes

Cet indicateur est défini en interne lorsque le code de niveau supérieur ajoute des transitions au storyboard.

##  <a name="m_badded"></a>  CBaseTransition::m_bAdded

Spécifie si une transition a été ajoutée à une table de montage séquentiel.

```
BOOL m_bAdded;
```

##  <a name="m_pendkeyframe"></a>  CBaseTransition::m_pEndKeyframe

Stocke un pointeur vers l’image clé qui spécifie la fin de la transition.

```
CBaseKeyFrame* m_pEndKeyframe;
```

##  <a name="m_prelatedvariable"></a>  CBaseTransition::m_pRelatedVariable

Pointeur vers une variable de l’animation, qui est animée avec la transition stockée dans m_transition.

```
CAnimationVariable* m_pRelatedVariable;
```

##  <a name="m_pstartkeyframe"></a>  CBaseTransition::m_pStartKeyframe

Stocke un pointeur vers l’image clé qui spécifie le début de la transition.

```
CBaseKeyFrame* m_pStartKeyframe;
```

##  <a name="m_transition"></a>  CBaseTransition::m_transition

Stocke un pointeur à IUIAnimationTransition. NULL si un objet de transition COM n’a pas été créé.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

##  <a name="m_type"></a>  CBaseTransition::m_type

Stocke le type de transition.

```
TRANSITION_TYPE m_type;
```

##  <a name="setkeyframes"></a>  CBaseTransition::SetKeyframes

Définit des images clés pour une transition.

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pStart*<br/>
Une image clé qui spécifie le début de la transition.

*mettre en attente*<br/>
Une image clé qui spécifie la fin de la transition.

### <a name="remarks"></a>Notes

Cette méthode indique à la transition pour démarrer après l’image clé spécifiée et, éventuellement, si vous mettre en attente n’est pas NULL, se terminer avant l’image clé spécifiée. Si la transition a été créée avec un paramètre de durée spécifié, cette durée est remplacée par la durée écoulée entre les images clés de début et de fin.

##  <a name="setrelatedvariable"></a>  CBaseTransition::SetRelatedVariable

Établit une relation entre la variable de l’animation et de transition.

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Pointeur vers la variable d’animation connexe.

### <a name="remarks"></a>Notes

Établit une relation entre la variable de l’animation et de transition. Une transition peut être appliquée uniquement à une variable.

##  <a name="transition_type_enumeration"></a>  Énumération CBaseTransition::TRANSITION_TYPE

Définit les types de transition actuellement pris en charge par l’implémentation MFC de l’API Windows Animation.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Notes

Un type de transition est défini dans le constructeur de transition spécifique. Par exemple, CSinusoidalTransitionFromRange définit son type avec la valeur SINUSOIDAL_FROM_RANGE.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
