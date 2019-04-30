---
title: CAnimationTimerEventHandler, classe
ms.date: 11/04/2016
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
ms.openlocfilehash: e5e6b0a22d438f9c26318129e2d04df96d386cda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391333"
---
# <a name="canimationtimereventhandler-class"></a>CAnimationTimerEventHandler, classe

Implémente un rappel, qui est appelé par l'API d'animation lorsque des événements de minutage se produisent.

## <a name="syntax"></a>Syntaxe

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Crée une instance de `CAnimationTimerEventHandler` rappel.|
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Gère les événements qui se produisent après qu’une mise à jour de l’animation est terminée. (Substitue `CUIAnimationTimerEventHandlerBase::OnPostUpdate`.)|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Gère les événements qui se produisent avant le début d’une mise à jour de l’animation. (Substitue `CUIAnimationTimerEventHandlerBase::OnPreUpdate`.)|
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Gère les événements qui se produisent lorsque la fréquence d’images de rendu pour une animation tombe en dessous de la fréquence d’images souhaitable minimale. (Substitue `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`.)|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événements est créé et transmis à IUIAnimationTimer::SetTimerEventHandler lorsque vous appelez CAnimationController::EnableAnimationTimerEventHandler.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxanimationcontroller.h

##  <a name="createinstance"></a>  CAnimationTimerEventHandler::CreateInstance

Crée une instance de rappel CAnimationTimerEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur de l’animation, qui recevra les événements.

*ppTimerEventHandler*

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

##  <a name="onpostupdate"></a>  CAnimationTimerEventHandler::OnPostUpdate

Gère les événements qui se produisent après qu’une mise à jour de l’animation est terminée.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode réussit ; Sinon, E_FAIL.

##  <a name="onpreupdate"></a>  CAnimationTimerEventHandler::OnPreUpdate

Gère les événements qui se produisent avant le début d’une mise à jour de l’animation.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode réussit ; Sinon, E_FAIL.

##  <a name="onrenderingtooslow"></a>  CAnimationTimerEventHandler::OnRenderingTooSlow

Gère les événements qui se produisent lorsque la fréquence d’images de rendu pour une animation tombe en dessous de la fréquence d’images souhaitable minimale.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Paramètres

*fps*

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode réussit ; Sinon, E_FAIL.

##  <a name="setanimationcontroller"></a>  CAnimationTimerEventHandler::SetAnimationController

Stocke un pointeur vers le contrôleur de l’animation pour acheminer les événements.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur de l’animation, qui recevra les événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
