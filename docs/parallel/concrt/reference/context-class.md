---
title: Classe de contexte | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
dev_langs:
- C++
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bf574fc679b879e2fa9084ed6fbd4ed82e66f70
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694178"
---
# <a name="context-class"></a>Context, classe
Représente une abstraction pour un contexte d'exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class Context;
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[~ Context, destructeur](#dtor)||  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Bloc](#block)|Bloque le contexte actuel.|  
|[CurrentContext](#currentcontext)|Retourne un pointeur vers le contexte actuel.|  
|[GetId](#getid)|Retourne un identificateur pour le contexte qui est unique dans le planificateur auquel appartient le contexte.|  
|[GetScheduleGroupId](#getschedulegroupid)|Retourne un identificateur pour le groupe de planification qui le contexte fonctionne actuellement.|  
|[GetVirtualProcessorId](#getvirtualprocessorid)|Retourne un identificateur pour le processeur virtuel sur lequel le contexte est en cours d’exécution sur.|  
|[Id](#id)|Retourne un identificateur pour le contexte actuel qui est unique dans le planificateur auquel appartient le contexte actuel.|  
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|Retourne une indication précisant si la collection de tâches qui s’exécute actuellement inline sur le contexte actuel est en cours d’annulation (ou sera bientôt).|  
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|Détermine si le contexte est bloqué de façon synchrone. Un contexte est considéré comme bloqué de façon synchrone s’il a exécuté une action qui a conduit à bloquer explicitement.|  
|[Sur-souscrire](#oversubscribe)|Injecte un processeur virtuel supplémentaire dans un planificateur pour la durée d’un bloc de code lorsqu’elle est appelée sur un contexte de l’exécution sur l’un des processeurs virtuels dans ce planificateur.|  
|[ScheduleGroupId](#schedulegroupid)|Retourne un identificateur pour le groupe de planification qui travaille sur le contexte actuel.|  
|[Débloquer](#unblock)|Débloque le contexte et le rend exécutable.|  
|[VirtualProcessorId](#virtualprocessorid)|Retourne un identificateur pour le processeur virtuel d’exécution sur le contexte actuel.|  
|[Yield](#yield)|Produit l'exécution pour qu'un autre contexte puisse s'exécuter. Si aucun autre contexte n'est disponible pour la production, le planificateur peut produire dans un autre thread du système d'exploitation.|  
  
## <a name="remarks"></a>Notes  
 Le Planificateur de Runtime d’accès concurrentiel (voir [planificateur](scheduler-class.md)) utilise des contextes d’exécution pour exécuter le travail en file d’attente à celui-ci par votre application. Un thread Win32 est un exemple d’un contexte d’exécution sur un système d’exploitation de Windows.  
  
 À tout moment, le niveau d’accès concurrentiel d’un planificateur est égal au nombre de processeurs virtuels accordées à ce dernier par le Gestionnaire de ressources. Un processeur virtuel est une abstraction pour une ressource de traitement et le mappe à un thread matériel sur le système sous-jacent. Uniquement un contexte de planificateur unique peut exécuter sur un processeur virtuel à un moment donné.  
  
 Le planificateur est coopératif par nature et un contexte d’exécution peut produire de son processeur virtuel dans un contexte différent à tout moment s’il souhaite entrer dans un état d’attente. Lors de l’issue de l’attente, il ne peut pas reprendre jusqu'à ce qu’un processeur virtuel disponible à partir du planificateur commence son exécution.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Context`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="block"></a> Bloc 

 Bloque le contexte actuel.  
  
```
static void __cdecl Block();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.  
  
 Si le contexte d’appel s’exécute sur un processeur virtuel, le processeur virtuel trouve un autre contexte exécutable à exécuter ou peut éventuellement créer un nouveau.  
  
 Après le `Block` méthode a été appelée ou sera appelée, vous devez la coupler avec un appel à la [Unblock](#unblock) méthode à partir d’un autre contexte d’exécution pour pouvoir exécuter à nouveau. Sachez qu’il existe une période critique entre le moment où votre code publie son contexte pour un autre thread pour être en mesure d’appeler le `Unblock` (méthode) et le point où la méthode réelle appel à `Block` est effectuée. Pendant cette période, vous ne devez appeler toute méthode qui peut bloquer et débloquer pour des raisons de son propre (par exemple, l’acquisition d’un verrou). Les appels à la `Block` et `Unblock` méthode ne suivent pas la raison du blocage et le déblocage. Seul un objet doit être propriétaire d’un `Block` -  `Unblock` paire.  
  
 Cette méthode peut lever des exceptions, y compris les diverses [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).  
  
##  <a name="dtor"></a> ~ Contexte 

```
virtual ~Context();
```  
  
##  <a name="currentcontext"></a> CurrentContext 

 Retourne un pointeur vers le contexte actuel.  
  
```
static Context* __cdecl CurrentContext();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le contexte actuel.  
  
### <a name="remarks"></a>Notes  
 Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.  
  
##  <a name="getid"></a> GetId 

 Retourne un identificateur pour le contexte qui est unique dans le planificateur auquel appartient le contexte.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Identificateur de contexte qui est unique dans le planificateur auquel appartient le contexte.  
  
##  <a name="getschedulegroupid"></a> GetScheduleGroupId 

 Retourne un identificateur pour le groupe de planification qui le contexte fonctionne actuellement.  
  
```
virtual unsigned int GetScheduleGroupId() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un identificateur pour le groupe de planification que le contexte fonctionne actuellement.  
  
### <a name="remarks"></a>Notes  
 La valeur de retour de cette méthode est un échantillonnage instantané du groupe de planification d’exécution sur le contexte. Si cette méthode est appelée sur un contexte autre que le contexte actuel, la valeur peut être obsolète au moment où elle est retournée et ne peut pas être fiables. En règle générale, cette méthode est utilisée pour le débogage ou uniquement à des fins de suivi.  
  
##  <a name="getvirtualprocessorid"></a> GetVirtualProcessorId 

 Retourne un identificateur pour le processeur virtuel sur lequel le contexte est en cours d’exécution sur.  
  
```
virtual unsigned int GetVirtualProcessorId() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si le contexte est en cours d’exécution sur un processeur virtuel, un identificateur pour le processeur virtuel sur lequel le contexte est en cours d’exécution. Sinon, la valeur `-1`.  
  
### <a name="remarks"></a>Notes  
 La valeur de retour de cette méthode est un échantillonnage instantané du processeur virtuel sur lequel le contexte s’exécute. Cette valeur peut être obsolète au moment où elle est retournée et ne peut pas être fiables. En règle générale, cette méthode est utilisée pour le débogage ou uniquement à des fins de suivi.  
  
##  <a name="id"></a> ID 

 Retourne un identificateur pour le contexte actuel qui est unique dans le planificateur auquel appartient le contexte actuel.  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si le contexte actuel est associé à un planificateur, un identificateur pour le contexte actuel qui est unique dans le planificateur auquel le contexte actuel appartient ; Sinon, la valeur `-1`.  
  
##  <a name="iscurrenttaskcollectioncanceling"></a> IsCurrentTaskCollectionCanceling 

 Retourne une indication précisant si la collection de tâches qui s’exécute actuellement inline sur le contexte actuel est en cours d’annulation (ou sera bientôt).  
  
```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si un planificateur est associé au contexte d’appel et un groupe de tâches exécute une tâche inline sur ce contexte, une indication précisant si ce groupe de tâches est en cours d’annulation (ou sera bientôt) ; Sinon, la valeur `false`.  
  
##  <a name="issynchronouslyblocked"></a> IsSynchronouslyBlocked 

 Détermine si le contexte est bloqué de façon synchrone. Un contexte est considéré comme bloqué de façon synchrone s’il a exécuté une action qui a conduit à bloquer explicitement.  
  
```
virtual bool IsSynchronouslyBlocked() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Indique si le contexte est bloqué de façon synchrone.  
  
### <a name="remarks"></a>Notes  
 Un contexte est considéré comme bloqué de façon synchrone s’il a exécuté une action qui a conduit à bloquer explicitement. Dans le Planificateur de threads, cela indique un appel direct à la `Context::Block` méthode ou un objet de synchronisation qui a été généré à l’aide de la `Context::Block` (méthode).  
  
 La valeur de retour de cette méthode est un échantillonnage instantané montrant si le contexte est bloqué de façon synchrone. Cette valeur peut être périmée au moment où elle est retournée et est utilisable uniquement dans des circonstances très spécifiques.  
  
##  <a name="operator_delete"></a> opérateur delete 

 A `Context` détruit en interne par le runtime. Il ne peut pas être explicitement supprimé.  
  
```
void operator delete(void* _PObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PObject`  
 Pointeur vers l’objet à supprimer.  
  
##  <a name="oversubscribe"></a> Sur-souscrire 

 Injecte un processeur virtuel supplémentaire dans un planificateur pour la durée d’un bloc de code lorsqu’elle est appelée sur un contexte de l’exécution sur l’un des processeurs virtuels dans ce planificateur.  
  
```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```  
  
### <a name="parameters"></a>Paramètres  
 `_BeginOversubscription`  
 Si `true`, indique qu’un processeur virtuel supplémentaire doit être ajouté pour la durée du surabonnement. Si `false`, indique que le surabonnement doit se terminer et que le processeur virtuel ajouté précédemment doit être supprimé.  
  
##  <a name="schedulegroupid"></a> ScheduleGroupId 

 Retourne un identificateur pour le groupe de planification qui travaille sur le contexte actuel.  
  
```
static unsigned int __cdecl ScheduleGroupId();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si le contexte actuel est associé à un planificateur et que vous travaillez sur un groupe de planification, un identificateur pour le Planificateur de groupe qui fonctionne le contexte actuel. Sinon, la valeur `-1`.  
  
##  <a name="unblock"></a> Débloquer 

 Débloque le contexte et le rend exécutable.  
  
```
virtual void Unblock() = 0;
```  
  
### <a name="remarks"></a>Notes  
 Il est parfaitement conforme pour un appel à la `Unblock` méthode avant un appel correspondant à la [bloc](#block) (méthode). Tant que les appels à la `Block` et `Unblock` méthodes sont appariés correctement, le runtime gère correctement le naturel des deux ordres. Un `Unblock` appel avant une `Block` appel annule simplement l’effet de la `Block` appeler.  
  
 Il existe plusieurs exceptions peuvent être levées à partir de cette méthode. Si un contexte tente d’appeler le `Unblock` méthode sur lui-même, un [context_self_unblock](context-self-unblock-class.md) exception sera levée. Si les appels à `Block` et `Unblock` ne sont pas correctement associés (par exemple, deux appels à `Unblock` sont effectuées pour un contexte qui est en cours d’exécution), un [context_unblock_unbalanced](context-unblock-unbalanced-class.md) exception sera levée.  
  
 Sachez qu’il existe une période critique entre le moment où votre code publie son contexte pour un autre thread pour être en mesure d’appeler le `Unblock` (méthode) et le point où la méthode réelle appel à `Block` est effectuée. Pendant cette période, vous ne devez appeler toute méthode qui peut bloquer et débloquer pour des raisons de son propre (par exemple, l’acquisition d’un verrou). Les appels à la `Block` et `Unblock` méthode ne suivent pas la raison du blocage et le déblocage. Seul un objet doit être propriétaire d’un `Block` et `Unblock` paire.  
  
##  <a name="virtualprocessorid"></a> VirtualProcessorId 

 Retourne un identificateur pour le processeur virtuel d’exécution sur le contexte actuel.  
  
```
static unsigned int __cdecl VirtualProcessorId();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si le contexte actuel est associé à un planificateur, un identificateur pour le processeur virtuel sur lequel le contexte actuel s’exécute ; Sinon, la valeur `-1`.  
  
### <a name="remarks"></a>Notes  
 La valeur de retour de cette méthode est un échantillonnage instantané du processeur virtuel sur lequel s’exécute le contexte actuel. Cette valeur peut être obsolète au moment où elle est retournée et ne peut pas être fiables. En règle générale, cette méthode est utilisée pour le débogage ou uniquement à des fins de suivi.  
  
##  <a name="yield"></a> Yield 

 Produit l'exécution pour qu'un autre contexte puisse s'exécuter. Si aucun autre contexte n'est disponible pour la production, le planificateur peut produire dans un autre thread du système d'exploitation.  
  
```
static void __cdecl Yield();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.  
  
##  <a name="yieldexecution"></a> YieldExecution 

 Produit l'exécution pour qu'un autre contexte puisse s'exécuter. Si aucun autre contexte n'est disponible pour la production, le planificateur peut produire dans un autre thread du système d'exploitation.  
  
```
static void __cdecl YieldExecution();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.  
  
 Cette fonction est une nouveauté de [!INCLUDE[vs_dev14](../../../ide/includes/vs_dev14_md.md)] et est identique à la [Yield](#yield) de fonctionner mais n’est pas en conflit avec la macro Yield dans Windows.h.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Scheduler, classe](scheduler-class.md)   
 [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



