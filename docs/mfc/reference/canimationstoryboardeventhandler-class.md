---
title: CAnimationStoryboardEventHandler, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
ms.openlocfilehash: 36b8b524591693775403d66fdc1f0754aaf67778
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364999"
---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler, classe

Implémente un rappel, qui est appelé par l'API d'animation lorsque l'état d'un storyboard est modifié ou qu'un storyboard est mis à jour.

## <a name="syntax"></a>Syntaxe

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|Construit un objet `CAnimationStoryboardEventHandler`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Crée un `CAnimationStoryboardEventHandler` exemple de rappel.|
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Gère `OnStoryboardStatusChanged` les événements, qui se produisent lorsque le statut `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`d’un storyboard change (Overrides .)|
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|Gère `OnStoryboardUpdated` les événements, qui se produisent lorsqu’un `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`storyboard est mis à jour (Overrides .)|
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur au contrôleur d’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événement `IUIAnimationStoryboard::SetStoryboardEventHandler` est créé et `CAnimationController::EnableStoryboardEventHandler`passé à la méthode, lorsque vous appelez .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a>CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler

Construit un objet CAnimationStoryboardEventHandler.

```
CAnimationStoryboardEventHandler();
```

## <a name="canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationStoryboardEventHandler::CreateInstance

Crée un exemple de rappel CAnimationStoryboardEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Un pointeur au contrôleur d’animation, qui recevra des événements.

*ppHandler (en)*

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationStoryboardEventHandler::OnStoryboardStatusChanged

Gère les événements OnStoryboardStatusChanged, qui se produisent lorsque le statut d’un storyboard change

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*Storyboard*<br/>
Un pointeur à storyboard dont le statut a changé.

*nouveauStatus*<br/>
Spécifie le nouveau statut de storyboard.

*précédentStatus*<br/>
Spécifie le statut précédent de storyboard.

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode réussit; autrement E_FAIL.

## <a name="canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationStoryboardEventHandler::OnStoryboardUpdated

Gère les événements OnStoryboardUpdated, qui se produisent lorsqu’un storyboard est mis à jour

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>Paramètres

*Storyboard*<br/>
Un pointeur à storyboard, qui a été mis à jour.

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode réussit; autrement E_FAIL.

## <a name="canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationStoryboardEventHandler::SetAnimationController

Stocke un pointeur au contrôleur d’animation pour acheminer les événements.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Un pointeur au contrôleur d’animation, qui recevra des événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
