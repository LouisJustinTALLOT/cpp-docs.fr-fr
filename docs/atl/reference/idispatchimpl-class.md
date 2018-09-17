---
title: IDispatchImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81feb345c25ea1c1e9d15dba8dceebb7a2cdb418
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709798"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl, classe

Fournit une implémentation par défaut pour le `IDispatch` dans le cadre d’une interface double.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
[in] Une interface double.

*piid*<br/>
[in] Un pointeur vers l’IID de *T*.

*plibid*<br/>
[in] Pointeur vers le LIBID de la bibliothèque de types qui contient des informations sur l’interface. Par défaut, la bibliothèque de types de niveau serveur est passée.

*wMajor*<br/>
[in] La version principale de la bibliothèque de types. Par défaut, la valeur est 1.

*wMinor*<br/>
[in] La version mineure de la bibliothèque de types. Par défaut, la valeur est 0.

*tihclass*<br/>
[in] La classe utilisée pour gérer les informations de type pour *T*. Par défaut, la valeur est définie sur `CComTypeInfoHolder`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Constructeur. Appels `AddRef` sur la variable de membre protégé qui gère les informations de type pour l’interface double. Le destructeur appelle `Release`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Mappe un jeu de noms avec un jeu correspondant d'identificateurs de dispatch.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Récupère les informations de type pour l’interface double.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Détermine si les informations de type est disponible pour l’interface double.|
|[IDispatchImpl::Invoke](#invoke)|Fournit l’accès aux méthodes et propriétés exposées par l’interface double.|

## <a name="remarks"></a>Notes

`IDispatchImpl` Fournit une implémentation par défaut pour le `IDispatch` dans le cadre de n’importe quelle interface double sur un objet. Une interface double dérive `IDispatch` et utilise uniquement des types compatibles Automation. Comme une dispinterface, une interface double prend en charge la liaison anticipée et liaison tardive ; Toutefois, une interface double prend également en charge liaison par vtable.

L’exemple suivant montre une implémentation classique de `IDispatchImpl`.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

Par défaut, le `IDispatchImpl` classe recherche les informations de type pour *T* dans le Registre. Pour implémenter une interface non inscrite, vous pouvez utiliser la `IDispatchImpl` classe sans l’accès au Registre à l’aide d’un numéro de version prédéfinies. Si vous créez un `IDispatchImpl` objet ayant 0xFFFF comme valeur pour *wMajor* et 0xFFFF comme valeur pour *wMinor*, la `IDispatchImpl` classe récupère la bibliothèque de types à partir du fichier .dll au lieu de la Registre.

`IDispatchImpl` contient un membre statique de type `CComTypeInfoHolder` qui gère les informations de type pour l’interface double. Si vous avez plusieurs objets qui implémentent la même double n'interface qu’une seule instance de `CComTypeInfoHolder` est utilisé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`IDispatchImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

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

Consultez [IDispatch::GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) dans le Kit de développement logiciel Windows.

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

Récupère les informations de type pour l’interface double.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch::GetTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) dans le Kit de développement logiciel Windows.

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

Détermine si les informations de type est disponible pour l’interface double.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Notes

Consultez `IDispatch::GetTypeInfoCount` dans le Kit de développement logiciel Windows.

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

Constructeur. Appels `AddRef` sur la variable de membre protégé qui gère les informations de type pour l’interface double. Le destructeur appelle `Release`.

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

Consultez [IDispatch::Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
