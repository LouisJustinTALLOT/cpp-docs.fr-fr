---
title: IDataObjectImpl, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
ms.openlocfilehash: 8e3369edd0731ede0892a405ef3de4e7b4cfdef1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495941"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl, classe

Cette classe fournit des méthodes pour la prise en charge de la Uniform Data Transfer et de la gestion des connexions.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IDataObjectImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Établit une connexion entre l’objet de données et un récepteur de notifications. Cela permet au récepteur de notifications de recevoir des notifications des modifications apportées à l’objet.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Met fin à une connexion précédemment établie `DAdvise`par le biais de.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Crée un énumérateur pour itérer au sein des connexions de notifications actuelles.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Crée un énumérateur pour itérer au sein `FORMATETC` des structures prises en charge par l’objet de données. L’implémentation ATL retourne E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Renvoie une notification de modification à chaque récepteur de notifications.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Récupère une structure logiquement équivalente `FORMATETC` à une structure qui est plus complexe. L’implémentation ATL retourne E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Transfère les données de l’objet de données vers le client. Les données sont décrites dans une `FORMATETC` structure et sont transférées via `STGMEDIUM` une structure.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Semblable à `GetData`, sauf que le client doit allouer la `STGMEDIUM` structure. L’implémentation ATL retourne E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Détermine si l’objet de données prend en `FORMATETC` charge une structure particulière pour le transfert de données. L’implémentation ATL retourne E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Transfère les données du client à l’objet de données. L’implémentation ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

L’interface [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) fournit des méthodes pour prendre en charge les Uniform Data Transfer. `IDataObject`utilise les structures de format standard [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) et [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) pour récupérer et stocker des données.

`IDataObject`gère également les connexions aux récepteurs de notification pour gérer les notifications de modification de données. Pour que le client reçoive des notifications de modification de données à partir de l’objet de données, le client doit implémenter l’interface [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) sur un objet appelé récepteur de notifications. Lorsque le client appelle `IDataObject::DAdvise`, une connexion est établie entre l’objet de données et le récepteur de notifications.

La `IDataObjectImpl` classe fournit une implémentation par `IDataObject` défaut de et `IUnknown` implémente en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlctl. h

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

Cela permet au récepteur de notifications de recevoir des notifications des modifications apportées à l’objet.

Pour mettre fin à la connexion, appelez [DUnadvise](#dunadvise).

Consultez [IDataObject::D conseiller](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) dans le SDK Windows.

##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise

Met fin à une connexion précédemment établie par le biais de [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Notes

Consultez [IDataObject::D](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) Unadvise dans le SDK Windows.

##  <a name="enumdadvise"></a>  IDataObjectImpl::EnumDAdvise

Crée un énumérateur pour itérer au sein des connexions de notifications actuelles.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Notes

Consultez [IDataObject:: EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) dans la SDK Windows.

##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc

Crée un énumérateur pour itérer au sein `FORMATETC` des structures prises en charge par l’objet de données.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Notes

Consultez [IDataObject:: EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) dans la SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange

Renvoie une notification de modification à chaque récepteur de notifications en cours de gestion.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc

Récupère une structure logiquement équivalente `FORMATETC` à une structure qui est plus complexe.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IDataObject:: GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) dans la SDK Windows.

##  <a name="getdata"></a>  IDataObjectImpl::GetData

Transfère les données de l’objet de données vers le client.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Notes

Le paramètre *pFormatetcIn* doit spécifier un type de support de stockage TYMED_MFPICT.

Consultez [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le SDK Windows.

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

Consultez [IDataObject:: GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) dans la SDK Windows.

##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData

Détermine si l’objet de données prend en `FORMATETC` charge une structure particulière pour le transfert de données.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) dans la SDK Windows.

##  <a name="setdata"></a>  IDataObjectImpl::SetData

Transfère les données du client à l’objet de données.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IDataObject:: SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
