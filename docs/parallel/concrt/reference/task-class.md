---
title: "Task, classe (Runtime d’accès concurrentiel) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ea618ca6a5784b44666c70d79bb10b2e9f6e394
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="task-class-concurrency-runtime"></a>task (Concurrency Runtime), classe
Classe `task` de la bibliothèque de modèles parallèles (PPL, Parallel Patterns Library). Un objet `task` représente le travail qui peut être exécuté de manière asynchrone et simultanément avec d'autres tâches et le travail parallèle produit par des algorithmes parallèles dans le runtime d'accès concurrentiel. Il génère un résultat de type `_ResultType` quand il s'exécute correctement. Les tâches de type `task<void>` ne génèrent aucun résultat. Une tâche peut être mise en attente et annulée indépendamment des autres tâches. Elle peut également être composée avec d’autres tâches à l’aide de continuations ( `then`) et de jointure ( `when_all`) et un choix ( `when_any`) des modèles.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>
class task;

template <>
class task<void>;

template<typename _ReturnType>
class task;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 `T`  
 `_ReturnType`  
 Type de résultat de cette tâche.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`result_type`|Type de résultat produit par un objet de cette classe.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[tâche](#ctor)|Surchargé. Construit un objet `task`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[get](#get)|Surchargé. Retourne le résultat produit par cette tâche. Si la tâche n'est pas dans un état terminal, un appel à `get` attendra que la tâche se termine. Cette méthode ne retourne pas de valeur lorsqu'elle est appelée sur une tâche dont le `result_type` a la valeur `void`.|  
|[is_apartment_aware](#is_apartment_aware)|Détermine si la tâche désencapsule une interface `IAsyncInfo` Windows Runtime ou descend de cette tâche.|  
|[is_done](#is_done)|Détermine si la tâche est terminée.|  
|[Planificateur](#scheduler)|Retourne le planificateur pour cette tâche.|  
|[puis](#then)|Surchargé. Ajoute une tâche de continuation à cette tâche.|  
|[attente](#wait)|Attend que cette tâche atteigne un état terminal. Il est possible que `wait` exécute la tâche inline si toutes les dépendances de tâches sont remplies et si elle n'a pas déjà été sélectionnée pour être exécutée par un processus de travail d'arrière-plan.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Surchargé. Détermine si deux objets `task` représentent différentes tâches internes.|  
|[operator=](#operator_eq)|Surchargé. Remplace le contenu d'un objet `task` par un autre.|  
|[operator==](#operator_eq_eq)|Surchargé. Détermine si deux objets `task` représentent la même tâche interne.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `task`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ppltasks.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="get"></a>Télécharger 

 Retourne le résultat produit par cette tâche. Si la tâche n'est pas dans un état terminal, un appel à `get` attendra que la tâche se termine. Cette méthode ne retourne pas de valeur lorsqu'elle est appelée sur une tâche dont le `result_type` a la valeur `void`.  
  
```
_ReturnType get() const;

void get() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Résultat de la tâche.  
  
### <a name="remarks"></a>Notes  
 Si la tâche est annulée, un appel à `get` lèvera une [task_canceled](task-canceled-class.md) exception. Si la tâche rencontre une exception différente ou si une exception est propagée à cette tâche à partir d'une tâche précédente, un appel à `get` lève cette exception.  
  
> [!IMPORTANT]
>  Dans un [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] application, n’appelez pas [Concurrency::Task :: wait](#wait) ou `get` ( `wait` appelle `get`) dans le code qui s’exécute sur le STA. Sinon, le runtime lève [concurrency::invalid_operation](invalid-operation-class.md) , car ces méthodes bloque le thread actuel et peut entraîner l’application de ne plus répondre. Toutefois, vous pouvez appeler la `get` méthode pour recevoir le résultat de la tâche précédente dans une continuation basée sur des tâches, car le résultat est immédiatement disponible.  
  
##  <a name="is_apartment_aware"></a>is_apartment_aware 

 Détermine si la tâche désencapsule une interface `IAsyncInfo` Windows Runtime ou descend de cette tâche.  
  
```
bool is_apartment_aware() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si la tâche désencapsule une interface `IAsyncInfo` ou est descendue de cette tâche ; sinon, `false`.  
  
##  <a name="is_done"></a>Task::is_done, méthode (Runtime d’accès concurrentiel)  
 Détermine si la tâche est terminée.  
  
```
bool is_done() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 True si la tâche est terminée, false dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 La fonction retourne la valeur true si la tâche est terminée ou annulée (avec ou sans exception utilisateur).  
  
##  <a name="operator_neq"></a>opérateur ! = 

 Détermine si deux objets `task` représentent différentes tâches internes.  
  
```
bool operator!= (const task<_ReturnType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les objets font référence à différentes tâches sous-jacentes ; sinon `false`.  
  
##  <a name="operator_eq"></a>opérateur = 

 Remplace le contenu d'un objet `task` par un autre.  
  
```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Objet `task` source.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Étant donné que `task` se comporte comme un pointeur intelligent, après une assignation de copie, cet objet `task` représente la même tâche réelle que `_Other`.  
  
##  <a name="operator_eq_eq"></a>opérateur == 

 Détermine si deux objets `task` représentent la même tâche interne.  
  
```
bool operator== (const task<_ReturnType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les objets font référence à la même tâche sous-jacente ; sinon, `false`.  
  
##  <a name="scheduler"></a>Task::Scheduler, méthode (Runtime d’accès concurrentiel)  
 Retourne le planificateur pour cette tâche.  
  
```
scheduler_ptr scheduler() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le planificateur  
  
##  <a name="ctor"></a>tâche 

 Construit un objet `task`.  
  
```
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
 `T`  
 Type du paramètre à partir duquel la tâche doit être construite.  
  
 `_Param`  
 Paramètre à partir duquel la tâche doit être construite. Il peut s'agir d'une expression lambda, d'un objet de fonction, d'un objet `task_completion_event<result_type>` ou d'une interface Windows::Foundation::IAsyncInfo si vous utilisez des tâches dans votre application Windows Store. L'expression lambda ou l'objet de fonction doit être un type équivalent à `std::function<X(void)>`, où X peut être une variable de type `result_type`, `task<result_type>` ou une interface Windows::Foundation::IAsyncInfo dans les applications Windows Store.  
  
 `_TaskOptions`  
 Les options de tâche incluent le jeton d’annulation, le planificateur, etc.  
  
 `_Other`  
 Objet `task` source.  
  
### <a name="remarks"></a>Notes  
 Le constructeur par défaut pour `task` est uniquement présent pour permettre l'utilisation des tâches dans des conteneurs. Une tâche créée par défaut ne peut pas être utilisée tant que vous ne lui assignez pas une tâche valide. Les méthodes telles que `get`, `wait` ou `then` lèvera une [invalid_argument](../../../standard-library/invalid-argument-class.md) exception lorsqu’elle est appelée sur une tâche créée par défaut.  
  
 Une tâche créée à partir d'un objet `task_completion_event` s'achève (et ses continuations sont planifiées) lorsque l'événement d'achèvement de tâche est défini.  
  
 La version du constructeur qui accepte un jeton d'annulation crée une tâche qui peut être annulée en utilisant la classe `cancellation_token_source` à partir de laquelle le jeton a été obtenu. Les tâches créées sans jeton d'annulation ne sont pas annulables.  
  
 Les tâches créées à partir d'une interface `Windows::Foundation::IAsyncInfo` ou d'une expression lambda qui retourne une interface `IAsyncInfo` atteignent leur état terminal lorsque l'opération ou l'action asynchrone Windows Runtime se termine. De même, les tâches créées à partir d'une expression lamda qui retourne un objet `task<result_type>` atteignent leur état terminal lorsque la tâche interne atteint son état terminal, et non lorsque le résultat de l'expression lamda est retourné.  
  
 `task` se comporte comme un pointeur intelligent dont le passage par valeur est sécurisé. Il est accessible par plusieurs threads sans nécessiter de verrous.  
  
 Les surcharges de constructeur qui acceptent une interface Windows::Foundation::IAsyncInfo ou une expression lambda retournant une telle interface sont uniquement disponibles pour les applications Windows Store.  
  
 Pour plus d’informations, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="then"></a>puis 

 Ajoute une tâche de continuation à cette tâche.  
  
```
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

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
 `_Function`  
 Type de l’objet fonction qui sera appelé par cette tâche.  
  
 `_Func`  
 Fonction de continuation à exécuter lorsque cette tâche se termine. Cette fonction de continuation doit accepter comme entrée une variable `result_type` ou `task<result_type>`, où `result_type` correspond au type du résultat produit par cette tâche.  
  
 `_TaskOptions`  
 Les options de la tâche incluent le jeton d’annulation, le planificateur et le contexte de continuation. Par défaut, les 3 options précédentes sont héritées de la tâche précédente.  
  
 `_CancellationToken`  
 Jeton d’annulation à associer à la tâche de continuation. Une tâche de continuation créée sans jeton d’annulation hérite du jeton de son antécédent.  
  
 `_ContinuationContext`  
 Variable qui spécifie où la continuation doit s'exécuter. Cette variable est utile uniquement lorsqu'elle est utilisée dans une application Windows Store. Pour plus d’informations, consultez [task_continuation_context](task-continuation-context-class.md)  
  
### <a name="return-value"></a>Valeur de retour  
 Tâche de continuation récemment créée. Le type de résultat de la tâche retournée est déterminé par l'élément retourné par `_Func`.  
  
### <a name="remarks"></a>Notes  
 Les surcharges de `then` qui acceptent une expression lambda ou un foncteur qui retourne une interface Windows::Foundation::IAsyncInfo sont uniquement disponibles pour les applications Windows Store.  
  
 Pour plus d’informations sur l’utilisation de continuations de tâches pour composer le travail asynchrone, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="wait"></a>attente 

 Attend que cette tâche atteigne un état terminal. Il est possible que `wait` exécute la tâche inline si toutes les dépendances de tâches sont remplies et si elle n'a pas déjà été sélectionnée pour être exécutée par un processus de travail d'arrière-plan.  
  
```
task_status wait() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `task_status` qui peut être `completed` ou `canceled`. Si la tâche rencontre une exception pendant l'exécution, ou si une exception y est propagée à partir d'une tâche précédente, `wait` lèvera cette exception.  
  
### <a name="remarks"></a>Notes  
  
> [!IMPORTANT]
>  Dans un [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] application, n’appelez pas `wait` dans le code qui s’exécute sur le STA. Sinon, le runtime lève [concurrency::invalid_operation](invalid-operation-class.md) , car cette méthode bloque le thread actuel et peut entraîner l’application de ne plus répondre. Toutefois, vous pouvez appeler la [Concurrency::Task :: Get](#get) méthode pour recevoir le résultat de la tâche précédente dans une continuation basée sur des tâches.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
