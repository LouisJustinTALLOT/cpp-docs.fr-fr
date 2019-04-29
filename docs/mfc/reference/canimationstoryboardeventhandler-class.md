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
ms.openlocfilehash: d12f38491cf3aafca41756ce97e1cad44deb67d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338257"
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
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Crée une instance de `CAnimationStoryboardEventHandler` rappel.|
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Gère `OnStoryboardStatusChanged` événements qui se produisent lors de l’état d’un storyboard change (substitue `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`.)|
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|Gère `OnStoryboardUpdated` événements qui se produisent lorsqu’un storyboard est mis à jour (remplace `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`.)|
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événements est créé et transmis à `IUIAnimationStoryboard::SetStoryboardEventHandler` (méthode), lorsque vous appelez `CAnimationController::EnableStoryboardEventHandler`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="canimationstoryboardeventhandler"></a>  CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler

Construit un objet CAnimationStoryboardEventHandler.

```
CAnimationStoryboardEventHandler();
```

##  <a name="createinstance"></a>  CAnimationStoryboardEventHandler::CreateInstance

Crée une instance de rappel CAnimationStoryboardEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur de l’animation, qui recevra les événements.

*ppHandler*

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="onstoryboardstatuschanged"></a>  CAnimationStoryboardEventHandler::OnStoryboardStatusChanged

Gère les événements OnStoryboardStatusChanged qui se produisent lors de l’état d’un storyboard

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Paramètres

*storyboard*<br/>
Pointeur vers la table de montage séquentiel dont l’état a changé.

*newStatus*<br/>
Spécifie le nouvel état de la table de montage séquentiel.

*previousStatus*<br/>
Spécifie l’état précédent de la table de montage séquentiel.

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode réussit ; Sinon, E_FAIL.

##  <a name="onstoryboardupdated"></a>  CAnimationStoryboardEventHandler::OnStoryboardUpdated

Gère les événements OnStoryboardUpdated qui se produisent lorsqu’un storyboard est mis à jour

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>Paramètres

*storyboard*<br/>
Pointeur vers le storyboard qui a été mise à jour.

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode réussit ; Sinon, E_FAIL.

##  <a name="setanimationcontroller"></a>  CAnimationStoryboardEventHandler::SetAnimationController

Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur de l’animation, qui recevra les événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
