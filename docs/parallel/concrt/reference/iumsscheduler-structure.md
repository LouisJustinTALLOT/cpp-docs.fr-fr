---
title: IUMSScheduler, Structure | Microsoft Docs
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
ms.openlocfilehash: 46ed7dac35dce4b5df51cd4c218a1a70a84d21df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079061"
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
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Assigne un `IUMSCompletionList` interface pour un planificateur de threads UMS.|  
  
## <a name="remarks"></a>Notes  
 Si vous implémentez un planificateur personnalisé qui communique avec le Gestionnaire de ressources, et que vous souhaitez que les threads UMS soient transmis à votre planificateur au lieu de threads Win32 ordinaires, vous devez fournir une implémentation de la `IUMSScheduler` interface. En outre, vous devez définir la valeur de stratégie pour la clé de stratégie du planificateur `SchedulerKind` être `UmsThreadDefault`. Si la stratégie spécifie le thread UMS, le `IScheduler` interface qui est passé en tant que paramètre à la [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) méthode doit être un `IUMSScheduler` interface.  
  
 Le Gestionnaire de ressources est en mesure de vous les threads UMS uniquement sur les systèmes d’exploitation qui ont la fonctionnalité UMS. les systèmes d’exploitation 64 bits avec la version Windows 7 et versions ultérieures prennent en charge des threads UMS. Si vous créez une stratégie du planificateur avec la `SchedulerKind` clé définie à la valeur `UmsThreadDefault` et la plateforme sous-jacente ne prend pas en charge UMS, la valeur de la `SchedulerKind` clé sur cette stratégie passera à la valeur `ThreadScheduler`. Vous devez toujours relire cette valeur de stratégie avant d’attendre de recevoir des threads UMS.  
  
 Le `IUMSScheduler` interface est une extrémité d’un canal bidirectionnel de communication entre un planificateur et le Gestionnaire de ressources. L’autre extrémité est représentée par le `IResourceManager` et `ISchedulerProxy` interfaces, qui sont implémentées par le Gestionnaire de ressources.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [IScheduler](ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="setcompletionlist"></a>  IUMSScheduler::SetCompletionList, méthode  
 Assigne un `IUMSCompletionList` interface pour un planificateur de threads UMS.  
  
```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*pCompletionList*<br/>
Interface de la liste de saisie semi-automatique pour le planificateur. Il existe une liste unique par planificateur.  
  
### <a name="remarks"></a>Notes  
 Le Gestionnaire des ressources appellera cette méthode sur un planificateur qui spécifie qu’il veut les threads UMS, une fois que le planificateur a demandé une allocation initiale de ressources. Le planificateur peut utiliser le `IUMSCompletionList` interface pour déterminer quand les proxys de thread UMS se sont débloqués. Il est uniquement valide pour accéder à cette interface à partir d’un proxy de thread en cours d’exécution sur une racine de processeur virtuel assignée au planificateur UMS.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [IScheduler, Structure](ischeduler-structure.md)   
 [IUMSCompletionList, Structure](iumscompletionlist-structure.md)   
 [IResourceManager, structure](iresourcemanager-structure.md)
