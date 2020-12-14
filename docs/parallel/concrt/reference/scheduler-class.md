---
description: 'En savoir plus sur : classe Scheduler'
title: Scheduler, classe
ms.date: 11/04/2016
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
ms.openlocfilehash: 2a509017c84f7f6c845c153c8c187f5885839035
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188896"
---
# <a name="scheduler-class"></a>Scheduler, classe

Représente une abstraction pour un planificateur de runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
class Scheduler;
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[Scheduler](#ctor)|Un objet de la `Scheduler` classe peut uniquement être créé à l’aide de méthodes de fabrique, ou implicitement.|
|[~ Destructeur du planificateur](#dtor)|Un objet de la `Scheduler` classe est implicitement détruit lorsque toutes les références externes à celui-ci cessent d’exister.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Attacher](#attach)|Attache le planificateur au contexte d’appel. Une fois que cette méthode a retourné une valeur, le contexte d’appel est géré par le planificateur et le planificateur devient le planificateur actuel.|
|[Créer](#create)|Crée un planificateur dont le comportement est décrit par le `_Policy` paramètre, place une référence initiale sur le planificateur et retourne un pointeur vers celui-ci.|
|[CreateScheduleGroup,](#createschedulegroup)|Surchargé. Crée un nouveau groupe de planification dans le planificateur. La version qui accepte le paramètre `_Placement` entraîne l’exécution des tâches dans le groupe de planification nouvellement créé vers l’emplacement spécifié par ce paramètre.|
|[GetNumberOfVirtualProcessors,](#getnumberofvirtualprocessors)|Retourne le nombre actuel de processeurs virtuels pour le planificateur.|
|[GetPolicy](#getpolicy)|Retourne une copie de la stratégie avec laquelle le planificateur a été créé.|
|[Id](#id)|Retourne un identificateur unique pour le planificateur.|
|[Isavailablelocation,](#isavailablelocation)|Détermine si un emplacement donné est disponible sur le planificateur.|
|[Référence](#reference)|Incrémente le nombre de références du planificateur.|
|[RegisterShutdownEvent,](#registershutdownevent)|Fait en sorte que le descripteur d’événement Windows passé dans le `_Event` paramètre soit signalé lorsque le planificateur s’arrête et se détruit lui-même. Au moment où l’événement est signalé, tout le travail qui avait été planifié dans le planificateur est terminé. Plusieurs événements d’arrêt peuvent être inscrits via cette méthode.|
|[Version release](#release)|Décrémente le nombre de références du planificateur.|
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|Rétablit la valeur par défaut d’exécution de la stratégie du planificateur par défaut. La prochaine fois qu’un planificateur par défaut sera créé, il utilisera les paramètres de stratégie par défaut du Runtime.|
|[ScheduleTask,](#scheduletask)|Surchargé. Planifie une tâche légère dans le planificateur. La tâche légère est placée dans un groupe de planification déterminé par le Runtime. La version qui accepte le paramètre `_Placement` entraîne l’exécution de la tâche vers l’emplacement spécifié.|
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|Permet d’utiliser une stratégie définie par l’utilisateur pour créer le planificateur par défaut. Cette méthode peut être appelée uniquement lorsqu’aucun planificateur par défaut n’existe dans le processus. Une fois qu’une stratégie par défaut a été définie, elle reste en vigueur jusqu’au prochain appel valide à la `SetDefaultSchedulerPolicy` méthode ou à la méthode [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) .|

## <a name="remarks"></a>Notes

Le planificateur runtime d’accès concurrentiel utilise des contextes d’exécution, qui mappent aux contextes d’exécution du système d’exploitation, tels qu’un thread, pour exécuter le travail mis en file d’attente par votre application. À tout moment, le niveau de concurrence d’un planificateur est égal au nombre de processeurs virtuels qui lui est accordé par le Gestionnaire des ressources. Un processeur virtuel est une abstraction d’une ressource de traitement qui est mappée à un thread matériel sur le système sous-jacent. Un seul contexte de planificateur peut s’exécuter sur un processeur virtuel à un moment donné.

Le runtime d’accès concurrentiel crée un planificateur par défaut par processus pour exécuter le travail parallèle. En outre, vous pouvez créer vos propres instances de planificateur et les manipuler à l’aide de cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Scheduler`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="attach"></a><a name="attach"></a> Attacher

Attache le planificateur au contexte d’appel. Une fois que cette méthode a retourné une valeur, le contexte d’appel est géré par le planificateur et le planificateur devient le planificateur actuel.

```cpp
virtual void Attach() = 0;
```

### <a name="remarks"></a>Notes

L’attachement d’un planificateur place implicitement une référence sur le planificateur.

À un moment donné à l’avenir, vous devez appeler la méthode [CurrentScheduler ::D Etach](currentscheduler-class.md#detach) pour permettre au planificateur de s’arrêter.

Si cette méthode est appelée à partir d’un contexte qui est déjà attaché à un autre planificateur, le planificateur existant est mémorisé comme planificateur précédent et le planificateur nouvellement créé devient le planificateur actuel. Quand vous appelez la `CurrentScheduler::Detach` méthode à un point ultérieur, le planificateur précédent est restauré en tant que planificateur actuel.

Cette méthode lève une exception [improper_scheduler_attach](improper-scheduler-attach-class.md) si ce planificateur est le planificateur actuel du contexte d’appel.

## <a name="create"></a><a name="create"></a> Créer

Crée un planificateur dont le comportement est décrit par le `_Policy` paramètre, place une référence initiale sur le planificateur et retourne un pointeur vers celui-ci.

```cpp
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Paramètres

*_Policy*<br/>
Stratégie du planificateur qui décrit le comportement du planificateur nouvellement créé.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un planificateur nouvellement créé. `Scheduler`Un décompte de références initial est placé sur cet objet.

### <a name="remarks"></a>Notes

Après avoir créé un planificateur à l’aide de la `Create` méthode, vous devez appeler la `Release` méthode à un moment donné dans le futur afin de supprimer le nombre de références initiales et autoriser le planificateur à s’arrêter.

Un planificateur créé avec cette méthode n’est pas attaché au contexte d’appel. Il peut être attaché à un contexte à l’aide de la méthode [Attach](#attach) .

Cette méthode peut lever diverses exceptions, notamment [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) et [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a><a name="createschedulegroup"></a> CreateScheduleGroup,

Crée un nouveau groupe de planification dans le planificateur. La version qui accepte le paramètre `_Placement` entraîne l’exécution des tâches dans le groupe de planification nouvellement créé vers l’emplacement spécifié par ce paramètre.

```cpp
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>Paramètres

*_Placement*<br/>
Référence à un emplacement où les tâches au sein du groupe de planification sont biaisées pour s’exécuter à.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le groupe de planification nouvellement créé. `ScheduleGroup`Un décompte de références initial est placé sur cet objet.

### <a name="remarks"></a>Notes

Vous devez appeler la méthode [Release](schedulegroup-class.md#release) sur un groupe de planification lorsque vous avez terminé de planifier le travail. Le planificateur détruira le groupe de planification lorsque toutes les tâches mises en file d’attente seront terminées.

Notez que si vous avez créé ce planificateur de manière explicite, vous devez libérer toutes les références aux groupes de planification qu’il contient avant de libérer vos références sur le planificateur.

## <a name="getnumberofvirtualprocessors"></a><a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors,

Retourne le nombre actuel de processeurs virtuels pour le planificateur.

```cpp
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre actuel de processeurs virtuels pour le planificateur.

## <a name="getpolicy"></a><a name="getpolicy"></a> GetPolicy

Retourne une copie de la stratégie avec laquelle le planificateur a été créé.

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Copie de la stratégie avec laquelle le planificateur a été créé.

## <a name="id"></a><a name="id"></a> Identifi

Retourne un identificateur unique pour le planificateur.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur unique pour le planificateur.

## <a name="isavailablelocation"></a><a name="isavailablelocation"></a> Isavailablelocation,

Détermine si un emplacement donné est disponible sur le planificateur.

```cpp
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>Paramètres

*_Placement*<br/>
Référence à l’emplacement à propos duquel interroger le planificateur.

### <a name="return-value"></a>Valeur renvoyée

Indique si l’emplacement spécifié par l' `_Placement` argument est disponible ou non sur le planificateur.

### <a name="remarks"></a>Notes

Notez que la valeur de retour est un échantillonnage instantané indiquant si l’emplacement donné est disponible. En présence de plusieurs planificateurs, la gestion dynamique des ressources peut ajouter ou retirer des ressources des planificateurs à tout moment. Si cela se produit, l’emplacement donné peut modifier la disponibilité.

## <a name="reference"></a><a name="reference"></a> Faire

Incrémente le nombre de références du planificateur.

```cpp
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de références récemment incrémentées.

### <a name="remarks"></a>Notes

Il est généralement utilisé pour gérer la durée de vie du planificateur pour la composition. Lorsque le nombre de références d’un planificateur est égal à zéro, le planificateur s’arrête et se détruit une fois que tout le travail sur le planificateur est terminé.

La méthode lève une exception [improper_scheduler_reference](improper-scheduler-reference-class.md) si le décompte de références avant d’appeler la `Reference` méthode a la valeur zéro et si l’appel est effectué à partir d’un contexte qui n’appartient pas au planificateur.

## <a name="registershutdownevent"></a><a name="registershutdownevent"></a> RegisterShutdownEvent,

Fait en sorte que le descripteur d’événement Windows passé dans le `_Event` paramètre soit signalé lorsque le planificateur s’arrête et se détruit lui-même. Au moment où l’événement est signalé, tout le travail qui avait été planifié dans le planificateur est terminé. Plusieurs événements d’arrêt peuvent être inscrits via cette méthode.

```cpp
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>Paramètres

*_Event*<br/>
Handle d’un objet d’événement Windows qui sera signalé par le runtime lorsque le planificateur s’arrête et se détruit lui-même.

## <a name="release"></a><a name="release"></a> 3/05

Décrémente le nombre de références du planificateur.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Le décompte de références qui vient d’être décrémenté.

### <a name="remarks"></a>Notes

Il est généralement utilisé pour gérer la durée de vie du planificateur pour la composition. Lorsque le nombre de références d’un planificateur est égal à zéro, le planificateur s’arrête et se détruit une fois que tout le travail sur le planificateur est terminé.

## <a name="resetdefaultschedulerpolicy"></a><a name="resetdefaultschedulerpolicy"></a> ResetDefaultSchedulerPolicy

Rétablit la valeur par défaut d’exécution de la stratégie du planificateur par défaut. La prochaine fois qu’un planificateur par défaut sera créé, il utilisera les paramètres de stratégie par défaut du Runtime.

```cpp
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>Notes

Cette méthode peut être appelée alors qu’un planificateur par défaut existe dans le processus. Elle n’affecte pas la stratégie du planificateur par défaut existant. Toutefois, si le planificateur par défaut devait être arrêté et qu’une nouvelle valeur par défaut devait être créée ultérieurement, le nouveau planificateur utilisera les paramètres de stratégie par défaut du Runtime.

## <a name="scheduler"></a><a name="ctor"></a> Planificateur

Un objet de la `Scheduler` classe peut uniquement être créé à l’aide de méthodes de fabrique, ou implicitement.

```cpp
Scheduler();
```

### <a name="remarks"></a>Notes

Le planificateur par défaut du processus est créé implicitement lorsque vous utilisez la plupart des fonctions d’exécution qui requièrent qu’un planificateur soit attaché au contexte d’appel. Les méthodes dans la `CurrentScheduler` classe et les fonctionnalités de la bibliothèque PPL et des couches agents exécutent généralement une pièce jointe implicite.

Vous pouvez également créer un planificateur de manière explicite à l’aide de la `CurrentScheduler::Create` méthode ou de la `Scheduler::Create` méthode.

## <a name="scheduler"></a><a name="dtor"></a> ~ Scheduler

Un objet de la `Scheduler` classe est implicitement détruit lorsque toutes les références externes à celui-ci cessent d’exister.

```cpp
virtual ~Scheduler();
```

## <a name="scheduletask"></a><a name="scheduletask"></a> ScheduleTask,

Planifie une tâche légère dans le planificateur. La tâche légère est placée dans un groupe de planification déterminé par le Runtime. La version qui accepte le paramètre `_Placement` entraîne l’exécution de la tâche vers l’emplacement spécifié.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```

### <a name="parameters"></a>Paramètres

*_Proc*<br/>
Pointeur vers la fonction à exécuter pour exécuter le corps de la tâche légère.

*_Data*<br/>
Pointeur void vers les données qui seront passées en tant que paramètre au corps de la tâche.

*_Placement*<br/>
Référence à un emplacement où la tâche légère sera biaisée pour s’exécuter à.

## <a name="setdefaultschedulerpolicy"></a><a name="setdefaultschedulerpolicy"></a> SetDefaultSchedulerPolicy

Permet d’utiliser une stratégie définie par l’utilisateur pour créer le planificateur par défaut. Cette méthode peut être appelée uniquement lorsqu’aucun planificateur par défaut n’existe dans le processus. Une fois qu’une stratégie par défaut a été définie, elle reste en vigueur jusqu’au prochain appel valide à la `SetDefaultSchedulerPolicy` méthode ou à la méthode [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) .

```cpp
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Paramètres

*_Policy*<br/>
Stratégie à définir en tant que stratégie du planificateur par défaut.

### <a name="remarks"></a>Notes

Si la `SetDefaultSchedulerPolicy` méthode est appelée alors qu’un planificateur par défaut existe déjà dans le processus, le runtime lève une exception [default_scheduler_exists](default-scheduler-exists-class.md) .

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)<br/>
[PolicyElementKey,](concurrency-namespace-enums.md)<br/>
[Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
