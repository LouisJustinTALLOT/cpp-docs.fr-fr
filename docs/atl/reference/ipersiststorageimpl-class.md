---
title: Ipersiststorageimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
dev_langs:
- C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 634a7a7373f6686ad36b645a73613a4ae350bbab
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884699"
---
# <a name="ipersiststorageimpl-class"></a>Ipersiststorageimpl, classe
Cette classe implémente le [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) interface.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `IPersistStorageImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|  
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Demande à l’objet pour libérer tous les objets de stockage et de passer en mode HandsOff. L’implémentation de ATL retourne S_OK.|  
|[IPersistStorageImpl::InitNew](#initnew)|Initialise un nouveau stockage.|  
|[IPersistStorageImpl::IsDirty](#isdirty)|Vérifie si les données de l’objet a été modifiée depuis son dernier enregistrement.|  
|[IPersistStorageImpl::Load](#load)|Charge les propriétés de l’objet à partir du stockage spécifié.|  
|[IPersistStorageImpl::Save](#save)|Enregistre les propriétés de l’objet dans le stockage spécifié.|  
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Avertit un objet qu’elle peut retourner en mode Normal pour écrire dans son objet de stockage. L’implémentation de ATL retourne S_OK.|  
  
## <a name="remarks"></a>Notes  
 `IPersistStorageImpl` implémente le [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) interface, ce qui permet à un client de demander à ce que votre charge de l’objet et enregistrer ses données persistantes à l’aide d’un stockage.  
  
 L’implémentation de cette classe nécessite classe `T` pour rendre une implémentation de la `IPersistStreamInit` interface disponible via `QueryInterface`. En général, cela signifie que cette classe `T` doit dériver de [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), fournir une entrée pour `IPersistStreamInit` dans le [mappage COM](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)et utiliser un [mappage des propriétés](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427) pour décrire les données persistantes de la classe.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID  
 Récupère le CLSID de l’objet.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) dans le Kit de développement logiciel Windows.  
  
##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage  
 Demande à l’objet pour libérer tous les objets de stockage et de passer en mode HandsOff.  
  
```
STDMETHOD(HandsOffStorage)(void);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/windows/desktop/ms679742) dans le Kit de développement logiciel Windows.  
  
##  <a name="initnew"></a>  IPersistStorageImpl::InitNew  
 Initialise un nouveau stockage.  
  
```
STDMETHOD(InitNew)(IStorage*);
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation de ATL délègue à la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interface.  
  
 Consultez [IPersistStorage:InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194) dans le Kit de développement logiciel Windows.  
  
##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty  
 Vérifie si les données de l’objet a été modifiée depuis son dernier enregistrement.  
  
```
STDMETHOD(IsDirty)(void);
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation de ATL délègue à la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interface.  
  
 Consultez [IPersistStorage:IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910) dans le Kit de développement logiciel Windows.  
  
##  <a name="load"></a>  IPersistStorageImpl::Load  
 Charge les propriétés de l’objet à partir du stockage spécifié.  
  
```
STDMETHOD(Load)(IStorage* pStorage);
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation de ATL délègue à la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interface. `Load` utilise un flux nommé « Contenu » pour récupérer les données de l’objet. Le [enregistrer](#save) méthode crée à l’origine de ce flux.  
  
 Consultez [IPersistStorage:Load](http://msdn.microsoft.com/library/windows/desktop/ms680557) dans le Kit de développement logiciel Windows.  
  
##  <a name="save"></a>  IPersistStorageImpl::Save  
 Enregistre les propriétés de l’objet dans le stockage spécifié.  
  
```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation de ATL délègue à la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interface. Lorsque `Save` est d’abord appelée, elle crée un flux nommé « Contenu » sur le stockage spécifié. Ce flux est ensuite utilisé dans les appels ultérieurs à `Save` et dans les appels à [charge](#load).  
  
 Consultez [IPersistStorage:Save](http://msdn.microsoft.com/library/windows/desktop/ms680680) dans le Kit de développement logiciel Windows.  
  
##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted  
 Avertit un objet qu’elle peut retourner en mode Normal pour écrire dans son objet de stockage.  
  
```
STDMETHOD(SaveCompleted)(IStorage*);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPersistStorage:SaveCompleted](http://msdn.microsoft.com/library/windows/desktop/ms679713) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux et stockages](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Ipersiststreaminitimpl, classe](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [Ipersistpropertybagimpl, classe](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
