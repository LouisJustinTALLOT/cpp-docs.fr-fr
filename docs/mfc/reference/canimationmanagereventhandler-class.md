---
title: CAnimationManagerEventHandler, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
ms.openlocfilehash: bd13ba4d0dd60f65372b2c1f51d70d338566301e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916257"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler, classe

Implémente un rappel, qui est appelé par l'API d'animation lorsque l'état d'un gestionnaire d'animation est modifié.

## <a name="syntax"></a>Syntaxe

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|Construit un objet `CAnimationManagerEventHandler`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|Crée une instance de `CAnimationManagerEventHandler` l’objet.|
|[CAnimationManagerEventHandler,:: OnManagerStatusChanged](#onmanagerstatuschanged)|Appelé lorsqu’un État du gestionnaire d’animations a changé. (Substitue `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`.)|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur d’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événements est créé et passé à la méthode IUIAnimationManager:: SetManagerEventHandler, quand vous appelez CAnimationController:: EnableAnimationManagerEvent.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="canimationmanagereventhandler"></a>  CAnimationManagerEventHandler::CAnimationManagerEventHandler

Visual Studio 2010 SP1 est requis

Construit un objet CAnimationManagerEventHandler,.

```
CAnimationManagerEventHandler();
```

##  <a name="createinstance"></a>  CAnimationManagerEventHandler::CreateInstance

Visual Studio 2010 SP1 est requis

Crée une instance de l’objet CAnimationManagerEventHandler,.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur d’animation, qui reçoit les événements.

*ppManagerEventHandler*<br/>
Sortie. Si la méthode est réussie, elle contient un pointeur vers un objet COM qui gérera les mises à jour d’état d’un gestionnaire d’animations.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="onmanagerstatuschanged"></a>  CAnimationManagerEventHandler::OnManagerStatusChanged

Visual Studio 2010 SP1 est requis

Appelé lorsqu’un État du gestionnaire d’animations a changé.

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*newStatus*<br/>
Nouvel État.

*previousStatus*<br/>
État précédent.

### <a name="return-value"></a>Valeur de retour

L’implémentation actuelle retourne toujours S_OK;

##  <a name="setanimationcontroller"></a>  CAnimationManagerEventHandler::SetAnimationController

Visual Studio 2010 SP1 est requis

Stocke un pointeur vers le contrôleur d’animation pour acheminer les événements.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur d’animation, qui reçoit les événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
