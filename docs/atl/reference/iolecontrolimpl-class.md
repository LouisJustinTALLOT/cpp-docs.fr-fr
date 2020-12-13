---
description: 'En savoir plus sur : classe IOleControlImpl'
title: IOleControlImpl, classe
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
ms.openlocfilehash: e224f6f8db79c05cb8a774cd57517ba06108e592
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139423"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl, classe

Cette classe fournit une implémentation par défaut de l' `IOleControl` interface et implémente `IUnknown` .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IOleControlImpl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleControlImpl :: FreezeEvents](#freezeevents)|Indique si le conteneur ignore ou accepte les événements du contrôle.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Renseigne les informations relatives au comportement du clavier du contrôle. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleControlImpl :: OnAmbientPropertyChange](#onambientpropertychange)|Informe un contrôle qu’une ou plusieurs des propriétés ambiantes du conteneur ont été modifiées. L’implémentation ATL retourne S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informe le contrôle qu’un utilisateur a appuyé sur une séquence de touches spécifiée. L’implémentation ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

`IOleControlImpl`La classe fournit une implémentation par défaut de l’interface [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) et implémente `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a> IOleControlImpl :: FreezeEvents

Dans l’implémentation de ATL, `FreezeEvents` incrémente le membre de données de la classe de contrôle `m_nFreezeEvents` si `bFreeze` a la valeur true, et décrémente `m_nFreezeEvents` si a la valeur `bFreeze` false.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Notes

`FreezeEvents` retourne ensuite S_OK.

Consultez [IOleControl :: FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) dans le SDK Windows.

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a> IOleControlImpl::GetControlInfo

Renseigne les informations relatives au comportement du clavier du contrôle.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Notes

Consultez [IOleControl : GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Retourne E_NOTIMPL.

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a> IOleControlImpl :: OnAmbientPropertyChange

Informe un contrôle qu’une ou plusieurs des propriétés ambiantes du conteneur ont été modifiées.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleControl :: OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) dans le SDK Windows.

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a> IOleControlImpl::OnMnemonic

Informe le contrôle qu’un utilisateur a appuyé sur une séquence de touches spécifiée.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleControl :: OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[IOleObjectImpl, classe](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Interfaces de contrôles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
