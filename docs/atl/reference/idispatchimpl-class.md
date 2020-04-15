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
ms.openlocfilehash: 3b3899a0c4a49aa7fb1bd82af330f5f1cc7329c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329794"
---
# <a name="idispatchimpl-class"></a>Classe IDispatchImpl

Fournit une implémentation par défaut pour la `IDispatch` partie d’une double interface.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
[dans] Une double interface.

*piid*<br/>
[dans] Un pointeur à l’IID de *T*.

*plibid*<br/>
[dans] Un pointeur pour le LIBID de la bibliothèque de type qui contient des informations sur l’interface. Par défaut, la bibliothèque de type serveur est passée.

*wMajor (en)*<br/>
[dans] La version principale de la bibliothèque de type. Par défaut, la valeur est de 1.

*wMinor (en)*<br/>
[dans] La version mineure de la bibliothèque de type. Par défaut, la valeur est de 0.

*tihclass*<br/>
[dans] La classe utilisée pour gérer les informations de type pour *T*. Par défaut, la `CComTypeInfoHolder`valeur est .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Constructeur. Fait `AddRef` appel à la variable de membre protégée qui gère les informations de type pour la double interface. Le destructeur appelle `Release`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Mappe un jeu de noms avec un jeu correspondant d'identificateurs de dispatch.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Récupère les informations de type pour la double interface.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Détermine s’il existe des informations de type disponibles pour la double interface.|
|[IDispatchImpl::Invoquer](#invoke)|Donne accès aux méthodes et aux propriétés exposées par la double interface.|

## <a name="remarks"></a>Notes

`IDispatchImpl`fournit une implémentation par défaut pour la `IDispatch` partie de toute double interface sur un objet. Une double interface `IDispatch` dérive et n’utilise que des types compatibles avec l’automatisation. Comme une dispinterface, une double interface prend en charge la liaison précoce et la liaison tardive; cependant, une double interface prend également en charge la liaison vtable.

L’exemple suivant montre `IDispatchImpl`une mise en œuvre typique de .

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Par défaut, `IDispatchImpl` la classe recherche les informations de type pour *T* dans le registre. Pour implémenter une interface non `IDispatchImpl` enregistrée, vous pouvez utiliser la classe sans accéder au registre en utilisant un numéro de version prédéfini. Si vous `IDispatchImpl` créez un objet qui a 0xFFFF comme la valeur pour *wMajor* et `IDispatchImpl` 0xFFFF comme la valeur pour *wMinor*, la classe récupère la bibliothèque de type du fichier .dll au lieu du registre.

`IDispatchImpl`contient un membre `CComTypeInfoHolder` statique de type qui gère les informations de type pour la double interface. Si vous avez plusieurs objets qui implémenter `CComTypeInfoHolder` la même double interface, une seule instance est utilisée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`IDispatchImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchImpl::GetIDsOfNames

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

Voir [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) dans le SDK Windows.

## <a name="idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl::GetTypeInfo

Récupère les informations de type pour la double interface.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

Voir [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) dans le Windows SDK.

## <a name="idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount

Détermine s’il existe des informations de type disponibles pour la double interface.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Notes

Voir `IDispatch::GetTypeInfoCount` dans le Windows SDK.

## <a name="idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl

Constructeur. Fait `AddRef` appel à la variable de membre protégée qui gère les informations de type pour la double interface. Le destructeur appelle `Release`.

```
IDispatchImpl();
```

## <a name="idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl::Invoquer

Donne accès aux méthodes et aux propriétés exposées par la double interface.

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

Voir [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
