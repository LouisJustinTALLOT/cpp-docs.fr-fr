---
title: task_group, classe
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 60c147f38ddc3936f47aea0cfd1ab1548b382441
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142565"
---
# <a name="task_group-class"></a>task_group, classe

La classe `task_group` représente une collection de travail parallèle qui peut être attendue ou annulée.

## <a name="syntax"></a>Syntaxe

```cpp
class task_group;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[task_group](#ctor)|Surchargé. Construit un nouvel objet `task_group`.|
|[Destructeur ~ task_group](#dtor)|Détruit un objet `task_group`. Vous devez appeler la méthode `wait` ou `run_and_wait` sur l’objet avant l’exécution du destructeur, à moins que le destructeur s’exécute en tant que résultat du déroulement de la pile en raison d’une exception.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[cancel](#cancel)|Tente d’annuler la sous-arborescence du travail enracinée dans ce groupe de tâches. Chaque tâche planifiée sur le groupe de tâches est annulée de manière transitive, si possible.|
|[is_canceling](#is_canceling)|Informe l’appelant si le groupe de tâches est actuellement au milieu d’une annulation. Cela n’indique pas nécessairement que la méthode `cancel` a été appelée sur l’objet `task_group` (bien que cela qualifie certainement cette méthode pour retourner `true`). Cela peut être le cas lorsque l’objet `task_group` s’exécute en ligne et qu’un groupe de tâches plus haut dans l’arborescence de travail a été annulé. Dans les cas tels que ceux où le runtime peut déterminer à l’avance que l’annulation passera par cet objet `task_group`, `true` sera également retourné.|
|[run](#run)|Surchargé. Planifie une tâche sur l’objet `task_group`. Si un objet `task_handle` est passé en tant que paramètre à `run`, l’appelant est responsable de la gestion de la durée de vie de l’objet `task_handle`. La version de la méthode qui prend une référence à un objet de fonction en tant que paramètre implique l’allocation du tas dans le runtime, qui peut être exécutée moins bien que l’utilisation de la version qui prend une référence à un objet `task_handle`. La version qui prend le paramètre `_Placement` fait passer la tâche à l’exécution à l’emplacement spécifié par ce paramètre.|
|[run_and_wait](#run_and_wait)|Surchargé. Planifie l’exécution d’une tâche Inline sur le contexte appelant avec l’assistance de l’objet `task_group` pour la prise en charge de l’annulation complète. La fonction attend ensuite que tout le travail sur l’objet `task_group` soit terminé ou a été annulé. Si un objet `task_handle` est passé en tant que paramètre à `run_and_wait`, l’appelant est responsable de la gestion de la durée de vie de l’objet `task_handle`.|
|[qu'](#wait)|Attend que tout le travail sur l’objet `task_group` soit terminé ou a été annulé.|

## <a name="remarks"></a>Notes

Contrairement à la classe `structured_task_group` très restreinte, la classe `task_group` est une construction beaucoup plus générale. Elle n’a aucune des restrictions décrites par [structured_task_group](structured-task-group-class.md). les objets `task_group` peuvent être utilisés en toute sécurité sur les threads et utilisés de manière libre. L’inconvénient de la construction `task_group` est qu’elle peut ne pas fonctionner aussi bien que la construction `structured_task_group` pour les tâches qui effectuent de petites quantités de travail.

Pour plus d’informations, consultez [parallélisme des tâches](../task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`task_group`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrency

## <a name="cancel"></a>Annuler

Tente d’annuler la sous-arborescence du travail enracinée dans ce groupe de tâches. Chaque tâche planifiée sur le groupe de tâches est annulée de manière transitive, si possible.

```cpp
void cancel();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [annulation](../cancellation-in-the-ppl.md).

## <a name="is_canceling"></a>is_canceling

