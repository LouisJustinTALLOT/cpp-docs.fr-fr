---
title: Outils de Diagnostic (Runtime d’accès concurrentiel) parallèles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb41f9630e22d9067743b106aed49ea9c51ee4ae
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538469"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Outils de diagnostic parallèles (runtime d'accès concurrentiel)
Visual Studio fournit une prise en charge complète des applications de débogage et de profilage multithread.  
  
## <a name="debugging"></a>Débogage  
 Le débogueur Visual Studio inclut la **piles parallèles** fenêtre, **tâches parallèles** fenêtre, et **espion parallèle** fenêtre. Pour plus d’informations, consultez [procédure pas à pas : débogage d’une Application parallèle](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) et [Comment : utiliser la fenêtre Espion parallèle](/visualstudio/debugger/how-to-use-the-parallel-watch-window).  
  
## <a name="profiling"></a>Profilage  
 Les outils de profilage fournissent trois vues de données qui affichent des informations graphiques, tabulaires et numériques sur la façon dont une application multithread interagit avec elle-même et avec d’autres programmes. Les vues vous permettent d’identifier rapidement les zones posant problème et de naviguer à partir de points sur les affichages graphiques pour les piles d’appels, appellent sites et le code source. Pour plus d’informations, consultez [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="event-tracing"></a>Suivi d’événements  
 Le Runtime d’accès concurrentiel utilise [suivi d’événements pour Windows](http://msdn.microsoft.com/library/windows/desktop/bb968803) (ETW) pour informer les outils d’instrumentation, tels que les profileurs, lorsque certains événements se produisent. Ces événements incluent un planificateur est activé ou désactivé, lorsqu’un contexte commence, se termine, bloque, débloque ou cède, et lorsqu’un algorithme parallèle commence ou se termine.  
  
 Des outils tels que le [visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer) utilisent cette fonctionnalité ; par conséquent, en général pas avoir à travailler directement avec ces événements. Toutefois, ces événements sont utiles lorsque vous développez un profileur personnalisé ou lorsque vous utilisez comme outils de suivi d’événements [Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628).  
  
 Le Runtime d’accès concurrentiel déclenche ces événements uniquement lorsque le traçage est activé. Appelez le [concurrency::EnableTracing](reference/concurrency-namespace-functions.md#enabletracing) (fonction) pour activer le suivi d’événements et le [concurrency::DisableTracing](reference/concurrency-namespace-functions.md#disabletracing) (fonction) pour désactiver le suivi.  
  
 Le tableau suivant décrit les événements que le runtime déclenche lorsque le suivi d’événements est activé :  
  
|Événement|Description|Value|  
|-----------|-----------------|-----------|  

|[Concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)| L’identificateur du fournisseur ETW pour le Runtime d’accès concurrentiel. |`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[Concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)| Marque les événements qui sont associés aux contextes. |`5727a00f-50be-4519-8256-f7699871fecb`|  
|[Concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)| Marque le début et la fin des appels à la [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme. |`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[Concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)| Marque le début et la fin des appels à la [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme. |`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[Concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)| Marque le début et la fin des appels à la [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorithme. |`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[Concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)| Marque les événements qui sont liées à la [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md). |`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[Concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)| Marque les événements qui sont associés aux processeurs virtuels. |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 Le Runtime d’accès concurrentiel définit, mais ne pas actuellement déclenche, les événements suivants. Le runtime réserve ces événements pour une utilisation ultérieure :  
  
-   [Concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)  
  
-   [Concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)  
  
-   [Concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)  
  
-   [Concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)  
  
-   [Concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)  
  
 Le [concurrency::ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) énumération spécifie les opérations qu’un événement effectue le suivi. Par exemple, à l’entrée de la `parallel_for` algorithme, le runtime déclenche le `PPLParallelForEventGuid` événement et fournit `CONCRT_EVENT_START` en tant que l’opération. Avant du `parallel_for` algorithme retourne, le runtime déclenche à nouveau le `PPLParallelForEventGuid` événement et fournit `CONCRT_EVENT_END` en tant que l’opération.  
  
 L’exemple suivant montre comment activer le suivi pour un appel à `parallel_for`. Le runtime ne suit le premier appel à `parallel_for` car le suivi n’est ne pas activé. L’appel à `EnableTracing` permet au runtime de suivi du deuxième appel à `parallel_for`.  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 Le runtime suit le nombre de fois que vous appelez `EnableTracing` et `DisableTracing`. Par conséquent, si vous appelez `EnableTracing` plusieurs fois, vous devez appeler `DisableTracing` le même nombre de fois afin de désactiver le suivi.  
  
## <a name="see-also"></a>Voir aussi  
 [Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)

