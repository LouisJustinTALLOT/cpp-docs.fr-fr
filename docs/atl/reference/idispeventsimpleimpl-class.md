---
title: Classe de IDispEventSimpleImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89f565c1e32f1208fbb039321d26b9175596d57e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365992"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl (classe)
Cette classe fournit des implémentations de la `IDispatch` méthodes, sans récupérer les informations de type à partir d’une bibliothèque de types.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <UINT nID, class T, const IID* pdiid>  
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```    
  
#### <a name="parameters"></a>Paramètres  
 `nID`  
 Identificateur unique de l’objet source. Lorsque `IDispEventSimpleImpl` est la classe de base pour un contrôle composite, utilisez l’ID de ressource du contrôle de contenu souhaité pour ce paramètre. Dans d’autres cas, utilisez un entier positif arbitraire.  
  
 `T`  
 Classe de l’utilisateur, qui est dérivée de `IDispEventSimpleImpl`.  
  
 `pdiid`  
 Pointeur vers l’IID de l’interface des événements implémentée par cette classe.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](#advise)|Établit une connexion avec la source d’événements par défaut.|  
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Établit une connexion avec la source d’événements.|  
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Interrompt la connexion avec la source d’événements.|  
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Retourne **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Retourne **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Retourne **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::Invoke](#invoke)|Appelle les gestionnaires d’événements répertoriées dans l’événement de table de récepteur.|  
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Interrompt la connexion avec la source d’événement par défaut.|  
  
## <a name="remarks"></a>Notes  
 `IDispEventSimpleImpl` offre un moyen de l’implémentation d’une interface des événements sans avoir à fournir un code d’implémentation pour chaque méthode/événement sur cette interface. `IDispEventSimpleImpl` Fournit des implémentations de la `IDispatch` méthodes. Vous devez uniquement fournir des implémentations pour les événements que vous êtes intéressé par la gestion.  
  
 `IDispEventSimpleImpl` fonctionne en association avec la table de récepteur d’événements dans votre classe pour les événements d’itinéraire à la fonction gestionnaire approprié. Pour utiliser cette classe :  
  
-   Ajouter un [macro SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) (macro) à la table de récepteur d’événements pour chaque événement sur chaque objet que vous souhaitez gérer.  
  
-   Fournir des informations de type pour chaque événement en passant un pointeur vers un [les structures _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) structure en tant que paramètre à chaque entrée. Sur le x86 plateforme, le `_ATL_FUNC_INFO.cc` la valeur doit être CC_CDECL avec la fonction de rappel que l’appel de méthode de __stdcall.  
  
-   Appelez [DispEventAdvise](#dispeventadvise) pour établir la connexion entre l’objet source et la classe de base.  
  
-   Appelez [DispEventUnadvise](#dispeventunadvise) pour rompre la liaison.  
  
 Vous devez dériver de `IDispEventSimpleImpl` (à l’aide d’une valeur unique pour `nID`) pour chaque objet pour lequel vous devez gérer les événements. Vous pouvez réutiliser la classe de base par désinformation sur objet d’une seule source puis conseiller par rapport à un objet source différente, mais le nombre maximal d’objets de source qui peuvent être gérés par un seul objet à la fois est limité par le nombre de `IDispEventSimpleImpl` classes de base.  
  
 **IDispEventSimplImpl** fournit les mêmes fonctionnalités que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), excepté qu’elle n’obtient pas le type d’informations sur l’interface à partir d’une bibliothèque de types. Les Assistants génèrent un code basé uniquement sur `IDispEventImpl`, mais vous pouvez utiliser `IDispEventSimpleImpl` en ajoutant le code manuellement. Utilisez `IDispEventSimpleImpl` lorsque vous ne disposez d’une bibliothèque de types décrivant l’interface d’événement ou pour éviter la surcharge associée à l’aide de la bibliothèque de types.  
  
> [!NOTE]
> `IDispEventImpl` et `IDispEventSimpleImpl` fournir leur propre implémentation de **IUnknown::QueryInterface** chaque activation `IDispEventImpl` ou `IDispEventSimpleImpl` d’agir comme une identité COM distincte tout en autorisant un accès direct aux membres de classe de classe de base votre objet COM principal.  
  
 Implémentation de CE ATL de ActiveX événement récepteurs uniquement prend en charge valeurs de retour de type HRESULT ou void à partir de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour non pris en charge et son comportement n’est pas défini.  
  
 Pour plus d’informations, consultez [prise en charge de IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="advise"></a>  IDispEventSimpleImpl::Advise  
 Appelez cette méthode pour établir une connexion avec la source d’événement représentée par *pUnk*.  
  
```
HRESULT Advise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Un pointeur vers le **IUnknown** interface de l’objet source d’événement.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` ou tout échec `HRESULT` valeur.  
  
### <a name="remarks"></a>Notes  
 Une fois que la connexion est établie, les événements déclenchés à partir de *pUnk* sera routé vers gestionnaires dans votre classe au moyen de la table de récepteur d’événements.  
  
> [!NOTE]
>  Si votre classe dérivée à partir de plusieurs `IDispEventSimpleImpl` classes, vous devez lever l’ambiguïté entre des appels à cette méthode par la portée de l’appel à la classe de base particulière vous intéressez.  
  
 `Advise` établit une connexion avec la source d’événement par défaut, il obtient l’IID de la source d’événement par défaut de l’objet, comme déterminé par [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).  
  
##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise  
 Appelez cette méthode pour établir une connexion avec la source d’événement représentée par *pUnk*.  
  
```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Un pointeur vers le **IUnknown** interface de l’objet source d’événement.  
  
 `piid`  
 Pointeur vers l’IID de l’objet source d’événement.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` ou tout échec `HRESULT` valeur.  
  
### <a name="remarks"></a>Notes  
 Par la suite, les événements déclenchés à partir de *pUnk* sera routé vers gestionnaires dans votre classe au moyen de la table de récepteur d’événements.  
  
> [!NOTE]
>  Si votre classe dérivée à partir de plusieurs `IDispEventSimpleImpl` classes, vous devez lever l’ambiguïté entre des appels à cette méthode par la portée de l’appel à la classe de base particulière vous intéressez.  
  
 `DispEventAdvise` établit une connexion avec la source d’événements spécifiée dans `pdiid`.  
  
##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise  
 Interrompt la connexion avec la source d’événement représentée par *pUnk*.  
  
```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Un pointeur vers le **IUnknown** interface de l’objet source d’événement.  
  
 `piid`  
 Pointeur vers l’IID de l’objet source d’événement.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` ou tout échec `HRESULT` valeur.  
  
### <a name="remarks"></a>Notes  
 Une fois que la connexion est interrompue, les événements ne sont plus seront routés pour les fonctions de gestionnaire répertoriées dans la table de récepteur d’événements.  
  
> [!NOTE]
>  Si votre classe dérivée à partir de plusieurs `IDispEventSimpleImpl` classes, vous devez lever l’ambiguïté entre des appels à cette méthode par la portée de l’appel à la classe de base particulière vous intéressez.  
  
 `DispEventAdvise` arrête une connexion qui a été établie avec la source d’événements spécifiée dans `pdiid`.  
  
##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames  
 Cette implémentation de **IDispatch::GetIDsOfNames** retourne **E_NOTIMPL**.  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) dans le Kit de développement logiciel Windows.  
  
##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo  
 Cette implémentation de **IDispatch::GetTypeInfo** retourne **E_NOTIMPL**.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) dans le Kit de développement logiciel Windows.  
  
##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount  
 Cette implémentation de **IDispatch::GetTypeInfoCount** retourne **E_NOTIMPL**.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) dans le Kit de développement logiciel Windows.  
  
##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke  
 Cette implémentation de **IDispatch::Invoke** appelle les gestionnaires d’événements répertoriées dans l’événement de table de récepteur.  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise  
 Interrompt la connexion avec la source d’événement représentée par *pUnk*.  
  
```
HRESULT Unadvise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Un pointeur vers le **IUnknown** interface de l’objet source d’événement.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK` ou tout échec `HRESULT` valeur.  
  
### <a name="remarks"></a>Notes  
 Une fois que la connexion est interrompue, les événements ne sont plus seront routés pour les fonctions de gestionnaire répertoriées dans la table de récepteur d’événements.  
  
> [!NOTE]
>  Si votre classe dérivée à partir de plusieurs `IDispEventSimpleImpl` classes, vous devez lever l’ambiguïté entre des appels à cette méthode par la portée de l’appel à la classe de base particulière vous intéressez.  
  
 `Unadvise` arrête une connexion qui a été établie avec la source d’événements par défaut spécifiée dans `pdiid`.  
  
 **Unavise** divise une connexion avec la source d’événements par défaut, il obtient l’IID de la source d’événement par défaut de l’objet, comme déterminé par [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).  
  
## <a name="see-also"></a>Voir aussi  
 [Les structures _ATL_FUNC_INFO structure](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl (classe)](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl (classe)](../../atl/reference/idispeventimpl-class.md)   
 [MACRO SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
