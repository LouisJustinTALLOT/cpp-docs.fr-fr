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
ms.openlocfilehash: a4e97c2a1188071b5bde0781630d0dfe52e8a72f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369720"
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
|[CAnimationManagerEventHandler::CréerInstance](#createinstance)|Crée une `CAnimationManagerEventHandler` instance d’objet.|
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|Appelé quand un statut de directeur d’animation a changé. (Substitue `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`.)|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur au contrôleur d’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événement est créé et passé à IUIAnimationManager::SetManagerEventHandler méthode, lorsque vous appelez CAnimationController::EnableAnimationManagerEvent.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationmanagereventhandlercanimationmanagereventhandler"></a><a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler::CAnimationManagerEventHandler

Visual Studio 2010 SP1 est requis

Construit un objet CAnimationManagerEventHandler.

```
CAnimationManagerEventHandler();
```

## <a name="canimationmanagereventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationManagerEventHandler::CréerInstance

Visual Studio 2010 SP1 est requis

Crée une instance de cAnimationManagerEventHandler objet.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Un pointeur au contrôleur d’animation, qui recevra des événements.

*ppManagerEventHandler*<br/>
Sortie : Si la méthode réussit, elle contient un pointeur à l’objet COM qui gérera les mises à jour de statut à un gestionnaire d’animation.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, retourne S_OK. Sinon, il renvoie un code d’erreur HRESULT.

## <a name="canimationmanagereventhandleronmanagerstatuschanged"></a><a name="onmanagerstatuschanged"></a>CAnimationManagerEventHandler::OnManagerStatusChanged

Visual Studio 2010 SP1 est requis

Appelé quand un statut de directeur d’animation a changé.

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*nouveauStatus*<br/>
Nouveau statut.

*précédentStatus*<br/>
Statut précédent.

### <a name="return-value"></a>Valeur de retour

La mise en œuvre actuelle revient toujours S_OK;

## <a name="canimationmanagereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationManagerEventHandler::SetAnimationController

Visual Studio 2010 SP1 est requis

Stocke un pointeur au contrôleur d’animation pour acheminer les événements.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Un pointeur au contrôleur d’animation, qui recevra des événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