Informe l’appelant si le groupe de tâches est actuellement au milieu d’une annulation. Cela n’indique pas nécessairement que la méthode `cancel` a été appelée sur l’objet `task_group` (bien que cela qualifie certainement cette méthode pour retourner `true`). Cela peut être le cas lorsque l’objet `task_group` s’exécute en ligne et qu’un groupe de tâches plus haut dans l’arborescence de travail a été annulé. Dans les cas tels que ceux où le runtime peut déterminer à l’avance que l’annulation passera par cet objet `task_group`, `true` sera également retourné.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Valeur de retour

Indique si l’objet `task_group` est au milieu d’une annulation (ou s’il est garanti qu’il sera bientôt).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [annulation](../cancellation-in-the-ppl.md).

## <a name="run"></a>Utilisez

Planifie une tâche sur l’objet `task_group`. Si un objet `task_handle` est passé en tant que paramètre à `run`, l’appelant est responsable de la gestion de la durée de vie de l’objet `task_handle`. La version de la méthode qui prend une référence à un objet de fonction en tant que paramètre implique l’allocation du tas dans le runtime, qui peut être exécutée moins bien que l’utilisation de la version qui prend une référence à un objet `task_handle`. La version qui prend le paramètre `_Placement` fait passer la tâche à l’exécution à l’emplacement spécifié par ce paramètre.

```cpp
template<
   typename _Function
>
void run(
   const _Function& _Func
);

template<
   typename _Function
>
void run(
   const _Function& _Func,
   location& _Placement
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle,
   location& _Placement
);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l’objet de fonction qui sera appelé pour exécuter le corps du handle de tâche.

*_Func*<br/>
Fonction qui sera appelée pour appeler le corps de la tâche. Il peut s’agir d’une expression lambda ou d’un autre objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature `void operator()()`.

*_Placement*<br/>
Référence à l’emplacement où la tâche représentée par le paramètre `_Func` doit s’exécuter.

*_Task_handle*<br/>
Handle du travail en cours de planification. Notez que l’appelant est responsable de la durée de vie de cet objet. Le runtime continuera à attendre qu’il se poursuive jusqu’à ce que la méthode `wait` ou `run_and_wait` soit appelée sur cet objet `task_group`.

### <a name="remarks"></a>Notes

Le runtime planifie la fonction de travail fournie à exécuter ultérieurement, qui peut être après le retour de la fonction appelante. Cette méthode utilise un objet [task_handle](task-handle-class.md) pour contenir une copie de la fonction de travail fournie. Par conséquent, les modifications d’État qui se produisent dans un objet de fonction que vous transmettez à cette méthode n’apparaîtront pas dans votre copie de cet objet de fonction. En outre, assurez-vous que la durée de vie de tous les objets que vous passez par pointeur ou par référence à la fonction de travail reste valide jusqu’au retour de la fonction de travail.

Si le `task_group` est détruit à la suite d’un déroulement de pile à partir d’une exception, vous n’avez pas besoin de garantir qu’un appel a été effectué à la méthode `wait` ou `run_and_wait`. Dans ce cas, le destructeur est correctement annulé et attend la fin de la tâche représentée par le paramètre `_Task_handle`.

La méthode lève une exception [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) si le handle de tâche donné par le paramètre `_Task_handle` a déjà été planifié sur un objet de groupe de tâches par le biais de la méthode `run` et qu’il n’y a eu aucun appel intermédiaire à la méthode `wait` ou `run_and_wait` sur ce groupe de tâches.

## <a name="run_and_wait"></a>run_and_wait

Planifie l’exécution d’une tâche Inline sur le contexte appelant avec l’assistance de l’objet `task_group` pour la prise en charge de l’annulation complète. La fonction attend ensuite que tout le travail sur l’objet `task_group` soit terminé ou a été annulé. Si un objet `task_handle` est passé en tant que paramètre à `run_and_wait`, l’appelant est responsable de la gestion de la durée de vie de l’objet `task_handle`.

```cpp
template<
   class _Function
>
task_group_status run_and_wait(
   task_handle<_Function>& _Task_handle
);

template<
   class _Function
>
task_group_status run_and_wait(
   const _Function& _Func
);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l’objet de fonction qui sera appelé pour exécuter le corps de la tâche.

