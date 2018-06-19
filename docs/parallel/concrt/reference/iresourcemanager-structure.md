---
title: IResourceManager, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
dev_langs:
- C++
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afd87a71c8f5d41e38f6a1b18be96a7bab8f3bb8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693495"
---
# <a name="iresourcemanager-structure"></a>IResourceManager, structure
Interface avec un gestionnaire des ressources du runtime d'accès concurrentiel. Il s'agit de l'interface par laquelle les planificateurs communiquent avec le gestionnaire des ressources.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IResourceManager;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-enumerations"></a>Énumérations publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IResourceManager::OSVersion](#osversion)|Type énuméré qui représente la version du système d'exploitation.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IResourceManager::CreateNodeTopology](#createnodetopology)|Actuellement en mode de débogage uniquement les versions du runtime, cette méthode est un crochet de test conçu pour faciliter le test du Gestionnaire de ressources sur divers topologies de matériel, sans nécessiter un matériel réel correspondant à la configuration. Avec les versions commerciales du runtime, cette méthode retournera sans exécuter d’action.|  
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Retourne le nombre de nœuds disponibles pour le Gestionnaire de ressources.|  
|[IResourceManager::GetFirstNode](#getfirstnode)|Retourne le premier nœud dans l’ordre d’énumération comme défini par le Gestionnaire de ressources.|  
|[IResourceManager::Reference](#reference)|Incrémente le décompte de références sur l’instance du Gestionnaire de ressources.|  
|[IResourceManager::RegisterScheduler](#registerscheduler)|Inscrit un planificateur avec le Gestionnaire de ressources. Une fois que le planificateur est inscrit, il doit communiquer avec le Gestionnaire de ressources à l’aide du `ISchedulerProxy` interface qui est retournée.|  
|[IResourceManager::Release](#release)|Décrémente le décompte de références sur l’instance du Gestionnaire de ressources. Le Gestionnaire de ressources est détruit lorsque son décompte de références atteint `0`.|  
  
## <a name="remarks"></a>Notes  
 Utilisez le [CreateResourceManager](concurrency-namespace-functions.md) fonction pour obtenir une interface pour l’instance du Gestionnaire de ressources du singleton. La méthode incrémente un décompte de références sur le Gestionnaire de ressources, et vous devez appeler la [IResourceManager::Release](#release) méthode pour libérer la référence lorsque vous avez terminé avec le Gestionnaire de ressources. En général, chaque planificateur que vous créez cette méthode est appelée lors de la création et libérer la référence au Gestionnaire de ressources après sa fermeture.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IResourceManager`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="createnodetopology"></a>  IResourceManager::CreateNodeTopology, méthode  
 Actuellement en mode de débogage uniquement les versions du runtime, cette méthode est un crochet de test conçu pour faciliter le test du Gestionnaire de ressources sur divers topologies de matériel, sans nécessiter un matériel réel correspondant à la configuration. Avec les versions commerciales du runtime, cette méthode retournera sans exécuter d’action.  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `nodeCount`  
 Le nombre de nœuds de processeur qui sont simulés.  
  
 `pCoreCount`  
 Tableau qui spécifie le nombre de cœurs sur chaque nœud.  
  
 `pNodeDistance`  
 Une matrice qui spécifie la distance de nœud entre deux nœuds. Ce paramètre peut avoir la valeur `NULL`.  
  
 `pProcessorGroups`  
 Un tableau qui spécifie le groupe de processeurs auquel chaque nœud appartient.  
  
### <a name="remarks"></a>Notes  
 [invalid_argument](../../../standard-library/invalid-argument-class.md) est levée si le paramètre `nodeCount` a la valeur `0` a été passé, ou si le paramètre `pCoreCount` a la valeur `NULL`.  
  
 [invalid_operation](invalid-operation-class.md) est levée si cette méthode est appelée lorsque d’autres planificateurs existent dans le processus.  
  
##  <a name="getavailablenodecount"></a>  IResourceManager::getavailablenodecount, méthode  
 Retourne le nombre de nœuds disponibles pour le Gestionnaire de ressources.  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de nœuds disponibles pour le Gestionnaire de ressources.  
  
##  <a name="getfirstnode"></a>  IResourceManager::getfirstnode, méthode  
 Retourne le premier nœud dans l’ordre d’énumération comme défini par le Gestionnaire de ressources.  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le premier nœud dans l’ordre d’énumération comme défini par le Gestionnaire de ressources.  
  
##  <a name="iresourcemanager__osversion"></a>  IResourceManager::OSVersion, énumération  
 Type énuméré qui représente la version du système d'exploitation.  
  
```
enum OSVersion;
```  
  
##  <a name="reference"></a>  IResourceManager::Reference, méthode  
 Incrémente le décompte de références sur l’instance du Gestionnaire de ressources.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décompte de références résultant.  
  
##  <a name="registerscheduler"></a>  IResourceManager::RegisterScheduler, méthode  
 Inscrit un planificateur avec le Gestionnaire de ressources. Une fois que le planificateur est inscrit, il doit communiquer avec le Gestionnaire de ressources à l’aide du `ISchedulerProxy` interface qui est retournée.  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `pScheduler`  
 Un `IScheduler` interface au planificateur à enregistrer.  
  
 `version`  
 La version de l’interface de communication que le planificateur utilise pour communiquer avec le Gestionnaire de ressources. À l’aide d’une version permet de faire évoluer l’interface de communication tout en permettant aux planificateurs d’obtenir l’accès aux fonctionnalités plus anciennes, le Gestionnaire de ressources. Les planificateurs qui souhaitent utiliser les fonctionnalités du Gestionnaire de ressources dans Visual Studio 2010 doivent utiliser la version `CONCRT_RM_VERSION_1`.  
  
### <a name="return-value"></a>Valeur de retour  
 Le `ISchedulerProxy` interface du Gestionnaire de ressources a associé à votre planificateur. Votre planificateur doit utiliser cette interface pour communiquer avec le Gestionnaire de ressources à partir de ce point sur.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour initialiser la communication avec le Gestionnaire de ressources. La méthode associe le `IScheduler` interface pour votre planificateur avec un `ISchedulerProxy` interface et fait appel à nouveau pour vous. Vous pouvez utiliser l’interface retournée pour demander des ressources d’exécution pour une utilisation par votre planificateur, ou abonner des threads avec le Gestionnaire de ressources. Le Gestionnaire de ressources utilisera les éléments de la stratégie du planificateur retournée par la [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) devez méthode pour déterminer le type du Planificateur de threads exécuter le travail. Si votre `SchedulerKind` clé de stratégie a la valeur `UmsThreadDefault` et la valeur est lue hors de la stratégie en tant que la valeur `UmsThreadDefault`, le `IScheduler` interface passé à la méthode doit être un `IUMSScheduler` interface.  
  
 La méthode lève un `invalid_argument` exception si le paramètre `pScheduler` a la valeur `NULL` ou si le paramètre `version` n’est pas une version valide pour l’interface de communication.  
  
##  <a name="release"></a>  IResourceManager::Release, méthode  
 Décrémente le décompte de références sur l’instance du Gestionnaire de ressources. Le Gestionnaire de ressources est détruit lorsque son décompte de références atteint `0`.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décompte de références résultant.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [ISchedulerProxy, Structure](ischedulerproxy-structure.md)   
 [IScheduler, structure](ischeduler-structure.md)
