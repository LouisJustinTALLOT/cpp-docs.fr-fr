---
title: IExecutionContext, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b3f33cf98adc011d872a7d71246e6b94afaf4cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059782"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext, structure
Interface avec un contexte d'exécution qui peut s'exécuter sur un processeur virtuel donné et dont le contexte peut être commuté de manière coopérative.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IExecutionContext;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IExecutionContext::Dispatch](#dispatch)|La méthode est appelée lorsqu’un proxy de thread commence à exécuter un contexte d’exécution particulière. Il s’agit de la routine de travail principal pour votre planificateur.|  
|[IExecutionContext::GetId](#getid)|Retourne un identificateur unique pour le contexte d’exécution.|  
|[IExecutionContext::GetProxy](#getproxy)|Retourne une interface au proxy de thread qui exécute ce contexte.|  
|[IExecutionContext::GetScheduler](#getscheduler)|Retourne une interface au planificateur auquel appartient ce contexte d’exécution.|  
|[IExecutionContext::SetProxy](#setproxy)|Associe un proxy de thread à ce contexte d’exécution. Le proxy de thread associé appelle cette méthode juste avant de commencer l’exécution du contexte `Dispatch` (méthode).|  
  
## <a name="remarks"></a>Notes  
 Si vous implémentez un planificateur personnalisé qui sert d’interface avec le Gestionnaire de ressources du Runtime d’accès concurrentiel, vous devez implémenter le `IExecutionContext` interface. Les threads créés par le Gestionnaire de ressources effectuer le travail pour le compte de votre planificateur en exécutant la `IExecutionContext::Dispatch` (méthode).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IExecutionContext`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="dispatch"></a>  IExecutionContext::dispatch, méthode  
 La méthode est appelée lorsqu’un proxy de thread commence à exécuter un contexte d’exécution particulière. Il s’agit de la routine de travail principal pour votre planificateur.  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*pDispatchState*<br/>
Pointeur vers l’état sous lequel ce contexte d’exécution est distribué. Pour plus d’informations sur l’état de distribution, consultez [DispatchState](dispatchstate-structure.md).  
  
##  <a name="getid"></a>  IExecutionContext::GetId, méthode  
 Retourne un identificateur unique pour le contexte d’exécution.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un identificateur entier unique.  
  
### <a name="remarks"></a>Notes  
 Vous devez utiliser la méthode `GetExecutionContextId` pour obtenir un identificateur unique pour l’objet qui implémente le `IExecutionContext` interface, avant d’utiliser l’interface en tant que paramètre aux méthodes fournies par le Gestionnaire de ressources. Vous êtes censé retourner le même identificateur lorsque le `GetId` fonction est appelée.  
  
 Un identificateur obtenu à partir d’une autre source peut entraîner un comportement non défini.  
  
##  <a name="getproxy"></a>  IExecutionContext::GetProxy, méthode  
 Retourne une interface au proxy de thread qui exécute ce contexte.  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Interface `IThreadProxy`. Si le proxy de thread du contexte d’exécution n’a pas été initialisé avec un appel à `SetProxy`, la fonction doit retourner `NULL`.  
  
### <a name="remarks"></a>Notes  
 Appelle le Gestionnaire de ressources le `SetProxy` méthode sur un contexte d’exécution, avec un `IThreadProxy` interface en tant que paramètre, avant d’entrer le `Dispatch` méthode sur le sur le contexte. Vous êtes censé stocker cet argument et le retourner lors des appels à `GetProxy()`.  
  
##  <a name="getscheduler"></a>  IExecutionContext::GetScheduler, méthode  
 Retourne une interface au planificateur auquel appartient ce contexte d’exécution.  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Interface `IScheduler`.  
  
### <a name="remarks"></a>Notes  
 Vous devez initialiser le contexte d’exécution avec valide `IScheduler` interface avant de l’utiliser en tant que paramètre aux méthodes fournies par le Gestionnaire de ressources.  
  
##  <a name="setproxy"></a>  IExecutionContext::SetProxy, méthode  
 Associe un proxy de thread à ce contexte d’exécution. Le proxy de thread associé appelle cette méthode juste avant de commencer l’exécution du contexte `Dispatch` (méthode).  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*pThreadProxy*<br/>
Une interface au proxy de thread qui est sur le point le `Dispatch` méthode sur ce contexte d’exécution.  
  
### <a name="remarks"></a>Notes  
 Vous êtes tenu d’enregistrer le paramètre `pThreadProxy` et retourner lors d’un appel à la `GetProxy` (méthode). Le Gestionnaire de ressources garantit que le proxy de thread associé au contexte d’exécution ne changera pas pendant que le proxy de thread est en cours d’exécution le `Dispatch` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [IScheduler, Structure](ischeduler-structure.md)   
 [IThreadProxy, structure](ithreadproxy-structure.md)
