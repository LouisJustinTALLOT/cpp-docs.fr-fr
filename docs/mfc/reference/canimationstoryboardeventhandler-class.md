---
description: 'En savoir plus sur : classe CAnimationStoryboardEventHandler,'
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
ms.openlocfilehash: 7208ba91ec78a6de688699183b55a691b8e3d28d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254740"
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
|[CAnimationStoryboardEventHandler, :: CAnimationStoryboardEventHandler,](#canimationstoryboardeventhandler)|Construit un objet `CAnimationStoryboardEventHandler`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationStoryboardEventHandler, :: CreateInstance](#createinstance)|Crée une instance de `CAnimationStoryboardEventHandler` callback.|
|[CAnimationStoryboardEventHandler, :: OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Gère `OnStoryboardStatusChanged` les événements qui se produisent quand l’état d’un Storyboard change (Substitue `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged` ).|
|[CAnimationStoryboardEventHandler, :: OnStoryboardUpdated](#onstoryboardupdated)|Gère `OnStoryboardUpdated` les événements qui se produisent lorsqu’une table de montage séquentiel est mise à jour (Substitue `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated` ).|
|[CAnimationStoryboardEventHandler, :: SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur d’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événements est créé et passé à la `IUIAnimationStoryboard::SetStoryboardEventHandler` méthode quand vous appelez `CAnimationController::EnableStoryboardEventHandler` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a> CAnimationStoryboardEventHandler, :: CAnimationStoryboardEventHandler,

Construit un objet CAnimationStoryboardEventHandler,.

```
CAnimationStoryboardEventHandler();
```

## <a name="canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a> CAnimationStoryboardEventHandler, :: CreateInstance

Crée une instance de rappel CAnimationStoryboardEventHandler,.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur d’animation, qui reçoit les événements.

*ppHandler*

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a> CAnimationStoryboardEventHandler, :: OnStoryboardStatusChanged

Gère les événements OnStoryboardStatusChanged, qui se produisent quand l’état d’un Storyboard change

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*s*<br/>
Pointeur vers le Storyboard dont l’État a changé.

*newStatus*<br/>
Spécifie le nouvel état de la table de montage séquentiel.

*previousStatus*<br/>
Spécifie l’état précédent de la table de montage séquentiel.

### <a name="return-value"></a>Valeur renvoyée

S_OK si la méthode est réussie ; sinon E_FAIL.

## <a name="canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a> CAnimationStoryboardEventHandler, :: OnStoryboardUpdated

Gère les événements OnStoryboardUpdated, qui se produisent lorsqu’une table de montage séquentiel est mise à jour

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>Paramètres

*s*<br/>
Pointeur vers le Storyboard, qui a été mis à jour.

### <a name="return-value"></a>Valeur renvoyée

S_OK si la méthode est réussie ; sinon E_FAIL.

## <a name="canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a> CAnimationStoryboardEventHandler, :: SetAnimationController

Stocke un pointeur vers le contrôleur d’animation pour acheminer les événements.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur d’animation, qui reçoit les événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
