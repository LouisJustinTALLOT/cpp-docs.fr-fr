---
title: IUMSScheduler, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
dev_langs:
- C++
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 489978a97d42439e5560a75e429c38be10c18c29
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688529"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler, structure
Interface avec une abstraction d'un planificateur de tâches qui veut que le gestionnaire des ressources du runtime d'accès concurrentiel lui remette des threads UMS (User-Mode Scheduling). Le gestionnaire des ressources utilise cette interface pour communiquer avec les planificateurs de threads UMS. L'interface `IUMSScheduler` hérite de l'interface `IScheduler`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IUMSScheduler : public IScheduler;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Affecte un `IUMSCompletionList` interface vers un planificateur de thread UMS.|  
  
## <a name="remarks"></a>Notes  
 Si vous implémentez un planificateur personnalisé qui communique avec le Gestionnaire de ressources, et que vous souhaitez que les threads UMS soient transmis à votre planificateur au lieu de threads Win32 ordinaires, vous devez fournir une implémentation de la `IUMSScheduler` interface. En outre, vous devez définir la valeur de stratégie pour la clé de stratégie du planificateur `SchedulerKind` être `UmsThreadDefault`. Si la stratégie spécifie le thread UMS, le `IScheduler` interface qui est passée en tant que paramètre à la [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) méthode doit être un `IUMSScheduler` interface.  
  
 Le Gestionnaire de ressources est en mesure de vous les threads UMS uniquement sur les systèmes d’exploitation qui ont la fonctionnalité UMS. les systèmes d’exploitation 64 bits avec la version Windows 7 et versions ultérieures prennent en charge des threads UMS. Si vous créez une stratégie du planificateur avec la `SchedulerKind` clé défini sur la valeur `UmsThreadDefault` et la plateforme sous-jacente ne prend pas en charge UMS, la valeur de la `SchedulerKind` clé de cette stratégie est remplacé par la valeur `ThreadScheduler`. Vous devez toujours relire cette valeur de stratégie avant d’attendre de recevoir des threads UMS.  
  
 Le `IUMSScheduler` interface est une extrémité d’un canal bidirectionnel de communication entre un planificateur et le Gestionnaire de ressources. L’autre extrémité est représentée par le `IResourceManager` et `ISchedulerProxy` interfaces qui sont implémentées par le Gestionnaire de ressources.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [IScheduler](ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="setcompletionlist"></a>  IUMSScheduler::SetCompletionList, méthode  
 Affecte un `IUMSCompletionList` interface vers un planificateur de thread UMS.  
  
```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `pCompletionList`  
 Interface de la liste de saisie semi-automatique pour le planificateur. Il existe une liste unique par planificateur.  
  
### <a name="remarks"></a>Notes  
 Le Gestionnaire des ressources appellera cette méthode sur un planificateur qui indique les threads UMS, une fois que le planificateur a demandé une allocation initiale de ressources. Le planificateur peut utiliser le `IUMSCompletionList` interface pour déterminer quand les proxys de thread UMS ont été débloqués. Il est uniquement valide pour accéder à cette interface à partir d’un proxy de thread en cours d’exécution sur une racine de processeur virtuel assignée au planificateur UMS.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [IScheduler, Structure](ischeduler-structure.md)   
 [IUMSCompletionList, Structure](iumscompletionlist-structure.md)   
 [IResourceManager, structure](iresourcemanager-structure.md)
