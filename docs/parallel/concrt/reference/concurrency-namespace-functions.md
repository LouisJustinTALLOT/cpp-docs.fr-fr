---
title: fonctions d’espace de noms d’accès concurrentiel
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
ms.openlocfilehash: 9cb726ccc475d6d08e036229d0d06089e3fac31c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278208"
---
# <a name="concurrency-namespace-functions"></a>fonctions d’espace de noms d’accès concurrentiel

||||
|-|-|-|
|[Alloc](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|
|[EnableTracing](#enabletracing)|[Gratuit](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[clear](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[receive](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[send](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[wait](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

##  <a name="alloc"></a>  Alloc

Alloue un bloc de mémoire de la taille spécifiée depuis le sous-allocateur de mise en cache du runtime d'accès concurrentiel.

```
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Paramètres

*_NumBytes*<br/>
Le nombre d’octets de mémoire à allouer.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la mémoire nouvellement allouée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les scénarios de votre application peut tirer parti d’à l’aide de sous-allocateur de mise en cache, consultez [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

##  <a name="asend"></a>  asend

Opération d’envoi asynchrone qui planifie une tâche pour propager les données vers le bloc cible.

```
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
Le type des données à envoyer.

*_Trg*<br/>
Pointeur ou référence à la cible à laquelle les données sont envoyées.

*_Data*<br/>
Une référence à l’envoi des données.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été accepté avant que la méthode est retournée, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [fonctions de passage de messages](../../../parallel/concrt/message-passing-functions.md).

##  <a name="cancel_current_task"></a>  cancel_current_task

Annule la tâche en cours d’exécution. Cette fonction peut être appelée à partir du corps d'une tâche pour annuler l'exécution de la tâche et la faire passer à l'état `canceled`.

L'appel de cette fonction en dehors du corps d'un objet `task` n'est pas pris en charge. Cela entraînerait un comportement non défini tel qu'un blocage dans votre application.

```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

##  <a name="clear"></a>  clear

Efface la file d’attente simultanée, en détruisant les actuellement les éléments en file d’attente. Cette méthode n’est pas concurrentiel.

```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Paramètres

*T*<br/>

*_Ax*<br/>

##  <a name="create_async"></a>  create_async

Crée une construction asynchrone Windows Runtime basée sur un objet lambda ou de fonction fourni par l'utilisateur. Le type de retour de `create_async` est `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` ou `IAsyncOperationWithProgress<TResult, TProgress>^` selon la signature de l’objet lambda passée à la méthode.

```
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

Construction asynchrone représentée par une IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^, ou une IAsyncOperationWithProgress\<TResult, TProgress > ^. L'interface retournée dépend de la signature de l'objet lambda passé dans la fonction.

### <a name="remarks"></a>Notes

Le type de retour de l’objet lambda détermine si la construction est une action ou une opération.

Les objets lambda qui retournent void provoquent la création d'actions. Les objets lambda qui retournent un résultat de type `TResult` provoquent la création d'opérations TResult.

L'objet lambda peut également retourner un résultat `task<TResult>` qui encapsule le travail asynchrone en lui-même ou qui est la continuation d'une chaîne de tâches représentant le travail asynchrone. Dans ce cas, l'objet lambda lui-même est exécuté en ligne, car les tâches sont celles exécutées de façon asynchrone et le type de retour de l'objet lambda est désencapsulé afin de produire la construction asynchrone retournée par `create_async`. Cela implique une expression lambda qui retourne une tâche\<void > provoque la création d’actions et une expression lambda qui retourne une tâche\<TResult > provoque la création d’opérations TResult.

L’objet lambda peut prendre zéro, un ou deux arguments. Les arguments valides sont `progress_reporter<TProgress>` et `cancellation_token`, dans cet ordre si les deux sont utilisés. Un objet lambda sans arguments provoque la création d’une construction asynchrone sans la capacité de créer un rapport de progression. Une expression lambda qui prend un argument progress_reporter\<TProgress > entraîne `create_async` retourne une construction asynchrone qui signale la progression de type TProgress chaque fois que le `report` méthode de l’objet progress_reporter est appelée. Un objet lambda qui prend un argument cancellation_token peut l’utiliser pour vérifier l’annulation, ou le passer aux tâches qu’il crée afin que l’annulation de la construction asynchrone provoque l’annulation de ces tâches.

Si le corps de l’objet lambda ou fonction retourne un résultat (et pas une tâche\<TResult >), l’objet lambda sera exécuté de façon asynchrone dans le processus MTA, dans le contexte d’une tâche, le Runtime crée implicitement pour celle-ci. La méthode `IAsyncInfo::Cancel` provoquera l’annulation de la tâche implicite.

Si le corps de l'objet lambda retourne une tâche, l'objet lamba s'exécute en ligne, et si vous déclarez que l'objet lambda prend un argument de type `cancellation_token`, vous pouvez déclencher l'annulation de toutes les tâches que vous créez au sein de l'objet lambda en passant ce jeton lorsque vous créez les tâches. Vous pouvez également utiliser la méthode `register_callback` sur le jeton pour forcer le runtime à effectuer un rappel lorsque vous appelez `IAsyncInfo::Cancel` sur l'opération ou l'action asynchrone produite.

Cette fonction est uniquement disponible pour les applications Windows Runtime.

##  <a name="createresourcemanager"></a>  CreateResourceManager

Retourne une interface qui représente l'instance singleton du gestionnaire des ressources du runtime d'accès concurrentiel. Le gestionnaire des ressources est responsable de l'affectation des ressources aux planificateurs qui veulent coopérer.

```
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Valeur de retour

Interface `IResourceManager`.

### <a name="remarks"></a>Notes

Plusieurs appels suivants à cette méthode retourne la même instance du Gestionnaire de ressources. Chaque appel à la méthode incrémente une référence de compter sur le Gestionnaire de ressources et doit être mise en correspondance avec un appel à la [IResourceManager::Release](iresourcemanager-structure.md) méthode lorsque votre planificateur a terminé communique avec le Gestionnaire de ressources.

[unsupported_os](unsupported-os-class.md) est levée si le système d’exploitation n’est pas pris en charge par le Runtime d’accès concurrentiel.

##  <a name="create_task"></a>  create_task

Crée une bibliothèque de modèles parallèles [tâche](task-class.md) objet. `create_task` peut être utilisé partout où vous auriez utilisé un constructeur de tâche. Il est fourni principalement pour des raisons pratiques, car il permet d'utiliser le mot clé `auto` pendant la création de tâches.

```
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
Paramètre à partir duquel la tâche doit être construite. Cela peut être un objet lambda ou fonction, un `task_completion_event` objet, un autre `task` objet ou une interface Windows::Foundation :: iasyncinfo si vous utilisez des tâches dans votre application UWP.

*_TaskOptions*<br/>
Les options de tâche.

*_Task*<br/>
Tâche à créer.

### <a name="return-value"></a>Valeur de retour

Une nouvelle tâche de type `T`, qui est déduit à partir de `_Param`.

### <a name="remarks"></a>Notes

La première surcharge se comporte comme un constructeur de tâche qui accepte un seul paramètre.

La seconde surcharge associe le jeton d’annulation fourni avec la tâche nouvellement créée. Si vous utilisez cette surcharge vous n’êtes pas autorisé à passer un autre `task` objet comme premier paramètre.

Le type de la tâche retournée est déduit du premier paramètre à la fonction. Si `_Param` est un `task_completion_event<T>`, un `task<T>`, ou un functor qui retourne le type `T` ou `task<T>`, le type de la tâche créée est `task<T>`.

Dans une application UWP, si `_Param` est de type Windows::Foundation :: iasyncoperation\<T > ^ ou Windows::Foundation :: iasyncoperationwithprogress\<T, P > ^, ou un functor qui retourne un de ces types, la tâche créée sera de type `task<T>`. Si `_Param` est de type Windows::Foundation :: iasyncaction ^ ou Windows::Foundation :: iasyncactionwithprogress\<P > ^, ou un functor qui retourne un de ces types, la tâche créée sera a le type `task<void>`.

##  <a name="disabletracing"></a>  DisableTracing

Désactive le traçage dans le runtime d'accès concurrentiel. Cette fonction est déconseillée car le suivi ETW est désinscrit par défaut.

```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Valeur de retour

Si le suivi a été correctement désactivé, `S_OK` est retournée. Si le suivi n’a pas été lancé précédemment, `E_NOT_STARTED` est retourné

##  <a name="enabletracing"></a>  EnableTracing

Active le traçage dans le runtime d'accès concurrentiel. Cette fonction est déconseillée car le suivi ETW est à présent activé par défaut.

```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Valeur de retour

Si le traçage a été correctement lancé, `S_OK` est retourné ; sinon, `E_NOT_STARTED` est retournée.

##  <a name="free"></a>  Gratuit

Libère un bloc de mémoire précédemment alloué par la méthode `Alloc` au sous-allocateur de mise en cache du runtime d'accès concurrentiel.

```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Paramètres

*_PAllocation*<br/>
Pointeur vers la mémoire précédemment alloué par la `Alloc` méthode qui doit être libérée. Si le paramètre `_PAllocation` a la valeur `NULL`, cette méthode l’ignorer et retourner immédiatement.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les scénarios de votre application peut tirer parti d’à l’aide de sous-allocateur de mise en cache, consultez [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler

```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Valeur de retour

##  <a name="getexecutioncontextid"></a>  GetExecutionContextId

Retourne un identificateur unique qui peut être affecté à un contexte d'exécution qui implémente l'interface `IExecutionContext`.

```
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Valeur de retour

Un identificateur unique pour un contexte d’exécution.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour obtenir un identificateur pour votre contexte d’exécution avant de passer un `IExecutionContext` interface en tant que paramètre à une des méthodes proposées par le Gestionnaire de ressources.

##  <a name="getosversion"></a>  GetOSVersion

Retourne la version du système d'exploitation.

```
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Valeur de retour

Valeur énumérée représentant le système d’exploitation.

### <a name="remarks"></a>Notes

[unsupported_os](unsupported-os-class.md) est levée si le système d’exploitation n’est pas pris en charge par le Runtime d’accès concurrentiel.

##  <a name="getprocessorcount"></a>  GetProcessorCount

Retourne le nombre de threads matériels sur le système sous-jacent.

```
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de threads matériels.

### <a name="remarks"></a>Notes

[unsupported_os](unsupported-os-class.md) est levée si le système d’exploitation n’est pas pris en charge par le Runtime d’accès concurrentiel.

##  <a name="getprocessornodecount"></a>  GetProcessorNodeCount

Retourne le nombre de nœuds NUMA ou de packages de processeurs sur le système sous-jacent.

```
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de nœuds NUMA ou packages de processeur.

### <a name="remarks"></a>Notes

Si le système contient plus de nœuds NUMA que les packages de processeur, le nombre de nœuds NUMA est retourné, sinon, le nombre de packages de processeur est retourné.

[unsupported_os](unsupported-os-class.md) est levée si le système d’exploitation n’est pas pris en charge par le Runtime d’accès concurrentiel.

##  <a name="getschedulerid"></a>  GetSchedulerId

Retourne un identificateur unique qui peut être affecté à un planificateur qui implémente l'interface `IScheduler`.

```
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Valeur de retour

Un identificateur unique pour un planificateur.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour obtenir un identificateur pour votre planificateur avant de passer un `IScheduler` interface en tant que paramètre à une des méthodes proposées par le Gestionnaire de ressources.

##  <a name="internal_assign_iterators"></a>  internal_assign_iterators

```
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

##  <a name="interruption_point"></a>  interruption_point

Crée un point d'interruption pour l'annulation. Si une annulation est en cours dans le contexte dans lequel cette fonction est appelée, une exception interne est levée et annule l'exécution du travail parallèle en cours. Si aucune annulation n'est en cours, la fonction ne fait rien.

```
inline void interruption_point();
```

### <a name="remarks"></a>Notes

Vous ne devez pas intercepter l’exception d’annulation interne levée par le `interruption_point()` (fonction). L’exception est interceptée et gérée par le runtime et intercepter risque de votre programme se comporte de façon anormale.

##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling

Retourne une indication qui détermine si le groupe de tâches qui s'exécute actuellement inline sur le contexte actuel est au beau milieu d'une annulation active (ou le sera bientôt). Notez que si aucun groupe de tâches ne s'exécute actuellement inline sur le contexte actuel, `false` est retourné.

```
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Valeur de retour

**true** si le groupe de tâches est en cours d’exécution est l’annulation, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [l’annulation](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

##  <a name="make_choice"></a>  make_choice

Construit un bloc de messagerie `choice` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.

```
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

*T2*<br/>
Le type de bloc de message de la deuxième source.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `choice` est planifiée.

*_Item1*<br/>
La première source.

*_Item2*<br/>
La deuxième source.

*_Items*<br/>
Sources supplémentaires.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `choice` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="return-value"></a>Valeur de retour

Un `choice` bloc de message avec deux ou plusieurs sources d’entrée.

##  <a name="make_greedy_join"></a>  make_greedy_join

Construit un bloc de messagerie `greedy multitype_join` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.

```
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

*T2*<br/>
Le type de bloc de message de la deuxième source.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée.

*_Item1*<br/>
La première source.

*_Item2*<br/>
La deuxième source.

*_Items*<br/>
Sources supplémentaires.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="return-value"></a>Valeur de retour

Un `greedy multitype_join` bloc de message avec deux ou plusieurs sources d’entrée.

##  <a name="make_join"></a>  make_join

Construit un bloc de messagerie `non_greedy multitype_join` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.

```
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

*T2*<br/>
Le type de bloc de message de la deuxième source.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée.

*_Item1*<br/>
La première source.

*_Item2*<br/>
La deuxième source.

*_Items*<br/>
Sources supplémentaires.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="return-value"></a>Valeur de retour

Un `non_greedy multitype_join` bloc de message avec deux ou plusieurs sources d’entrée.

##  <a name="make_task"></a>  make_task

Méthode de fabrique pour la création d'un objet `task_handle`.

```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Le type de l’objet de fonction qui sera appelé pour exécuter le travail représenté par la `task_handle` objet.

*_Func*<br/>
La fonction qui sera appelée pour exécuter le travail représenté par la `task_handle` objet. Il peut s’agir d’un functor lambda, un pointeur vers une fonction, ou de tout objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature `void operator()()`.

### <a name="return-value"></a>Valeur de retour

Objet `task_handle`.

### <a name="remarks"></a>Notes

Cette fonction est utile lorsque vous avez besoin créer un `task_handle` de l’objet avec une expression lambda, car il vous permet de créer l’objet sans connaître le type réel de la fonction lambda.

##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort

Réorganise les éléments d’une plage spécifiée dans un ordre non décroissant ou selon un critère de tri spécifié par un prédicat binaire, en parallèle. Cette fonction est sémantiquement similaire à `std::sort` en ce sens qu'il s'agit d'un tri sur place, par comparaison et instable, à l'exception près qu'elle a besoin d'un espace supplémentaire `O(n)` et qu'elle requiert une initialisation par défaut pour les éléments triés.

```
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
Type d’itérateur de la plage d’entrée.

*_Allocator*<br/>
Le type d’un allocateur de mémoire compatible de bibliothèque C++ Standard.

*_Function*<br/>
Le type de la comparaison binaire.

*_Begin*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*_End*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier.

*_Alloc*<br/>
Une instance d’un allocateur de mémoire compatible de bibliothèque C++ Standard.

*_Func*<br/>
Un objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans le classement. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas. Cette fonction de comparaison doit imposer un ordre faible strict sur les paires d’éléments de la séquence.

*_Chunk_size*<br/>
La taille au minimum d’un segment est fractionné en deux pour l’exécution parallèle.

### <a name="remarks"></a>Notes

Toutes les surcharges nécessitent `n * sizeof(T)` espace supplémentaire, où `n` est le nombre d’éléments à trier, et `T` est le type d’élément. Dans la plupart des cas parallel_buffered_sort affichera une amélioration des performances sur [parallel_sort](concurrency-namespace-functions.md), et vous devez l’utiliser sur parallel_sort si vous disposez de la mémoire disponible.

Si vous ne fournissez pas un comparateur binaire `std::less` est utilisé en tant que la valeur par défaut, ce qui nécessite le type d’élément fournir l’opérateur `operator<()`.

Si vous ne fournissez pas un type d’allocateur ou une instance, l’allocateur de mémoire de bibliothèque C++ Standard `std::allocator<T>` est utilisé pour allouer la mémoire tampon.

L’algorithme divise la plage d’entrée en deux blocs et successivement divise chaque segment en deux blocs de sous-répertoire pour l’exécution en parallèle. L’argument facultatif `_Chunk_size` peut être utilisé pour indiquer à l’algorithme qu’il doit gère des segments de taille < `_Chunk_size` en série.

##  <a name="parallel_for"></a>  parallel_for

`parallel_for` effectue une itération sur une plage d'index et exécute une fonction fournie par l'utilisateur à chaque itération, en parallèle.

```
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
Le type de l’index utilisé pour l’itération.

*_Function*<br/>
Le type de la fonction qui sera exécuté sur chaque itération.

*_Partitioner*<br/>
Le type du partitionneur qui est utilisé pour partitionner la plage fournie.

*first*<br/>
Le premier index à inclure dans l’itération.

*last*<br/>
L’index d’un après le dernier index à inclure dans l’itération.

*_Step*<br/>
La valeur par laquelle lors de l’itération à partir de l’étape `first` à `last`. L’étape doit être positive. [invalid_argument](../../../standard-library/invalid-argument-class.md) est levée si l’étape est inférieure à 1.

*_Func*<br/>
La fonction doit être exécuté à chaque itération. Cela peut être une expression lambda, un pointeur de fonction, ou de tout objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature `void operator()(_Index_type)`.

*_Part*<br/>
Référence au partitionneur d'objet. L’argument peut être une des `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ partitionneur](simple-partitioner-class.md) `&` ou [affinity_partitioner](affinity-partitioner-class.md) `&` si un [affinity_partitioner](affinity-partitioner-class.md) objet est utilisé, la référence doit être une l-value de non const référence, afin que l’algorithme peut stocker l’état pour les futures boucles à réutiliser.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [algorithmes parallèles](../../../parallel/concrt/parallel-algorithms.md).

##  <a name="parallel_for_each"></a>  parallel_for_each

`parallel_for_each` applique une fonction spécifiée à chaque élément dans une plage, en parallèle. Sémantiquement, elle équivaut à la fonction `for_each` dans l'espace de noms `std`, si ce n'est que l'itération des éléments est effectuée en parallèle et que l'ordre d'itération n'est pas spécifié. L’argument `_Func` doit prendre en charge un opérateur d’appel de fonction sous la forme de `operator()(T)` où le paramètre `T` est le type d’élément du conteneur en cours d’itération.

```
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
Le type de l’itérateur utilisé pour itérer au sein du conteneur.

*_Function*<br/>
Le type de la fonction qui s’appliqueront à chaque élément dans la plage.

*_Partitioner*<br/>
*first*<br/>
Un itérateur qui traite la position du premier élément à inclure dans l’itération parallèle.

*last*<br/>
Un itérateur qui traite la position juste après le dernier élément à inclure dans l’itération parallèle.

*_Func*<br/>
Un objet de fonction définie par l’utilisateur qui est appliqué à chaque élément de la plage.

*_Part*<br/>
Référence au partitionneur d'objet. L’argument peut être une des `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ partitionneur](simple-partitioner-class.md) `&` ou [affinity_partitioner](affinity-partitioner-class.md) `&` si un [affinity_partitioner](affinity-partitioner-class.md) objet est utilisé, la référence doit être une l-value de non const référence, afin que l’algorithme peut stocker l’état pour les futures boucles à réutiliser.

### <a name="remarks"></a>Notes

[auto_partitioner](auto-partitioner-class.md) sera utilisé pour la surcharge sans un partitionneur explicite.

Pour les itérateurs ne prenant pas en charge aléatoire d’accès, uniquement [auto_partitioner](auto-partitioner-class.md) est pris en charge.

Pour plus d’informations, consultez [algorithmes parallèles](../../../parallel/concrt/parallel-algorithms.md).

##  <a name="parallel_invoke"></a>  parallel_invoke

Exécute les objets de fonction fournis comme paramètres en parallèle et se bloque jusqu'à la fin de leur exécution. Chaque objet de fonction peut être une expression lambda, un pointeur vers une fonction ou tout objet qui prend en charge l’opérateur d’appel de fonction avec la signature `void operator()()`.

```
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
Le type du deuxième objet de fonction à exécuter en parallèle.

*_Function3*<br/>
Le type du troisième objet de fonction à exécuter en parallèle.

*_Function4*<br/>
Le type du quatrième objet de fonction à exécuter en parallèle.

*_Function5*<br/>
Le type du cinquième objet de fonction à exécuter en parallèle.

*_Function6*<br/>
Le type du sixième objet de fonction à exécuter en parallèle.

*_Function7*<br/>
Le type du septième objet de fonction à exécuter en parallèle.

*_Function8*<br/>
Le type du huitième objet de fonction à exécuter en parallèle.

*_Function9*<br/>
Le type du neuvième objet de fonction à exécuter en parallèle.

*_Function10*<br/>
Le type du dixième objet de fonction à exécuter en parallèle.

*_Func1*<br/>
Premier objet de fonction à exécuter en parallèle.

*_Func2*<br/>
Deuxième objet de fonction à exécuter en parallèle.

*_Func3*<br/>
Troisième objet de fonction à exécuter en parallèle.

*_Func4*<br/>
Quatrième objet de fonction à exécuter en parallèle.

*_Func5*<br/>
La cinquième objet de fonction à exécuter en parallèle.

*_Func6*<br/>
La sixième objet de fonction à exécuter en parallèle.

*_Func7*<br/>
La septième objet de fonction à exécuter en parallèle.

*_Func8*<br/>
Huitième objet de fonction à exécuter en parallèle.

*_Func9*<br/>
La neuvième objet de fonction à exécuter en parallèle.

*_Func10*<br/>
La dixième objet de fonction à exécuter en parallèle.

### <a name="remarks"></a>Notes

Notez qu’un ou plusieurs des objets de fonction fournis comme paramètres peuvent s’exécuter inline dans le contexte d’appel.

Si un ou plusieurs des objets de fonction passés comme paramètres à cette fonction lèvent une exception, le runtime est une exception de ce type de son choix et se propager en dehors de l’appel à `parallel_invoke`.

Pour plus d’informations, consultez [algorithmes parallèles](../../../parallel/concrt/parallel-algorithms.md).

##  <a name="parallel_radixsort"></a>  parallel_radixsort

Réorganise les éléments d'une plage spécifiée dans un ordre non décroissant à l'aide d'un algorithme de tri de base. Il s'agit d'une fonction de tri stable qui requiert une fonction de projection capable de projeter les éléments à trier dans des clés de type entiers non signés. L'initialisation par défaut est requise pour les éléments triés.

```
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
Type d’itérateur de la plage d’entrée.

*_Allocator*<br/>
Le type d’un allocateur de mémoire compatible de bibliothèque C++ Standard.

*_Function*<br/>
Le type de la fonction de projection.

*_Begin*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*_End*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier.

*_Alloc*<br/>
Une instance d’un allocateur de mémoire compatible de bibliothèque C++ Standard.

*_Proj_func*<br/>
Un objet de fonction de projection défini par l’utilisateur qui convertit un élément en une valeur intégrale.

*_Chunk_size*<br/>
La taille au minimum d’un segment est fractionné en deux pour l’exécution parallèle.

### <a name="remarks"></a>Notes

Toutes les surcharges nécessitent `n * sizeof(T)` espace supplémentaire, où `n` est le nombre d’éléments à trier, et `T` est le type d’élément. Un functor de projection unaire avec la signature `I _Proj_func(T)` est nécessaire pour retourner une clé en fonction d’un élément, où `T` est le type d’élément et `I` est un type de type entier non signé.

Si vous ne fournissez pas une fonction de projection, une fonction de projection par défaut qui renvoie simplement l’élément est utilisée pour les types intégraux. La fonction compilation échouera si l’élément n’est pas un type intégral en l’absence d’une fonction de projection.

Si vous ne fournissez pas un type d’allocateur ou une instance, l’allocateur de mémoire de bibliothèque C++ Standard `std::allocator<T>` est utilisé pour allouer la mémoire tampon.

L’algorithme divise la plage d’entrée en deux blocs et successivement divise chaque segment en deux blocs de sous-répertoire pour l’exécution en parallèle. L’argument facultatif `_Chunk_size` peut être utilisé pour indiquer à l’algorithme qu’il doit gère des segments de taille < `_Chunk_size` en série.

##  <a name="parallel_reduce"></a>  parallel_reduce

Calcule la somme de tous les éléments d'une plage spécifiée en calculant des sommes partielles successives, ou calcule le résultat des résultats partiels successifs obtenus de la même façon en utilisant une opération binaire spécifiée autre que la somme, en parallèle. `parallel_reduce` est sémantiquement similaire à `std::accumulate`, à l'exception près qu'elle a besoin que l'opération binaire soit associative et qu'elle requiert une valeur d'identité au lieu d'une valeur initiale.

```
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
Type d’itérateur de la plage d’entrée.

*_Sym_reduce_fun*<br/>
Le type de la fonction de réduction symétrique. Cela doit être un type de fonction avec la signature `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, où _Reduce_type est le même que le type d’identité et le type de résultat de la réduction. Pour la troisième surcharge, cela doit être cohérente avec le type de sortie `_Range_reduce_fun`.

*_Reduce_type*<br/>
Type permettant de réduire l’entrée, qui peut être différent du type d’élément d’entrée. La valeur de retour et la valeur d’identité sera a ce type.

*_Range_reduce_fun*<br/>
Le type de la fonction de réduction de la plage. Cela doit être un type de fonction avec la signature `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type est le même que le type d’identité et le type de résultat de la réduction.

*_Begin*<br/>
Itérateur d’entrée ciblant le premier élément dans la plage est réduite.

*_End*<br/>
Un itérateur d’entrée qui traite de l’élément qui est une position après le dernier élément dans la plage est réduite.

*_Identity*<br/>
La valeur d’identité `_Identity` est du même type que le type de résultat de la réduction et également le `value_type` de l’itérateur pour les surcharges de la première et deuxième. Pour la troisième surcharge, la valeur d’identité doit avoir le même type que le type de résultat de la réduction, mais peut être différente de la `value_type` de l’itérateur. Il doit avoir une valeur appropriée telle que l’opérateur de réduction de la plage `_Range_fun`, lorsqu’il est appliqué à une plage d’un seul élément de type `value_type` et la valeur d’identité se comporte comme un cast de type de la valeur de type `value_type` au type d’identité.

*_Sym_fun*<br/>
La fonction symétrique qui sera utilisée dans la seconde de la réduction. Pour plus d’informations, consultez Remarques.

*_Range_fun*<br/>
La fonction qui sera utilisée dans la première phase de réduction. Pour plus d’informations, consultez Remarques.

### <a name="return-value"></a>Valeur de retour

Le résultat de la réduction.

### <a name="remarks"></a>Notes

Pour effectuer une réduction parallèle, la fonction divise la plage en segments en fonction du nombre de travaux disponibles pour le planificateur sous-jacent. La réduction s’effectue en deux phases, la première phase effectue une réduction au sein de chaque segment, et la deuxième phase effectue une réduction entre les résultats partiels à partir de chaque segment.

La première surcharge requiert que l’itérateur `value_type`, `T`, être le même que le type de valeur d’identité, ainsi que le type de résultat de réduction. Le type d’élément T doit fournir l’opérateur `T T::operator + (T)` afin de réduire les éléments dans chaque segment. Le même opérateur est utilisé dans la deuxième phase également.

La deuxième surcharge requiert également que l’itérateur `value_type` être le même que le type de valeur d’identité, ainsi que le type de résultat de réduction. L’opérateur binaire fourni `_Sym_fun` est utilisé dans les deux phases de réduction, avec la valeur d’identité comme valeur initiale pour la première phase.

Pour la troisième surcharge, le type de valeur d’identité doit être le même que le type de résultat de réduction, mais l’itérateur `value_type` peuvent être différents des deux. La fonction de réduction de la plage `_Range_fun` est utilisé dans la première phase avec la valeur d’identité en tant que la valeur initiale et la fonction binaire `_Sym_reduce_fun` est appliqué pour sub les résultats dans la deuxième phase.

##  <a name="parallel_sort"></a>  parallel_sort

Réorganise les éléments d’une plage spécifiée dans un ordre non décroissant ou selon un critère de tri spécifié par un prédicat binaire, en parallèle. Cette fonction est sémantiquement similaire à `std::sort` en ce sens qu'il s'agit d'un tri sur place, par comparaison et instable.

```
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
Type d’itérateur de la plage d’entrée.

*_Function*<br/>
Le type de foncteur comparaison binaire.

*_Begin*<br/>
Itérateur d’accès aléatoire ciblant la position du premier élément de la plage à trier.

*_End*<br/>
Itérateur d’accès aléatoire ciblant la position juste après le dernier élément de la plage à trier.

*_Func*<br/>
Un objet de fonction de prédicat défini par l’utilisateur qui définit le critère de comparaison à satisfaire par les éléments consécutifs dans le classement. Un prédicat binaire accepte deux arguments et retourne **true** quand la condition est satisfaite et **false** quand elle ne l’est pas. Cette fonction de comparaison doit imposer un ordre faible strict sur les paires d’éléments de la séquence.

*_Chunk_size*<br/>
La taille au minimum d’un segment est fractionné en deux pour l’exécution parallèle.

### <a name="remarks"></a>Notes

La première surcharge utilise le comparateur binaire `std::less`.

La deuxième surcharge utilise le comparateur fourni binaire doit avoir la signature `bool _Func(T, T)` où `T` est le type des éléments dans la plage d’entrée.

L’algorithme divise la plage d’entrée en deux blocs et successivement divise chaque segment en deux blocs de sous-répertoire pour l’exécution en parallèle. L’argument facultatif `_Chunk_size` peut être utilisé pour indiquer à l’algorithme qu’il doit gère des segments de taille < `_Chunk_size` en série.

##  <a name="parallel_transform"></a>  parallel_transform

Applique un objet de fonction spécifié à chaque élément d'une plage source ou à une paire d'éléments de deux plages sources, et copie les valeurs de retour de l'objet de fonction dans une plage de destination, en parallèle. Cette fonction équivaut sémantiquement à `std::transform`.

```
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
*first1*<br/>
Itérateur d'entrée qui traite la position du premier élément de la première ou de l'unique plage source à traiter.

*last1*<br/>
Itérateur d'entrée qui traite la position de l'élément final dans la première ou dans l'unique plage source à traiter.

*_Result*<br/>
Itérateur de sortie qui traite la position du premier élément dans la plage de destination.

*_Unary_op*<br/>
Objet de fonction unaire défini par l'utilisateur appliqué à chaque élément dans la plage source.

*_Part*<br/>
Référence au partitionneur d'objet. L’argument peut être une des `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ partitionneur](simple-partitioner-class.md) `&` ou [affinity_partitioner](affinity-partitioner-class.md) `&` si un [affinity_partitioner](affinity-partitioner-class.md) objet est utilisé, la référence doit être une l-value de non const référence, afin que l’algorithme peut stocker l’état pour les futures boucles à réutiliser.

*first2*<br/>
Itérateur d'entrée qui traite la position du premier élément de la seconde plage source à traiter.

*_Binary_op*<br/>
Objet de fonction binaire défini par l'utilisateur qui est appliqué par couple, progressivement, sur les deux plages sources.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située immédiatement après le dernier élément de la plage de destination qui reçoit les éléments de sortie transformés par l'objet de fonction.

### <a name="remarks"></a>Notes

[auto_partitioner](auto-partitioner-class.md) sera utilisé pour les surcharges sans argument explicite de partitionneur.

Pour les itérateurs ne prenant pas en charge aléatoire d’accès, uniquement [auto_partitioner](auto-partitioner-class.md) est pris en charge.

Les surcharges prenant l'argument `_Unary_op` transforment la plage d'entrée en plage de sortie en appliquant le foncteur unaire à chaque élément de la plage d'entrée. `_Unary_op` doit prendre en charge l'opérateur d'appel de fonction avec la signature `operator()(T)` où `T` est le type de valeur de la plage à itérer.

Les surcharges prenant l'argument `_Binary_op` transforment deux plages d'entrée en une plage de sortie en appliquant le foncteur binaire à un élément de la première plage d'entrée et à un élément de la deuxième plage d'entrée. `_Binary_op` doit prendre en charge l'opérateur d'appel de fonction avec la signature `operator()(T, U)` où `T`, `U` sont des types de valeur des deux itérateurs d'entrée.

Pour plus d’informations, consultez [algorithmes parallèles](../../../parallel/concrt/parallel-algorithms.md).

##  <a name="receive"></a>  receive

Implémentation générale de la fonction receive, qui permet à un contexte d'attendre des données en provenance d'une seule source exactement et de filtrer les valeurs qui sont acceptées.

```
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
Type de charge utile.

*_Src*<br/>
Pointeur ou référence à la source à partir de laquelle les données sont attendues.

*_Timeout*<br/>
La durée maximale pour laquelle la méthode doit pour les données, en millisecondes.

*_Filter_proc*<br/>
Une fonction de filtre qui détermine si les messages doivent être acceptés.

### <a name="return-value"></a>Valeur de retour

Une valeur de la source, de type de charge utile.

### <a name="remarks"></a>Notes

Si le paramètre `_Timeout` a une valeur autre que la constante `COOPERATIVE_TIMEOUT_INFINITE`, l’exception [operation_timed_out](operation-timed-out-class.md) est levée si le délai spécifié expire avant la réception d’un message. Si vous souhaitez un délai d’attente de longueur nulle, vous devez utiliser le [try_receive](concurrency-namespace-functions.md) (fonction), par opposition à appeler `receive` avec un délai de `0` (zéro), car elle est plus efficace et ne lève pas d’exceptions sur les délais d’attente.

Pour plus d’informations, consultez [fonctions de passage de messages](../../../parallel/concrt/message-passing-functions.md).

##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token

Exécute un objet de fonction immédiatement et de manière synchrone dans le contexte d’un jeton d’annulation donné.

```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Le type de l’objet de fonction qui sera appelé.

*_Func*<br/>
L’objet de fonction qui sera exécuté. Cet objet doit prendre en charge l’opérateur d’appel de fonction avec une signature de void(void).

*_Ct*<br/>
Le jeton d’annulation qui contrôlera implicite d’annulation de l’objet de fonction. Utilisez `cancellation_token::none()` si vous souhaitez que la fonction s’exécuter sans aucune possibilité d’implicite d’annulation à partir d’un groupe de tâches parent qui est annulé.

### <a name="remarks"></a>Notes

Les points d’interruption dans l’objet de fonction sera déclenchée lorsque le `cancellation_token` est annulée. Le jeton explicit `_Ct` cela isolera `_Func` à partir de l’annulation de parent si le parent a un jeton différent ou aucun jeton.

##  <a name="send"></a>  send

Opération d’envoi synchrone qui attend que la cible accepte ou refuse le message.

```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de charge utile.

*_Trg*<br/>
Pointeur ou référence à la cible à laquelle les données sont envoyées.

*_Data*<br/>
Une référence à l’envoi des données.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été accepté, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [fonctions de passage de messages](../../../parallel/concrt/message-passing-functions.md).

##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler

```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Paramètres

*_Scheduler*<br/>
L’utilisation du planificateur ambiant à définir.

##  <a name="set_task_execution_resources"></a>  set_task_execution_resources

Limite les ressources d'exécution utilisées par les threads de travail interne du runtime d'accès concurrentiel à l'ensemble d'affinités spécifié.

Il est possible d'appeler cette méthode uniquement avant de créer le gestionnaire des ressources, ou entre deux durées de vie de gestionnaires des ressources. Cette méthode peut être appelée plusieurs fois tant que le gestionnaire des ressources n'existe pas au moment de l'appel. Une fois qu'une limite d'affinité a été définie, elle reste en vigueur jusqu'au prochain appel valide à la méthode `set_task_execution_resources`.

Le masque d'affinité fourni n'a pas besoin de correspondre à un sous-ensemble du masque d'affinité du processus. L'affinité du processus est mis à jour si besoin.

```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Paramètres

*_ProcessAffinityMask*<br/>
Le masque d’affinité dont les threads de travail du Runtime d’accès concurrentiel doivent être limitées à. Utilisez cette méthode sur un système avec plus de 64 threads matériels uniquement si vous souhaitez limiter le Runtime d’accès concurrentiel à un sous-ensemble du groupe de processeur actuel. En général, vous devez utiliser la version de la méthode qui accepte un tableau d’affinités pour le groupe en tant que paramètre, pour restreindre l’affinité sur les machines de plus de 64 threads matériels.

*count*<br/>
Le nombre de `GROUP_AFFINITY` entrées dans le tableau spécifié par le paramètre `_PGroupAffinity`.

*_PGroupAffinity*<br/>
Un tableau de `GROUP_AFFINITY` entrées.

### <a name="remarks"></a>Notes

La méthode lève un [invalid_operation](invalid-operation-class.md) exception si un gestionnaire de ressources est présent au moment il est appelé, et un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si l’affinité spécifiée des résultats dans un ensemble de vide ressources.

La version de la méthode qui accepte un tableau d’affinités pour le groupe en tant que paramètre doit uniquement être utilisée sur des systèmes d’exploitation avec la version Windows 7 ou version ultérieure. Sinon, un [invalid_operation](invalid-operation-class.md) exception est levée.

Modification par programmation l’affinité du processus une fois que cette méthode a été appelée n’entraîne pas le Gestionnaire de ressources pour réévaluer l’affinité, qu'il se limite aux. Par conséquent, tous les traiter d’affinités doit être modifiées avant d’appeler cette méthode.

##  <a name="swap"></a>  swap

Échange les éléments de deux objets `concurrent_vector`.

```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs simultanés.

*_Ax*<br/>
Le type d’allocateur des vecteurs simultanés.

*_A*<br/>
Vecteur simultané dont les éléments doivent être échangés avec ceux du vecteur simultané `_B`.

*_B*<br/>
Le vecteur simultané qui fournit les éléments à échanger, ou le vecteur dont les éléments doivent être échangés avec ceux du vecteur simultané `_A`.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur `concurrent_vector` pour exécuter la fonction membre `_A`. [concurrent_vector::swap](concurrent-vector-class.md#swap)( `_B`). Il s’agit d’instances de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, `template <class T> void swap(T&, T&)`, dans l’algorithme fonctionne par assignation et est une opération lente de classe. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe de conteneur.

Cette méthode n’est pas concurrentiel. Vous devez vous assurer qu’aucun autre thread n’exécutent des opérations sur un des vecteurs simultanés lorsque vous appelez cette méthode.

##  <a name="task_from_exception"></a>  task_from_exception

```
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

##  <a name="task_from_result"></a>  task_from_result

```
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

##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name

Associe le nom donné au bloc de message ou à l'agent dans le suivi ETW.

```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de l'objet. Il s’agit généralement d’un bloc de message ou d’un agent.

*_PObject*<br/>
Pointeur vers le bloc de message ou d’un agent nommé dans la trace.

*_Name*<br/>
Le nom de l’objet donné.

##  <a name="try_receive"></a>  try_receive

Implémentation générale de la fonction try-receive, qui permet à un contexte de rechercher des données en provenance d'une seule source exactement et de filtrer les valeurs qui sont acceptées. Si les données ne sont pas prêtes, la méthode retourne **false**.

```
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
Type de charge utile

*_Src*<br/>
Pointeur ou référence à la source à partir de laquelle les données sont attendues.

*_value*<br/>
Une référence à un emplacement où le résultat sera placé.

*_Filter_proc*<br/>
Une fonction de filtre qui détermine si les messages doivent être acceptés.

### <a name="return-value"></a>Valeur de retour

Un `bool` valeur indiquant si une charge utile a été placée dans `_value`.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [fonctions de passage de messages](../../../parallel/concrt/message-passing-functions.md).

##  <a name="wait"></a>  wait

Suspend le contexte actuel pendant une durée spécifiée.

```
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Paramètres

*_Milliseconds*<br/>
Le nombre de millisecondes que le contexte actuel doit être suspendu. Si le `_Milliseconds` paramètre est défini sur la valeur `0`, le contexte actuel doit céder l’exécution à d’autres contextes exécutables avant de continuer.

### <a name="remarks"></a>Notes

Si cette méthode est appelée sur un contexte de planificateur de Runtime d’accès concurrentiel, le planificateur trouve un contexte différent pour s’exécuter sur la ressource sous-jacente. Étant donné que le planificateur est coopératif par nature, ce contexte ne peut pas reprendre exactement après le nombre de millisecondes spécifié. Si le planificateur est occupé à exécuter d’autres tâches qui ne génèrent pas manière coopérative au planificateur, le délai d’attente peut être indéfini.

##  <a name="when_all"></a>  when_all

Crée une tâche qui s’effectue correctement lorsque toutes les tâches fournies comme arguments s’effectuent correctement.

```
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

Tâche qui s’effectue correctement lorsque toutes les tâches d’entrée se sont correctement déroulées. Si les tâches d'entrée sont de type `T`, le résultat de cette fonction sera `task<std::vector<T>>`. Si les tâches d’entrée sont de type `void`, la tâche de sortie sera également `task<void>`.

### <a name="remarks"></a>Notes

`when_all` est une fonction non bloquante qui produit un `task` en tant que résultat. Contrairement aux [task::wait](task-class.md#wait), il est déconseillé d’appeler cette fonction dans une application UWP sur le thread ASTA (Application STA).

Si l’une des tâches est annulée ou lève une exception, la tâche retournée se termine au plus tôt, à l’état annulé, et l’exception, si un est prématurément, sera levée si vous appelez [task::get](task-class.md#get) ou `task::wait` sur la tâche.

Pour plus d’informations, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="when_any"></a>  when_any

Crée une tâche qui s'effectue quand l'une des tâches fournies en tant qu'arguments s'effectue.

```
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

Tâche qui s'effectue quand l'une des deux tâches d'entrée s'est correctement déroulée. Si les tâches d'entrée sont de type `T`, la sortie de cette fonction est une `task<std::pair<T, size_t>>>`, où le premier élément de la paire est le résultat de la fin de la tâche et le deuxième élément est l'index de la tâche terminée. Si les tâches d’entrée sont de type `void`, la sortie est une `task<size_t>`, où le résultat est l’index de fin de la tâche.

### <a name="remarks"></a>Notes

`when_any` est une fonction non bloquante qui produit un `task` en tant que résultat. Contrairement aux [task::wait](task-class.md#wait), il est déconseillé d’appeler cette fonction dans une application UWP sur le thread ASTA (Application STA).

Pour plus d’informations, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
