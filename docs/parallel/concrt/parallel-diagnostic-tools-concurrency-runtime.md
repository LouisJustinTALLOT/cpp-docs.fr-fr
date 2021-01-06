---
description: 'En savoir plus sur : Parallel Outils de diagnostic (runtime d’accès concurrentiel)'
title: Outils de diagnostic parallèles (runtime d'accès concurrentiel)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: ac6afbbc2bfef3793e9685a7c9e1054b7d677bd8
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951517"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>Outils de diagnostic parallèles (runtime d'accès concurrentiel)

Visual Studio fournit une prise en charge complète des applications de débogage et de profilage multithread.

## <a name="debugging"></a>Débogage

Le débogueur Visual Studio comprend la fenêtre **Piles parallèles** , la fenêtre **tâches parallèles** et la fenêtre **Espion parallèle** . Pour plus d’informations, consultez [procédure pas à pas : débogage d’une application parallèle](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) et [Comment : utiliser la fenêtre Espion parallèle](/visualstudio/debugger/how-to-use-the-parallel-watch-window).

## <a name="profiling"></a>Profilage

Les outils de profilage fournissent trois vues de données qui affichent des informations graphiques, tabulaires et numériques sur la façon dont une application multithread interagit avec elle-même et avec d’autres programmes. Les affichages vous permettent d’identifier rapidement les zones de préoccupation et de naviguer à partir de points sur les affichages graphiques vers les piles d’appels, les sites d’appel et le code source. Pour plus d’informations, consultez [Visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer).

## <a name="event-tracing"></a>Suivi d’événements

Le runtime d’accès concurrentiel utilise [suivi d’v nements pour Windows](/windows/win32/ETW/event-tracing-portal) (ETW) pour notifier les outils d’instrumentation, tels que les profileurs, lorsque divers événements se produisent. Ces événements incluent le moment où un planificateur est activé ou désactivé, quand un contexte commence, se termine, se bloque ou produit, et quand un algorithme parallèle commence ou se termine.

Les outils, tels que le [visualiseur concurrentiel](/visualstudio/profiling/concurrency-visualizer) , utilisent cette fonctionnalité. par conséquent, vous n’avez généralement pas besoin de travailler directement avec ces événements. Toutefois, ces événements sont utiles quand vous développez un profileur personnalisé ou lorsque vous utilisez des outils de suivi d’événements tels que [Windows performance Toolkit](/windows-hardware/test/wpt/).

Le runtime d’accès concurrentiel déclenche ces événements uniquement lorsque le suivi est activé. Appelez la fonction [Concurrency :: EnableTracing,](reference/concurrency-namespace-functions.md#enabletracing) pour activer le suivi d’événements et la fonction [concurrency ::D isabletracing](reference/concurrency-namespace-functions.md#disabletracing) pour désactiver le suivi.

Le tableau suivant décrit les événements déclenchés par le runtime lorsque le suivi d’événements est activé :

|Événement|Description|Value|
|-----------|-----------------|-----------|
|[concurrence :: ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|Identificateur du fournisseur ETW pour le runtime d’accès concurrentiel.|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrence :: ContextEventGuid,](reference/concurrency-namespace-constants1.md#contexteventguid)|Marque les événements liés aux contextes.|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrence ::P PLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|Marque l’entrée et la sortie des appels à l’algorithme d' [accès concurrentiel ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrence ::P PLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Marque l’entrée et la sortie des appels à l’algorithme d' [accès concurrentiel ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) .|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrence ::P PLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Marque l’entrée et la sortie des appels à l’algorithme d' [accès concurrentiel ::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) .|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrence :: SchedulerEventGuid,](reference/concurrency-namespace-constants1.md#schedulereventguid)|Marque les événements liés au [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrence :: VirtualProcessorEventGuid,](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|Marque les événements liés aux processeurs virtuels.|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

Le runtime d’accès concurrentiel définit, mais ne déclenche pas actuellement, les événements suivants. Le runtime réserve ces événements pour une utilisation ultérieure :

- [concurrence :: ConcRTEventGuid,](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrence :: ScheduleGroupEventGuid,](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrence :: ChoreEventGuid,](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrence :: LockEventGuid,](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrence :: ResourceManagerEventGuid,](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

L’énumération [Concurrency :: ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype) spécifie les opérations possibles suivies par un événement. Par exemple, à l’entrée de l' `parallel_for` algorithme, le runtime déclenche l' `PPLParallelForEventGuid` événement et fournit `CONCRT_EVENT_START` comme opération. Avant le `parallel_for` retour de l’algorithme, le runtime déclenche à nouveau l' `PPLParallelForEventGuid` événement et fournit `CONCRT_EVENT_END` comme opération.

L’exemple suivant montre comment activer le traçage pour un appel à `parallel_for` . Le runtime n’effectue pas le suivi du premier appel à `parallel_for` , car il n’est pas activé. L’appel à `EnableTracing` permet au runtime de suivre le deuxième appel à `parallel_for` .

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

Le Runtime effectue le suivi du nombre de fois que vous appelez `EnableTracing` et `DisableTracing` . Par conséquent, si vous appelez `EnableTracing` plusieurs fois, vous devez appeler `DisableTracing` le même nombre de fois pour désactiver le suivi.

## <a name="see-also"></a>Voir aussi

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)
