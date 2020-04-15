---
title: task (Concurrency Runtime), classe
ms.date: 07/30/2019
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: d42c7fbd3e065fc295027b7c56e207b2a49221bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358737"
---
# <a name="task-class-concurrency-runtime"></a>task (Concurrency Runtime), classe

Classe `task` de la bibliothèque de modèles parallèles (PPL, Parallel Patterns Library). Un `task` objet représente un travail qui peut être exécuté asynchronement et en même temps avec d’autres tâches et un travail parallèle produit par des algorithmes parallèles dans le Temps d’exécution De concurrency. Il génère un résultat de type `_ResultType` quand il s'exécute correctement. Les tâches de type `task<void>` ne génèrent aucun résultat. Une tâche peut être mise en attente et annulée indépendamment des autres tâches. Il peut également être composé avec `then`d’autres `when_all`tâches en `when_any`utilisant des continuations ( ), et rejoindre ( ) et le choix) ) modèles. Lorsqu’un objet de tâche est assigné à `std::shared_ptr`une nouvelle variable, le comportement est celui de ; en d’autres termes, les deux objets représentent la même tâche sous-jacente.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>Paramètres

*_ResultType*<br/>
Le type de résultat produit par la tâche.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`result_type`|Type de résultat produit par un objet de cette classe.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Tâche](#ctor)|Surchargé. Construit un objet `task`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get](#get)|Surchargé. Retourne le résultat produit par cette tâche. Si la tâche n’est pas dans un état terminal, un appel à `get` attendra que la tâche se termine. Cette méthode ne retourne pas de valeur lorsqu’elle est appelée sur une tâche dont le `result_type` a la valeur `void`.|
|[is_apartment_aware](#is_apartment_aware)|Détermine si la tâche désencapsule une interface `IAsyncInfo` Windows Runtime ou descend de cette tâche.|
|[is_done](#is_done)|Détermine si la tâche est terminée.|
|[Planificateur](#scheduler)|Retourne le planificateur pour cette tâche.|
|[, puis](#then)|Surchargé. Ajoute une tâche de continuation à cette tâche.|
|[Attendre](#wait)|Attend que cette tâche atteigne un état terminal. Il est possible que `wait` exécute la tâche inline si toutes les dépendances de tâches sont remplies et si elle n’a pas déjà été sélectionnée pour être exécutée par un processus de travail d’arrière-plan.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur!](#operator_neq)|Surchargé. Détermine si deux objets `task` représentent différentes tâches internes.|
|[opérateur](#operator_eq)|Surchargé. Remplace le contenu d'un objet `task` par un autre.|
|[opérateur](#operator_eq_eq)|Surchargé. Détermine si deux objets `task` représentent la même tâche interne.|

## <a name="remarks"></a>Notes

Pour plus d’informations, voir [Le parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`task`

## <a name="requirements"></a>Spécifications

**En-tête:** ppltasks.h

**Namespace:** concurrence

## <a name="get"></a><a name="get"></a>Avoir

Retourne le résultat produit par cette tâche. Si la tâche n’est pas dans un état terminal, un appel à `get` attendra que la tâche se termine. Cette méthode ne retourne pas de valeur lorsqu’elle est appelée sur une tâche dont le `result_type` a la valeur `void`.

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>Valeur de retour

Résultat de la tâche.

### <a name="remarks"></a>Notes

Si la tâche est annulée, `get` un appel à jeter une [task_canceled](task-canceled-class.md) exception. Si la tâche rencontre une exception différente ou si une exception est propagée à cette tâche à partir d'une tâche précédente, un appel à `get` lève cette exception.

> [!IMPORTANT]
> Dans une application Universal Windows Platform (UWP), n’appelez pas [la concurrence::task::wait](#wait) or `get` ( `wait` calls `get`) dans le code qui s’exécute sur le thread utilisateur-interface. Sinon, le temps d’exécution jette [la concurrence::invalid_operation](invalid-operation-class.md) parce que ces méthodes bloquent le thread actuel et peuvent provoquer l’application de devenir insensible. Cependant, vous pouvez `get` appeler la méthode pour recevoir le résultat de la tâche antérieure dans une continuation basée sur les tâches parce que le résultat est immédiatement disponible.

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a>is_apartment_aware

Détermine si la tâche désencapsule une interface `IAsyncInfo` Windows Runtime ou descend de cette tâche.

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si la tâche déballe une `IAsyncInfo` interface ou descend d’une telle tâche, **faux** autrement.

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a>tâche::is_done Méthode (Concurrency Runtime)

Détermine si la tâche est terminée.

```cpp
bool is_done() const;
```

### <a name="return-value"></a>Valeur de retour

C’est vrai que si la tâche est terminée, faux sinon.

### <a name="remarks"></a>Notes

La fonction renvoie si la tâche est terminée ou annulée (avec ou sans exception utilisateur).

## <a name="operator"></a><a name="operator_neq"></a>opérateur!

Détermine si deux objets `task` représentent différentes tâches internes.

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
La tâche à comparer.

### <a name="return-value"></a>Valeur de retour

**vrai** si les objets se réfèrent à différentes tâches sous-jacentes, et **faux** autrement.

## <a name="operator"></a><a name="operator_eq"></a>opérateur

Remplace le contenu d'un objet `task` par un autre.

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `task` source.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Étant donné que `task` se comporte comme un pointeur intelligent, après une assignation de copie, cet objet `task` représente la même tâche réelle que `_Other`.

## <a name="operator"></a><a name="operator_eq_eq"></a>opérateur

Détermine si deux objets `task` représentent la même tâche interne.

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
La tâche à comparer.

### <a name="return-value"></a>Valeur de retour

**vrai** si les objets se réfèrent à la même tâche sous-jacente, et **faux** autrement.

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a>tâche::méthode de planificateur (Concurrency Runtime)

Retourne le planificateur pour cette tâche.

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur pour le planificateur

## <a name="task"></a>Tâche <a name="ctor"></a>

Construit un objet `task`.

```cpp
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type du paramètre à partir duquel la tâche doit être construite.

*_Param*<br/>
Paramètre à partir duquel la tâche doit être construite. Il peut s’agir d’un `task_completion_event<result_type>` lambda, d’un objet de fonction, d’un objet ou d’un Windows::Foundation::IAsyncInfo si vous utilisez des tâches dans votre application Windows Runtime. Le lambda ou l’objet de `std::function<X(void)>`fonction doit être un `result_type`type `task<result_type>`équivalent à , où X peut être une variable de type , , ou un Windows::Foundation::IAsyncInfo dans windows Runtime applications.

*_TaskOptions*<br/>
Les options de tâche incluent le jeton d’annulation, le planificateur, etc.

*_Other*<br/>
Objet `task` source.

### <a name="remarks"></a>Notes

Le constructeur par défaut pour `task` est uniquement présent pour permettre l’utilisation des tâches dans des conteneurs. Une tâche créée par défaut ne peut pas être utilisée tant que vous ne lui assignez pas une tâche valide. Méthodes telles `get` `wait` que `then` , ou jettera une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) lorsqu’il est appelé sur une tâche construite par défaut.

Une tâche créée à partir d’un objet `task_completion_event` s’achève (et ses continuations sont planifiées) lorsque l’événement d’achèvement de tâche est défini.

La version du constructeur qui accepte un jeton d’annulation crée une tâche qui peut être annulée en utilisant la classe `cancellation_token_source` à partir de laquelle le jeton a été obtenu. Les tâches créées sans jeton d'annulation ne sont pas annulables.

Les tâches créées à partir d’une interface `Windows::Foundation::IAsyncInfo` ou d’une expression lambda qui retourne une interface `IAsyncInfo` atteignent leur état terminal lorsque l’opération ou l’action asynchrone Windows Runtime se termine. De même, les tâches créées `task<result_type>` à partir d’un lambda qui retourne un accès à leur état terminal lorsque la tâche interne atteint son état terminal, et non pas quand le lambda revient.

`task` se comporte comme un pointeur intelligent dont le passage par valeur est sécurisé. Il est accessible par plusieurs threads sans nécessiter de verrous.

Les surcharges de constructeurs qui prennent un Windows::Foundation::IAsyncInfo interface ou un lambda retour d’une telle interface, ne sont disponibles que pour les applications Windows Runtime.

Pour plus d’informations, voir [Le parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="then"></a><a name="then"></a>Puis

Ajoute une tâche de continuation à cette tâche.

```cpp
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l’objet fonction qui sera appelé par cette tâche.

*_Func*<br/>
Fonction de continuation à exécuter lorsque cette tâche se termine. Cette fonction de continuation doit accepter comme entrée une variable `result_type` ou `task<result_type>`, où `result_type` correspond au type du résultat produit par cette tâche.

*_TaskOptions*<br/>
Les options de la tâche incluent le jeton d'annulation, le planificateur et le contexte de continuation. Par défaut, les 3 options précédentes sont héritées de la tâche précédente.

*_CancellationToken*<br/>
Jeton d'annulation à associer à la tâche de continuation. Une tâche de continuation créée sans jeton d‘annulation hérite du jeton de son antécédent.

*_ContinuationContext*<br/>
Variable qui spécifie où la continuation doit s'exécuter. Cette variable n’est utile que lorsqu’elle est utilisée dans une application UWP. Pour plus d’informations, voir [task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Valeur de retour

Tâche de continuation récemment créée. Le type de résultat de la tâche retournée est déterminé par l’élément retourné par `_Func`.

### <a name="remarks"></a>Notes

Les surcharges `then` de ce prendre un lambda ou functor qui retourne un Windows::Foundation::IAsyncInfo interface, ne sont disponibles que pour les applications Windows Runtime.

Pour plus d’informations sur la façon d’utiliser les continuations des tâches pour composer un travail asynchrone, voir [Le parallélisme de tâche](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="wait"></a><a name="wait"></a>Attendre

Attend que cette tâche atteigne un état terminal. Il est possible que `wait` exécute la tâche inline si toutes les dépendances de tâches sont remplies et si elle n’a pas déjà été sélectionnée pour être exécutée par un processus de travail d’arrière-plan.

```cpp
task_status wait() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur `task_status` qui peut être `completed` ou `canceled`. Si la tâche rencontre une exception pendant l‘exécution, ou si une exception y est propagée à partir d‘une tâche précédente, `wait` lèvera cette exception.

### <a name="remarks"></a>Notes

> [!IMPORTANT]
> Dans une application Universal Windows Platform (UWP), n’appelez `wait` pas de code qui s’exécute sur le thread utilisateur-interface. Sinon, le runtime lève [concurrency::invalid_operation](invalid-operation-class.md) , car cette méthode bloque le thread actuel et peut provoquer le blocage de l'application. Toutefois, vous pouvez appeler la méthode [concurrency::task::get](#get) pour recevoir le résultat de la tâche précédente dans une continuation basée sur des tâches.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
