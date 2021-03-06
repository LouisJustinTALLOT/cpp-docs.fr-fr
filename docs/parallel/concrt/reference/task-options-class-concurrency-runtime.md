---
description: 'En savoir plus sur : classe task_options (runtime d’accès concurrentiel)'
title: task_options, classe (runtime d’accès concurrentiel)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: 3752d23e68096df22d076afc5c07dc3d66cc881a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188207"
---
# <a name="task_options-class-concurrency-runtime"></a>task_options, classe (runtime d’accès concurrentiel)

Représente les options autorisées pour la création d’une tâche.

## <a name="syntax"></a>Syntaxe

```cpp
class task_options;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[task_options::task_options, constructeur (runtime d'accès concurrentiel)](#ctor)|Surchargé. Liste des options de création de tâche par défaut|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[task_options::get_cancellation_token, méthode (runtime d’accès concurrentiel)](#get_cancellation_token)|Retourne le jeton d'annulation|
|[task_options::get_continuation_context, méthode (runtime d'accès concurrentiel)](#get_continuation_context)|Retourne le contexte de continuation|
|[task_options::get_scheduler, méthode (runtime d’accès concurrentiel)](#get_scheduler)|Retourne le planificateur|
|[task_options::has_cancellation_token, méthode (runtime d’accès concurrentiel)](#has_cancellation_token)|Indique si un jeton d'annulation a été spécifié par l'utilisateur|
|[task_options::has_scheduler, méthode (runtime d'accès concurrentiel)](#has_scheduler)|Indique si un planificateur n a été spécifié par l'utilisateur|
|[task_options::set_cancellation_token, méthode (runtime d’accès concurrentiel)](#set_cancellation_token)|Définit le jeton donné dans les options|
|[task_options::set_continuation_context, méthode (runtime d'accès concurrentiel)](#set_continuation_context)|Définit le contexte de continuation donné dans les options|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`task_options`

## <a name="requirements"></a>Spécifications

**En-tête :** ppltasks. h

**Espace de noms :** concurrence

## <a name="task_optionsget_cancellation_token-method-concurrency-runtime"></a><a name="get_cancellation_token"></a> task_options :: get_cancellation_token, méthode (runtime d’accès concurrentiel)

Retourne le jeton d'annulation

```cpp
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>Valeur renvoyée

## <a name="task_optionsget_continuation_context-method-concurrency-runtime"></a><a name="get_continuation_context"></a> task_options :: get_continuation_context, méthode (runtime d’accès concurrentiel)

Retourne le contexte de continuation

```cpp
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>Valeur renvoyée

## <a name="task_optionsget_scheduler-method-concurrency-runtime"></a><a name="get_scheduler"></a> task_options :: get_scheduler, méthode (runtime d’accès concurrentiel)

Retourne le planificateur

```cpp
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>Valeur renvoyée

## <a name="task_optionshas_cancellation_token-method-concurrency-runtime"></a><a name="has_cancellation_token"></a> task_options :: has_cancellation_token, méthode (runtime d’accès concurrentiel)

Indique si un jeton d'annulation a été spécifié par l'utilisateur

```cpp
bool has_cancellation_token() const;
```

### <a name="return-value"></a>Valeur renvoyée

## <a name="task_optionshas_scheduler-method-concurrency-runtime"></a><a name="has_scheduler"></a> task_options :: has_scheduler, méthode (runtime d’accès concurrentiel)

Indique si un planificateur n a été spécifié par l'utilisateur

```cpp
bool has_scheduler() const;
```

### <a name="return-value"></a>Valeur renvoyée

## <a name="task_optionsset_cancellation_token-method-concurrency-runtime"></a><a name="set_cancellation_token"></a> task_options :: set_cancellation_token, méthode (runtime d’accès concurrentiel)

Définit le jeton donné dans les options

```cpp
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>Paramètres

`_Token`

## <a name="task_optionsset_continuation_context-method-concurrency-runtime"></a><a name="set_continuation_context"></a> task_options :: set_continuation_context, méthode (runtime d’accès concurrentiel)

Définit le contexte de continuation donné dans les options

```cpp
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>Paramètres

`_ContinuationContext`

## <a name="task_optionstask_options-constructor-concurrency-runtime"></a><a name="ctor"></a> task_options :: task_options, constructeur (runtime d’accès concurrentiel)

Liste des options de création de tâche par défaut

```cpp
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```

### <a name="parameters"></a>Paramètres

`_SchedType`

`_Token`

`_ContinuationContext`

`_Scheduler`

`_TaskOptions`

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
