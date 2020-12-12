---
description: 'En savoir plus sur : classe CBaseTransition'
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
ms.openlocfilehash: 16a7b5e7f88e292fd2b771c627f7169c70fec2c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122822"
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
|[CBaseTransition :: TRANSITION_TYPE, énumération](#transition_type_enumeration)|Définit les types de transition actuellement pris en charge par l’implémentation MFC de l’API d’animation Windows.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBaseTransition :: CBaseTransition](#cbasetransition)|Construit un objet de transition de base.|
|[CBaseTransition :: ~ CBaseTransition](#_dtorcbasetransition)|Destructeur. Appelé lorsqu’un objet de transition est en cours de destruction.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBaseTransition :: AddToStoryboard](#addtostoryboard)|Ajoute une transition à une table de montage séquentiel.|
|[CBaseTransition :: AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Ajoute une transition à une table de montage séquentiel.|
|[CBaseTransition :: Clear](#clear)|Libère l’objet COM IUIAnimationTransition encapsulé.|
|[CBaseTransition :: Create](#create)|Crée une transition COM.|
|[CBaseTransition :: GetEndKeyframe](#getendkeyframe)|Retourne une image clé de début.|
|[CBaseTransition :: GetRelatedVariable](#getrelatedvariable)|Retourne un pointeur vers une variable associée.|
|[CBaseTransition :: GetStartKeyframe](#getstartkeyframe)|Retourne une image clé de début.|
|[CBaseTransition :: GetTransition](#gettransition)|Surchargé. Retourne un pointeur vers l’objet de transition COM sous-jacent.|
|[CBaseTransition :: GetType](#gettype)|Retourne le type de transition.|
|[CBaseTransition :: IsAdded](#isadded)|Indique si une transition a été ajoutée à une table de montage séquentiel.|
|[CBaseTransition :: SetKeyframes](#setkeyframes)|Définit les images clés pour une transition.|
|[CBaseTransition :: SetRelatedVariable](#setrelatedvariable)|Établit une relation entre une variable d’animation et une transition.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CBaseTransition :: m_bAdded](#m_badded)|Spécifie si une transition a été ajoutée à une table de montage séquentiel.|
|[CBaseTransition :: m_pEndKeyframe](#m_pendkeyframe)|Stocke un pointeur vers l’image clé qui spécifie la fin de la transition.|
|[CBaseTransition :: m_pRelatedVariable](#m_prelatedvariable)|Pointeur vers une variable d’animation, qui est animée avec la transition stockée dans m_transition.|
|[CBaseTransition :: m_pStartKeyframe](#m_pstartkeyframe)|Stocke un pointeur vers l’image clé qui spécifie le début de la transition.|
|[CBaseTransition :: m_transition](#m_transition)|Stocke un pointeur vers IUIAnimationTransition. NULL si aucun objet de transition COM n’a été créé.|
|[CBaseTransition :: m_type](#m_type)|Stocke le type de transition.|

## <a name="remarks"></a>Notes

Cette classe encapsule l’interface IUIAnimationTransition et sert de classe de base pour toutes les transitions.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a> CBaseTransition :: ~ CBaseTransition

Destructeur. Appelé lorsqu’un objet de transition est en cours de destruction.

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a> CBaseTransition :: AddToStoryboard

Ajoute une transition à une table de montage séquentiel.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers le Storyboard, qui animera la variable associée.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la transition a été correctement ajoutée à une table de montage séquentiel.

### <a name="remarks"></a>Notes

Applique la transition à la variable associée dans le Storyboard. S’il s’agit de la première transition appliquée à cette variable dans cette table de montage séquentiel, la transition commence au début de la table de montage séquentiel. Dans le cas contraire, la transition est ajoutée à la transition ajoutée la plus récente à la variable.

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a> CBaseTransition :: AddToStoryboardAtKeyframes

Ajoute une transition à une table de montage séquentiel.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Paramètres

*pStoryboard*<br/>
Pointeur vers le Storyboard, qui animera la variable associée.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la transition a été correctement ajoutée à une table de montage séquentiel.

### <a name="remarks"></a>Notes

Applique la transition à la variable associée dans le Storyboard. Si l’image clé de début a été spécifiée, la transition commence à cette image clé. Si l’image clé de fin a été spécifiée, la transition commence au niveau de l’image clé de début et s’arrête à la fin de l’image clé. Si la transition a été créée avec un paramètre Duration spécifié, cette durée est remplacée par la durée écoulée entre les images clés Start et end. Si aucune image clé n’a été spécifiée, la transition est ajoutée à la transition ajoutée la plus récente à la variable.

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a> CBaseTransition :: CBaseTransition

Construit un objet de transition de base.

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a> CBaseTransition :: Clear

Libère l’objet COM IUIAnimationTransition encapsulé.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

Cette méthode doit être appelée à partir de la méthode Create d’une classe dérivée afin d’éviter la fuite de l’interface IUITransition.

## <a name="cbasetransitioncreate"></a><a name="create"></a> CBaseTransition :: Create

Crée une transition COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers la bibliothèque de transition qui crée des transitions standard. Elle peut avoir la valeur NULL pour les transitions personnalisées.

*pFactory*<br/>
Pointeur vers la fabrique de transition, qui crée des transitions personnalisées. Elle peut avoir la valeur NULL pour les transitions standard.

### <a name="return-value"></a>Valeur renvoyée

TRUE si un objet COM de transition a été créé avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Il s’agit d’une fonction virtuelle pure qui doit être substituée dans une classe dérivée. Elle est appelée par l’infrastructure pour instancier l’objet de transition COM sous-jacent.

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a> CBaseTransition :: GetEndKeyframe

Retourne une image clé de début.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur valide vers une image clé, ou NULL si une transition ne doit pas être insérée entre les images clés.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour accéder à un objet KeyFrame qui a été précédemment défini par SetKeyframes. Elle est appelée par du code de niveau supérieur lorsque des transitions sont ajoutées à la table de montage séquentiel.

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a> CBaseTransition :: GetRelatedVariable

Retourne un pointeur vers une variable associée.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur valide vers une variable d’animation, ou NULL si une variable d’animation n’a pas été définie par SetRelatedVariable.

### <a name="remarks"></a>Notes

Il s’agit d’un accesseur à la variable d’animation associée.

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a> CBaseTransition :: GetStartKeyframe

Retourne une image clé de début.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur valide vers une image clé, ou NULL si une transition ne doit pas démarrer après une image clé.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour accéder à un objet KeyFrame qui a été précédemment défini par SetKeyframes. Elle est appelée par du code de niveau supérieur lorsque des transitions sont ajoutées à la table de montage séquentiel.

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a> CBaseTransition :: GetTransition

Retourne un pointeur vers l’objet de transition COM sous-jacent.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers la bibliothèque de transition qui crée des transitions standard. Elle peut avoir la valeur NULL pour les transitions personnalisées.

*pFactory*<br/>
Pointeur vers la fabrique de transition, qui crée des transitions personnalisées. Elle peut avoir la valeur NULL pour les transitions standard.

### <a name="return-value"></a>Valeur renvoyée

Pointeur valide vers IUIAnimationTransition ou NULL si la transition sous-jacente ne peut pas être créée.

### <a name="remarks"></a>Notes

Cette méthode retourne un pointeur vers l’objet de transition COM sous-jacent et le crée si nécessaire.

## <a name="cbasetransitiongettype"></a><a name="gettype"></a> CBaseTransition :: GetType

Retourne le type de transition.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’une des TRANSITION_TYPE des valeurs énumérées.

### <a name="remarks"></a>Notes

Cette méthode peut être utilisée pour identifier un objet de transition par son type. Le type est défini dans un constructeur dans une classe dérivée.

## <a name="cbasetransitionisadded"></a><a name="isadded"></a> CBaseTransition :: IsAdded

Indique si une transition a été ajoutée à une table de montage séquentiel.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si une transition a été ajoutée à une table de montage séquentiel, sinon FALSe.

### <a name="remarks"></a>Notes

Cet indicateur est défini en interne quand le code de niveau supérieur ajoute des transitions à la table de montage séquentiel.

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a> CBaseTransition :: m_bAdded

Spécifie si une transition a été ajoutée à une table de montage séquentiel.

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a> CBaseTransition :: m_pEndKeyframe

Stocke un pointeur vers l’image clé qui spécifie la fin de la transition.

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a> CBaseTransition :: m_pRelatedVariable

Pointeur vers une variable d’animation, qui est animée avec la transition stockée dans m_transition.

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a> CBaseTransition :: m_pStartKeyframe

Stocke un pointeur vers l’image clé qui spécifie le début de la transition.

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a> CBaseTransition :: m_transition

Stocke un pointeur vers IUIAnimationTransition. NULL si aucun objet de transition COM n’a été créé.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a> CBaseTransition :: m_type

Stocke le type de transition.

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a> CBaseTransition :: SetKeyframes

Définit les images clés pour une transition.

```cpp
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pStart*<br/>
Image clé qui spécifie le début de la transition.

*Attente*<br/>
Image clé qui spécifie la fin de la transition.

### <a name="remarks"></a>Notes

Cette méthode indique à la transition de démarrer après l’image clé spécifiée et, éventuellement, si l’attente n’est pas NULL, se termine avant l’image clé spécifiée. Si la transition a été créée avec un paramètre Duration spécifié, cette durée est remplacée par la durée écoulée entre les images clés Start et end.

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a> CBaseTransition :: SetRelatedVariable

Établit une relation entre une variable d’animation et une transition.

```cpp
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Paramètres

*pVariable*<br/>
Pointeur vers une variable d’animation associée.

### <a name="remarks"></a>Notes

Établit une relation entre une variable d’animation et une transition. Une transition ne peut être appliquée qu’à une seule variable.

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a> CBaseTransition :: TRANSITION_TYPE, énumération

Définit les types de transition actuellement pris en charge par l’implémentation MFC de l’API d’animation Windows.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Notes

Un type de transition est défini dans le constructeur d’une transition spécifique. Par exemple, CSinusoidalTransitionFromRange, définit son type sur SINUSOIDAL_FROM_RANGE.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
