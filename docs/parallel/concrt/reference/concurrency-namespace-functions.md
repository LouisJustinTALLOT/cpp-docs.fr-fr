---
title: concurrency, fonctions de l’espace de noms
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
ms.openlocfilehash: 15b265744640628425502706d69fd98a1c64bda2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374370"
---
# <a name="concurrency-namespace-functions"></a>concurrency, fonctions de l’espace de noms

||||
|-|-|-|
|[Alloc](#alloc)|[CréerResourceManager](#createresourcemanager)|[Désactiver](#disabletracing)|
|[EnableTracing (en)](#enabletracing)|[Gratuit](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[GetOSVersion (en)](#getosversion)|[GetProcessorCount (en)](#getprocessorcount)|[GetProcessorNodeCount (en)](#getprocessornodecount)|
|[GetSchedulerId GetSchedulerId GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[Clair](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[Parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[Parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[Recevoir](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[envoyer](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[Attendre](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

## <a name="alloc"></a><a name="alloc"></a>Alloc

Alloue un bloc de mémoire de la taille spécifiée depuis le sous-allocateur de mise en cache du runtime d'accès concurrentiel.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Paramètres

*_NumBytes*<br/>
Le nombre d’octets de mémoire à allouer.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la mémoire nouvellement allouée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les scénarios de votre application qui pourraient bénéficier de l’utilisation du suballocateur de cachage, voir [Task Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a><a name="asend"></a>asend

Opération d’envoi asynchrone qui planifie une tâche pour propager les données vers le bloc cible.

```cpp
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à envoyer.

*_Trg*<br/>
Un pointeur ou une référence à la cible à laquelle les données sont envoyées.

*_Data*<br/>
Une référence aux données à envoyer.

### <a name="return-value"></a>Valeur de retour

**vrai** si le message a été accepté avant le retour de la méthode, **faux** autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Fonctions de passage de message](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a><a name="cancel_current_task"></a>cancel_current_task

Annule la tâche en cours d’exécution. Cette fonction peut être appelée à partir du corps d'une tâche pour annuler l'exécution de la tâche et la faire passer à l'état `canceled`.

L'appel de cette fonction en dehors du corps d'un objet `task` n'est pas pris en charge. Cela entraînerait un comportement non défini tel qu'un blocage dans votre application.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a><a name="clear"></a>Clair

Efface la file d’attente simultanée, détruisant tous les éléments actuellement enqueued. Cette méthode n’est pas de la concurrence-sûr.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Paramètres

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a><a name="create_async"></a>create_async

Crée une construction asynchrone Windows Runtime basée sur un objet lambda ou de fonction fourni par l'utilisateur. Le type de retour de `create_async` est `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` ou `IAsyncOperationWithProgress<TResult, TProgress>^` selon la signature de l’objet lambda passée à la méthode.

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type.

*_Func*<br/>
Objet lambda ou de fonction à partir duquel créer une construction asynchrone Windows Runtime.

### <a name="return-value"></a>Valeur de retour

Une construction asynchrone représentée par un IAsyncActionMD, IAsyncActionWithProgress\<TProgress>, IAsyncOperation\<TResult>, ou une IAsyncOperationWithProgress\<TResult, TProgress>. L'interface retournée dépend de la signature de l'objet lambda passé dans la fonction.

### <a name="remarks"></a>Notes

Le type de retour de l’objet lambda détermine si la construction est une action ou une opération.

Les objets lambda qui retournent void provoquent la création d'actions. Les objets lambda qui retournent un résultat de type `TResult` provoquent la création d'opérations TResult.

L’objet lambda peut également retourner un résultat `task<TResult>` qui encapsule le travail asynchrone en lui-même ou qui est la continuation d’une chaîne de tâches représentant le travail asynchrone. Dans ce cas, l'objet lambda lui-même est exécuté en ligne, car les tâches sont celles exécutées de façon asynchrone et le type de retour de l'objet lambda est désencapsulé afin de produire la construction asynchrone retournée par `create_async`. Cela implique qu’un lambda\<qui retourne un vide de tâche> provoquera la création\<d’actions, et un lambda qui retourne une tâche TResult> provoquera la création d’opérations de TResult.

L’objet lambda peut prendre zéro, un ou deux arguments. Les arguments valides sont `progress_reporter<TProgress>` et `cancellation_token`, dans cet ordre si les deux sont utilisés. Un objet lambda sans arguments provoque la création d’une construction asynchrone sans la capacité de créer un rapport de progression. Un lambda qui prend une\<progress_reporter TProgress> `create_async` provoquera de retourner une construction asynchrone qui rapporte `report` l’avancement du type TProgress chaque fois que la méthode de l’objet progress_reporter est appelée. Un objet lambda qui prend un argument cancellation_token peut l’utiliser pour vérifier l’annulation, ou le passer aux tâches qu’il crée afin que l’annulation de la construction asynchrone provoque l’annulation de ces tâches.

Si le corps de l’objet lambda ou fonction\<renvoie un résultat (et non une tâche TResult>), le lamdba sera exécuté asynchronement dans le processus MTA dans le cadre d’une tâche que le Runtime crée implicitement pour elle. La méthode `IAsyncInfo::Cancel` provoquera l’annulation de la tâche implicite.

Si le corps de l'objet lambda retourne une tâche, l'objet lamba s'exécute en ligne, et si vous déclarez que l'objet lambda prend un argument de type `cancellation_token`, vous pouvez déclencher l'annulation de toutes les tâches que vous créez au sein de l'objet lambda en passant ce jeton lorsque vous créez les tâches. Vous pouvez également utiliser la méthode `register_callback` sur le jeton pour forcer le runtime à effectuer un rappel lorsque vous appelez `IAsyncInfo::Cancel` sur l'opération ou l'action asynchrone produite.

Cette fonction n’est disponible que pour les applications Windows Runtime.

## <a name="createresourcemanager"></a><a name="createresourcemanager"></a>CréerResourceManager

Retourne une interface qui représente l'instance singleton du gestionnaire des ressources du runtime d'accès concurrentiel. Le gestionnaire des ressources est responsable de l'affectation des ressources aux planificateurs qui veulent coopérer.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Valeur de retour

Interface `IResourceManager`.

### <a name="remarks"></a>Notes

Plusieurs appels subséquents à cette méthode retourneront le même cas du gestionnaire des ressources. Chaque appel à la méthode incrémente un compte de référence sur le gestionnaire de ressources, et doit être jumelé à un appel à [l’IResourceManager::Release](iresourcemanager-structure.md) méthode lorsque votre planificateur a terminé de communiquer avec le gestionnaire de ressources.

[unsupported_os](unsupported-os-class.md) est lancé si le système d’exploitation n’est pas pris en charge par le Temps d’exécution de concurrency.

## <a name="create_task"></a><a name="create_task"></a>create_task

Crée un objet [de tâche](task-class.md) PPL. `create_task` peut être utilisé partout où vous auriez utilisé un constructeur de tâche. Il est fourni principalement pour des raisons pratiques, car il permet d'utiliser le mot clé `auto` pendant la création de tâches.

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type du paramètre à partir duquel la tâche doit être construite.

*_ReturnType*<br/>
Type.

*_Param*<br/>
Paramètre à partir duquel la tâche doit être construite. Il peut s’agir d’un `task_completion_event` lambda `task` ou d’un objet de fonction, d’un objet, d’un objet différent ou d’un Windows ::Foundation::IAsyncInfo interface si vous utilisez des tâches dans votre application UWP.

*_TaskOptions*<br/>
Les options de tâche.

*_Task*<br/>
Tâche à créer.

### <a name="return-value"></a>Valeur de retour

Une nouvelle tâche `T`de type , `_Param`qui est déduit de .

### <a name="remarks"></a>Notes

La première surcharge se comporte comme un constructeur de tâches qui prend un seul paramètre.

La deuxième surcharge associe le jeton d’annulation fourni avec la tâche nouvellement créée. Si vous utilisez cette surcharge, vous n’êtes `task` pas autorisé à passer dans un autre objet comme premier paramètre.

Le type de tâche retournée est déduit du premier paramètre à la fonction. Si `_Param` est `task_completion_event<T>`un `task<T>`, un , ou `T` un `task<T>`functor qui retourne `task<T>`soit type ou , le type de la tâche créée est .

Dans `_Param` une application UWP, si est de type Windows::Foundation::IAsyncOperation\<T>ou Windows::Foundation::IAsyncOperationWithProgress\<T,P>, ou un functor qui retourne `task<T>`l’un de ces types, la tâche créée sera de type . Si `_Param` est de type Windows::Foundation::IAsyncAction OU Windows::Foundation::IAsyncActionWithProgress\<P>, ou un functor qui retourne l’un de ces types, la tâche créée aura le type `task<void>`.

## <a name="disabletracing"></a><a name="disabletracing"></a>Désactiver

Désactive le traçage dans le runtime d'accès concurrentiel. Cette fonction est déconseillée car le suivi ETW est désinscrit par défaut.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Valeur de retour

Si le traçage `S_OK` a été correctement désactivé, est retourné. Si le traçage `E_NOT_STARTED` n’a pas été amorcé précédemment, est retourné

## <a name="enabletracing"></a><a name="enabletracing"></a>EnableTracing (en)

Active le traçage dans le runtime d'accès concurrentiel. Cette fonction est déconseillée car le suivi ETW est à présent activé par défaut.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Valeur de retour

Si le tracé `S_OK` a été correctement amorcé, est retourné; sinon, `E_NOT_STARTED` est retourné.

## <a name="free"></a><a name="free"></a>Gratuit

Libère un bloc de mémoire précédemment alloué par la méthode `Alloc` au sous-allocateur de mise en cache du runtime d'accès concurrentiel.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Paramètres

*_PAllocation*<br/>
Un pointeur à la `Alloc` mémoire précédemment attribué par la méthode qui doit être libérée. Si le `_PAllocation` paramètre est `NULL`réglé à la valeur, cette méthode l’ignorera et reviendra immédiatement.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les scénarios de votre application qui pourraient bénéficier de l’utilisation du suballocateur de cachage, voir [Task Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a><a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Valeur de retour

## <a name="getexecutioncontextid"></a><a name="getexecutioncontextid"></a>GetExecutionContextId

Retourne un identificateur unique qui peut être affecté à un contexte d'exécution qui implémente l'interface `IExecutionContext`.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Valeur de retour

Un identifiant unique pour un contexte d’exécution.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour obtenir un identifiant pour `IExecutionContext` votre contexte d’exécution avant de passer une interface comme paramètre à l’une des méthodes offertes par le gestionnaire de ressources.

## <a name="getosversion"></a><a name="getosversion"></a>GetOSVersion (en)

Retourne la version du système d'exploitation.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Valeur de retour

Une valeur énumérée représentant le système d’exploitation.

### <a name="remarks"></a>Notes

[unsupported_os](unsupported-os-class.md) est lancé si le système d’exploitation n’est pas pris en charge par le Temps d’exécution de concurrency.

## <a name="getprocessorcount"></a><a name="getprocessorcount"></a>GetProcessorCount (en)

Retourne le nombre de threads matériels sur le système sous-jacent.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de fils matériels.

### <a name="remarks"></a>Notes

[unsupported_os](unsupported-os-class.md) est lancé si le système d’exploitation n’est pas pris en charge par le Temps d’exécution de concurrency.

## <a name="getprocessornodecount"></a><a name="getprocessornodecount"></a>GetProcessorNodeCount (en)

Retourne le nombre de nœuds NUMA ou de packages de processeurs sur le système sous-jacent.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre de nœuds NUMA ou de paquets de processeurs.

### <a name="remarks"></a>Notes

Si le système contient plus de nœuds NUMA que les paquets de processeur, le nombre de nœuds NUMA est retourné, sinon, le nombre de paquets de processeur est retourné.

[unsupported_os](unsupported-os-class.md) est lancé si le système d’exploitation n’est pas pris en charge par le Temps d’exécution de concurrency.

## <a name="getschedulerid"></a><a name="getschedulerid"></a>GetSchedulerId GetSchedulerId GetSchedulerId

Retourne un identificateur unique qui peut être affecté à un planificateur qui implémente l'interface `IScheduler`.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Valeur de retour

Un identifiant unique pour un planificateur.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour obtenir un identifiant pour `IScheduler` votre planificateur avant de passer une interface comme paramètre à l’une des méthodes offertes par le gestionnaire de ressources.

## <a name="internal_assign_iterators"></a><a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>Paramètres

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*first*<br/>

*last*<br/>

## <a name="interruption_point"></a><a name="interruption_point"></a>interruption_point

Crée un point d'interruption pour l'annulation. Si une annulation est en cours dans le contexte dans lequel cette fonction est appelée, une exception interne est levée et annule l'exécution du travail parallèle en cours. Si aucune annulation n'est en cours, la fonction ne fait rien.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Notes

Vous ne devez pas attraper l’exception d’annulation interne jetée par la `interruption_point()` fonction. L’exception sera prise et manipulée par le temps d’exécution, et l’attraper peut causer votre programme de se comporter anormalement.

## <a name="is_current_task_group_canceling"></a><a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

Retourne une indication qui détermine si le groupe de tâches qui s'exécute actuellement inline sur le contexte actuel est au beau milieu d'une annulation active (ou le sera bientôt). Notez que si aucun groupe de tâches ne s'exécute actuellement inline sur le contexte actuel, `false` est retourné.

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Valeur de retour

**vrai** si le groupe de travail qui exécute actuellement est annulée, **faux** sinon.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Annulation](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a><a name="make_choice"></a>make_choice

Construit un bloc de messagerie `choice` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.

```cpp
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Paramètres

*T1*<br/>
Le type de bloc de message de la première source.

*T2 T2*<br/>
Le type de bloc de message de la deuxième source.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `choice` est planifiée.

*_Item1*<br/>
Première source.

*_Item2*<br/>
Deuxième source.

*_Items*<br/>
D’autres sources.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `choice` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="return-value"></a>Valeur de retour

Un `choice` bloc de messages avec deux sources d’entrée ou plus.

## <a name="make_greedy_join"></a><a name="make_greedy_join"></a>make_greedy_join

Construit un bloc de messagerie `greedy multitype_join` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>Paramètres

*T1*<br/>
Le type de bloc de message de la première source.

*T2 T2*<br/>
Le type de bloc de message de la deuxième source.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée.

*_Item1*<br/>
Première source.

*_Item2*<br/>
Deuxième source.

*_Items*<br/>
D’autres sources.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="return-value"></a>Valeur de retour

Un `greedy multitype_join` bloc de messages avec deux sources d’entrée ou plus.

## <a name="make_join"></a><a name="make_join"></a>make_join

Construit un bloc de messagerie `non_greedy multitype_join` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Paramètres

*T1*<br/>
Le type de bloc de message de la première source.

*T2 T2*<br/>
Le type de bloc de message de la deuxième source.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée.

*_Item1*<br/>
Première source.

*_Item2*<br/>
Deuxième source.

*_Items*<br/>
D’autres sources.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="return-value"></a>Valeur de retour

Un `non_greedy multitype_join` bloc de messages avec deux sources d’entrée ou plus.

## <a name="make_task"></a><a name="make_task"></a>make_task

Méthode de fabrique pour la création d'un objet `task_handle`.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Le type de l’objet de fonction qui sera invoqué `task_handle` pour exécuter l’œuvre représentée par l’objet.

*_Func*<br/>
La fonction qui sera invoquée pour exécuter `task_handle` l’œuvre représentée par l’objet. Il peut s’agir d’un functor lambda, d’un pointeur d’une `void operator()()`fonction ou de tout objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature .

### <a name="return-value"></a>Valeur de retour

Objet `task_handle` .

### <a name="remarks"></a>Notes

Cette fonction est utile lorsque `task_handle` vous avez besoin de créer un objet avec une expression lambda, car il vous permet de créer l’objet sans connaître le vrai type de functor lambda.

## <a name="parallel_buffered_sort"></a><a name="parallel_buffered_sort"></a>parallel_buffered_sort

Organise les éléments dans une plage spécifiée dans un ordre non descendant, ou selon un critère de commande spécifié par un prédicat binaire, en parallèle. Cette fonction est sémantiquement similaire à `std::sort` en ce sens qu'il s'agit d'un tri sur place, par comparaison et instable, à l'exception près qu'elle a besoin d'un espace supplémentaire `O(n)` et qu'elle requiert une initialisation par défaut pour les éléments triés.

```cpp
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Paramètres

*_Random_iterator*<br/>
Le type itérateur de la plage d’entrée.

*_Allocator*<br/>
Le type d’un alloueur de mémoire compatible pour la Bibliothèque standard.

*_Function*<br/>
Le type de comparateur binaire.

*_Begin*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*_End*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier.

*_Alloc*<br/>
Un exemple d’un alloueur de mémoire compatible pour la Bibliothèque Standard.

*_Func*<br/>
Objet de fonction prédicatif défini par l’utilisateur qui définit le critère de comparaison à satisfaire par des éléments successifs dans la commande. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas. Cette fonction de comparaison doit imposer un ordre faible strict sur les paires d’éléments de la séquence.

*_Chunk_size*<br/>
La taille mimimum d’un morceau qui sera divisé en deux pour l’exécution parallèle.

### <a name="remarks"></a>Notes

Toutes les surcharges nécessitent `n * sizeof(T)` `n` un espace supplémentaire, où est `T` le nombre d’éléments à trier, et est le type d’élément. Dans la plupart des cas, parallel_buffered_sort affichera une amélioration des performances par rapport [à parallel_sort,](concurrency-namespace-functions.md)et vous devriez l’utiliser sur parallel_sort si vous avez la mémoire disponible.

Si vous ne fournissez `std::less` pas un comparateur binaire est utilisé comme `operator<()`par défaut, ce qui nécessite le type d’élément pour fournir l’opérateur .

Si vous ne fournissez pas de type d’alloueur `std::allocator<T>` ou d’instance, l’alloueur de mémoire de la Bibliothèque standard de CMD est utilisé pour allouer le tampon.

L’algorithme divise la plage d’entrée en deux morceaux et divise successivement chaque morceau en deux sous-morceaux pour l’exécution en parallèle. L’argument `_Chunk_size` facultatif peut être utilisé pour indiquer à l’algorithme `_Chunk_size` qu’il doit gérer des morceaux de taille < en série.

## <a name="parallel_for"></a><a name="parallel_for"></a>Parallel_for

`parallel_for` effectue une itération sur une plage d'index et exécute une fonction fournie par l'utilisateur à chaque itération, en parallèle.

```cpp
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>Paramètres

*_Index_type*<br/>
Le type d’index utilisé pour l’itération.

*_Function*<br/>
Le type de fonction qui sera exécuté à chaque itération.

*_Partitioner*<br/>
Le type de partitionneur qui est utilisé pour diviser la gamme fournie.

*first*<br/>
Le premier indice à être inclus dans l’itération.

*last*<br/>
L’indice un passé le dernier indice à inclure dans l’itération.

*_Step*<br/>
La valeur par laquelle marcher lors `first` `last`de l’itération de . L’étape doit être positive. [invalid_argument](../../../standard-library/invalid-argument-class.md) est lancée si l’étape est inférieure à 1.

*_Func*<br/>
La fonction à exécuter à chaque itération. Il peut s’agir d’une expression lambda, d’un pointeur de `void operator()(_Index_type)`fonction ou de tout objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature .

*_Part*<br/>
Référence au partitionneur d'objet. L’argument peut `const`être l’un `const`des [auto_partitioner](auto-partitioner-class.md)`&` `const`, [static_partitioner](static-partitioner-class.md)`&`, [simple_partitioner](simple-partitioner-class.md) `&` ou [affinity_partitioner](affinity-partitioner-class.md) `&` Si un objet [affinity_partitioner](affinity-partitioner-class.md) est utilisé, la référence doit être une référence non-const l-valeur, de sorte que l’algorithme peut stocker l’état pour les boucles futures à réutiliser.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Algorithmes parallèles](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a><a name="parallel_for_each"></a>parallel_for_each

`parallel_for_each` applique une fonction spécifiée à chaque élément dans une plage, en parallèle. Sémantiquement, elle équivaut à la fonction `for_each` dans l'espace de noms `std`, si ce n'est que l'itération des éléments est effectuée en parallèle et que l'ordre d'itération n'est pas spécifié. L’argument `_Func` doit prendre en charge un opérateur d’appel de fonction sous la forme de `operator()(T)` où le paramètre `T` est le type d’élément du conteneur en cours d’itération.

```cpp
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>Paramètres

*_Iterator*<br/>
Le type d’itérateur utilisé pour itérer sur le conteneur.

*_Function*<br/>
Le type de fonction qui sera appliqué à chaque élément dans la plage.

*_Partitioner*<br/>
*first*<br/>
Un itérateur traitant de la position du premier élément à inclure dans l’itération parallèle.

*last*<br/>
Un itérateur traitant de la position un passé l’élément final à inclure dans l’itération parallèle.

*_Func*<br/>
Un objet de fonction défini par l’utilisateur qui est appliqué à chaque élément de la plage.

*_Part*<br/>
Référence au partitionneur d'objet. L’argument peut `const`être l’un `const`des [auto_partitioner](auto-partitioner-class.md)`&` `const`, [static_partitioner](static-partitioner-class.md)`&`, [simple_partitioner](simple-partitioner-class.md) `&` ou [affinity_partitioner](affinity-partitioner-class.md) `&` Si un objet [affinity_partitioner](affinity-partitioner-class.md) est utilisé, la référence doit être une référence non-const l-valeur, de sorte que l’algorithme peut stocker l’état pour les boucles futures à réutiliser.

### <a name="remarks"></a>Notes

[auto_partitioner](auto-partitioner-class.md) sera utilisé pour la surcharge sans partitionneur explicite.

Pour les itérateurs qui ne prennent pas en charge l’accès aléatoire, seul [auto_partitioner](auto-partitioner-class.md) est pris en charge.

Pour plus d’informations, voir [Algorithmes parallèles](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a><a name="parallel_invoke"></a>Parallel_invoke

Exécute les objets de fonction fournis comme paramètres en parallèle et se bloque jusqu'à la fin de leur exécution. Chaque objet de fonction peut être une expression lambda, un pointeur vers une fonction ou tout objet qui prend en charge l’opérateur d’appel de fonction avec la signature `void operator()()`.

```cpp
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>Paramètres

*_Function1*<br/>
Le type du premier objet de fonction à exécuter en parallèle.

*_Function2*<br/>
Le type de deuxième objet de fonction à exécuter en parallèle.

*_Function3*<br/>
Le type de troisième objet de fonction à exécuter en parallèle.

*_Function4*<br/>
Le type de quatrième objet de fonction à exécuter en parallèle.

*_Function5*<br/>
Le type de l’objet de la cinquième fonction à exécuter en parallèle.

*_Function6*<br/>
Le type de l’objet de la sixième fonction à exécuter en parallèle.

*_Function7*<br/>
Le type de septième objet de fonction à exécuter en parallèle.

*_Function8*<br/>
Le type de l’objet de la huitième fonction à exécuter en parallèle.

*_Function9*<br/>
Le type de neuvième objet de fonction à exécuter en parallèle.

*_Function10*<br/>
Le type de l’objet de la dixième fonction à exécuter en parallèle.

*_Func1*<br/>
Le premier objet de fonction à exécuter en parallèle.

*_Func2*<br/>
La deuxième fonction s’oppose à exécuter en parallèle.

*_Func3*<br/>
La troisième fonction s’oppose à l’exécution en parallèle.

*_Func4*<br/>
Le quatrième objet de fonction à exécuter en parallèle.

*_Func5*<br/>
Le cinquième objet de fonction à exécuter en parallèle.

*_Func6*<br/>
Le sixième objet de fonction à exécuter en parallèle.

*_Func7*<br/>
Le septième objet de fonction à exécuter en parallèle.

*_Func8*<br/>
Le huitième objet de fonction à exécuter en parallèle.

*_Func9*<br/>
La neuvième fonction s’oppose à exécuter en parallèle.

*_Func10*<br/>
Le dixième objet de fonction à exécuter en parallèle.

### <a name="remarks"></a>Notes

Notez qu’un ou plusieurs des objets de fonction fournis sous forme de paramètres peuvent s’exécuter en ligne sur le contexte de l’appel.

Si un ou plusieurs des objets de fonction transmis comme paramètres de cette fonction jette une exception, le temps d’exécution sélectionnera une telle exception de son choix et le propager hors de l’appel à `parallel_invoke`.

Pour plus d’informations, voir [Algorithmes parallèles](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a><a name="parallel_radixsort"></a>parallel_radixsort

Réorganise les éléments d'une plage spécifiée dans un ordre non décroissant à l'aide d'un algorithme de tri de base. Il s'agit d'une fonction de tri stable qui requiert une fonction de projection capable de projeter les éléments à trier dans des clés de type entiers non signés. L'initialisation par défaut est requise pour les éléments triés.

```cpp
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>Paramètres

*_Random_iterator*<br/>
Le type itérateur de la plage d’entrée.

*_Allocator*<br/>
Le type d’un alloueur de mémoire compatible pour la Bibliothèque standard.

*_Function*<br/>
Le type de fonction de projection.

*_Begin*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*_End*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier.

*_Alloc*<br/>
Un exemple d’un alloueur de mémoire compatible pour la Bibliothèque Standard.

*_Proj_func*<br/>
Un objet de fonction de projection défini par l’utilisateur qui convertit un élément en valeur intégrale.

*_Chunk_size*<br/>
La taille mimimum d’un morceau qui sera divisé en deux pour l’exécution parallèle.

### <a name="remarks"></a>Notes

Toutes les surcharges nécessitent `n * sizeof(T)` `n` un espace supplémentaire, où est `T` le nombre d’éléments à trier, et est le type d’élément. Un functor de projection `I _Proj_func(T)` nonary avec la signature est exigé `T` pour retourner `I` une clé une fois donné un élément, où est le type d’élément et est un type insigned-like.

Si vous ne fournissez pas de fonction de projection, une fonction de projection par défaut qui renvoie simplement l’élément est utilisée pour les types intégrals. La fonction ne sera pas compilée si l’élément n’est pas un type intégral en l’absence d’une fonction de projection.

Si vous ne fournissez pas de type d’alloueur `std::allocator<T>` ou d’instance, l’alloueur de mémoire de la Bibliothèque standard de CMD est utilisé pour allouer le tampon.

L’algorithme divise la plage d’entrée en deux morceaux et divise successivement chaque morceau en deux sous-morceaux pour l’exécution en parallèle. L’argument `_Chunk_size` facultatif peut être utilisé pour indiquer à l’algorithme `_Chunk_size` qu’il doit gérer des morceaux de taille < en série.

## <a name="parallel_reduce"></a><a name="parallel_reduce"></a>parallel_reduce

Calcule la somme de tous les éléments d'une plage spécifiée en calculant des sommes partielles successives, ou calcule le résultat des résultats partiels successifs obtenus de la même façon en utilisant une opération binaire spécifiée autre que la somme, en parallèle. `parallel_reduce` est sémantiquement similaire à `std::accumulate`, à l'exception près qu'elle a besoin que l'opération binaire soit associative et qu'elle requiert une valeur d'identité au lieu d'une valeur initiale.

```cpp
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>Paramètres

*_Forward_iterator*<br/>
Le type itérateur de gamme d’entrée.

*_Sym_reduce_fun*<br/>
Le type de la fonction de réduction symétrique. Il doit s’agir `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`d’un type de fonction avec signature, où _Reduce_type est le même que le type d’identité et le type de résultat de la réduction. Pour la troisième surcharge, cela devrait être `_Range_reduce_fun`compatible avec le type de sortie de .

*_Reduce_type*<br/>
Le type auquel l’entrée sera réduit, ce qui peut être différent du type d’élément d’entrée. La valeur de rendement et la valeur d’identité auront ce type.

*_Range_reduce_fun*<br/>
Le type de fonction de réduction de la plage. Il doit s’agir `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`d’un type de fonction avec signature, _Reduce_type est le même que le type d’identité et le type de résultat de la réduction.

*_Begin*<br/>
Un itérateur d’entrée traitant du premier élément de la plage à réduire.

*_End*<br/>
Un itérateur d’entrée répondant à l’élément qui est une position au-delà de l’élément final de la plage à réduire.

*_Identity*<br/>
La valeur `_Identity` d’identité est du même type que `value_type` le type de résultat de la réduction et aussi de l’itérateur pour les premières et deuxième surcharges. Pour la troisième surcharge, la valeur d’identité doit avoir le même type que `value_type` le type de résultat de la réduction, mais peut être différente de l’itérateur. Il doit avoir une valeur appropriée `_Range_fun`de telle sorte que l’opérateur `value_type` de réduction de la plage , lorsqu’il `value_type` est appliqué à une gamme d’un seul élément de type et la valeur d’identité, se comporte comme un type de distribution de la valeur du type au type d’identité.

*_Sym_fun*<br/>
La fonction symétrique qui sera utilisée dans la seconde de la réduction. Consultez remarques pour plus d’informations.

*_Range_fun*<br/>
La fonction qui sera utilisée dans la première phase de la réduction. Consultez remarques pour plus d’informations.

### <a name="return-value"></a>Valeur de retour

Le résultat de la réduction.

### <a name="remarks"></a>Notes

Pour effectuer une réduction parallèle, la fonction divise la plage en morceaux en fonction du nombre de travailleurs disponibles pour le planificateur sous-jacent. La réduction se déroule en deux phases, la première phase effectue une réduction dans chaque morceau, et la deuxième phase effectue une réduction entre les résultats partiels de chaque morceau.

La première surcharge exige que l’itérateur , `value_type` `T`, être le même que le type de valeur d’identité ainsi que le type de résultat de réduction. Le type d’élément `T T::operator + (T)` T doit fournir à l’opérateur de réduire les éléments dans chaque morceau. Le même opérateur est également utilisé dans la deuxième phase.

La deuxième surcharge exige également que l’itérateur soit le même que le type de valeur d’identité `value_type` ainsi que le type de résultat de réduction. L’opérateur `_Sym_fun` binaire fourni est utilisé dans les deux phases de réduction, avec la valeur d’identité comme valeur initiale pour la première phase.

Pour la troisième surcharge, le type de valeur d’identité doit être le `value_type` même que le type de résultat de réduction, mais l’itérateur peut être différent des deux. La fonction `_Range_fun` de réduction de la plage est utilisée dans la première `_Sym_reduce_fun` phase avec la valeur d’identité comme valeur initiale, et la fonction binaire est appliquée aux sous-résultats dans la deuxième phase.

## <a name="parallel_sort"></a><a name="parallel_sort"></a>parallel_sort

Organise les éléments dans une plage spécifiée dans un ordre non descendant, ou selon un critère de commande spécifié par un prédicat binaire, en parallèle. Cette fonction est sémantiquement similaire à `std::sort` en ce sens qu'il s'agit d'un tri sur place, par comparaison et instable.

```cpp
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Paramètres

*_Random_iterator*<br/>
Le type itérateur de la plage d’entrée.

*_Function*<br/>
Le type de functor de comparaison binaire.

*_Begin*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*_End*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier.

*_Func*<br/>
Objet de fonction prédicatif défini par l’utilisateur qui définit le critère de comparaison à satisfaire par des éléments successifs dans la commande. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas. Cette fonction de comparaison doit imposer un ordre faible strict sur les paires d’éléments de la séquence.

*_Chunk_size*<br/>
La taille minimale d’un morceau qui sera divisé en deux pour l’exécution parallèle.

### <a name="remarks"></a>Notes

La première surcharge utilise le `std::less`comparateur binaire .

La deuxième surcharge utilise le comparateur binaire fourni `bool _Func(T, T)` `T` qui devrait avoir la signature où est le type d’éléments dans la plage d’entrée.

L’algorithme divise la plage d’entrée en deux morceaux et divise successivement chaque morceau en deux sous-morceaux pour l’exécution en parallèle. L’argument `_Chunk_size` facultatif peut être utilisé pour indiquer à l’algorithme `_Chunk_size` qu’il doit gérer des morceaux de taille < en série.

## <a name="parallel_transform"></a><a name="parallel_transform"></a>parallel_transform

Applique un objet de fonction spécifié à chaque élément d'une plage source ou à une paire d'éléments de deux plages sources, et copie les valeurs de retour de l'objet de fonction dans une plage de destination, en parallèle. Cette fonction équivaut sémantiquement à `std::transform`.

```cpp
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>Paramètres

*_Input_iterator1*<br/>
Le type du premier itérateur ou du seul itérateur d'entrée.

*_Output_iterator*<br/>
Le type de l’itérateur de sortie.

*_Unary_operator*<br/>
Le type de foncteur unaire à exécuter sur chaque élément de la plage d'entrée.

*_Input_iterator2*<br/>
Le type du second itérateur d'entrée.

*_Binary_operator*<br/>
Le type de foncteur binaire exécuté par couple sur les éléments des deux plages sources.

*_Partitioner*<br/>
*première1*<br/>
Itérateur d'entrée qui traite la position du premier élément de la première ou de l'unique plage source à traiter.

*last1*<br/>
Itérateur d'entrée qui traite la position de l'élément final dans la première ou dans l'unique plage source à traiter.

*_Result*<br/>
Itérateur de sortie qui traite la position du premier élément dans la plage de destination.

*_Unary_op*<br/>
Objet de fonction unaire défini par l'utilisateur appliqué à chaque élément dans la plage source.

*_Part*<br/>
Référence au partitionneur d'objet. L’argument peut `const`être l’un `const`des [auto_partitioner](auto-partitioner-class.md)`&` `const`, [static_partitioner](static-partitioner-class.md)`&`, [simple_partitioner](simple-partitioner-class.md) `&` ou [affinity_partitioner](affinity-partitioner-class.md) `&` Si un objet [affinity_partitioner](affinity-partitioner-class.md) est utilisé, la référence doit être une référence non-const l-valeur, de sorte que l’algorithme peut stocker l’état pour les boucles futures à réutiliser.

*premier2*<br/>
Itérateur d'entrée qui traite la position du premier élément de la seconde plage source à traiter.

*_Binary_op*<br/>
Objet de fonction binaire défini par l'utilisateur qui est appliqué par couple, progressivement, sur les deux plages sources.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située immédiatement après le dernier élément de la plage de destination qui reçoit les éléments de sortie transformés par l'objet de fonction.

### <a name="remarks"></a>Notes

[auto_partitioner](auto-partitioner-class.md) sera utilisé pour les surcharges sans argument de partitionneur explicite.

Pour les itérateurs qui ne prennent pas en charge l’accès aléatoire, seul [auto_partitioner](auto-partitioner-class.md) est pris en charge.

Les surcharges prenant l'argument `_Unary_op` transforment la plage d'entrée en plage de sortie en appliquant le foncteur unaire à chaque élément de la plage d'entrée. `_Unary_op` doit prendre en charge l'opérateur d'appel de fonction avec la signature `operator()(T)` où `T` est le type de valeur de la plage à itérer.

Les surcharges prenant l'argument `_Binary_op` transforment deux plages d'entrée en une plage de sortie en appliquant le foncteur binaire à un élément de la première plage d'entrée et à un élément de la deuxième plage d'entrée. `_Binary_op` doit prendre en charge l'opérateur d'appel de fonction avec la signature `operator()(T, U)` où `T`, `U` sont des types de valeur des deux itérateurs d'entrée.

Pour plus d’informations, voir [Algorithmes parallèles](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a><a name="receive"></a>Recevoir

Implémentation générale de la fonction receive, qui permet à un contexte d'attendre des données en provenance d'une seule source exactement et de filtrer les valeurs qui sont acceptées.

```cpp
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de charge utile.

*_Src*<br/>
Un pointeur ou une référence à la source à partir de laquelle les données sont attendues.

*_Timeout*<br/>
Le temps maximum pour lequel la méthode devrait pour les données, en millisecondes.

*_Filter_proc*<br/>
Une fonction de filtre qui détermine si les messages doivent être acceptés.

### <a name="return-value"></a>Valeur de retour

Une valeur de la source, du type de charge utile.

### <a name="remarks"></a>Notes

Si le `_Timeout` paramètre a une `COOPERATIVE_TIMEOUT_INFINITE`valeur autre que la constante, [l’exception operation_timed_out](operation-timed-out-class.md) est jetée si le temps spécifié expire avant qu’un message soit reçu. Si vous voulez un délai de durée zéro, vous devriez utiliser `receive` la fonction `0` [try_receive,](concurrency-namespace-functions.md) par opposition à appeler avec un délai d’attente de (zéro), car il est plus efficace et ne jette pas d’exceptions sur les délais d’attente.

Pour plus d’informations, voir [Fonctions de passage de message](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a><a name="run_with_cancellation_token"></a>run_with_cancellation_token

Exécute un objet de fonction immédiatement et de manière synchrone dans le contexte d’un jeton d’annulation donné.

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Le type de l’objet de fonction qui sera invoqué.

*_Func*<br/>
L’objet de fonction qui sera exécuté. Cet objet doit prendre en charge l’opérateur d’appel de fonction avec une signature de vide (vide).

*_Ct*<br/>
Le jeton d’annulation qui contrôlera l’annulation implicite de l’objet de fonction. Utilisez `cancellation_token::none()` si vous voulez que la fonction s’exécute sans aucune possibilité d’annulation implicite d’un groupe de travail parent annulé.

### <a name="remarks"></a>Notes

Tous les points d’interruption de `cancellation_token` l’objet de fonction seront déclenchés lorsque l’objet est annulé. Le jeton `_Ct` explicite `_Func` isolera ceci de l’annulation de parent si le parent a un jeton différent ou pas de jeton.

## <a name="send"></a><a name="send"></a>Envoyer

Opération d’envoi synchrone qui attend que la cible accepte ou refuse le message.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de charge utile.

*_Trg*<br/>
Un pointeur ou une référence à la cible à laquelle les données sont envoyées.

*_Data*<br/>
Une référence aux données à envoyer.

### <a name="return-value"></a>Valeur de retour

**vrai** si le message a été accepté, **faux** sinon.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Fonctions de passage de message](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a><a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Paramètres

*_Scheduler*<br/>
L’horaire ambiant à définir.

## <a name="set_task_execution_resources"></a><a name="set_task_execution_resources"></a>set_task_execution_resources

Limite les ressources d'exécution utilisées par les threads de travail interne du runtime d'accès concurrentiel à l'ensemble d'affinités spécifié.

Il est possible d'appeler cette méthode uniquement avant de créer le gestionnaire des ressources, ou entre deux durées de vie de gestionnaires des ressources. Cette méthode peut être appelée plusieurs fois tant que le gestionnaire des ressources n'existe pas au moment de l'appel. Une fois qu'une limite d'affinité a été définie, elle reste en vigueur jusqu'au prochain appel valide à la méthode `set_task_execution_resources`.

Le masque d'affinité fourni n'a pas besoin de correspondre à un sous-ensemble du masque d'affinité du processus. L'affinité du processus est mis à jour si besoin.

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Paramètres

*_ProcessAffinityMask*<br/>
Le masque d’affinité que les fils de travailleur De Concurrency Runtime doivent être limités à. Utilisez cette méthode sur un système avec plus de 64 threads matériels seulement si vous souhaitez limiter le Temps de fonctionnement De concurrency à un sous-ensemble du groupe de processeur actuel. En général, vous devez utiliser la version de la méthode qui accepte un tableau d’affinités de groupe comme un paramètre, pour limiter l’affinité sur les machines avec plus de 64 threads matériels.

*count*<br/>
Le nombre `GROUP_AFFINITY` d’entrées dans le `_PGroupAffinity`tableau spécifié par le paramètre .

*_PGroupAffinity*<br/>
Un éventail `GROUP_AFFINITY` d’entrées.

### <a name="remarks"></a>Notes

La méthode prévoit une exception [invalid_operation](invalid-operation-class.md) si un gestionnaire de ressources est présent au moment où elle est invoquée, et une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si l’affinité spécifiée entraîne un ensemble de ressources vides.

La version de la méthode qui prend un tableau d’affinités de groupe comme un paramètre ne doit être utilisé sur les systèmes d’exploitation avec la version Windows 7 ou plus. Sinon, une exception [invalid_operation](invalid-operation-class.md) est lancée.

Modifier de façon programmatique l’affinité du processus après l’invoquage de cette méthode n’amènera pas le gestionnaire des ressources à réévaluer l’affinité à laquelle elle est limitée. Par conséquent, tous les changements à l’affinité de processus devraient être faites avant d’appeler cette méthode.

## <a name="swap"></a><a name="swap"></a>Swap

Échange les éléments de deux objets `concurrent_vector`.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs concomitants.

*_Ax*<br/>
Le type d’allocateur des vecteurs concomitants.

*_a*<br/>
Le vecteur concomitant dont les éléments doivent `_B`être échangés avec ceux du vecteur concomitant.

*_B*<br/>
Le vecteur concomitant fournissant les éléments à échanger, ou le vecteur dont `_A`les éléments doivent être échangés avec ceux du vecteur concomitant.

### <a name="remarks"></a>Notes

La fonction de modèle est un `concurrent_vector` algorithme spécialisé `_A`sur la classe de conteneur pour exécuter la fonction de membre. [concurrent_vector::swap](concurrent-vector-class.md#swap)( `_B`). Il s’agit d’instances de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de `template <class T> void swap(T&, T&)`la fonction de modèle, , dans la classe d’algorithme fonctionne par affectation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

Cette méthode n’est pas de la concurrence-sûr. Vous devez vous assurer qu’aucun autre thread n’effectue d’opérations sur l’un ou l’autre des vecteurs concomitants lorsque vous appelez cette méthode.

## <a name="task_from_exception"></a><a name="task_from_exception"></a>task_from_exception

```cpp
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Paramètres

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Valeur de retour

## <a name="task_from_result"></a><a name="task_from_result"></a>task_from_result

```cpp
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Paramètres

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Valeur de retour

## <a name="trace_agents_register_name"></a><a name="trace_agents_register_name"></a>Trace_agents_register_name

Associe le nom donné au bloc de message ou à l'agent dans le suivi ETW.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de l’objet. Il s’agit généralement d’un bloc de messages ou d’un agent.

*_PObject*<br/>
Un pointeur vers le bloc de messages ou l’agent qui est nommé dans la trace.

*_Name*<br/>
Le nom de l’objet donné.

## <a name="try_receive"></a><a name="try_receive"></a>try_receive

Implémentation générale de la fonction try-receive, qui permet à un contexte de rechercher des données en provenance d'une seule source exactement et de filtrer les valeurs qui sont acceptées. Si les données ne sont pas prêtes, la méthode reviendra **fausse**.

```cpp
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de charge utile

*_Src*<br/>
Un pointeur ou une référence à la source à partir de laquelle les données sont attendues.

*_value*<br/>
Une référence à un endroit où le résultat sera placé.

*_Filter_proc*<br/>
Une fonction de filtre qui détermine si les messages doivent être acceptés.

### <a name="return-value"></a>Valeur de retour

Une `bool` valeur indiquant si une charge `_value`utile a été placée ou non .

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Fonctions de passage de message](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a><a name="wait"></a>Attendre

Suspend le contexte actuel pendant une durée spécifiée.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Paramètres

*_Milliseconds*<br/>
Le nombre de millisecondes dans le contexte actuel doit être mis en pause. Si `_Milliseconds` le paramètre est `0`défini à la valeur, le contexte actuel doit donner lieu à l’exécution à d’autres contextes runnables avant de se poursuivre.

### <a name="remarks"></a>Notes

Si cette méthode est appelée sur un contexte de planificateur De temps d’exécution de concurrence, le planificateur trouvera un contexte différent pour fonctionner sur la ressource sous-jacente. Étant donné que l’horaire est de nature coopérative, ce contexte ne peut pas reprendre exactement après le nombre de millisecondes spécifiées. Si le planificateur est occupé à exécuter d’autres tâches qui ne cèdent pas en coopération au planificateur, la période d’attente pourrait être indéfinie.

## <a name="when_all"></a><a name="when_all"></a>when_all

Crée une tâche qui s’effectue correctement lorsque toutes les tâches fournies comme arguments s’effectuent correctement.

```cpp
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>Paramètres

*_Iterator*<br/>
Type de l'itérateur d'entrée.

*_Begin*<br/>
Position du premier élément dans la plage d’éléments à combiner dans la tâche obtenue.

*_End*<br/>
Position du premier élément au-delà de la plage d’éléments à combiner dans la tâche obtenue.

*_TaskOptions*<br/>
Objet `task_options`.

### <a name="return-value"></a>Valeur de retour

Une tâche qui se termine avec succès lorsque toutes les tâches d’entrée ont été accomplies avec succès. Si les tâches d’entrée sont de type `T`, le résultat de cette fonction sera `task<std::vector<T>>`. Si les tâches d’entrée sont de type `void`, la tâche de sortie sera également `task<void>`.

### <a name="remarks"></a>Notes

`when_all` est une fonction non bloquante qui produit un `task` en tant que résultat. Contrairement à [la tâche::wait](task-class.md#wait), il est sûr d’appeler cette fonction dans une application UWP sur le fil ASTA (Application STA).

Si l’une des tâches est annulée ou jette une exception, la tâche retournée se terminera tôt, dans l’état annulé, et `task::wait` l’exception, si l’on se produit, sera jetée si vous appelez [la tâche::get](task-class.md#get) ou sur cette tâche.

Pour plus d’informations, voir [Le parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a><a name="when_any"></a>when_any

Crée une tâche qui s'effectue quand l'une des tâches fournies en tant qu'arguments s'effectue.

```cpp
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>Paramètres

*_Iterator*<br/>
Type de l'itérateur d'entrée.

*_Begin*<br/>
Position du premier élément dans la plage d’éléments à combiner dans la tâche obtenue.

*_End*<br/>
Position du premier élément au-delà de la plage d’éléments à combiner dans la tâche obtenue.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Jeton d'annulation contrôlant l'annulation de la tâche retournée. Si vous ne fournissez pas de jeton d’annulation, la tâche qui en résulte recevra le jeton d’annulation de la tâche entraînant sa fin.

### <a name="return-value"></a>Valeur de retour

Tâche qui s'effectue quand l'une des deux tâches d'entrée s'est correctement déroulée. Si les tâches d’entrée sont de type `T`, la sortie de cette fonction est une `task<std::pair<T, size_t>>>`, où le premier élément de la paire est le résultat de la fin de la tâche et le deuxième élément est l’index de la tâche terminée. Si les tâches d’entrée sont de type `void`, la sortie est une `task<size_t>`, où le résultat est l’index de fin de la tâche.

### <a name="remarks"></a>Notes

`when_any` est une fonction non bloquante qui produit un `task` en tant que résultat. Contrairement à [la tâche::wait](task-class.md#wait), il est sûr d’appeler cette fonction dans une application UWP sur le fil ASTA (Application STA).

Pour plus d’informations, voir [Le parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
