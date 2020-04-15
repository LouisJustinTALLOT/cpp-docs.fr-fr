---
title: Classe IPointerInactiveImpl
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
ms.openlocfilehash: 229b8c6803aa7b3817cb3d95474bde0502829f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326449"
---
# <a name="ipointerinactiveimpl-class"></a>Classe IPointerInactiveImpl

Cette classe `IUnknown` implémente et les méthodes [d’interface IPointerInactive.](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IPointerInactiveImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Récupère la stratégie d’activation actuelle de l’objet. La mise en œuvre d’ATL E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Informe l’objet que le pointeur de la souris s’est déplacé sur elle, indiquant que l’objet peut tirer des événements de souris. La mise en œuvre d’ATL E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Définit le pointeur de souris pour l’objet inactif. La mise en œuvre d’ATL E_NOTIMPL.|

## <a name="remarks"></a>Notes

Un objet inactif est un objet qui est simplement chargé ou en cours d’exécution. Contrairement à un objet actif, un objet inactif ne peut pas recevoir de messages de souris et de clavier Windows. Ainsi, les objets inactifs utilisent moins de ressources et sont généralement plus efficaces.

[L’interface IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) permet à un objet de prendre en charge un niveau minimal d’interaction avec la souris tout en restant inactif. Cette fonctionnalité est particulièrement utile pour les contrôles.

La `IPointerInactiveImpl` classe `IPointerInactive` met en œuvre les méthodes en retournant simplement E_NOTIMPL. Cependant, il `IUnknown` implémente en envoyant des informations à l’appareil de décharge dans les constructions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy IPointerInactiveImpl::GetActivationPolicy

Récupère la stratégie d’activation actuelle de l’objet.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IPointerInactive::GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) dans le SDK Windows.

## <a name="ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove

Informe l’objet que le pointeur de la souris s’est déplacé sur elle, indiquant que l’objet peut tirer des événements de souris.

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

Voir [IPointerInactive::OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) dans le SDK Windows.

## <a name="ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor

Définit le pointeur de souris pour l’objet inactif.

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

Voir [IPointerInactive::OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
