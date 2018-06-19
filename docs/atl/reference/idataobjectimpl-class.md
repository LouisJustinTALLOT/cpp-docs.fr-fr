---
title: Classe de IDataObjectImpl | Documents Microsoft
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
ms.openlocfilehash: a3ffcdd8cc8320b2534d928171fe75619062b300
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365479"
---
# <a name="idataobjectimpl-class"></a>Classe de IDataObjectImpl
Cette classe fournit des méthodes pour prendre en charge le transfert de données uniforme et de gestion des connexions.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IDataObjectImpl
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IDataObjectImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IDataObjectImpl::DAdvise](#dadvise)|Établit une connexion entre l’objet de données et un récepteur de notifications. Ainsi, le récepteur de notifications recevoir des notifications de modifications dans l’objet.|  
|[IDataObjectImpl::DUnadvise](#dunadvise)|Termine une connexion précédemment établie via `DAdvise`.|  
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Crée un énumérateur pour itérer au sein des connexions de notifications actuelles.|  
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Crée un énumérateur pour itérer au sein du **FORMATETC** structures pris en charge par l’objet de données. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IDataObjectImpl::FireDataChange](#firedatachange)|Envoie une notification de modification à chaque récepteur de notifications.|  
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Récupère un logiquement équivalentes **FORMATETC** structure par celle qui est plus complexe. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IDataObjectImpl::GetData](#getdata)|Transfère des données à partir de l’objet de données au client. Décrit les données dans un **FORMATETC** de la structure et est transférée via un **STGMEDIUM** structure.|  
|[IDataObjectImpl::GetDataHere](#getdatahere)|Semblable à `GetData`, sauf le client doit allouer la **STGMEDIUM** structure. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IDataObjectImpl::QueryGetData](#querygetdata)|Détermine si l’objet de données prend en charge un particulier **FORMATETC** structure pour le transfert de données. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IDataObjectImpl::SetData](#setdata)|Transfère des données à partir du client à l’objet de données. L’implémentation ATL retourne **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Notes  
 Le [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) interface fournit des méthodes pour prendre en charge le transfert de données uniforme. `IDataObject` utilise les structures de format standard [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) et [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) pour récupérer et stocker des données.  
  
 `IDataObject` gère également des connexions pour informer les récepteurs pour gérer les notifications de modification de données. Pour que le client de recevoir des notifications de modification de données à partir de l’objet de données, le client doit implémenter la [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interface sur un objet appelé un récepteur de notifications. Lorsque le client appelle ensuite **IDataObject::DAdvise**, une connexion est établie entre l’objet de données et le récepteur de notifications.  
  
 Classe `IDataObjectImpl` fournit une implémentation par défaut de `IDataObject` et implémente **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## <a name="requirements"></a>Spécifications  
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
  
 Pour mettre fin à la connexion, appelez [DUnadvise](#dunadvise).  
  
 Consultez [IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) dans le Kit de développement logiciel Windows.  
  
##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise  
 Termine une connexion précédemment établie via [DAdvise](#dadvise).  
  
```
HRESULT DUnadvise(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) dans le Kit de développement logiciel Windows.  
  
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
 Consultez [IDataObject::EnumDAdvise](http://msdn.microsoft.com/library/windows/desktop/ms680127) dans le Kit de développement logiciel Windows.  
  
##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc  
 Crée un énumérateur pour itérer au sein du **FORMATETC** structures pris en charge par l’objet de données.  
  
```
HRESULT EnumFormatEtc(  
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) dans le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange  
 Envoie une notification de modification à chaque récepteur de notifications qui est actuellement géré.  
  
```
HRESULT FireDataChange();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc  
 Récupère un logiquement équivalentes **FORMATETC** structure par celle qui est plus complexe.  
  
```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IDataObject::GetCanonicalFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms680685) dans le Kit de développement logiciel Windows.  
  
##  <a name="getdata"></a>  IDataObjectImpl::GetData  
 Transfère des données à partir de l’objet de données au client.  
  
```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```  
  
### <a name="remarks"></a>Notes  
 Le *pformatetcIn* paramètre doit spécifier un type de support de stockage de **TYMED_MFPICT**.  
  
 Consultez [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) dans le Kit de développement logiciel Windows.  
  
##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere  
 Semblable à `GetData`, sauf le client doit allouer la **STGMEDIUM** structure.  
  
```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IDataObject::GetDataHere a](http://msdn.microsoft.com/library/windows/desktop/ms687266) dans le Kit de développement logiciel Windows.  
  
##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData  
 Détermine si l’objet de données prend en charge un particulier **FORMATETC** structure pour le transfert de données.  
  
```
HRESULT QueryGetData(FORMATETC* pformatetc);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) dans le Kit de développement logiciel Windows.  
  
##  <a name="setdata"></a>  IDataObjectImpl::SetData  
 Transfère des données à partir du client à l’objet de données.  
  
```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IDataObject::SetData](http://msdn.microsoft.com/library/windows/desktop/ms686626) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
