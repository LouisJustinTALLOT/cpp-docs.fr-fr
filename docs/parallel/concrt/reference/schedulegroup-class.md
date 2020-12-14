---
description: 'En savoir plus sur : ScheduleGroup, classe'
title: ScheduleGroup, classe
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: ca6678cd8d8c13c5d62b3d98b0a0bb1ab14e29c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188909"
---
# <a name="schedulegroup-class"></a>ScheduleGroup, classe

Représente une abstraction d'un groupe de planification. Les groupes de planification organisent un ensemble de travaux connexes qui ont l’avantage d’être planifiés de façon rapprochée soit dans le temps, en exécutant une autre tâche dans le même groupe avant de passer à un autre groupe, soit dans l’espace, en exécutant plusieurs éléments au sein du même groupe sur le même nœud NUMA ou socket physique.

## <a name="syntax"></a>Syntaxe

```cpp
class ScheduleGroup;
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[~ ScheduleGroup, destructeur](#dtor)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Id](#id)|Retourne un identificateur pour le groupe de planification qui est unique dans le planificateur auquel le groupe appartient.|
|[Référence](#reference)|Incrémente le nombre de références du groupe de planification.|
|[Version release](#release)|Décrémente le nombre de références de groupe du planificateur.|
|[ScheduleTask,](#scheduletask)|Planifie une tâche légère dans le groupe de planification.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ScheduleGroup`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="id"></a><a name="id"></a> Identifi

Retourne un identificateur pour le groupe de planification qui est unique dans le planificateur auquel le groupe appartient.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur du groupe de planification qui est unique dans le planificateur auquel le groupe appartient.

## <a name="operator-delete"></a><a name="operator_delete"></a> opérateur delete

Un `ScheduleGroup` objet est détruit en interne par le runtime lorsque toutes les références externes à celui-ci sont libérées. Elle ne peut pas être supprimée explicitement.

```cpp
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
const char *,
    int);
```

### <a name="parameters"></a>Paramètres

*_PObject*<br/>
Pointeur vers l’objet à supprimer.

## <a name="reference"></a><a name="reference"></a> Faire

Incrémente le nombre de références du groupe de planification.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de références récemment incrémentées.

### <a name="remarks"></a>Notes

Cette valeur est généralement utilisée pour gérer la durée de vie du groupe de planification pour la composition. Lorsque le nombre de références d’un groupe de planifications est égal à zéro, le groupe de planification est supprimé par le Runtime. Un groupe de planification créé à l’aide de la méthode [CurrentScheduler :: CreateScheduleGroup](currentscheduler-class.md#createschedulegroup) ou de la méthode [Scheduler :: CreateScheduleGroup](scheduler-class.md#createschedulegroup) démarre avec un décompte de références d’un.

## <a name="release"></a><a name="release"></a> 3/05

Décrémente le nombre de références de groupe du planificateur.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Le décompte de références qui vient d’être décrémenté.

### <a name="remarks"></a>Notes

Cette valeur est généralement utilisée pour gérer la durée de vie du groupe de planification pour la composition. Lorsque le nombre de références d’un groupe de planifications est égal à zéro, le groupe de planification est supprimé par le Runtime. Une fois que vous avez appelé la `Release` méthode le nombre de fois spécifié pour supprimer le décompte de références de création et toute autre référence placée à l’aide de la `Reference` méthode, vous ne pouvez plus utiliser le groupe de planification. Cela entraînera un comportement indéfini.

Un groupe de planification est associé à une instance de planificateur particulière. Vous devez vous assurer que toutes les références au groupe de planification sont libérées avant que toutes les références au planificateur ne soient libérées, car ce dernier peut entraîner la destruction du planificateur. Sinon, le comportement n’est pas défini.

## <a name="schedulegroup"></a><a name="dtor"></a> ~ ScheduleGroup

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a><a name="scheduletask"></a> ScheduleTask,

Planifie une tâche légère dans le groupe de planification.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>Paramètres

*_Proc*<br/>
Pointeur vers la fonction à exécuter pour exécuter le corps de la tâche légère.

*_Data*<br/>
Pointeur void vers les données qui seront passées en tant que paramètre au corps de la tâche.

### <a name="remarks"></a>Notes

L’appel de la `ScheduleTask` méthode place implicitement un décompte de références sur le groupe de planification qui est supprimé par le runtime à un moment approprié après l’exécution de la tâche.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[CurrentScheduler, classe](currentscheduler-class.md)<br/>
[Scheduler, classe](scheduler-class.md)<br/>
[Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
