---
title: structured_task_group, classe
ms.date: 11/04/2016
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
ms.openlocfilehash: 93dd79b755f79dcb4857c1b1c4856362b0bd45dd
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422128"
---
# <a name="structured_task_group-class"></a>structured_task_group, classe

La classe `structured_task_group` représente une collection très structurée de travail parallèle. Vous pouvez mettre en file d'attente des tâches parallèles individuelles dans un `structured_task_group` à l'aide d'objets `task_handle`, attendre qu'elles se terminent ou annuler le groupe de tâches avant la fin de leur exécution, ce qui annule toutes les tâches dont l'exécution n'a pas commencé.

## <a name="syntax"></a>Syntaxe

```cpp
class structured_task_group;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[structured_task_group](#ctor)|Surchargé. Construit un nouvel objet `structured_task_group`.|
|[Destructeur ~ structured_task_group](#dtor)|Détruit un objet `structured_task_group`. Vous devez appeler la méthode `wait` ou `run_and_wait` sur l’objet avant l’exécution du destructeur, sauf si le destructeur s’exécute à la suite d’un déroulement de pile en raison d’une exception.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[cancel](#cancel)|Tente d’annuler la sous-arborescence du travail enracinée dans ce groupe de tâches. Chaque tâche planifiée sur le groupe de tâches est annulée de manière transitive, si possible.|
|[is_canceling](#is_canceling)|Informe l’appelant si le groupe de tâches est actuellement au milieu d’une annulation. Cela n’indique pas nécessairement que la méthode `cancel` a été appelée sur l’objet `structured_task_group` (bien que cela qualifie certainement cette méthode pour retourner la **valeur true**). Cela peut être le cas lorsque l’objet `structured_task_group` s’exécute en ligne et qu’un groupe de tâches plus haut dans l’arborescence de travail a été annulé. Dans les cas tels que ceux où le runtime peut déterminer à l’avance que l’annulation passera par cet objet `structured_task_group`, la **valeur true** sera également retournée.|
|[run](#run)|Surchargé. Planifie une tâche sur l’objet `structured_task_group`. L’appelant gère la durée de vie de l’objet `task_handle` passé dans le paramètre `_Task_handle`. La version qui accepte le paramètre `_Placement` entraîne l’exécution de la tâche à l’emplacement spécifié par ce paramètre.|
|[run_and_wait](#run_and_wait)|Surchargé. Planifie l’exécution d’une tâche Inline sur le contexte appelant avec l’assistance de l’objet `structured_task_group` pour la prise en charge de l’annulation complète. Si un objet `task_handle` est passé en tant que paramètre à `run_and_wait`, l’appelant est responsable de la gestion de la durée de vie de l’objet `task_handle`. La fonction attend ensuite que tout le travail sur l’objet `structured_task_group` soit terminé ou a été annulé.|
|[qu'](#wait)|Attend que tout le travail sur le `structured_task_group` soit terminé ou qu’il soit annulé.|

## <a name="remarks"></a>Notes

Il existe un certain nombre de restrictions graves placées sur l’utilisation d’un objet `structured_task_group` pour obtenir des performances :

- Un objet `structured_task_group` unique ne peut pas être utilisé par plusieurs threads. Toutes les opérations sur un objet `structured_task_group` doivent être effectuées par le thread qui a créé l’objet. Les deux exceptions à cette règle sont les fonctions membres `cancel` et `is_canceling`. L’objet ne peut pas figurer dans la liste de capture d’une expression lambda et être utilisé dans une tâche, à moins que la tâche utilise l’une des opérations d’annulation.

- Toutes les tâches planifiées pour un objet `structured_task_group` sont planifiées à l’aide d’objets `task_handle` qui doivent gérer explicitement la durée de vie de.

- Plusieurs groupes peuvent uniquement être utilisés dans un ordre absolument imbriqué. Si deux objets `structured_task_group` sont déclarés, le deuxième qui est déclaré (l’objet interne) doit être détruit avant toute méthode, à l’exception de `cancel` ou `is_canceling` est appelé sur le premier objet (externe). Cette condition est vraie dans le cas d’une simple déclaration de plusieurs objets `structured_task_group` dans les mêmes étendues ou dans des étendues imbriquées de manière fonctionnelle, ainsi que dans le cas d’une tâche qui a été mise en file d’attente dans la `structured_task_group` via les méthodes `run` ou `run_and_wait`.

- Contrairement à la classe `task_group` générale, tous les États de la classe `structured_task_group` sont finaux. Une fois que vous avez mis en file d’attente des tâches dans le groupe et ATTENDU qu’elles se terminent, vous ne pouvez pas réutiliser le même groupe.

Pour plus d’informations, consultez [parallélisme des tâches](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`structured_task_group`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrency

## <a name="cancel"></a>Annuler

Tente d’annuler la sous-arborescence du travail enracinée dans ce groupe de tâches. Chaque tâche planifiée sur le groupe de tâches est annulée de manière transitive, si possible.

```cpp
void cancel();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [annulation](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="is_canceling"></a>is_canceling

Informe l’appelant si le groupe de tâches est actuellement au milieu d’une annulation. Cela n’indique pas nécessairement que la méthode `cancel` a été appelée sur l’objet `structured_task_group` (bien que cela qualifie certainement cette méthode pour retourner la **valeur true**). Cela peut être le cas lorsque l’objet `structured_task_group` s’exécute en ligne et qu’un groupe de tâches plus haut dans l’arborescence de travail a été annulé. Dans les cas tels que ceux où le runtime peut déterminer à l’avance que l’annulation passera par cet objet `structured_task_group`, la **valeur true** sera également retournée.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Valeur de retour

Indique si l’objet `structured_task_group` est au milieu d’une annulation (ou s’il est garanti qu’il sera bientôt).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [annulation](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="run"></a>Utilisez

Planifie une tâche sur l’objet `structured_task_group`. L’appelant gère la durée de vie de l’objet `task_handle` passé dans le paramètre `_Task_handle`. La version qui accepte le paramètre `_Placement` entraîne l’exécution de la tâche à l’emplacement spécifié par ce paramètre.

```cpp
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
Type de l’objet de fonction qui sera appelé pour exécuter le corps du handle de tâche.

*_Task_handle*<br/>
Handle du travail en cours de planification. Notez que l’appelant est responsable de la durée de vie de cet objet. Le runtime continuera à attendre qu’il se poursuive jusqu’à ce que la méthode `wait` ou `run_and_wait` soit appelée sur cet objet `structured_task_group`.

*_Placement*<br/>
Référence à l’emplacement où la tâche représentée par le paramètre `_Task_handle` doit s’exécuter.

### <a name="remarks"></a>Notes

Le runtime crée une copie de la fonction de travail que vous transmettez à cette méthode. Les modifications d’État qui se produisent dans un objet de fonction que vous transmettez à cette méthode n’apparaîtront pas dans votre copie de cet objet de fonction.

Si le `structured_task_group` est détruit à la suite d’un déroulement de pile à partir d’une exception, vous n’avez pas besoin de garantir qu’un appel a été effectué à la méthode `wait` ou `run_and_wait`. Dans ce cas, le destructeur est correctement annulé et attend la fin de la tâche représentée par le paramètre `_Task_handle`.

Lève une exception [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) si le handle de tâche donné par le paramètre `_Task_handle` a déjà été planifié sur un objet de groupe de tâches par le biais de la méthode `run` et qu’il n’y a eu aucun appel intermédiaire à la méthode `wait` ou `run_and_wait` sur ce groupe de tâches.

## <a name="run_and_wait"></a>run_and_wait

Planifie l’exécution d’une tâche Inline sur le contexte appelant avec l’assistance de l’objet `structured_task_group` pour la prise en charge de l’annulation complète. Si un objet `task_handle` est passé en tant que paramètre à `run_and_wait`, l’appelant est responsable de la gestion de la durée de vie de l’objet `task_handle`. La fonction attend ensuite que tout le travail sur l’objet `structured_task_group` soit terminé ou a été annulé.

```cpp
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l’objet de fonction qui sera appelé pour exécuter la tâche.

*_Task_handle*<br/>
Handle vers la tâche qui est exécutée Inline sur le contexte d’appel. Notez que l’appelant est responsable de la durée de vie de cet objet. Le runtime continuera à attendre qu’il se poursuive jusqu’à la fin de l’exécution de la méthode `run_and_wait`.

*_Func*<br/>
Fonction qui sera appelée pour appeler le corps du travail. Il peut s’agir d’une expression lambda ou d’un autre objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature `void operator()()`.

### <a name="return-value"></a>Valeur de retour

Indique si l’attente a été satisfaite ou si le groupe de tâches a été annulé, en raison d’une opération d’annulation explicite ou d’une exception levée à partir de l’une de ses tâches. Pour plus d’informations, consultez [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Notes

Notez qu’une ou plusieurs des tâches planifiées pour cet objet `structured_task_group` peuvent s’exécuter Inline sur le contexte d’appel.

Si une ou plusieurs tâches planifiées pour cet objet `structured_task_group` lèvent une exception, le runtime sélectionne une telle exception de son choix et la propage en dehors de l’appel à la méthode `run_and_wait`.

Une fois que cette fonction a retourné une valeur, l’objet `structured_task_group` est considéré comme étant dans un état final et ne doit pas être utilisé. Notez que l’utilisation après le retour de la méthode `run_and_wait` entraînera un comportement indéfini.

Dans le chemin d’exécution non exceptionnel, vous avez l’autorisation d’appeler cette méthode ou la méthode `wait` avant l’exécution du destructeur du `structured_task_group`.

## <a name="ctor"></a>structured_task_group

Construit un nouvel objet `structured_task_group`.

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Paramètres

*_CancellationToken*<br/>
Jeton d’annulation à associer à ce groupe de tâches structuré. Le groupe de tâches structuré est annulé lorsque le jeton est annulé.

### <a name="remarks"></a>Notes

Le constructeur qui prend un jeton d’annulation crée une `structured_task_group` qui sera annulée lorsque la source associée au jeton est annulée. Le fait de fournir un jeton d’annulation explicite isole également ce groupe de tâches structuré de participer à une annulation implicite d’un groupe parent avec un jeton différent ou aucun jeton.

## <a name="dtor"></a>~ structured_task_group

Détruit un objet `structured_task_group`. Vous devez appeler la méthode `wait` ou `run_and_wait` sur l’objet avant l’exécution du destructeur, sauf si le destructeur s’exécute à la suite d’un déroulement de pile en raison d’une exception.

```cpp
~structured_task_group();
```

### <a name="remarks"></a>Notes

Si le destructeur s’exécute à la suite d’une exécution normale (par exemple, pas de déroulement de pile en raison d’une exception) et que ni les méthodes `wait`, ni `run_and_wait` n’ont été appelées, le destructeur peut lever une exception [missing_wait](missing-wait-class.md) .

## <a name="wait"></a>qu'

Attend que tout le travail sur le `structured_task_group` soit terminé ou qu’il soit annulé.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Valeur de retour

Indique si l’attente a été satisfaite ou si le groupe de tâches a été annulé, en raison d’une opération d’annulation explicite ou d’une exception levée à partir de l’une de ses tâches. Pour plus d’informations, consultez [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Notes

Notez qu’une ou plusieurs des tâches planifiées pour cet objet `structured_task_group` peuvent s’exécuter Inline sur le contexte d’appel.

Si une ou plusieurs tâches planifiées pour cet objet `structured_task_group` lèvent une exception, le runtime sélectionne une telle exception de son choix et la propage en dehors de l’appel à la méthode `wait`.

Une fois que cette fonction a retourné une valeur, l’objet `structured_task_group` est considéré comme étant dans un état final et ne doit pas être utilisé. Notez que l’utilisation après le retour de la méthode `wait` entraînera un comportement indéfini.

Dans le chemin d’exécution non exceptionnel, vous avez l’autorisation d’appeler cette méthode ou la méthode `run_and_wait` avant l’exécution du destructeur du `structured_task_group`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Classe task_group](task-group-class.md)<br/>
[task_handle, classe](task-handle-class.md)
