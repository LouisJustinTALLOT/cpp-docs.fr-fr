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
ms.openlocfilehash: ad27c4288d7e16949fe38ea6b8a686e3d6916ee6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275228"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl, classe

Cette classe fournit des méthodes autorisant un objet communiquer avec son site.

## <a name="syntax"></a>Syntaxe

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IObjectWithSiteImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Interroge le site pour un pointeur d’interface.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Fournit l’objet avec le site `IUnknown` pointeur.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Fournit l’objet avec le site `IUnknown` pointeur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Gère le site `IUnknown` pointeur.|

## <a name="remarks"></a>Notes

Le [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) interface permet à un objet communiquer avec son site. Classe `IObjectWithSiteImpl` fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

`IObjectWithSiteImpl` Spécifie les deux méthodes. Le client appelle d’abord `SetSite`, en passant le site `IUnknown` pointeur. Ce pointeur est stocké dans l’objet et peuvent être récupéré ultérieurement via un appel à `GetSite`.

En règle générale, vous dérivez votre classe de `IObjectWithSiteImpl` quand vous créez un objet qui n’est pas un contrôle. Pour les contrôles, dérivez votre classe de [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), qui fournit également un pointeur de site. Ne dérivent pas de votre classe à partir des deux `IObjectWithSiteImpl` et `IOleObjectImpl`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite

Interroge le site pour un pointeur vers l’interface identifiée par `riid`.

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Notes

Si le site prend en charge cette interface, le pointeur est retourné par le biais de `ppvSite`. Sinon, `ppvSite` est définie sur NULL.

Consultez [IObjectWithSite::GetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-getsite) dans le Kit de développement logiciel Windows.

##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite

Gère le site `IUnknown` pointeur.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Notes

`m_spUnkSite` ne reçoit initialement ce pointeur via un appel à [SetSite](#setsite).

##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite

Fournit l’objet avec le site `IUnknown` pointeur.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Paramètres

*pUnkSite*<br/>
[in] Pointeur vers le `IUnknown` pointeur d’interface du site de la gestion de cet objet. Si NULL, l’objet doit appeler `IUnknown::Release` sur n’importe quel site existante à quel point l’objet n’est plus sait que son site.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite

Fournit l’objet avec le site `IUnknown` pointeur.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Notes

Consultez [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
