---
title: Classe IOleControlImpl
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 947ec16e91b99cc42cff90abe7df4a5d13576e98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329623"
---
# <a name="iolecontrolimpl-class"></a>Classe IOleControlImpl

Cette classe fournit une `IOleControl` implémentation `IUnknown`par défaut de l’interface et des implémentations .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IOleControlImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indique si le conteneur ignore ou accepte les événements du contrôle.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Remplit des informations sur le comportement du clavier du contrôleur. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informe un contrôle qu’une ou plusieurs des propriétés ambiantes du conteneur ont changé. La mise en œuvre d’ATL S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informe le contrôle qu’un utilisateur a appuyé sur une frappe spécifiée. La mise en œuvre d’ATL E_NOTIMPL.|

## <a name="remarks"></a>Notes

La `IOleControlImpl` classe fournit une implémentation par défaut `IUnknown` de l’interface et des instruments [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) en envoyant des informations à l’appareil de décharge dans les versions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a>IOleControlImpl::FreezeEvents

Dans la mise en `FreezeEvents` œuvre d’ATL, incréments le membre des données de la classe de `m_nFreezeEvents` contrôle s’il `bFreeze` est VRAI, et décroisse `m_nFreezeEvents` si `bFreeze` est FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Notes

`FreezeEvents`retourne alors S_OK.

Voir [IOleControl::FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) in the Windows SDK.

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo

Remplit des informations sur le comportement du clavier du contrôleur.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Notes

Voir [IOleControl:GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a>IOleControlImpl::OnAmbientPropertyChange

Informe un contrôle qu’une ou plusieurs des propriétés ambiantes du conteneur ont changé.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IOleControl::OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) dans le Windows SDK.

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a>IOleControlImpl::OnMnemonic

Informe le contrôle qu’un utilisateur a appuyé sur une frappe spécifiée.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IOleControl::OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX contrôle les interfaces](/windows/win32/com/activex-controls-interfaces)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
