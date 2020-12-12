---
description: 'En savoir plus sur : classe CurrentScheduler'
title: CurrentScheduler, classe
ms.date: 11/04/2016
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: d2456513dba05f8e38035eb96709e540cb781629
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115233"
---
# <a name="currentscheduler-class"></a>CurrentScheduler, classe

Représente une abstraction pour le planificateur actuel associé au contexte d'appel.

## <a name="syntax"></a>Syntaxe

```cpp
class CurrentScheduler;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Créer](#create)|Crée un planificateur dont le comportement est décrit par le `_Policy` paramètre et l’attache au contexte d’appel. Le planificateur qui vient d’être créé devient le planificateur actuel du contexte d’appel.|
|[CreateScheduleGroup,](#createschedulegroup)|Surchargé. Crée un nouveau groupe de planification dans le planificateur associé au contexte d’appel. La version qui accepte le paramètre `_Placement` entraîne l’exécution des tâches dans le groupe de planification nouvellement créé vers l’emplacement spécifié par ce paramètre.|
|[Détacher](#detach)|Détache le planificateur actuel du contexte appelant et restaure le planificateur précédemment attaché en tant que planificateur actuel, le cas échéant. Après le retour de cette méthode, le contexte d’appel est alors géré par le planificateur précédemment attaché au contexte à l’aide de `CurrentScheduler::Create` la `Scheduler::Attach` méthode ou.|
|[Get](#get)|Retourne un pointeur vers le planificateur associé au contexte d’appel, également appelé planificateur actuel.|
|[GetNumberOfVirtualProcessors,](#getnumberofvirtualprocessors)|Retourne le nombre actuel de processeurs virtuels pour le planificateur associé au contexte d’appel.|
|[GetPolicy](#getpolicy)|Retourne une copie de la stratégie avec laquelle le planificateur actuel a été créé.|
|[Id](#id)|Retourne un identificateur unique pour le planificateur actuel.|
|[Isavailablelocation,](#isavailablelocation)|Détermine si un emplacement donné est disponible sur le planificateur actuel.|
|[RegisterShutdownEvent,](#registershutdownevent)|Fait en sorte que le handle d’événement Windows passé dans le `_ShutdownEvent` paramètre soit signalé lorsque le planificateur associé au contexte actuel s’arrête et se détruit lui-même. Au moment où l’événement est signalé, tout le travail qui avait été planifié dans le planificateur est terminé. Plusieurs événements d’arrêt peuvent être inscrits via cette méthode.|
|[ScheduleTask,](#scheduletask)|Surchargé. Planifie une tâche légère dans le planificateur associé au contexte d’appel. La tâche légère est placée dans un groupe de planification déterminé par le Runtime. La version qui accepte le paramètre `_Placement` entraîne l’exécution de la tâche vers l’emplacement spécifié.|

## <a name="remarks"></a>Notes

S’il n’existe aucun planificateur (voir [Scheduler](scheduler-class.md)) associé au contexte d’appel, de nombreuses méthodes de la `CurrentScheduler` classe génèrent une pièce jointe du planificateur par défaut du processus. Cela peut également impliquer que le planificateur par défaut du processus est créé pendant un tel appel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CurrentScheduler`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="create"></a><a name="create"></a> Créer

Crée un planificateur dont le comportement est décrit par le `_Policy` paramètre et l’attache au contexte d’appel. Le planificateur qui vient d’être créé devient le planificateur actuel du contexte d’appel.

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Paramètres

*_Policy*<br/>
Stratégie du planificateur qui décrit le comportement du planificateur nouvellement créé.

### <a name="remarks"></a>Notes

La pièce jointe du planificateur au contexte d’appel place implicitement un décompte de références sur le planificateur.

