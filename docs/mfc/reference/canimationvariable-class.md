---
description: 'En savoir plus sur : CAnimationVariable, classe'
title: CAnimationVariable, classe
ms.date: 03/27/2019
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
ms.openlocfilehash: 66f0aacc0338acd4096b4c65cec45489a625910c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207915"
---
# <a name="canimationvariable-class"></a>CAnimationVariable, classe

Représente une variable de l'animation.

## <a name="syntax"></a>Syntaxe

```
class CAnimationVariable;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationVariable :: CAnimationVariable](#canimationvariable)|Construit un objet de variable d’animation.|
|[CAnimationVariable :: ~ CAnimationVariable](#_dtorcanimationvariable)|Destructeur. Appelé lorsqu’un objet CAnimationVariable est détruit.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationVariable :: AddTransition](#addtransition)|Ajoute une transition.|
|[CAnimationVariable :: ApplyTransitions](#applytransitions)|Ajoute des transitions à partir de la liste interne vers le Storyboard.|
|[CAnimationVariable :: ClearTransitions](#cleartransitions)|Efface les transitions.|
|[CAnimationVariable :: Create](#create)|Crée l’objet COM de la variable d’animation sous-jacente.|
|[CAnimationVariable :: CreateTransitions](#createtransitions)|Crée toutes les transitions à appliquer à cette variable d’animation.|
|[CAnimationVariable :: EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Active ou désactive l’événement IntegerValueChanged.|
|[CAnimationVariable :: EnableValueChangedEvent](#enablevaluechangedevent)|Active ou désactive l’événement ValueChanged.|
|[CAnimationVariable :: GetDefaultValue](#getdefaultvalue)|Retourne la valeur par défaut.|
|[CAnimationVariable :: GetParentAnimationObject](#getparentanimationobject)|Retourne l’objet d’animation parent.|
|[CAnimationVariable :: GetValue](#getvalue)|Surchargé. Retourne la valeur actuelle de la variable d’animation.|
|[CAnimationVariable :: GetVariable](#getvariable)|Retourne un pointeur vers un objet COM IUIAnimationVariable.|
|[CAnimationVariable :: SetDefaultValue](#setdefaultvalue)|Définit la valeur par défaut et libère l’objet COM IUIAnimationVariable.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAnimationVariable :: SetParentAnimationObject](#setparentanimationobject)|Définit la relation entre une variable d’animation et un objet d’animation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAnimationVariable :: m_bAutodestroyTransitions](#m_bautodestroytransitions)|Spécifie si les objets de transition associés doivent être supprimés.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAnimationVariable :: m_dblDefaultValue](#m_dbldefaultvalue)|Spécifie la valeur par défaut, qui est propagée à IUIAnimationVariable.|
|[CAnimationVariable :: m_lstTransitions](#m_lsttransitions)|Contient une liste de transitions qui animent cette variable d’animation.|
|[CAnimationVariable :: m_pParentObject](#m_pparentobject)|Pointeur vers un objet d’animation qui encapsule cette variable d’animation.|
|[CAnimationVariable :: m_variable](#m_variable)|Stocke un pointeur vers l’objet COM IUIAnimationVariable. NULL si l’objet COM n’a pas encore été créé, ou si la création a échoué.|

## <a name="remarks"></a>Notes

La classe CAnimationVariable encapsule l’objet COM IUIAnimationVariable. Elle contient également une liste de transitions à appliquer à la variable d’animation dans une table de montage séquentiel. Les objets CAnimationVariable sont incorporés aux objets d’animation, qui peuvent représenter dans une application une valeur animée, un point, une taille, une couleur et un rectangle.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CAnimationVariable`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a> CAnimationVariable :: ~ CAnimationVariable

Destructeur. Appelé lorsqu’un objet CAnimationVariable est détruit.

```
virtual ~CAnimationVariable();
```

## <a name="canimationvariableaddtransition"></a><a name="addtransition"></a> CAnimationVariable :: AddTransition

Ajoute une transition.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Paramètres

*pTransition*<br/>
Pointeur vers une transition à ajouter.

### <a name="remarks"></a>Notes

Cette méthode est appelée pour ajouter une transition à la liste interne des transitions à appliquer à la variable d’animation. Cette liste doit être effacée lorsqu’une animation a été planifiée.

