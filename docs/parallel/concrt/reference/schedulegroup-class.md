---
title: ScheduleGroup, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
dev_langs:
- C++
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5df2ad30fca410a71bc6333e34948bc938ca38d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039986"
---
# <a name="schedulegroup-class"></a>ScheduleGroup, classe
Représente une abstraction d'un groupe de planification. Les groupes de planification organisent un ensemble de travaux connexes qui ont l’avantage d’être planifiés de façon rapprochée soit dans le temps, en exécutant une autre tâche dans le même groupe avant de passer à un autre groupe, soit dans l’espace, en exécutant plusieurs éléments au sein du même groupe sur le même nœud NUMA ou socket physique.  
  
## <a name="syntax"></a>Syntaxe  
  
```
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
|[Référence](#reference)|Incrémente le décompte de références de groupe de planification.|  
|[Version release](#release)|Décrémente le planificateur groupe nombre de références.|  
|[ScheduleTask](#scheduletask)|Planifie une tâche légère dans le groupe de planification.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ScheduleGroup`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="id"></a> ID 

 Retourne un identificateur pour le groupe de planification qui est unique dans le planificateur auquel le groupe appartient.  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un identificateur pour le groupe de planification qui est unique dans le planificateur auquel le groupe appartient.  
  
##  <a name="operator_delete"></a> opérateur delete 

 Un `ScheduleGroup` détruit en interne par le runtime lorsque toutes les références externes à celle-ci sont libérés. Il ne peut pas être supprimé explicitement.  
  
```
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
  
##  <a name="reference"></a> Référence 

 Incrémente le décompte de références de groupe de planification.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décompte de références qui vient d’être incrémentée.  
  
### <a name="remarks"></a>Notes  
 Cela est généralement utilisé pour gérer la durée de vie du groupe de planification pour la composition. Lorsque le décompte de références d’un groupe de planification atteint zéro, le groupe de planification est supprimé par le runtime. Un groupe de planification créé à l’aide du [CurrentScheduler::CreateScheduleGroup](currentscheduler-class.md#createschedulegroup) (méthode), ou le [Scheduler::CreateScheduleGroup](scheduler-class.md#createschedulegroup) méthode commence par un décompte de références d’un.  
  
##  <a name="release"></a> Mise en production 

 Décrémente le planificateur groupe nombre de références.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décompte de références qui vient d’être décrémentée.  
  
### <a name="remarks"></a>Notes  
 Cela est généralement utilisé pour gérer la durée de vie du groupe de planification pour la composition. Lorsque le décompte de références d’un groupe de planification atteint zéro, le groupe de planification est supprimé par le runtime. Après avoir appelé la `Release` (méthode) le nombre de fois pour supprimer la création de référence nombre ainsi que les références supplémentaires placés à l’aide de la `Reference` (méthode), vous ne pourrez pas utiliser le groupe de planification. Cela entraînerait un comportement non défini.  
  
 Un groupe de planification est associé à une instance de planificateur spécifique. Vous devez vous assurer que toutes les références au groupe de planification sont libérées avant toutes les références au planificateur, car ce dernier pourrait entraîner la destruction du planificateur. Permet de faire sinon les résultats dans un comportement non défini.  
  
##  <a name="dtor"></a> ~ScheduleGroup 

```
virtual ~ScheduleGroup();
```  
  
##  <a name="scheduletask"></a> ScheduleTask 

 Planifie une tâche légère dans le groupe de planification.  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
*_Proc*<br/>
Pointeur vers la fonction à exécuter pour exécuter le corps de la tâche légère.  
  
*_Data*<br/>
Un pointeur void vers les données qui seront passées en tant que paramètre au corps de la tâche.  
  
### <a name="remarks"></a>Notes  
 Appel de la `ScheduleTask` méthode place implicitement un décompte de références sur le groupe de planification qui est supprimé par le runtime à un moment approprié après l’exécution de la tâche.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [CurrentScheduler, classe](currentscheduler-class.md)   
 [Scheduler, classe](scheduler-class.md)   
 [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