*_Task_handle*<br/>
Handle vers la tâche qui est exécutée Inline sur le contexte d’appel. Notez que l’appelant est responsable de la durée de vie de cet objet. Le runtime continuera à attendre qu’il se poursuive jusqu’à la fin de l’exécution de la méthode `run_and_wait`.

*_Func*<br/>
Fonction qui sera appelée pour appeler le corps du travail. Il peut s’agir d’une expression lambda ou d’un autre objet qui prend en charge une version de l’opérateur d’appel de fonction avec la signature `void operator()()`.

### <a name="return-value"></a>Valeur de retour

Indique si l’attente a été satisfaite ou si le groupe de tâches a été annulé, en raison d’une opération d’annulation explicite ou d’une exception levée à partir de l’une de ses tâches. Pour plus d’informations, consultez [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Notes

Notez qu’une ou plusieurs des tâches planifiées pour cet objet `task_group` peuvent s’exécuter Inline sur le contexte d’appel.

Si une ou plusieurs tâches planifiées pour cet objet `task_group` lèvent une exception, le runtime sélectionne une telle exception de son choix et la propage en dehors de l’appel à la méthode `run_and_wait`.

Lors du retour de la méthode `run_and_wait` sur un objet `task_group`, le runtime réinitialise l’objet à un état propre où il peut être réutilisé. Cela comprend le cas où l’objet `task_group` a été annulé.

Dans le chemin d’exécution non exceptionnel, vous avez l’autorisation d’appeler cette méthode ou la méthode `wait` avant l’exécution du destructeur du `task_group`.

## <a name="ctor"></a>task_group

Construit un nouvel objet `task_group`.

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>Paramètres

*_CancellationToken*<br/>
Jeton d’annulation à associer à ce groupe de tâches. Le groupe de tâches est annulé lorsque le jeton est annulé.

### <a name="remarks"></a>Notes

Le constructeur qui prend un jeton d’annulation crée une `task_group` qui sera annulée lorsque la source associée au jeton est annulée. Le fait de fournir un jeton d’annulation explicite isole également ce groupe de tâches de participer à une annulation implicite d’un groupe parent avec un jeton différent ou aucun jeton.

## <a name="dtor"></a>~ task_group

Détruit un objet `task_group`. Vous devez appeler la méthode `wait` ou `run_and_wait` sur l’objet avant l’exécution du destructeur, à moins que le destructeur s’exécute en tant que résultat du déroulement de la pile en raison d’une exception.

```cpp
~task_group();
```

### <a name="remarks"></a>Notes

Si le destructeur s’exécute à la suite d’une exécution normale (par exemple, pas de déroulement de pile en raison d’une exception) et que ni les méthodes `wait`, ni `run_and_wait` n’ont été appelées, le destructeur peut lever une exception [missing_wait](missing-wait-class.md) .

## <a name="wait"></a>qu'

Attend que tout le travail sur l’objet `task_group` soit terminé ou a été annulé.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Valeur de retour

Indique si l’attente a été satisfaite ou si le groupe de tâches a été annulé, en raison d’une opération d’annulation explicite ou d’une exception levée à partir de l’une de ses tâches. Pour plus d’informations, consultez [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Notes

Notez qu’une ou plusieurs des tâches planifiées pour cet objet `task_group` peuvent s’exécuter Inline sur le contexte d’appel.

Si une ou plusieurs tâches planifiées pour cet objet `task_group` lèvent une exception, le runtime sélectionne une telle exception de son choix et la propage en dehors de l’appel à la méthode `wait`.

L’appel de `wait` sur un objet `task_group` le réinitialise à un état propre où il peut être réutilisé. Cela comprend le cas où l’objet `task_group` a été annulé.

Dans le chemin d’exécution non exceptionnel, vous avez l’autorisation d’appeler cette méthode ou la méthode `run_and_wait` avant l’exécution du destructeur du `task_group`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[structured_task_group, classe](structured-task-group-class.md)<br/>
[task_handle, classe](task-handle-class.md)