Après la création d’un planificateur à l’aide de la `Create` méthode, vous devez appeler la méthode [CurrentScheduler ::D Etach](#detach) à un moment donné dans le futur afin d’autoriser le planificateur à s’arrêter.

Si cette méthode est appelée à partir d’un contexte qui est déjà attaché à un autre planificateur, le planificateur existant est mémorisé comme planificateur précédent et le planificateur nouvellement créé devient le planificateur actuel. Quand vous appelez la `CurrentScheduler::Detach` méthode à un point ultérieur, le planificateur précédent est restauré en tant que planificateur actuel.

Cette méthode peut lever diverses exceptions, notamment [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) et [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a><a name="createschedulegroup"></a> CreateScheduleGroup,

Crée un nouveau groupe de planification dans le planificateur associé au contexte d’appel. La version qui accepte le paramètre `_Placement` entraîne l’exécution des tâches dans le groupe de planification nouvellement créé vers l’emplacement spécifié par ce paramètre.

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>Paramètres

*_Placement*<br/>
Une référence à un emplacement où les tâches dans le groupe de planification seront biaisées pour s’exécuter à.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le groupe de planification nouvellement créé. `ScheduleGroup`Un décompte de références initial est placé sur cet objet.

### <a name="remarks"></a>Notes

Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.

Vous devez appeler la méthode [Release](schedulegroup-class.md#release) sur un groupe de planification lorsque vous avez terminé de planifier le travail. Le planificateur détruira le groupe de planification lorsque toutes les tâches mises en file d’attente seront terminées.

Notez que si vous avez créé ce planificateur de manière explicite, vous devez libérer toutes les références aux groupes de planification qu’il contient, avant de libérer votre référence sur le planificateur, en détachant le contexte actuel de celui-ci.

## <a name="detach"></a><a name="detach"></a> Dissocié

Détache le planificateur actuel du contexte appelant et restaure le planificateur précédemment attaché en tant que planificateur actuel, le cas échéant. Après le retour de cette méthode, le contexte d’appel est alors géré par le planificateur précédemment attaché au contexte à l’aide de `CurrentScheduler::Create` la `Scheduler::Attach` méthode ou.

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>Notes

La `Detach` méthode supprime implicitement un décompte de références du planificateur.

Si aucun planificateur n’est attaché au contexte d’appel, l’appel de cette méthode entraîne la levée d’une exception [scheduler_not_attached](scheduler-not-attached-class.md) .

L’appel de cette méthode à partir d’un contexte interne et géré par un planificateur, ou d’un contexte attaché à l’aide d’une méthode autre que les méthodes [Scheduler :: Attach](scheduler-class.md#attach) ou [CurrentScheduler :: Create](#create) , entraîne la levée d’une exception [improper_scheduler_detach](improper-scheduler-detach-class.md) .

## <a name="get"></a><a name="get"></a> Télécharger

Retourne un pointeur vers le planificateur associé au contexte d’appel, également appelé planificateur actuel.

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le planificateur associé au contexte d’appel (planificateur actuel).

### <a name="remarks"></a>Notes

Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel. Aucune référence supplémentaire n’est placée sur l' `Scheduler` objet retourné par cette méthode.

## <a name="getnumberofvirtualprocessors"></a><a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors,

Retourne le nombre actuel de processeurs virtuels pour le planificateur associé au contexte d’appel.

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>Valeur renvoyée

Si un planificateur est associé au contexte d’appel, le nombre actuel de processeurs virtuels pour ce planificateur ; Sinon, la valeur `-1` .

### <a name="remarks"></a>Notes

Cette méthode n’entraîne pas de pièce jointe du planificateur si le contexte d’appel n’est pas déjà associé à un planificateur.

La valeur de retour de cette méthode est un échantillonnage instantané du nombre de processeurs virtuels pour le planificateur associé au contexte d’appel. Cette valeur peut être obsolète au moment où elle est retournée.

## <a name="getpolicy"></a><a name="getpolicy"></a> GetPolicy

Retourne une copie de la stratégie avec laquelle le planificateur actuel a été créé.

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>Valeur renvoyée

Copie de la stratégie avec laquelle le planificateur actuel a été créé.

### <a name="remarks"></a>Notes

Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.

## <a name="id"></a><a name="id"></a> Identifi

Retourne un identificateur unique pour le planificateur actuel.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Valeur renvoyée

Si un planificateur est associé au contexte d’appel, il s’agit d’un identificateur unique pour ce planificateur ; Sinon, la valeur `-1` .

### <a name="remarks"></a>Notes

Cette méthode n’entraîne pas de pièce jointe du planificateur si le contexte d’appel n’est pas déjà associé à un planificateur.

## <a name="isavailablelocation"></a><a name="isavailablelocation"></a> Isavailablelocation,

Détermine si un emplacement donné est disponible sur le planificateur actuel.

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>Paramètres

*_Placement*<br/>
Référence à l’emplacement à partir duquel interroger le planificateur actuel.

### <a name="return-value"></a>Valeur renvoyée

Indique si l’emplacement spécifié par l' `_Placement` argument est disponible ou non sur le planificateur actuel.

### <a name="remarks"></a>Notes

Cette méthode n’entraîne pas de pièce jointe du planificateur si le contexte d’appel n’est pas déjà associé à un planificateur.

Notez que la valeur de retour est un échantillonnage instantané indiquant si l’emplacement donné est disponible. En présence de plusieurs planificateurs, la gestion dynamique des ressources peut ajouter ou retirer des ressources des planificateurs à tout moment. Si cela se produit, l’emplacement donné peut modifier la disponibilité.

## <a name="registershutdownevent"></a><a name="registershutdownevent"></a> RegisterShutdownEvent,

Fait en sorte que le handle d’événement Windows passé dans le `_ShutdownEvent` paramètre soit signalé lorsque le planificateur associé au contexte actuel s’arrête et se détruit lui-même. Au moment où l’événement est signalé, tout le travail qui avait été planifié dans le planificateur est terminé. Plusieurs événements d’arrêt peuvent être inscrits via cette méthode.

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>Paramètres

*_ShutdownEvent*<br/>
Handle d’un objet d’événement Windows qui sera signalé par le runtime lorsque le planificateur associé au contexte actuel s’arrête et se détruit lui-même.

### <a name="remarks"></a>Notes

Si aucun planificateur n’est attaché au contexte d’appel, l’appel de cette méthode entraîne la levée d’une exception [scheduler_not_attached](scheduler-not-attached-class.md) .

## <a name="scheduletask"></a><a name="scheduletask"></a> ScheduleTask,

Planifie une tâche légère dans le planificateur associé au contexte d’appel. La tâche légère est placée dans un groupe de planification déterminé par le Runtime. La version qui accepte le paramètre `_Placement` entraîne l’exécution de la tâche vers l’emplacement spécifié.

```cpp
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>Paramètres

*_Proc*<br/>
Pointeur vers la fonction à exécuter pour exécuter le corps de la tâche légère.

*_Data*<br/>
Pointeur void vers les données qui seront passées en tant que paramètre au corps de la tâche.

*_Placement*<br/>
Référence à un emplacement où la tâche légère sera biaisée pour s’exécuter à.

### <a name="remarks"></a>Notes

Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)<br/>
[PolicyElementKey,](concurrency-namespace-enums.md)<br/>
[Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
