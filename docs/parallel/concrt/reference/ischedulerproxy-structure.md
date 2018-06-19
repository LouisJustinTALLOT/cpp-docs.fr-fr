---
title: ISchedulerProxy, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
dev_langs:
- C++
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65198998666391763ef32a55cd12e86529e619ed
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693921"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy, structure
Interface par laquelle les planificateurs communiquent avec le gestionnaire des ressources du runtime d'accès concurrentiel pour négocier l'allocation des ressources.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ISchedulerProxy::BindContext](#bindcontext)|Associe un contexte d’exécution à un proxy de thread, si elle ne l’est pas déjà.|  
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Crée une nouvelle racine de processeur virtuel sur le thread matériel associé à une ressource d’exécution existant.|  
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Demande une allocation initiale de racines de processeur virtuel. Chaque racine de processeur virtuel représente la capacité à exécuter un thread qui peut effectuer un travail pour le planificateur.|  
|[ISchedulerProxy::Shutdown](#shutdown)|Notifie le Gestionnaire de ressources que le planificateur est en cours d’arrêt. Cela entraîne le Gestionnaire de ressources à récupérer immédiatement toutes les ressources accordées au planificateur.|  
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Inscrit le thread actuel avec le Gestionnaire de ressources, son association à ce planificateur.|  
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Dissocie un proxy de thread du contexte d’exécution spécifié par le `pContext` paramètre et le retourne au pool libre de la fabrique de proxy de thread. Cette méthode peut uniquement être appelée sur un contexte d’exécution qui a été lié via la [ISchedulerProxy::BindContext](#bindcontext) (méthode) et n’a pas encore été démarré en étant le `pContext` paramètre d’une [IThreadProxy::SwitchTo ](ithreadproxy-structure.md#switchto) appel de méthode.|  
  
## <a name="remarks"></a>Notes  
 Le Gestionnaire des ressources donne une `ISchedulerProxy` interface à chaque planificateur qui s’inscrit à l’aide de la [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) (méthode).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="bindcontext"></a>  ISchedulerProxy::BindContext, méthode  
 Associe un contexte d’exécution à un proxy de thread, si elle ne l’est pas déjà.  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `pContext`  
 Une interface pour le contexte d’exécution à associer à un proxy de thread.  
  
### <a name="remarks"></a>Notes  
 Normalement, le [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) méthode lie un proxy de thread à un contexte d’exécution à la demande. Il existe, toutefois, les cas où il est nécessaire de lier un contexte à l’avance pour vous assurer que le `SwitchTo` méthode bascule vers un contexte déjà lié. C’est le cas dans un contexte de planification comme elle ne peut pas appeler les méthodes qui allouent la mémoire UMS, et la liaison d’un proxy de thread peut impliquer l’allocation de mémoire si un proxy de thread n’est pas immédiatement disponible dans le pool libre de la fabrique de proxy de thread.  
  
 `invalid_argument` est levée si le paramètre `pContext` a la valeur `NULL`.  
  
##  <a name="createoversubscriber"></a>  ISchedulerProxy::CreateOversubscriber, méthode  
 Crée une nouvelle racine de processeur virtuel sur le thread matériel associé à une ressource d’exécution existant.  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `pExecutionResource`  
 Un `IExecutionResource` interface qui représente le thread matériel que vous souhaitez sur-souscrire.  
  
### <a name="return-value"></a>Valeur de retour  
 Interface `IVirtualProcessorRoot`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode lorsque votre planificateur souhaite surabonner un thread matériel particulier pour une durée limitée. Une fois que vous avez terminé avec la racine de processeur virtuel, vous devez le retourner au Gestionnaire de ressources en appelant le [supprimer](iexecutionresource-structure.md#remove) méthode sur le `IVirtualProcessorRoot` interface.  
  
 Vous pouvez même sur-souscrire une racine de processeur virtuel existante, car le `IVirtualProcessorRoot` interface hérite de la `IExecutionResource` interface.  
  
##  <a name="requestinitialvirtualprocessors"></a>  ISchedulerProxy::RequestInitialVirtualProcessors, méthode  
 Demande une allocation initiale de racines de processeur virtuel. Chaque racine de processeur virtuel représente la capacité à exécuter un thread qui peut effectuer un travail pour le planificateur.  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `doSubscribeCurrentThread`  
 Si vous souhaitez vous abonner le thread actuel compte pendant l’allocation de ressources.  
  
### <a name="return-value"></a>Valeur de retour  
 Le `IExecutionResource` interface pour le thread actuel, si le paramètre `doSubscribeCurrentThread` a la valeur `true`. Si la valeur est `false`, la méthode retourne `NULL`.  
  
### <a name="remarks"></a>Notes  
 Avant l’exécution d’un planificateur de n’importe quel travail, elle doit utiliser cette méthode pour demander les racines de processeur virtuel à partir du Gestionnaire de ressources. Le Gestionnaire des ressources accédera à la stratégie du planificateur à l’aide de [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) et utiliser les valeurs pour les clés de stratégie `MinConcurrency`, `MaxConcurrency` et `TargetOversubscriptionFactor` pour déterminer le nombre de threads matériels à affecter à la Planificateur initialement et combien de racines de processeur virtuel à créer pour chaque thread matériel. Pour plus d’informations sur l’utilisation des stratégies de planificateur pour déterminer l’allocation initiale d’un planificateur, consultez [PolicyElementKey](concurrency-namespace-enums.md).  
  
 Le Gestionnaire des ressources accorde des ressources à un planificateur en appelant la méthode [IScheduler::AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) avec une liste de racines de processeur virtuel. La méthode est appelée en tant qu’un rappel dans le planificateur avant le retour de cette méthode.  
  
 Si le planificateur a demandé l’abonnement pour le thread actuel en définissant le paramètre `doSubscribeCurrentThread` à `true`, la méthode retourne un `IExecutionResource` interface. L’abonnement doit se terminer à un moment ultérieur à l’aide de la [IExecutionResource::Remove](iexecutionresource-structure.md#remove) (méthode).  
  
 Lors de la détermination des threads matériels sont sélectionnées, le Gestionnaire de ressources tente d’optimiser pour l’affinité de nœud de processeur. Si l’abonnement est demandé pour le thread actuel, il indique que le thread actuel a l’intention de participer au travail assigné à ce planificateur. Dans ce cas, les racines de processeur virtuel allouées se trouvent sur le nœud de processeur qu'exécute le thread actuel, si possible.  
  
 L’acte d’abonnement d’un thread augmente le niveau d’abonnement du thread matériel sous-jacent d’une unité. Niveau de l’abonnement est diminué d’une unité lorsque l’abonnement est terminé. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="shutdown"></a>  ISchedulerProxy::Shutdown, méthode  
 Notifie le Gestionnaire de ressources que le planificateur est en cours d’arrêt. Cela entraîne le Gestionnaire de ressources à récupérer immédiatement toutes les ressources accordées au planificateur.  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>Notes  
 Tous les `IExecutionContext` le planificateur a reçues en souscrivant un thread externe à l’aide des méthodes des interfaces `ISchedulerProxy::RequestInitialVirtualProcessors` ou `ISchedulerProxy::SubscribeCurrentThread` doit être renvoyé au Gestionnaire de ressources à l’aide de `IExecutionResource::Remove` avant un planificateur s’arrête.  
  
 Si votre planificateur avait une désactivation des racines de processeur virtuel, vous devez les activer à l’aide de [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate)et l’exécution sur les serveurs proxy thread laisser le `Dispatch` de l’exécution (méthode) ils sont la distribution avant d’appeler des contextes `Shutdown` sur un proxy de planificateur.  
  
 Il n’est pas nécessaire pour le Planificateur de retourner toutes les racines de processeur virtuel du Gestionnaire de ressources lui a accordées via des appels à la `Remove` méthode étant donné que toutes les racines de processeur virtuel seront affichera pour le Gestionnaire de ressources à l’arrêt.  
  
##  <a name="subscribecurrentthread"></a>  ISchedulerProxy::SubscribeCurrentThread, méthode  
 Inscrit le thread actuel avec le Gestionnaire de ressources, son association à ce planificateur.  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le `IExecutionResource` d’interface qui représente le thread actuel dans le runtime.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode si vous souhaitez que le Gestionnaire de ressources pour prendre en compte pour le thread actuel lors de l’allocation de ressources à votre planificateur et d’autres planificateurs. Il est particulièrement utile lorsque le thread projette de participer au travail en attente dans votre planificateur, ainsi que les racines de processeur virtuel que le planificateur reçoit du Gestionnaire de ressources. Le Gestionnaire de ressources utilise des informations pour empêcher le surabonnement inutile de threads matériels sur le système.  
  
 La ressource d’exécution reçue via cette méthode doit être retournée au Gestionnaire de ressources à l’aide de la [IExecutionResource::Remove](iexecutionresource-structure.md#remove) (méthode). Le thread qui appelle la `Remove` méthode doit être le même thread que celui qui a appelé le `SubscribeCurrentThread` (méthode).  
  
 L’acte d’abonnement d’un thread augmente le niveau d’abonnement du thread matériel sous-jacent d’une unité. Niveau de l’abonnement est diminué d’une unité lorsque l’abonnement est terminé. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="unbindcontext"></a>  ISchedulerProxy::UnbindContext, méthode  
 Dissocie un proxy de thread du contexte d’exécution spécifié par le `pContext` paramètre et le retourne au pool libre de la fabrique de proxy de thread. Cette méthode peut uniquement être appelée sur un contexte d’exécution qui a été lié via la [ISchedulerProxy::BindContext](#bindcontext) (méthode) et n’a pas encore été démarré en étant le `pContext` paramètre d’une [IThreadProxy::SwitchTo ](ithreadproxy-structure.md#switchto) appel de méthode.  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `pContext`  
 Le contexte d’exécution à dissocier de son proxy de thread.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [IScheduler, Structure](ischeduler-structure.md)   
 [IThreadProxy, Structure](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot, Structure](ivirtualprocessorroot-structure.md)   
 [IResourceManager, structure](iresourcemanager-structure.md)
