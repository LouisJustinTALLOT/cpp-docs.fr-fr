---
title: Ipointerinactiveimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
dev_langs:
- C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f44bcdedc718ce4d6459fea7f8581273e49caa10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097560"
---
# <a name="ipointerinactiveimpl-class"></a>Ipointerinactiveimpl, classe

Cette classe implémente `IUnknown` et [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) méthodes d’interface.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPointerInactiveImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Récupère la stratégie d’activation en cours pour l’objet. L’implémentation de ATL retourne E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Notifie l’objet qui le pointeur de la souris a été déplacé sur celui-ci, indiquant l’objet peut déclencher des événements de souris. L’implémentation de ATL retourne E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Définit le pointeur de la souris pour l’objet inactif. L’implémentation de ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

Un objet inactif est un est simplement chargée ou en cours d’exécution. Contrairement à un objet actif, un objet inactif ne peut pas recevoir des messages de clavier et souris Windows. Par conséquent, les objets inactifs utilisent moins de ressources et sont généralement plus efficaces.

Le [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) interface permet à un objet prendre en charge un niveau minimal d’interaction de la souris tout en restant inactif. Cette fonctionnalité est particulièrement utile pour les contrôles.

Classe `IPointerInactiveImpl` implémente le `IPointerInactive` méthodes en retournant simplement E_NOTIMPL. Toutefois, il implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

Récupère la stratégie d’activation en cours pour l’objet.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPointerInactive::GetActivationPolicy](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) dans le Kit de développement logiciel Windows.

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

Notifie l’objet qui le pointeur de la souris a été déplacé sur celui-ci, indiquant l’objet peut déclencher des événements de souris.

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPointerInactive::OnInactiveMouseMove](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) dans le Kit de développement logiciel Windows.

##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor

Définit le pointeur de la souris pour l’objet inactif.

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPointerInactive::OnInactiveSetCursor](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
