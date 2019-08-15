---
title: IObjectWithSiteImpl, classe
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
ms.openlocfilehash: e857f739e3ff7235c473e99abbef6aab0d3f4205
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495835"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl, classe

Cette classe fournit des méthodes qui permettent à un objet de communiquer avec son site.

## <a name="syntax"></a>Syntaxe

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IObjectWithSiteImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Interroge le site pour obtenir un pointeur d’interface.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Fournit l’objet avec le pointeur du `IUnknown` site.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Fournit l’objet avec le pointeur du `IUnknown` site.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Gère le pointeur du `IUnknown` site.|

## <a name="remarks"></a>Notes

L’interface [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) permet à un objet de communiquer avec son site. La `IObjectWithSiteImpl` classe fournit une implémentation par défaut de cette interface et `IUnknown` implémente en envoyant des informations à l’appareil de vidage dans les versions Debug.

`IObjectWithSiteImpl`spécifie deux méthodes. Le client appelle `SetSite`d’abord, en passant le `IUnknown` pointeur du site. Ce pointeur est stocké dans l’objet et peut être récupéré ultérieurement par le biais d' `GetSite`un appel à.

En général, vous dérivez `IObjectWithSiteImpl` votre classe de lorsque vous créez un objet qui n’est pas un contrôle. Pour les contrôles, dérivez votre classe de [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), qui fournit également un pointeur de site. Ne dérivez pas votre classe `IObjectWithSiteImpl` de `IOleObjectImpl`et.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite

Interroge le site pour obtenir un pointeur vers l’interface identifiée par `riid`.

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Notes

Si le site prend en charge cette interface, le pointeur est `ppvSite`retourné via. Sinon, `ppvSite` a la valeur null.

Consultez [IObjectWithSite:: GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) dans la SDK Windows.

##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite

Gère le pointeur du `IUnknown` site.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Notes

`m_spUnkSite`reçoit initialement ce pointeur via un appel à [SetSite](#setsite).

##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite

Fournit l’objet avec le pointeur du `IUnknown` site.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Paramètres

*pUnkSite*<br/>
dans Pointeur vers le `IUnknown` pointeur d’interface du site qui gère cet objet. Si la valeur est null, l' `IUnknown::Release` objet doit appeler sur tout site existant à partir duquel l’objet ne connaît plus son site.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite

Fournit l’objet avec le pointeur du `IUnknown` site.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Notes

Consultez [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
