---
title: Classe IDataObjectImpl
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
ms.openlocfilehash: 618f8248a03297120ae2504bcb30ba8f080b184d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329837"
---
# <a name="idataobjectimpl-class"></a>Classe IDataObjectImpl

Cette classe fournit des méthodes pour soutenir le transfert de données uniforme et la gestion des connexions.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IDataObjectImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Établit une connexion entre l’objet de données et un évier de conseil. Cela permet à l’évier de conseiller de recevoir des notifications de modifications de l’objet.|
|[IDataObjectImpl::DUnedvise](#dunadvise)|Termine une connexion précédemment `DAdvise`établie par .|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Crée un énumérateur pour itérer au sein des connexions de notifications actuelles.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Crée un énumérateur pour itérer au sein des structures `FORMATETC` prises en charge par l'objet de données. La mise en œuvre d’ATL E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Envoie une notification de modification à chaque évier de conseil.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Récupère une structure `FORMATETC` logiquement équivalente à celle qui est plus complexe. La mise en œuvre d’ATL E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Transfère les données de l'objet de données au client. Les données sont `FORMATETC` décrites dans une `STGMEDIUM` structure et sont transférées par une structure.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Semblable `GetData`à , sauf que `STGMEDIUM` le client doit allouer la structure. La mise en œuvre d’ATL E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Détermine si l'objet de données prend en charge une structure `FORMATETC` spécifique pour transférer des données. La mise en œuvre d’ATL E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Transfère les données du client à l'objet de données. La mise en œuvre d’ATL E_NOTIMPL.|

## <a name="remarks"></a>Notes

[L’interface IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) fournit des méthodes pour prendre en charge le transfert de données uniforme. `IDataObject`utilise les structures de format standard [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) et [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) pour récupérer et stocker des données.

`IDataObject`gère également des connexions pour conseiller les éviers pour gérer les notifications de changement de données. Pour que le client reçoive des notifications de modification de données à partir de l’objet de données, le client doit implémenter [l’interface IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) sur un objet appelé évier de conseil. Lorsque le client `IDataObject::DAdvise`appelle alors, une connexion est établie entre l’objet de données et l’évier de conseil.

La `IDataObjectImpl` classe fournit `IDataObject` une mise `IUnknown` en œuvre par défaut et des implémentations en envoyant des informations à l’appareil de décharge dans les versions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectImpl::DAdvise

Établit une connexion entre l’objet de données et un évier de conseil.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Notes

Cela permet à l’évier de conseiller de recevoir des notifications de modifications de l’objet.

Pour mettre fin à la connexion, appelez [DUnadvise](#dunadvise).

Voir [IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) in the Windows SDK.

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectImpl::DUnedvise

Termine une connexion précédemment établie par [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Notes

Voir [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) in the Windows SDK.

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise

Crée un énumérateur pour itérer au sein des connexions de notifications actuelles.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Notes

Voir [IDataObject:EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) dans le Windows SDK.

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc

Crée un énumérateur pour itérer au sein des structures `FORMATETC` prises en charge par l'objet de données.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Notes

Voir [IDataObject:EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectImpl::FireDataChange

Envoie une notification de modification à chaque évier de conseil qui est actuellement géré.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc

Récupère une structure `FORMATETC` logiquement équivalente à celle qui est plus complexe.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IDataObject:GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) dans le Windows SDK.

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectImpl::GetData

Transfère les données de l'objet de données au client.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Notes

Le *paramètre pformatetcIn* doit spécifier un type moyen de stockage de TYMED_MFPICT.

Voir [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) dans le Windows SDK.

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectImpl::GetDataHere

Semblable `GetData`à , sauf que `STGMEDIUM` le client doit allouer la structure.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IDataObject:GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) dans le Windows SDK.

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectImpl::QueryGetData

Détermine si l'objet de données prend en charge une structure `FORMATETC` spécifique pour transférer des données.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IDataObject:QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) dans le SDK Windows.

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectImpl::SetData

Transfère les données du client à l'objet de données.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IDataObject:SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
