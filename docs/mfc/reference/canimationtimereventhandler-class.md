---
description: 'En savoir plus sur : classe CAnimationTimerEventHandler,'
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
ms.openlocfilehash: 5d5f3e07eeb7ffe3f3bb226afd566330808303ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336761"
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
|[CAnimationTimerEventHandler, :: CreateInstance](#createinstance)|Crée une instance de `CAnimationTimerEventHandler` callback.|
|[CAnimationTimerEventHandler, :: OnPostUpdate](#onpostupdate)|Gère les événements qui se produisent une fois la mise à jour d’une animation terminée. (Substitue `CUIAnimationTimerEventHandlerBase::OnPostUpdate`.)|
|[CAnimationTimerEventHandler, :: OnPreUpdate](#onpreupdate)|Gère les événements qui se produisent avant le début d’une mise à jour d’animation. (Substitue `CUIAnimationTimerEventHandlerBase::OnPreUpdate`.)|
|[CAnimationTimerEventHandler, :: OnRenderingTooSlow](#onrenderingtooslow)|Gère les événements qui se produisent lorsque la fréquence d’images de rendu d’une animation passe sous la fréquence d’images minimale recommandée. (Substitue `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`.)|
|[CAnimationTimerEventHandler, :: SetAnimationController](#setanimationcontroller)|Stocke un pointeur vers le contrôleur d’animation pour acheminer les événements.|

## <a name="remarks"></a>Notes

Ce gestionnaire d’événements est créé et passé à IUIAnimationTimer :: SetTimerEventHandler lorsque vous appelez CAnimationController :: EnableAnimationTimerEventHandler.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Spécifications

**En-tête :** afxanimationcontroller.h

## <a name="canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a> CAnimationTimerEventHandler, :: CreateInstance

Crée une instance de rappel CAnimationTimerEventHandler,.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur d’animation, qui reçoit les événements.

*ppTimerEventHandler*

### <a name="return-value"></a>Valeur renvoyée

Si la méthode réussit, retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.

## <a name="canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a> CAnimationTimerEventHandler, :: OnPostUpdate

Gère les événements qui se produisent une fois la mise à jour d’une animation terminée.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK si la méthode est réussie ; sinon E_FAIL.

## <a name="canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a> CAnimationTimerEventHandler, :: OnPreUpdate

Gère les événements qui se produisent avant le début d’une mise à jour d’animation.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Valeur renvoyée

S_OK si la méthode est réussie ; sinon E_FAIL.

## <a name="canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a> CAnimationTimerEventHandler, :: OnRenderingTooSlow

Gère les événements qui se produisent lorsque la fréquence d’images de rendu d’une animation passe sous la fréquence d’images minimale recommandée.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Paramètres

*fps*

### <a name="return-value"></a>Valeur renvoyée

S_OK si la méthode est réussie ; sinon E_FAIL.

## <a name="canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a> CAnimationTimerEventHandler, :: SetAnimationController

Stocke un pointeur vers le contrôleur d’animation pour acheminer les événements.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Paramètres

*pAnimationController*<br/>
Pointeur vers le contrôleur d’animation, qui reçoit les événements.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