## <a name="canimationvariableapplytransitions"></a><a name="applytransitions"></a> CAnimationVariable :: ApplyTransitions

Ajoute des transitions à partir de la liste interne vers le Storyboard.

```cpp
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Paramètres

*pController*<br/>
Pointeur vers le contrôleur d’animation parent.

*pStoryboard*<br/>
Pointeur vers le Storyboard.

*bDependOnKeyframes*<br/>
TRUE si cette méthode doit ajouter des transitions qui dépendent d’images clés.

### <a name="remarks"></a>Notes

Cette méthode ajoute des transitions à partir de la liste interne vers le Storyboard. Elle est appelée à partir du code de niveau supérieur plusieurs fois pour ajouter des transitions qui ne dépendent pas d’images clés et ajoutent des transitions qui dépendent d’images clés. Si l’objet COM de la variable d’animation sous-jacente n’a pas été créé, cette méthode la crée à ce niveau.

## <a name="canimationvariablecanimationvariable"></a><a name="canimationvariable"></a> CAnimationVariable :: CAnimationVariable

Construit un objet de variable d’animation.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Paramètres

*dblDefaultValue*<br/>
Spécifie la valeur par défaut.

### <a name="remarks"></a>Notes

Construit un objet de variable d’animation et définit sa valeur par défaut. Une valeur par défaut est utilisée lorsqu’une variable n’est pas animée ou ne peut pas être animée.

## <a name="canimationvariablecleartransitions"></a><a name="cleartransitions"></a> CAnimationVariable :: ClearTransitions

Efface les transitions.

```cpp
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Paramètres

*bAutodestroy*<br/>
Spécifie si cette méthode doit supprimer les objets de transition.

### <a name="remarks"></a>Notes

Cette méthode supprime toutes les transitions de la liste interne des transitions. Si bAutodestroy a la valeur TRUE ou que m_bAutodestroyTransitions a la valeur TRUE, les transitions sont supprimées. Dans le cas contraire, l’appelant doit désallouer les objets de transition.

## <a name="canimationvariablecreate"></a><a name="create"></a> CAnimationVariable :: Create

Crée l’objet COM de la variable d’animation sous-jacente.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Paramètres

*pManager*<br/>
Pointeur vers le gestionnaire d’animations.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la variable d’animation a été créée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode crée l’objet COM de la variable d’animation sous-jacente et définit sa valeur par défaut.

## <a name="canimationvariablecreatetransitions"></a><a name="createtransitions"></a> CAnimationVariable :: CreateTransitions

Crée toutes les transitions à appliquer à cette variable d’animation.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Paramètres

*pLibrary*<br/>
Pointeur vers une [interface IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), qui définit une bibliothèque de transitions standard.

### <a name="return-value"></a>Valeur renvoyée

TRUE si les transitions ont été créées avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure quand elle doit créer des transitions qui ont été ajoutées à la liste interne des transitions de la variable.

## <a name="canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a> CAnimationVariable :: EnableIntegerValueChangedEvent

Active ou désactive l’événement IntegerValueChanged.

```cpp
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*pController*<br/>
Pointeur vers le contrôleur parent.

*bEnable*<br/>
Événement TRUE-Enable, FALSe-Disable.

### <a name="remarks"></a>Notes

Lorsque l’événement ValueChanged est activé, l’infrastructure appelle la méthode virtuelle CAnimationController :: OnAnimationIntegerValueChanged. Vous devez la substituer dans une classe dérivée de CAnimationController pour traiter cet événement. Cette méthode est appelée chaque fois que la valeur entière de la variable d’animation est modifiée.

## <a name="canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a> CAnimationVariable :: EnableValueChangedEvent

Active ou désactive l’événement ValueChanged.

```cpp
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*pController*<br/>
Pointeur vers le contrôleur parent.

*bEnable*<br/>
Événement TRUE-Enable, FALSe-Disable.

### <a name="remarks"></a>Notes

Lorsque l’événement ValueChanged est activé, l’infrastructure appelle la méthode virtuelle CAnimationController :: OnAnimationValueChanged. Vous devez la substituer dans une classe dérivée de CAnimationController pour traiter cet événement. Cette méthode est appelée chaque fois que la valeur de la variable d’animation est modifiée.

## <a name="canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationVariable :: GetDefaultValue

