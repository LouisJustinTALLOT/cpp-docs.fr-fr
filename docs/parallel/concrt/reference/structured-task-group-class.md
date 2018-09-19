---
title: structured_task_group, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45daf3c2b2fe71d6e1954d489359e5ebe68ab54d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038592"
---
# <a name="structuredtaskgroup-class"></a>structured_task_group, classe
La classe `structured_task_group` représente une collection très structurée de travail parallèle. Vous pouvez mettre en file d'attente des tâches parallèles individuelles dans un `structured_task_group` à l'aide d'objets `task_handle`, attendre qu'elles se terminent ou annuler le groupe de tâches avant la fin de leur exécution, ce qui annule toutes les tâches dont l'exécution n'a pas commencé.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class structured_task_group;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[structured_task_group](#ctor)|Surchargé. Construit un nouvel `structured_task_group` objet.|  
|[~ structured_task_group, destructeur](#dtor)|Détruit un objet `structured_task_group`. Vous êtes tenu d’appeler le `wait` ou `run_and_wait` méthode sur l’objet avant l’exécution du destructeur, sauf si le destructeur s’exécute comme résultat de déroulement de pile en raison d’une exception.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[cancel](#cancel)|Permet un meilleur effort essaie d’annuler la sous-arborescence de travail rattachée à ce groupe de tâches. Chaque tâche planifiée sur le groupe de tâches sera annulée de manière transitive si possible.|  
|[is_canceling](#is_canceling)|Indique si le groupe de tâches est actuellement en cours d’annulation à l’appelant. Cela n’en indique pas nécessairement que le `cancel` méthode a été appelée sur le `structured_task_group` objet (bien que ce cas la méthode retourne `true`). Il peut arriver que le `structured_task_group` objet exécute inline et un groupe de tâches supplémentaire en haut de l’arborescence de travail a été annulé. Dans tels cas où le runtime peut déterminer avance annulation passera via cet `structured_task_group` objet, `true` s’affichera également.|  
|[run](#run)|Surchargé. Planifie une tâche sur le `structured_task_group` objet. L’appelant gère la durée de vie de la `task_handle` objet passé dans le `_Task_handle` paramètre. La version qui prend le paramètre `_Placement` force la tâche à être orientées vers l’exécution à l’emplacement spécifié par ce paramètre.|  
|[run_and_wait](#run_and_wait)|Surchargé. Planifie une tâche à exécuter inline dans le contexte d’appel avec l’aide de la `structured_task_group` objet pour la prise en charge complète de l’annulation. Si un `task_handle` objet est passé en tant que paramètre à `run_and_wait`, l’appelant est chargé de gérer la durée de vie de la `task_handle` objet. La fonction attend ensuite que tout le travail sur le `structured_task_group` objet est terminée ou annulé.|  
|[attente](#wait)|Attend que tout le travail sur le `structured_task_group` terminée ou est annulée.|  
  
## <a name="remarks"></a>Notes  
 Il existe plusieurs restrictions importantes sur l’utilisation d’un `structured_task_group` objet afin d’obtenir des performances :  
  
-   Un seul `structured_task_group` objet ne peut pas être utilisé par plusieurs threads. Toutes les opérations sur un `structured_task_group` objet doit être effectué par le thread qui a créé l’objet. Les deux exceptions à cette règle sont les fonctions membres `cancel` et `is_canceling`. L’objet ne peut pas être dans la liste de capture d’une expression lambda et être utilisé dans une tâche, à moins que la tâche est à l’aide de l’une des opérations d’annulation.  
  
-   Toutes les tâches planifiées pour un `structured_task_group` objet sont planifiées à l’aide de `task_handle` dont vous devez gérer explicitement la durée de vie des objets.  
  
-   Plusieurs groupes utilisables uniquement dans l’ordre absolument imbriqué. Si deux `structured_task_group` objets sont déclarés, le deuxième déclaré (celui interne) doit être détruit avant toute autre méthode sauf `cancel` ou `is_canceling` est appelée sur le premier (celui externe). Cette condition est vraie en cas de simplement déclarer plusieurs `structured_task_group` objets dans des portées identiques ou fonctionnellement imbriquées, ainsi que le cas d’une tâche qui a été en file d’attente pour le `structured_task_group` via la `run` ou `run_and_wait` méthodes.  
  
-   Contrairement à générales `task_group` classe, tous les États dans le `structured_task_group` classe sont définitives. Après avoir en file d’attente de tâches pour le groupe et attendre qu’elles se terminent, vous ne pouvez pas utiliser le même groupe à nouveau.  
  
 Pour plus d’informations, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `structured_task_group`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ppl.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="cancel"></a> Annuler 

 Permet un meilleur effort essaie d’annuler la sous-arborescence de travail rattachée à ce groupe de tâches. Chaque tâche planifiée sur le groupe de tâches sera annulée de manière transitive si possible.  
  
```
void cancel();
```  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [l’annulation](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="is_canceling"></a> is_canceling 

 Indique si le groupe de tâches est actuellement en cours d’annulation à l’appelant. Cela n’en indique pas nécessairement que le `cancel` méthode a été appelée sur le `structured_task_group` objet (bien que ce cas la méthode retourne `true`). Il peut arriver que le `structured_task_group` objet exécute inline et un groupe de tâches supplémentaire en haut de l’arborescence de travail a été annulé. Dans tels cas où le runtime peut déterminer avance annulation passera via cet `structured_task_group` objet, `true` s’affichera également.  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une indication précisant si le `structured_task_group` objet est en cours d’annulation (ou est garantie comme étant peu de temps).  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [l’annulation](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="run"></a> exécuter 

 Planifie une tâche sur le `structured_task_group` objet. L’appelant gère la durée de vie de la `task_handle` objet passé dans le `_Task_handle` paramètre. La version qui prend le paramètre `_Placement` force la tâche à être orientées vers l’exécution à l’emplacement spécifié par ce paramètre.  
  
```
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```  
  
### <a name="parameters"></a>Paramètres  
*_Function*<br/>
Le type de l’objet de fonction qui sera appelé pour exécuter le corps de la poignée de la tâche.  
  
*_Task_handle*<br/>
Handle vers le travail planifié. Notez que l’appelant est responsable de la durée de vie de cet objet. Le runtime continue à attendre qu’il live jusqu'à ce que le `wait` ou `run_and_wait` méthode a été appelée sur ce `structured_task_group` objet.  
  
*_Placement*<br/>
Une référence à l’emplacement où la tâche représentée par le `_Task_handle` paramètre doit s’exécuter.  
  
### <a name="remarks"></a>Notes  
 Le runtime crée une copie de la fonction de travail que vous passez à cette méthode. Modifications d’état qui se produisent dans un objet de fonction que vous passez à cette méthode n’apparaîtra pas dans votre copie de cet objet de fonction.  
  
 Si le `structured_task_group` résulte du déroulement d’une exception de la pile, vous n’avez pas besoin garantir qu’un appel a été effectué avec la valeur la `wait` ou `run_and_wait` (méthode). Dans ce cas, le destructeur annulera et attendez que la tâche représentée par le `_Task_handle` paramètre pour terminer.  
  
 Lève une [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) exception si la tâche gérer donné par le `_Task_handle` paramètre a déjà été planifié sur un objet de groupe de tâches via la `run` (méthode) et il n’y a eu aucun appel à soit le `wait` ou `run_and_wait` méthode sur ce groupe de tâches.  
  
##  <a name="run_and_wait"></a> run_and_wait 

 Planifie une tâche à exécuter inline dans le contexte d’appel avec l’aide de la `structured_task_group` objet pour la prise en charge complète de l’annulation. Si un `task_handle` objet est passé en tant que paramètre à `run_and_wait`, l’appelant est chargé de gérer la durée de vie de la `task_handle` objet. La fonction attend ensuite que tout le travail sur le `structured_task_group` objet est terminée ou annulé.  
  
```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```  
  
### <a name="parameters"></a>Paramètres  
*_Function*<br/>
Le type de l’objet de fonction qui sera appelé pour exécuter la tâche.  
  
*_Task_handle*<br/>
Handle vers la tâche qui sera exécutée inline sur le contexte d’appel. Notez que l’appelant est responsable de la durée de vie de cet objet. Le runtime continue à attendre qu’il vivre jusqu'à la `run_and_wait` méthode termine son exécution.  
  
*_Func*<br/>
Une fonction qui sera appelée pour appeler le corps du travail. Cela peut être une expression lambda ou un autre objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature `void operator()()`.  
  
### <a name="return-value"></a>Valeur de retour  
 Indique si l’attente a été satisfaite ou le groupe de tâches a été annulé en raison d’une opération d’annulation explicite ou une exception levée par une de ses tâches. Pour plus d’informations, consultez [task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>Notes  
 Notez qu’une ou plusieurs des tâches planifiées pour cet `structured_task_group` objet peut-être s’exécuter inline dans le contexte d’appel.  
  
 Si un ou plusieurs des tâches planifiées pour cet `structured_task_group` objet lève une exception, le runtime sélectionne une exception de ce type de son choix et se propager en dehors de l’appel à la `run_and_wait` (méthode).  
  
 Une fois que cette fonction retourne, le `structured_task_group` objet soit considérée comme étant un état final et ne doit pas être utilisé. Notez que son utilisation après le `run_and_wait` méthode retourne entraîne un comportement non défini.  
  
 Dans le chemin d’accès non exceptionnel d’exécution, vous avez un mandat pour appeler cette méthode ou la `wait` méthode avant le destructeur de la `structured_task_group` s’exécute.  
  
##  <a name="ctor"></a> structured_task_group 

 Construit un nouvel `structured_task_group` objet.  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>Paramètres  
*_CancellationToken*<br/>
Un jeton d’annulation à associer à ce groupe de tâches structurés. Le groupe de tâches structurés sera annulé lorsque le jeton est annulé.  
  
### <a name="remarks"></a>Notes  
 Le constructeur qui accepte un jeton d’annulation crée un `structured_task_group` qui sera annulée lors de l’annulation de la source associée au jeton. En fournissant un jeton d’annulation explicite isole également ce groupe de tâches structurés de participer à une annulation implicite d’un groupe parent avec un autre jeton ou aucun jeton.  
  
##  <a name="dtor"></a> ~structured_task_group 

 Détruit un objet `structured_task_group`. Vous êtes tenu d’appeler le `wait` ou `run_and_wait` méthode sur l’objet avant l’exécution du destructeur, sauf si le destructeur s’exécute comme résultat de déroulement de pile en raison d’une exception.  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>Notes  
 Si le destructeur s’exécute en tant que le résultat de l’exécution normale (par exemple, pas déroulement de pile en raison d’une exception) et ni le `wait` ni `run_and_wait` méthodes ont été appelées, le destructeur peut lever une [missing_wait](missing-wait-class.md) exception.  
  
##  <a name="wait"></a> attente 

 Attend que tout le travail sur le `structured_task_group` terminée ou est annulée.  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Indique si l’attente a été satisfaite ou le groupe de tâches a été annulé en raison d’une opération d’annulation explicite ou une exception levée par une de ses tâches. Pour plus d’informations, consultez [task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>Notes  
 Notez qu’une ou plusieurs des tâches planifiées pour cet `structured_task_group` objet peut-être s’exécuter inline dans le contexte d’appel.  
  
 Si un ou plusieurs des tâches planifiées pour cet `structured_task_group` objet lève une exception, le runtime sélectionne une exception de ce type de son choix et se propager en dehors de l’appel à la `wait` (méthode).  
  
 Une fois que cette fonction retourne, le `structured_task_group` objet soit considérée comme étant un état final et ne doit pas être utilisé. Notez que son utilisation après le `wait` méthode retourne entraîne un comportement non défini.  
  
 Dans le chemin d’accès non exceptionnel d’exécution, vous avez un mandat pour appeler cette méthode ou la `run_and_wait` méthode avant le destructeur de la `structured_task_group` s’exécute.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [task_group, classe](task-group-class.md)   
 [task_handle, classe](task-handle-class.md)
