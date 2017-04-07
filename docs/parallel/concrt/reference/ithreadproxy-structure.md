---
title: IThreadProxy (Structure) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
dev_langs:
- C++
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 0a002dc4440b4784dee7f808a9e3be8dd4f89124
ms.lasthandoff: 03/17/2017

---
# <a name="ithreadproxy-structure"></a>IThreadProxy, structure
Abstraction d'un thread d'exécution. Selon la clé de stratégie `SchedulerType` du planificateur que vous créez, le gestionnaire des ressources vous accorde un proxy de thread assorti d'un thread Win32 standard ou d'un thread UMS (User-Mode Scheduling). Les threads UMS sont pris en charge sur les systèmes d'exploitation 64 bits avec Windows 7 et ses versions ultérieures.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IThreadProxy::GetId](#getid)|Retourne un identificateur unique pour le proxy de thread.|  
|[IThreadProxy::SwitchOut](#switchout)|Dissocie le contexte de la racine sous-jacente du processeur virtuel.|  
|[IThreadProxy::SwitchTo](#switchto)|Effectue un changement de contexte coopératif du contexte en cours d’exécution vers un autre.|  
|[IThreadProxy::YieldToSystem](#yieldtosystem)|Oblige le thread appelant à céder l'exécution à un autre thread prêt à s'exécuter sur le processeur actuel. Le système d’exploitation sélectionne le thread suivant à exécuter.|  
  
## <a name="remarks"></a>Remarques  
 Les proxys de thread sont associés aux contextes d’exécution représentés par l’interface `IExecutionContext` comme un moyen de distribuer le travail.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 `IThreadProxy`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="getid"></a>IThreadProxy::GetId, méthode  
 Retourne un identificateur unique pour le proxy de thread.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Identificateur entier unique.  
  
##  <a name="switchout"></a>IThreadProxy::SwitchOut, méthode  
 Dissocie le contexte de la racine sous-jacente du processeur virtuel.  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `switchState`  
 Indique l’état du proxy de thread qui exécute le commutateur. Le paramètre est de type `SwitchingProxyState`.  
  
### <a name="remarks"></a>Remarques  
 Utilisez `SwitchOut` si vous devez dissocier un contexte de la racine du processeur virtuel sur laquelle il s'exécute, quelle que soit la raison. Selon la valeur que vous passez dans le paramètre `switchState`, et peu importe s'il s'exécute ou non sur une racine du processeur virtuel, l'appel retourne immédiatement ou bloque le proxy de thread associé au contexte. C'est une erreur que d'appeler `SwitchOut` avec le jeu de paramètres défini sur `Idle`. Cela entraîne une [invalid_argument](../../../standard-library/invalid-argument-class.md) exception.  
  
 `SwitchOut` est utile lorsque vous souhaitez réduire le nombre de racines de processeur virtuel de votre planificateur, soit parce que le Gestionnaire des ressources vous a demandé de le faire, soit parce que vous avez demandé une racine de processeur virtuel sursouscrite temporaire et que vous n'en avez plus besoin. Dans ce cas, vous devez appeler la méthode [IVirtualProcessorRoot::Remove](http://msdn.microsoft.com/en-us/ad699b4a-1972-4390-97ee-9c083ba7d9e4) à la racine de processeur virtuel, avant d’effectuer un appel à `SwitchOut` avec le paramètre `switchState` la valeur `Blocking`. Cela bloquera le proxy de thread et il reprendra l'exécution lorsqu'une racine de processeur virtuel différente dans le planificateur sera disponible pour l'exécuter. Le proxy de thread bloquant peut être repris en appelant la fonction `SwitchTo` pour basculer vers le contexte d’exécution de ce proxy de thread. Vous pouvez également reprendre le proxy de thread, à l’aide de son contexte associé pour activer une racine de processeur virtuel. Pour plus d’informations sur la façon de procéder, consultez la page [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).  
  
 `SwitchOut` peut également être utilisé lorsque vous souhaitez réinitialiser le processeur virtuel afin qu'il puisse être activé à l'avenir en bloquant le proxy de thread ou en le détachant temporairement de la racine du processeur virtuel sur lequel il s'exécute, et du planificateur pour lequel il distribue le travail. Utilisez `SwitchOut` avec le paramètre `switchState` défini sur la valeur `Blocking` si vous voulez bloquer le proxy de thread. Il peut ensuite être redémarré en utilisant `SwitchTo` ou `IVirtualProcessorRoot::Activate` comme mentionné ci-dessus. Utilisez `SwitchOut` avec le jeu de paramètres défini sur `Nesting` lorsque vous souhaitez détacher temporairement ce proxy de thread de la racine de processeur virtuel sur lequel il s'exécute, et du planificateur auquel le processeur virtuel est associé. Appeler `SwitchOut` avec le paramètre `switchState` défini sur `Nesting` pendant son exécution sur une racine du processeur virtuel entraînera la réinitialisation de la racine, et le proxy du thread actuel continuera à s'exécuter sans nécessiter de racine. Le proxy de thread est considéré comme ayant quitté le planificateur jusqu'à ce qu’il appelle le [IThreadProxy::SwitchOut](#switchout) méthode avec `Blocking` à un moment ultérieur dans le temps. Le deuxième appel à `SwitchOut` avec le jeu de paramètres défini sur `Blocking` est conçu pour retourner le contexte vers un état bloqué afin qu'il puisse être repris par `SwitchTo` ou `IVirtualProcessorRoot::Activate` dans le planificateur dont il est détaché. Comme il ne s'exécutait pas sur une racine du processeur virtuel, aucune réinitialisation n'est effectuée.  
  
 Une racine de processeur virtuel réinitialisée n'est aucunement différente d'une racine de processeur virtuel toute neuve qui a été accordée à votre planificateur par le gestionnaire de ressources. Vous pouvez l'utiliser pour exécution en l'activant avec un contexte d'exécution en utilisant `IVirtualProcessorRoot::Activate`.  
  
 `SwitchOut`doit être appelée sur le `IThreadProxy` interface qui représente le thread en cours d’exécution ou les résultats sont indéfinis.  
  
 Dans les bibliothèques et les en-têtes fournis avec Visual Studio 2010, cette méthode ne prenait pas de paramètre et ne réinitialisait pas la racine du processeur virtuel. Pour conserver l'ancien comportement, la valeur de paramètre par défaut de `Blocking` est fournie.  
  
##  <a name="switchto"></a>IThreadProxy::SwitchTo, méthode  
 Effectue un changement de contexte coopératif du contexte en cours d’exécution vers un autre.  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `pContext`  
 Le contexte d’exécution pour basculer en coopération.  
  
 `switchState`  
 Indique l’état du proxy de thread qui exécute le commutateur. Le paramètre est de type `SwitchingProxyState`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour basculer d’un contexte d’exécution à l’autre à partir de la [IExecutionContext::Dispatch](iexecutioncontext-structure.md#dispatch) méthode du premier contexte d’exécution. La méthode associe le contexte d’exécution `pContext` avec un proxy de thread si elle ne l’est pas déjà. La propriété du proxy de thread actuel est déterminée par la valeur que vous spécifiez pour le `switchState` argument.  
  
 Utilisez la valeur `Idle` lorsque vous souhaitez renvoyer le proxy de thread en cours d’exécution pour le Gestionnaire de ressources. Appel de `SwitchTo` avec le paramètre `switchState` la valeur `Idle` entraîne le contexte d’exécution `pContext` pour démarrer l’exécution de la ressource d’exécution sous-jacente. La propriété de ce proxy de thread est transférée au Gestionnaire de ressources, et vous devez retourner à partir du contexte de l’exécution `Dispatch` méthode peu après `SwitchTo` retourne, afin de terminer le transfert. Le contexte d’exécution que le proxy de thread distribuait est dissocié du proxy de thread, et le planificateur est libre de le réutiliser ou détruire comme il convient.  
  
 Utilisez la valeur `Blocking` lorsque vous souhaitez que ce proxy de thread entre dans un état bloqué. Appel de `SwitchTo` avec le paramètre `switchState` la valeur `Blocking` entraîne le contexte d’exécution `pContext` pour démarrer l’exécution et bloquer le proxy de thread actuel jusqu'à sa reprise. Le planificateur conserve la propriété du proxy de thread lorsque le proxy de thread est dans la `Blocking` état. Le proxy de thread bloquant peut être repris en appelant la fonction `SwitchTo` pour basculer vers le contexte d’exécution de ce proxy de thread. Vous pouvez également reprendre le proxy de thread, à l’aide de son contexte associé pour activer une racine de processeur virtuel. Pour plus d’informations sur la façon de procéder, consultez la page [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).  
  
 Utilisez la valeur `Nesting` lorsque vous souhaitez détacher temporairement ce proxy de thread de la racine de processeur virtuel il s’exécute et le planificateur il distribue le travail. Appel de `SwitchTo` avec le paramètre `switchState` la valeur `Nesting` entraîne le contexte d’exécution `pContext` pour démarrer l’exécution et actuel proxy de thread poursuite de l’exécution sans la nécessité d’une racine de processeur virtuel. Le proxy de thread est considéré comme ayant quitté le planificateur jusqu'à ce qu’il appelle le [IThreadProxy::SwitchOut](#switchout) méthode à un moment ultérieur dans le temps. Le `IThreadProxy::SwitchOut` méthode pourrait bloquer le proxy de thread jusqu'à ce qu’une racine de processeur virtuel soit disponible pour le replanifier.  
  
 `SwitchTo`doit être appelée sur le `IThreadProxy` interface qui représente le thread en cours d’exécution ou les résultats sont indéfinis. La fonction lève `invalid_argument` si le paramètre `pContext` est défini sur `NULL`.  
  
##  <a name="yieldtosystem"></a>IThreadProxy::YieldToSystem, méthode  
 Oblige le thread appelant à céder l'exécution à un autre thread prêt à s'exécuter sur le processeur actuel. Le système d’exploitation sélectionne le thread suivant à exécuter.  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>Remarques  
 Lorsqu’elle est appelée par un proxy de thread soutenu par un thread Windows normal, `YieldToSystem` se comporte exactement comme la fonction Windows `SwitchToThread`. Toutefois, lorsqu’elle est appelée à partir de threads planifiables de (UMS) en mode utilisateur, le `SwitchToThread` fonction délègue la tâche de choisir le prochain thread pour exécuter le Planificateur de mode utilisateur, pas le système d’exploitation. Pour obtenir l’effet souhaité du basculement vers un autre thread prêt dans le système, utilisez `YieldToSystem`.  
  
 `YieldToSystem`doit être appelée sur le `IThreadProxy` interface qui représente le thread en cours d’exécution ou les résultats sont indéfinis.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [IExecutionContext (Structure)](iexecutioncontext-structure.md)   
 [IScheduler (Structure)](ischeduler-structure.md)   
 [IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)

