---
title: Scheduler, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97abec33d5fa4b372bc26874fd37397a2b78bb29
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693677"
---
# <a name="scheduler-class"></a>Scheduler, classe
Représente une abstraction pour un planificateur de runtime d'accès concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class Scheduler;
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[Planificateur](#ctor)|Un objet de la `Scheduler` classe peut uniquement être créé à l’aide des méthodes de fabrique, ou implicitement.|  
|[~ Scheduler, destructeur](#dtor)|Un objet de la `Scheduler` classe est détruit implicitement lorsque toutes les références externes cessent d’exister.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Attacher](#attach)|Attache le planificateur au contexte d’appel. Une fois que cette méthode retourne le contexte d’appel est géré par le planificateur et le planificateur devient le planificateur actuel.|  
|[Créer](#create)|Crée un nouveau planificateur dont le comportement est décrit par le `_Policy` , place une référence initiale sur le planificateur et retourne un pointeur vers elle.|  
|[CreateScheduleGroup](#createschedulegroup)|Surchargé. Crée un nouveau groupe de planification dans le planificateur. La version qui prend le paramètre `_Placement` entraîne des tâches au sein du groupe de planification qui vient d’être créé pour être en faveur de l’exécution à l’emplacement spécifié par ce paramètre.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Retourne le nombre actuel de processeurs virtuels pour le planificateur.|  
|[GetPolicy](#getpolicy)|Retourne une copie de la stratégie que le planificateur a été créé.|  
|[Id](#id)|Retourne un identificateur unique pour le planificateur.|  
|[IsAvailableLocation](#isavailablelocation)|Détermine si un emplacement donné est disponible sur le planificateur.|  
|[Référence](#reference)|Incrémente le décompte de références du planificateur.|  
|[RegisterShutdownEvent](#registershutdownevent)|Le handle d’événement Windows passé dans le `_Event` paramètre soit signalé lorsque le planificateur s’arrête et détruit lui-même. Au moment de que l’événement est signalé, tout le travail qui a été planifié pour le planificateur est terminé. Plusieurs événements d’arrêt peuvent être inscrits via cette méthode.|  
|[Version release](#release)|Décrémente le planificateur décompte de références.|  
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|Réinitialise la stratégie du planificateur par défaut à la valeur par défaut du runtime. La prochaine fois qu’un planificateur par défaut est créé, il utilisera les paramètres de stratégie d’exécution par défaut.|  
|[ScheduleTask](#scheduletask)|Surchargé. Planifie une tâche légère dans le planificateur. La tâche légère sera placée dans un groupe de planification déterminé par le runtime. La version qui prend le paramètre `_Placement` amène la tâche à être favorise l’exécution à l’emplacement spécifié.|  
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|Permet à une stratégie définie par l’utilisateur à utiliser pour créer le planificateur par défaut. Cette méthode peut être appelée uniquement lorsque aucun planificateur par défaut n’existe dans le processus. Une fois une stratégie par défaut a été définie, elle reste en vigueur jusqu’au prochain appel valid soit le `SetDefaultSchedulerPolicy` ou [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) (méthode).|  
  
## <a name="remarks"></a>Notes  
 Le Planificateur de Runtime d’accès concurrentiel utilise des contextes d’exécution, qui correspondent à des contextes d’exécution de système d’exploitation, par exemple un thread, pour exécuter le travail en file d’attente à celui-ci par votre application. À tout moment, le niveau d’accès concurrentiel d’un planificateur est égal au nombre de processeurs virtuels accordées à ce dernier par le Gestionnaire de ressources. Un processeur virtuel est une abstraction pour une ressource de traitement et le mappe à un thread matériel sur le système sous-jacent. Uniquement un contexte de planificateur unique peut exécuter sur un processeur virtuel à un moment donné.  
  
 Le Runtime d’accès concurrentiel créera un planificateur par défaut par processus pour exécuter le travail parallèle. En outre, vous pouvez créer des instances de votre propre planificateur et les manipuler à l’aide de cette classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Scheduler`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="attach"></a> Joindre 

 Attache le planificateur au contexte d’appel. Une fois que cette méthode retourne le contexte d’appel est géré par le planificateur et le planificateur devient le planificateur actuel.  
  
```
virtual void Attach() = 0;
```  
  
### <a name="remarks"></a>Notes  
 Attachement d’un planificateur implicitement la place une référence sur le planificateur.  
  
 À un moment donné dans le futur, vous devez appeler la [CurrentScheduler::Detach](currentscheduler-class.md#detach) méthode afin de permettre l’arrêt du planificateur.  
  
 Si cette méthode est appelée à partir d’un contexte qui est déjà attaché à un planificateur différent, le planificateur existant est mémorisé comme le planificateur précédent, et le planificateur créé récemment devient le planificateur actuel. Lorsque vous appelez le `CurrentScheduler::Detach` (méthode) à un moment ultérieur, le planificateur précédent est restauré comme planificateur actuel.  
  
 Cette méthode lève un [improper_scheduler_attach](improper-scheduler-attach-class.md) exception si ce planificateur est le planificateur actuel du contexte d’appel.  
  
##  <a name="create"></a> Créer 

 Crée un nouveau planificateur dont le comportement est décrit par le `_Policy` , place une référence initiale sur le planificateur et retourne un pointeur vers elle.  
  
```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Policy`  
 La stratégie du planificateur qui décrit le comportement du planificateur qui vient d’être créé.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un planificateur qui vient d’être créé. Cela `Scheduler` objet possède un décompte de références initial.  
  
### <a name="remarks"></a>Notes  
 Après la création d’un planificateur par le `Create` (méthode), vous devez appeler la `Release` méthode à un moment donné dans le futur pour supprimer le décompte de références initial et autoriser l’arrêt du planificateur.  
  
 Un planificateur créé avec cette méthode n’est pas attaché au contexte d’appel. Elle peut être jointe à un contexte à l’aide de la [attacher](#attach) (méthode).  
  
 Cette méthode peut lever des exceptions, y compris les diverses [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) et [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a> CreateScheduleGroup 

 Crée un nouveau groupe de planification dans le planificateur. La version qui prend le paramètre `_Placement` entraîne des tâches au sein du groupe de planification qui vient d’être créé pour être en faveur de l’exécution à l’emplacement spécifié par ce paramètre.  
  
```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Placement`  
 Une référence à un emplacement où les tâches au sein du groupe de planification est en faveur de l’exécution à.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le groupe de planification nouvellement créé. Cela `ScheduleGroup` objet possède un décompte de références initial.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler la [version](schedulegroup-class.md#release) méthode sur un groupe de planification lorsque vous avez terminé de planifier le travail pour elle. Le planificateur détruira la planification de groupe lorsque tout le travail en file d’attente pour qu’il s’est terminée.  
  
 Notez que si vous avez créé ce planificateur explicitement, vous devez libérer toutes les références pour planifier des groupes, avant de libérer votre référence sur le planificateur.  
  
##  <a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors 

 Retourne le nombre actuel de processeurs virtuels pour le planificateur.  
  
```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de processeurs virtuels pour le planificateur actuel.  
  
##  <a name="getpolicy"></a> GetPolicy 

 Retourne une copie de la stratégie que le planificateur a été créé.  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une copie de la stratégie que le planificateur a été créé.  
  
##  <a name="id"></a> ID 

 Retourne un identificateur unique pour le planificateur.  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Identificateur unique pour le planificateur.  
  
##  <a name="isavailablelocation"></a> IsAvailableLocation 

 Détermine si un emplacement donné est disponible sur le planificateur.  
  
```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Placement`  
 Une référence à l’emplacement d’une requête sur le planificateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Indique si l’emplacement spécifié par le `_Placement` argument n’est disponible sur le planificateur.  
  
### <a name="remarks"></a>Notes  
 Notez que la valeur de retour est un échantillonnage instantané si l’emplacement donné est disponible. En présence de plusieurs planificateurs, gestion des ressources dynamiques pour ajouter ou d’empiéter sur ressources à partir des planificateurs à tout moment. Le cas échéant, l’emplacement donné peut modifier la disponibilité.  
  
##  <a name="reference"></a> Référence 

 Incrémente le décompte de références du planificateur.  
  
```
virtual unsigned int Reference() = 0 ;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le décompte de références qui vient d’être incrémenté.  
  
### <a name="remarks"></a>Notes  
 Cela est généralement utilisé pour gérer la durée de vie du planificateur pour la composition. Lorsque le décompte de références d’une chute planificateur à zéro, le planificateur s’arrête et CAPACITE de destruction lui-même après tout fonctionne sur le planificateur est terminée.  
  
 La méthode lève un [improper_scheduler_reference](improper-scheduler-reference-class.md) exception si le nombre de références avant d’appeler le `Reference` méthode était zéro et l’appel est effectué à partir d’un contexte qui n’appartienne pas par le planificateur.  
  
##  <a name="registershutdownevent"></a> RegisterShutdownEvent 

 Le handle d’événement Windows passé dans le `_Event` paramètre soit signalé lorsque le planificateur s’arrête et détruit lui-même. Au moment de que l’événement est signalé, tout le travail qui a été planifié pour le planificateur est terminé. Plusieurs événements d’arrêt peuvent être inscrits via cette méthode.  
  
```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Event`  
 Handle vers un objet d’événement Windows qui sera signalé par l’exécution lorsque le planificateur s’arrête et détruit lui-même.  
  
##  <a name="release"></a> mise en production 

 Décrémente le planificateur décompte de références.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de références décrémenté récemment.  
  
### <a name="remarks"></a>Notes  
 Cela est généralement utilisé pour gérer la durée de vie du planificateur pour la composition. Lorsque le décompte de références d’une chute planificateur à zéro, le planificateur s’arrête et CAPACITE de destruction lui-même après tout fonctionne sur le planificateur est terminée.  
  
##  <a name="resetdefaultschedulerpolicy"></a> ResetDefaultSchedulerPolicy 

 Réinitialise la stratégie du planificateur par défaut à la valeur par défaut du runtime. La prochaine fois qu’un planificateur par défaut est créé, il utilisera les paramètres de stratégie d’exécution par défaut.  
  
```
static void __cdecl ResetDefaultSchedulerPolicy();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode peut être appelée pendant un planificateur par défaut existe dans le processus. Il n’affecte pas la stratégie du planificateur par défaut existant. Toutefois, si le planificateur par défaut s’arrête, et une nouvelle valeur par défaut ont été doit être créée à un moment ultérieur, le nouveau planificateur serait d’utiliser les paramètres de stratégie d’exécution par défaut.  
  
##  <a name="ctor"></a> Planificateur 

 Un objet de la `Scheduler` classe peut uniquement être créé à l’aide des méthodes de fabrique, ou implicitement.  
  
```
Scheduler();
```  
  
### <a name="remarks"></a>Notes  
 Le planificateur du processus par défaut est créé implicitement lorsque vous utilisez beaucoup des fonctions runtime qui nécessitent un planificateur soit joint au contexte d’appel. Méthodes dans la `CurrentScheduler` classe et les fonctionnalités des bibliothèque de modèles parallèles et couches d’agents généralement effectuent une pièce jointe implicite.  
  
 Vous pouvez également créer un planificateur explicitement par le biais du `CurrentScheduler::Create` méthode ou la `Scheduler::Create` (méthode).  
  
##  <a name="dtor"></a> ~ Scheduler 

 Un objet de la `Scheduler` classe est détruit implicitement lorsque toutes les références externes cessent d’exister.  
  
```
virtual ~Scheduler();
```  
  
##  <a name="scheduletask"></a> ScheduleTask 

 Planifie une tâche légère dans le planificateur. La tâche légère sera placée dans un groupe de planification déterminé par le runtime. La version qui prend le paramètre `_Placement` amène la tâche à être favorise l’exécution à l’emplacement spécifié.  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Proc`  
 Pointeur vers la fonction à exécuter pour exécuter le corps de la tâche non activable.  
  
 `_Data`  
 Un pointeur void vers les données qui seront passées en tant que paramètre dans le corps de la tâche.  
  
 `_Placement`  
 Une référence à un emplacement où la tâche légère sera être favorise l’exécution au niveau.  
  
##  <a name="setdefaultschedulerpolicy"></a> SetDefaultSchedulerPolicy 

 Permet à une stratégie définie par l’utilisateur à utiliser pour créer le planificateur par défaut. Cette méthode peut être appelée uniquement lorsque aucun planificateur par défaut n’existe dans le processus. Une fois une stratégie par défaut a été définie, elle reste en vigueur jusqu’au prochain appel valid soit le `SetDefaultSchedulerPolicy` ou [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) (méthode).  
  
```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Policy`  
 La stratégie à définir en tant que la stratégie du planificateur par défaut.  
  
### <a name="remarks"></a>Notes  
 Si le `SetDefaultSchedulerPolicy` méthode est appelée lorsqu’un planificateur par défaut existe déjà dans le processus, le runtime lève une [default_scheduler_exists](default-scheduler-exists-class.md) exception.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Scheduler, classe](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



