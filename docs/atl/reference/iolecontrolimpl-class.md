---
title: Iolecontrolimpl, classe
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
ms.openlocfilehash: 50119d21b041f37f03ca416a9a56ca9e29ae3344
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263531"
---
# <a name="iolecontrolimpl-class"></a>Iolecontrolimpl, classe

Cette classe fournit une implémentation par défaut de la `IOleControl` interface et implémente `IUnknown`.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IOleControlImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indique si le conteneur ignore ou accepte les événements à partir du contrôle.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Renseigne les informations sur le comportement du clavier du contrôle. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Indique un contrôle qu’un ou plusieurs des propriétés ambiantes du conteneur a changé. L’implémentation de ATL retourne S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informe le contrôle qu’un utilisateur a appuyé sur une séquence de touches spécifiée. L’implémentation de ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

Classe `IOleControlImpl` fournit une implémentation par défaut de la [IOleControl](/windows/desktop/api/ocidl/nn-ocidl-iolecontrol) interface et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl.h

##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents

Dans l’implémentation d’ATL, `FreezeEvents` incrémente la classe de contrôle `m_nFreezeEvents` membre de données si `bFreeze` est TRUE et décrémente `m_nFreezeEvents` si `bFreeze` a la valeur FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Notes

`FreezeEvents` puis retourne S_OK.

Consultez [IOleControl::FreezeEvents](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-freezeevents) dans le Kit de développement logiciel Windows.

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

Renseigne les informations sur le comportement du clavier du contrôle.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Notes

Consultez [IOleControl:GetControlInfo](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) dans le Kit de développement logiciel Windows.

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

Indique un contrôle qu’un ou plusieurs des propriétés ambiantes du conteneur a changé.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleControl::OnAmbientPropertyChange](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) dans le Kit de développement logiciel Windows.

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

Informe le contrôle qu’un utilisateur a appuyé sur une séquence de touches spécifiée.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleControl::OnMnemonic](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[IOleObjectImpl, classe](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Interfaces de contrôles ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