Retourne la valeur par défaut.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur par défaut.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour obtenir la valeur par défaut de la variable d’animation. La valeur par défaut peut être définie dans le constructeur ou par la méthode SetDefaultValue.

## <a name="canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a> CAnimationVariable :: GetParentAnimationObject

Retourne l’objet d’animation parent.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet d’animation parent, si la relation a été établie ; sinon, NULL.

### <a name="remarks"></a>Notes

Cette méthode peut être appelée pour récupérer un pointeur vers un objet d’animation parent (un conteneur).

## <a name="canimationvariablegetvalue"></a><a name="getvalue"></a> CAnimationVariable :: GetValue

Retourne la valeur actuelle de la variable d’animation.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>Paramètres

*dblValue*<br/>
Valeur actuelle de la variable d’animation.

*nValeur*<br/>
Valeur actuelle de la variable d’animation.

### <a name="return-value"></a>Valeur renvoyée

S_OK si la valeur a été obtenue avec succès ou si la variable d’animation sous-jacente n’a pas été créée. Sinon, code d’erreur HRESULT.

### <a name="remarks"></a>Notes

Cette méthode peut être appelée pour récupérer la valeur actuelle de la variable d’animation. Si l’objet COM sous-jacent n’a pas été créé, dblValue contient une valeur par défaut, lorsque la fonction est retournée.

## <a name="canimationvariablegetvariable"></a><a name="getvariable"></a> CAnimationVariable :: GetVariable

Retourne un pointeur vers un objet COM IUIAnimationVariable.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur valide vers l’objet COM IUIAnimationVariable, ou valeur NULL si la variable d’animation n’a pas été créée ou ne peut pas être créée.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour accéder à l’objet COM IUIAnimationVariable sous-jacent et appeler ses méthodes directement si nécessaire.

## <a name="canimationvariablem_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a> CAnimationVariable :: m_bAutodestroyTransitions

Spécifie si les objets de transition associés doivent être supprimés.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Notes

Définissez cette valeur sur TRUE pour forcer la suppression des objets de transition lorsqu’ils sont supprimés de la liste interne des transitions. Si cette valeur est FALSe, les transitions doivent être supprimées en appelant l’application. La liste des transitions est toujours effacée après qu’une animation a été planifiée. La valeur par défaut est FALSE.

## <a name="canimationvariablem_dbldefaultvalue"></a><a name="m_dbldefaultvalue"></a> CAnimationVariable :: m_dblDefaultValue

Spécifie la valeur par défaut, qui est propagée à IUIAnimationVariable.

```
DOUBLE m_dblDefaultValue;
```

## <a name="canimationvariablem_lsttransitions"></a><a name="m_lsttransitions"></a> CAnimationVariable :: m_lstTransitions

Contient une liste de transitions qui animent cette variable d’animation.

```
CObList m_lstTransitions;
```

## <a name="canimationvariablem_pparentobject"></a><a name="m_pparentobject"></a> CAnimationVariable :: m_pParentObject

Pointeur vers un objet d’animation qui encapsule cette variable d’animation.

```
CAnimationBaseObject* m_pParentObject;
```

## <a name="canimationvariablem_variable"></a><a name="m_variable"></a> CAnimationVariable :: m_variable

Stocke un pointeur vers l’objet COM IUIAnimationVariable. NULL si l’objet COM n’a pas encore été créé, ou si la création a échoué.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

## <a name="canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationVariable :: SetDefaultValue

Définit la valeur par défaut et libère l’objet COM IUIAnimationVariable.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Paramètres

*dblDefaultValue*<br/>
Spécifie la nouvelle valeur par défaut.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour réinitialiser la valeur par défaut. Cette méthode libère l’objet COM IUIAnimationVariable interne, donc lorsque la variable d’animation est recréée, l’objet COM sous-jacent obtient la nouvelle valeur par défaut. La valeur par défaut est retournée par GetValue si l’objet COM représentant la variable d’animation n’est pas créé, ou si la variable n’a pas été animée.

## <a name="canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a> CAnimationVariable :: SetParentAnimationObject

Définit la relation entre une variable d’animation et un objet d’animation.

```cpp
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Paramètres

*pParentObject*<br/>
Pointeur vers un objet d’animation qui contient cette variable.

### <a name="remarks"></a>Notes

Cette méthode est appelée en interne pour établir une relation un-à-un entre une variable d’animation et un objet d’animation qui l’encapsule.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
