---
title: IPointerInactiveImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: 6fb5d9f2bcbdeda61f32947bf339d134c4924b72
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495651"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl, classe

Cette classe implémente `IUnknown` et les méthodes de l’interface [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) .

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IPointerInactiveImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Récupère la stratégie d’activation actuelle pour l’objet. L’implémentation ATL retourne E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Indique à l’objet que le pointeur de la souris a été déplacé au-dessus, ce qui indique que l’objet peut déclencher des événements de souris. L’implémentation ATL retourne E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Définit le pointeur de la souris pour l’objet inactif. L’implémentation ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

Un objet inactif est un objet qui est simplement chargé ou en cours d’exécution. Contrairement à un objet actif, un objet inactif ne peut pas recevoir de messages de la souris et du clavier Windows. Ainsi, les objets inactifs utilisent moins de ressources et sont généralement plus efficaces.

L’interface [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) permet à un objet de prendre en charge un niveau minimal d’interaction avec la souris, tout en restant inactif. Cette fonctionnalité est particulièrement utile pour les contrôles.

La `IPointerInactiveImpl` classe implémente `IPointerInactive` les méthodes en retournant simplement E_NOTIMPL. Toutefois, elle implémente `IUnknown` en envoyant des informations à l’unité de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlctl. h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

Récupère la stratégie d’activation actuelle pour l’objet.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPointerInactive:: GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) dans le SDK Windows.

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

Indique à l’objet que le pointeur de la souris a été déplacé au-dessus, ce qui indique que l’objet peut déclencher des événements de souris.

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

Consultez [IPointerInactive:: OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) dans le SDK Windows.

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

Consultez [IPointerInactive:: OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
