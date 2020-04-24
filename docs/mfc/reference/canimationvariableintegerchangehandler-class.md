---
title: CAnimationVariableIntegerChangeHandler, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
ms.openlocfilehash: dec940d2f5e68f0531fc917df447b5a1a5cb8189
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755055"
---
# <a name="canimationvariableintegerchangehandler-class"></a>CAnimationVariableIntegerChangeHandler, classe

Implémente un rappel, qui est appelé par l'API d'animation lorsque la valeur d'une variable de l'animation est modifiée.

## <a name="syntax"></a>Syntaxe

```
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|Construit un objet `CAnimationVariableIntegerChangeHandler`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CreateInstance](#createinstance)|Crée un `CAnimationVariableIntegerChangeHandler` exemple de rappel.|
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|Appelé quand une valeur d’une variable d’animation a changé. (Substitue `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`.)|
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur au contrôleur d’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événement est créé et transmis à IUIAnimationVariable::SetVariableIntegerChangeHandler méthode, lorsque vous appelez CAnimationVariable::EnableIntegerValueChangedEvent ou CAnimationBaseObject::EnableIntegerValueChangedEvent (qui permet cet événement pour toutes les variables d’animation encapsulées dans un objet d’animation).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[Classes MFC](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationvariableintegerchangehandlercanimationvariableintegerchangehandler"></a><a name="canimationvariableintegerchangehandler"></a>CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler

Construit un objet CAnimationVariableIntegerChangeHandler.

```
CAnimationVariableIntegerChangeHandler ();
```

## <a name="canimationvariableintegerchangehandlercreateinstance"></a><a name="createinstance"></a>CAnimationVariableIntegerChangeHandler::CreateInstance

Crée un exemple de rappel CAnimationVariableIntegerChangeHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Un pointeur au contrôleur d’animation, qui recevra des événements.

*ppHandler (en)*

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="canimationvariableintegerchangehandleronintegervaluechanged"></a><a name="onintegervaluechanged"></a>CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged

Appelé quand une valeur d’une variable d’animation a changé.

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>Paramètres

*Storyboard*<br/>
Le storyboard qui anime la variable.

*Variable*<br/>
La variable d’animation qui a été mise à jour.

*newValue*<br/>
La nouvelle valeur arrondie.

*previousValue (en)*<br/>
La valeur arrondie précédente.

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode réussit; autrement E_FAIL.

## <a name="canimationvariableintegerchangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationVariableIntegerChangeHandler::SetAnimationController

Stocke un pointeur au contrôleur d’animation pour acheminer les événements.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Un pointeur au contrôleur d’animation, qui recevra des événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
