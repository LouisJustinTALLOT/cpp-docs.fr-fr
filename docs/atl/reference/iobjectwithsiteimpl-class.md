---
title: Classe IObjectWithSiteImpl
ms.date: 11/04/2016
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
ms.openlocfilehash: 034e5dd42f6e10286520bb2a08effc40b0aca71a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329641"
---
# <a name="iobjectwithsiteimpl-class"></a>Classe IObjectWithSiteImpl

Cette classe fournit des méthodes permettant à un objet de communiquer avec son site.

## <a name="syntax"></a>Syntaxe

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IObjectWithSiteImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Interroge le site pour un pointeur d’interface.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Fournit l’objet avec `IUnknown` le pointeur du site.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Fournit l’objet avec `IUnknown` le pointeur du site.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Gère le pointeur du `IUnknown` site.|

## <a name="remarks"></a>Notes

[L’interface IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) permet à un objet de communiquer avec son site. La `IObjectWithSiteImpl` classe fournit une implémentation par défaut de cette interface et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

`IObjectWithSiteImpl`spécifie deux méthodes. Le client `SetSite`appelle d’abord, `IUnknown` en passant le pointeur du site. Ce pointeur est stocké dans l’objet, et `GetSite`peut plus tard être récupéré par un appel à .

En règle générale, `IObjectWithSiteImpl` vous dérivez votre classe à partir de la création d’un objet qui n’est pas un contrôle. Pour les contrôles, dérivez votre classe [d’IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), qui fournit également un pointeur de site. Ne dérivez pas `IObjectWithSiteImpl` votre `IOleObjectImpl`classe des deux et .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="iobjectwithsiteimplgetsite"></a><a name="getsite"></a>IObjectWithSiteImpl::GetSite

Requête le site pour un pointeur `riid`à l’interface identifiée par .

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Notes

Si le site prend en charge `ppvSite`cette interface, le pointeur est retourné via . Sinon, `ppvSite` est réglé à NULL.

Voir [IObjectWithSite:GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) dans le Windows SDK.

## <a name="iobjectwithsiteimplm_spunksite"></a><a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite

Gère le pointeur du `IUnknown` site.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Notes

`m_spUnkSite`reçoit d’abord ce pointeur par un appel à [SetSite](#setsite).

## <a name="iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite

Fournit l’objet avec `IUnknown` le pointeur du site.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Paramètres

*pUnkSite (en)*<br/>
[dans] Pointeur `IUnknown` sur le pointeur d’interface du site gérant cet objet. Si NULL, l’objet doit faire appel `IUnknown::Release` à n’importe quel site existant à quel point l’objet ne connaît plus son site.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="iobjectwithsiteimplsetsite"></a><a name="setsite"></a>IObjectWithSiteImpl::SetSite

Fournit l’objet avec `IUnknown` le pointeur du site.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Notes

Voir [IObjectWithSite:SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
