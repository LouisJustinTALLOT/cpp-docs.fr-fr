---
title: Classe IDispatchImpl
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 7e9cb903742cdc31c1d9bba2c4aabbb0472407c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495950"
---
# <a name="idispatchimpl-class"></a>Classe IDispatchImpl

Fournit une implémentation par défaut pour `IDispatch` la partie d’une interface double.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
dans Interface double.

*piid*<br/>
dans Pointeur vers l’IID de *T*.

*plibid*<br/>
dans Pointeur vers le LIBID de la bibliothèque de types qui contient des informations sur l’interface. Par défaut, la bibliothèque de types au niveau du serveur est passée.

*wMajor*<br/>
dans Version principale de la bibliothèque de types. Par défaut, la valeur est 1.

*wMinor*<br/>
dans Version mineure de la bibliothèque de types. Par défaut, la valeur est 0.

*tihclass*<br/>
dans Classe utilisée pour gérer les informations de type pour *T*. Par défaut, la valeur est définie sur `CComTypeInfoHolder`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Constructeur. Appelle `AddRef` sur la variable membre protégée qui gère les informations de type pour l’interface double. Le destructeur appelle `Release`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Mappe un jeu de noms avec un jeu correspondant d'identificateurs de dispatch.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Récupère les informations de type pour l’interface double.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Détermine si des informations de type sont disponibles pour l’interface double.|
|[IDispatchImpl::Invoke](#invoke)|Fournit l’accès aux méthodes et propriétés exposées par l’interface double.|

## <a name="remarks"></a>Notes

`IDispatchImpl`fournit une implémentation par défaut pour `IDispatch` la partie d’une interface double sur un objet. Une interface double dérive de `IDispatch` et utilise uniquement des types compatibles Automation. À l’instar d’une dispinterface, une interface double prend en charge la liaison précoce et la liaison tardive; Toutefois, une interface double prend également en charge la liaison vtable.

L’exemple suivant montre une implémentation classique de `IDispatchImpl`.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Par défaut, la `IDispatchImpl` classe recherche les informations de type pour *T* dans le registre. Pour implémenter une interface non inscrite, vous pouvez `IDispatchImpl` utiliser la classe sans accéder au registre à l’aide d’un numéro de version prédéfini. Si vous créez un `IDispatchImpl` objet qui a 0xFFFF comme valeur pour *wMajor* et 0xFFFF comme valeur pour *wMinor*, la `IDispatchImpl` classe récupère la bibliothèque de types à partir du fichier. dll au lieu du Registre.

`IDispatchImpl`contient un membre statique de type `CComTypeInfoHolder` qui gère les informations de type de l’interface double. Si vous avez plusieurs objets qui implémentent la même interface double, une seule instance `CComTypeInfoHolder` de est utilisée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`IDispatchImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames

Mappe un jeu de noms avec un jeu correspondant d'identificateurs de dispatch.

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) dans le SDK Windows.

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

Récupère les informations de type pour l’interface double.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) dans la SDK Windows.

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

Détermine si des informations de type sont disponibles pour l’interface double.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Notes

Consultez `IDispatch::GetTypeInfoCount` dans la SDK Windows.

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

Constructeur. Appelle `AddRef` sur la variable membre protégée qui gère les informations de type pour l’interface double. Le destructeur appelle `Release`.

```
IDispatchImpl();
```

##  <a name="invoke"></a>  IDispatchImpl::Invoke

Fournit l’accès aux méthodes et propriétés exposées par l’interface double.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
