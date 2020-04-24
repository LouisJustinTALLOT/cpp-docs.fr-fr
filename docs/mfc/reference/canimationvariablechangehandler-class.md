---
title: CAnimationVariableChangeHandler, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 2dc8f2c03f9df34012fb9db1ed5e5b0bb448b17f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755043"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler, classe

Implémente un rappel, qui est appelé par l'API d'animation lorsque la valeur d'une variable de l'animation est modifiée.

## <a name="syntax"></a>Syntaxe

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Construit un objet `CAnimationVariableChangeHandler`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|Crée une `CAnimationVariableChangeHandler` instance d’objet.|
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Appelé quand une valeur d’une variable d’animation a changé. (Substitue `CUIAnimationVariableChangeHandlerBase::OnValueChanged`.)|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur au contrôleur d’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événements `IUIAnimationVariable::SetVariableChangeHandler` est créé et `CAnimationVariable::EnableValueChangedEvent` `CAnimationBaseObject::EnableValueChangedEvent` transmis à la méthode, lorsque vous appelez ou (ce qui permet cet événement pour toutes les variables d’animation encapsulées dans un objet d’animation).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationvariablechangehandleronvaluechanged"></a><a name="onvaluechanged"></a>CAnimationVariableChangeHandler::OnValueChanged

Appelé quand une valeur d’une variable d’animation a changé.

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>Paramètres

*Storyboard*<br/>
Le storyboard qui anime la variable.

*Variable*<br/>
La variable d’animation qui a été mise à jour.

*newValue*<br/>
Nouvelle valeur.

*previousValue (en)*<br/>
Valeur précédente.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="canimationvariablechangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationVariableChangeHandler::SetAnimationController

Stocke un pointeur au contrôleur d’animation pour acheminer les événements.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Un pointeur au contrôleur d’animation, qui recevra des événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
