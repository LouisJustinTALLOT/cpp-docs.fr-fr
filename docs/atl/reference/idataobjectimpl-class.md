---
title: Idataobjectimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
dev_langs:
- C++
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7444cfe152d964318ea9786f4e4f7718e11d71cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069805"
---
# <a name="idataobjectimpl-class"></a>Idataobjectimpl, classe

Cette classe fournit des méthodes pour prendre en charge le transfert de données uniforme et de gestion des connexions.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IDataObjectImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Établit une connexion entre l’objet de données et un récepteur de notifications. Ainsi, le récepteur de notifications recevoir des notifications de modifications dans l’objet.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Met fin à une connexion précédemment établie par `DAdvise`.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Crée un énumérateur pour itérer via les connexions de notifications actuelles.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Crée un énumérateur pour itérer la `FORMATETC` structures prises en charge par l’objet de données. L’implémentation de ATL retourne E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Renvoie une notification de modification à chaque récepteur de notifications.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Récupère un logiquement équivalente `FORMATETC` structure pour qu’il est plus complexe. L’implémentation de ATL retourne E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Transfère les données à partir de l’objet de données au client. Les données sont décrites dans un `FORMATETC` structurer et sont transférées via un `STGMEDIUM` structure.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Semblable à `GetData`, sauf que le client doit allouer la `STGMEDIUM` structure. L’implémentation de ATL retourne E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Détermine si l’objet de données prend en charge un particulier `FORMATETC` structure pour transférer des données. L’implémentation de ATL retourne E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Transfère les données à partir du client à l’objet de données. L’implémentation de ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

Le [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) interface fournit des méthodes pour prendre en charge le transfert de données uniforme. `IDataObject` utilise les structures de format standard [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) et [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) pour récupérer et stocker des données.

`IDataObject` gère également les connexions pour informer les récepteurs pour gérer les notifications de modification de données. Le client peut recevoir des notifications de modification de données à partir de l’objet de données, le client doit implémenter le [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interface sur un objet appelé un récepteur de notifications. Lorsque le client appelle ensuite `IDataObject::DAdvise`, une connexion est établie entre l’objet de données et le récepteur de notifications.

Classe `IDataObjectImpl` fournit une implémentation par défaut de `IDataObject` et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="dadvise"></a>  IDataObjectImpl::DAdvise

Établit une connexion entre l’objet de données et un récepteur de notifications.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Notes

Ainsi, le récepteur de notifications recevoir des notifications de modifications dans l’objet.

Pour terminer la connexion, appelez [DUnadvise](#dunadvise).

Consultez [IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) dans le Kit de développement logiciel Windows.

##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise

Arrête une connexion précédemment établie par le biais [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Notes

Consultez [IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) dans le Kit de développement logiciel Windows.

##  <a name="enumdadvise"></a>  IDataObjectImpl::EnumDAdvise

Crée un énumérateur pour itérer via les connexions de notifications actuelles.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Notes

Consultez [IDataObject::EnumDAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-enumdadvise) dans le Kit de développement logiciel Windows.

##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc

Crée un énumérateur pour itérer la `FORMATETC` structures prises en charge par l’objet de données.

```
HRESULT EnumFormatEtc(  
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Notes

Consultez [IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) dans le Kit de développement logiciel Windows.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange

Renvoie une notification de modification à chaque récepteur de notifications en cours de gestion.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc

Récupère un logiquement équivalente `FORMATETC` structure pour qu’il est plus complexe.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IDataObject::GetCanonicalFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) dans le Kit de développement logiciel Windows.

##  <a name="getdata"></a>  IDataObjectImpl::GetData

Transfère les données à partir de l’objet de données au client.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Notes

Le *pformatetcIn* paramètre doit spécifier un type de support de stockage de TYMED_MFPICT.

Consultez [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) dans le Kit de développement logiciel Windows.

##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere

Semblable à `GetData`, sauf que le client doit allouer la `STGMEDIUM` structure.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IDataObject::GetDataHere a](/windows/desktop/api/objidl/nf-objidl-idataobject-getdatahere) dans le Kit de développement logiciel Windows.

##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData

Détermine si l’objet de données prend en charge un particulier `FORMATETC` structure pour transférer des données.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) dans le Kit de développement logiciel Windows.

##  <a name="setdata"></a>  IDataObjectImpl::SetData

Transfère les données à partir du client à l’objet de données.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IDataObject::SetData](/windows/desktop/api/objidl/nf-objidl-idataobject-setdata) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
