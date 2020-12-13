---
description: 'En savoir plus sur : classe CAnimationVariableIntegerChangeHandler,'
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
ms.openlocfilehash: 53a0a1838e021294b4ccc870e6f01b873233a0c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336735"
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
|[CAnimationVariableIntegerChangeHandler, :: CAnimationVariableIntegerChangeHandler,](#canimationvariableintegerchangehandler)|Construit un objet `CAnimationVariableIntegerChangeHandler`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler, :: CreateInstance](#createinstance)|Crée une instance de `CAnimationVariableIntegerChangeHandler` callback.|
|[CAnimationVariableIntegerChangeHandler, :: OnIntegerValueChanged](#onintegervaluechanged)|Appelée lorsqu’une valeur d’une variable d’animation a été modifiée. (Substitue `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`.)|
|[CAnimationVariableIntegerChangeHandler, :: SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur d’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événements est créé et passé à la méthode IUIAnimationVariable :: SetVariableIntegerChangeHandler, quand vous appelez CAnimationVariable :: EnableIntegerValueChangedEvent ou CAnimationBaseObject, :: EnableIntegerValueChangedEvent (ce qui active cet événement pour toutes les variables d’animation encapsulées dans un objet d’animation).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[Classes MFC](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationvariableintegerchangehandlercanimationvariableintegerchangehandler"></a><a name="canimationvariableintegerchangehandler"></a> CAnimationVariableIntegerChangeHandler, :: CAnimationVariableIntegerChangeHandler,

Construit un objet CAnimationVariableIntegerChangeHandler,.

```
CAnimationVariableIntegerChangeHandler ();
```

## <a name="canimationvariableintegerchangehandlercreateinstance"></a><a name="createinstance"></a> CAnimationVariableIntegerChangeHandler, :: CreateInstance

Crée une instance de rappel CAnimationVariableIntegerChangeHandler,.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur d’animation, qui reçoit les événements.

*ppHandler*

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="canimationvariableintegerchangehandleronintegervaluechanged"></a><a name="onintegervaluechanged"></a> CAnimationVariableIntegerChangeHandler, :: OnIntegerValueChanged

Appelée lorsqu’une valeur d’une variable d’animation a été modifiée.

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>Paramètres

*s*<br/>
Le Storyboard qui anime la variable.

*variable*<br/>
Variable d’animation qui a été mise à jour.

*newValue*<br/>
Nouvelle valeur arrondie.

*previousValue*<br/>
Valeur arrondie précédente.

### <a name="return-value"></a>Valeur renvoyée

S_OK si la méthode est réussie ; sinon E_FAIL.

## <a name="canimationvariableintegerchangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a> CAnimationVariableIntegerChangeHandler, :: SetAnimationController

Stocke un pointeur vers le contrôleur d’animation pour acheminer les événements.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur d’animation, qui reçoit les événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
