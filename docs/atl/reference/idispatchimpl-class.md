---
title: Classe de IDispatchImpl | Documents Microsoft
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
ms.openlocfilehash: 7fddf556eba07264f6ea0b01edea3e3d1e8a3a7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364364"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl (classe)
Fournit une implémentation par défaut pour le `IDispatch` dans le cadre d’une interface double.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
 [in] `T`  
 Une interface double.  
  
 [in] `piid`  
 Un pointeur vers l’IID de `T`.  
  
 [in] `plibid`  
 Pointeur vers le LIBID de la bibliothèque de types qui contient des informations sur l’interface. Par défaut, la bibliothèque de types de niveau serveur est passée.  
  
 [in] `wMajor`  
 Version principale de la bibliothèque de types. Par défaut, la valeur est 1.  
  
 [in] `wMinor`  
 Version secondaire de la bibliothèque de types. Par défaut, la valeur est 0.  
  
 [in] `tihclass`  
 La classe utilisée pour gérer les informations de type `T`. Par défaut, la valeur est définie sur `CComTypeInfoHolder`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Constructeur. Appels `AddRef` sur la variable membre protégé qui gère les informations de type pour l’interface double. Le destructeur appelle `Release`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Mappe un jeu de noms avec un jeu correspondant d'identificateurs de dispatch.|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Récupère les informations de type pour l’interface double.|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Détermine si les informations de type est disponible pour l’interface double.|  
|[IDispatchImpl::Invoke](#invoke)|Fournit l’accès aux méthodes et propriétés exposées par l’interface double.|  
  
## <a name="remarks"></a>Notes  
 `IDispatchImpl` Fournit une implémentation par défaut pour le `IDispatch` dans le cadre d’une interface double sur un objet. Une interface double dérive `IDispatch` et utilise uniquement des types compatibles Automation. Comme une dispinterface, une interface double prend en charge la liaison anticipée et liaison tardive ; Toutefois, une interface double prend également en charge liaison par vtable.  
  
 L’exemple suivant montre une implémentation classique des `IDispatchImpl`.  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 Par défaut, le `IDispatchImpl` recherche les informations de type classe `T` dans le Registre. Pour implémenter une interface non inscrite, vous pouvez utiliser la `IDispatchImpl` classe sans accès au Registre à l’aide d’un numéro de version prédéfinies. Si vous créez un `IDispatchImpl` objet ayant 0xFFFF comme valeur pour `wMajor` et 0xFFFF comme valeur pour `wMinor`, la `IDispatchImpl` classe récupère la bibliothèque de types à partir du fichier .dll au lieu du Registre.  
  
 `IDispatchImpl` contient un membre statique de type `CComTypeInfoHolder` qui gère les informations de type pour l’interface double. Si vous avez plusieurs objets qui implémentent la même double interface, une seule instance de `CComTypeInfoHolder` est utilisé.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>Spécifications  
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
 Consultez [IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) dans le Kit de développement logiciel Windows.  
  
##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo  
 Récupère les informations de type pour l’interface double.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) dans le Kit de développement logiciel Windows.  
  
##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount  
 Détermine si les informations de type est disponible pour l’interface double.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Notes  
 Consultez `IDispatch::GetTypeInfoCount` dans le Kit de développement logiciel Windows.  
  
##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl  
 Constructeur. Appels `AddRef` sur la variable membre protégé qui gère les informations de type pour l’interface double. Le destructeur appelle **version**.  
  
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
 Consultez [IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
