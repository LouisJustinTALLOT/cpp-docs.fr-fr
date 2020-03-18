---
title: Context, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 7c47d9db64b0af7d5413abed3f85e9d41a591fa2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422177"
---
# <a name="context-class"></a>Context, classe

Représente une abstraction pour un contexte d'exécution.

## <a name="syntax"></a>Syntaxe

```cpp
class Context;
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Name|Description|
|----------|-----------------|
|[~, Destructeur de contexte](#dtor)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[Bloc](#block)|Bloque le contexte actuel.|
|[CurrentContext](#currentcontext)|Retourne un pointeur vers le contexte actuel.|
|[GetId](#getid)|Retourne un identificateur pour le contexte qui est unique dans le planificateur auquel le contexte appartient.|
|[GetScheduleGroupId](#getschedulegroupid)|Retourne un identificateur pour le groupe de planification sur lequel le contexte est actuellement utilisé.|
|[GetVirtualProcessorId](#getvirtualprocessorid)|Retourne un identificateur pour le processeur virtuel sur lequel s’exécute actuellement le contexte.|
|[Id](#id)|Retourne un identificateur pour le contexte actuel qui est unique dans le planificateur auquel le contexte actuel appartient.|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|Retourne une indication précisant si la collection de tâches en cours d’exécution inline sur le contexte actuel est au milieu d’une annulation active (ou sera bientôt).|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|Détermine si le contexte est bloqué de manière synchrone ou non. Un contexte est considéré comme bloqué de façon synchrone s’il a effectué explicitement une action qui a entraîné un blocage.|
|[Manquer](#oversubscribe)|Injecte un processeur virtuel supplémentaire dans un planificateur pour la durée d’un bloc de code lorsqu’il est appelé sur un contexte s’exécutant sur l’un des processeurs virtuels de ce planificateur.|
|[ScheduleGroupId](#schedulegroupid)|Retourne un identificateur pour le groupe de planification sur lequel le contexte actuel travaille.|
|[Verrouillage](#unblock)|Débloque le contexte et le rend exécutable.|
|[VirtualProcessorId](#virtualprocessorid)|Retourne un identificateur pour le processeur virtuel sur lequel s’exécute le contexte actuel.|
|[Yield](#yield)|Produit l'exécution pour qu'un autre contexte puisse s'exécuter. Si aucun autre contexte n'est disponible pour la production, le planificateur peut produire dans un autre thread du système d'exploitation.|

## <a name="remarks"></a>Notes

Le planificateur runtime d’accès concurrentiel (consultez [Scheduler](scheduler-class.md)) utilise des contextes d’exécution pour exécuter le travail mis en file d’attente par votre application. Un thread Win32 est un exemple de contexte d’exécution sur un système d’exploitation Windows.

À tout moment, le niveau de concurrence d’un planificateur est égal au nombre de processeurs virtuels qui lui sont accordés par le Gestionnaire des ressources. Un processeur virtuel est une abstraction d’une ressource de traitement qui est mappée à un thread matériel sur le système sous-jacent. Un seul contexte de planificateur peut s’exécuter sur un processeur virtuel à un moment donné.

Le planificateur est coopératif par nature et un contexte d’exécution peut produire son processeur virtuel dans un contexte différent à tout moment s’il souhaite entrer dans un état d’attente. Lorsque l’attente est satisfaite, il ne peut pas reprendre tant qu’un processeur virtuel disponible à partir du planificateur ne commence pas à l’exécuter.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`Context`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="block"></a>Plage

Bloque le contexte actuel.

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>Notes

Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.

Si le contexte d’appel s’exécute sur un processeur virtuel, le processeur virtuel trouvera un autre contexte exécutable à exécuter ou peut en créer un nouveau.

Une fois que la méthode `Block` a été appelée ou sera appelée, vous devez la coupler avec un appel à la méthode [Unblock](#unblock) d’un autre contexte d’exécution afin qu’elle s’exécute à nouveau. N’oubliez pas qu’il existe une période critique entre le moment où votre code publie son contexte pour qu’un autre thread soit en mesure d’appeler la méthode `Unblock` et le point où l’appel de méthode réel à `Block` est effectué. Pendant cette période, vous ne devez pas appeler de méthode qui peut à son tour bloquer et débloquer pour ses propres raisons (par exemple, en acquérant un verrou). Les appels à la méthode `Block` et `Unblock` n’effectuent pas le suivi de la raison du blocage et du déblocage. Un seul objet doit avoir la propriété d’une paire d' `Unblock` de - `Block`.

Cette méthode peut lever diverses exceptions, y compris [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).

## <a name="dtor"></a>~ Contexte

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a>CurrentContext

Retourne un pointeur vers le contexte actuel.

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le contexte actuel.

### <a name="remarks"></a>Notes

Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.

## <a name="getid"></a>GetId

Retourne un identificateur pour le contexte qui est unique dans le planificateur auquel le contexte appartient.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur du contexte qui est unique dans le planificateur auquel le contexte appartient.

## <a name="getschedulegroupid"></a>GetScheduleGroupId

Retourne un identificateur pour le groupe de planification sur lequel le contexte est actuellement utilisé.

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur du groupe de planification sur lequel le contexte est actuellement utilisé.

### <a name="remarks"></a>Notes

La valeur de retour de cette méthode est un échantillonnage instantané du groupe de planification sur lequel s’exécute le contexte. Si cette méthode est appelée dans un contexte autre que le contexte actuel, la valeur peut être obsolète au moment où elle est retournée et ne peut pas être reposée. En général, cette méthode est utilisée à des fins de débogage ou de suivi uniquement.

## <a name="getvirtualprocessorid"></a>GetVirtualProcessorId

Retourne un identificateur pour le processeur virtuel sur lequel s’exécute actuellement le contexte.

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Si le contexte est en cours d’exécution sur un processeur virtuel, il s’agit d’un identificateur pour le processeur virtuel sur lequel le contexte est actuellement exécuté ; Sinon, la valeur `-1`.

### <a name="remarks"></a>Notes

La valeur de retour de cette méthode est un échantillonnage instantané du processeur virtuel sur lequel s’exécute le contexte. Cette valeur peut être obsolète au moment où elle est retournée et ne peut pas être invoquée. En général, cette méthode est utilisée à des fins de débogage ou de suivi uniquement.

## <a name="id"></a>Identifi

Retourne un identificateur pour le contexte actuel qui est unique dans le planificateur auquel le contexte actuel appartient.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Valeur de retour

Si le contexte actuel est attaché à un planificateur, identificateur du contexte actuel qui est unique dans le planificateur auquel le contexte actuel appartient ; Sinon, la valeur `-1`.

## <a name="iscurrenttaskcollectioncanceling"></a>IsCurrentTaskCollectionCanceling

Retourne une indication précisant si la collection de tâches en cours d’exécution inline sur le contexte actuel est au milieu d’une annulation active (ou sera bientôt).

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Valeur de retour

Si un planificateur est attaché au contexte d’appel et qu’un groupe de tâches exécute une tâche Inline sur ce contexte, indiquant si ce groupe de tâches est au milieu d’une annulation active (ou sera bientôt); Sinon, la valeur `false`.

## <a name="issynchronouslyblocked"></a>IsSynchronouslyBlocked

Détermine si le contexte est bloqué de manière synchrone ou non. Un contexte est considéré comme bloqué de façon synchrone s’il a effectué explicitement une action qui a entraîné un blocage.

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Indique si le contexte est bloqué de manière synchrone.

### <a name="remarks"></a>Notes

Un contexte est considéré comme bloqué de façon synchrone s’il a effectué explicitement une action qui a entraîné un blocage. Dans le planificateur de threads, cela indique un appel direct à la méthode `Context::Block` ou à un objet de synchronisation qui a été créé à l’aide de la méthode `Context::Block`.

La valeur de retour de cette méthode est un exemple instantané indiquant si le contexte est bloqué de manière synchrone. Cette valeur peut être obsolète au moment où elle est retournée et ne peut être utilisée que dans des circonstances très spécifiques.

## <a name="operator_delete"></a>opérateur delete

Un objet `Context` est détruit en interne par le Runtime. Elle ne peut pas être supprimée explicitement.

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Paramètres

*_PObject*<br/>
Pointeur vers l’objet à supprimer.

## <a name="oversubscribe"></a>Manquer

Injecte un processeur virtuel supplémentaire dans un planificateur pour la durée d’un bloc de code lorsqu’il est appelé sur un contexte s’exécutant sur l’un des processeurs virtuels de ce planificateur.

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Paramètres

*_BeginOversubscription*<br/>
Si la **valeur est true**, une indication qu’un processeur virtuel supplémentaire doit être ajouté pour la durée du surabonnement. Si la **valeur est false**, une indication que le surabonnement doit se terminer et que le processeur virtuel ajouté précédemment doit être supprimé.

## <a name="schedulegroupid"></a>ScheduleGroupId

Retourne un identificateur pour le groupe de planification sur lequel le contexte actuel travaille.

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Valeur de retour

Si le contexte actuel est attaché à un planificateur et s’il travaille sur un groupe de planification, il s’agit d’un identificateur pour le groupe de planificateur sur lequel le contexte actuel travaille ; Sinon, la valeur `-1`.

## <a name="unblock"></a>Verrouillage

Débloque le contexte et le rend exécutable.

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Notes

Il est parfaitement légal qu’un appel à la méthode `Unblock` précède un appel correspondant à la méthode [Block](#block) . Tant que les appels aux méthodes `Block` et `Unblock` sont correctement couplés, le Runtime gère correctement la course naturelle de l’un ou l’autre ordre. Un appel de `Unblock` qui vient avant un appel de `Block` inverse simplement l’effet de l’appel de `Block`.

Il existe plusieurs exceptions qui peuvent être levées à partir de cette méthode. Si un contexte tente d’appeler la méthode `Unblock` sur lui-même, une exception [context_self_unblock](context-self-unblock-class.md) est levée. Si les appels à `Block` et `Unblock` ne sont pas associés correctement (par exemple, deux appels à `Unblock` sont effectués pour un contexte qui est en cours d’exécution), une exception [context_unblock_unbalanced](context-unblock-unbalanced-class.md) est levée.

N’oubliez pas qu’il existe une période critique entre le moment où votre code publie son contexte pour qu’un autre thread soit en mesure d’appeler la méthode `Unblock` et le point où l’appel de méthode réel à `Block` est effectué. Pendant cette période, vous ne devez pas appeler de méthode qui peut à son tour bloquer et débloquer pour ses propres raisons (par exemple, en acquérant un verrou). Les appels à la méthode `Block` et `Unblock` n’effectuent pas le suivi de la raison du blocage et du déblocage. Un seul objet doit avoir la propriété d’une paire `Block` et `Unblock`.

## <a name="virtualprocessorid"></a>VirtualProcessorId

Retourne un identificateur pour le processeur virtuel sur lequel s’exécute le contexte actuel.

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Valeur de retour

Si le contexte actuel est attaché à un planificateur, un identificateur pour le processeur virtuel sur lequel le contexte actuel s’exécute ; Sinon, la valeur `-1`.

### <a name="remarks"></a>Notes

La valeur de retour de cette méthode est un échantillonnage instantané du processeur virtuel sur lequel s’exécute le contexte actuel. Cette valeur peut être obsolète au moment où elle est retournée et ne peut pas être invoquée. En général, cette méthode est utilisée à des fins de débogage ou de suivi uniquement.

## <a name="yield"></a>Génér

Produit l'exécution pour qu'un autre contexte puisse s'exécuter. Si aucun autre contexte n'est disponible pour la production, le planificateur peut produire dans un autre thread du système d'exploitation.

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>Notes

Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.

## <a name="yieldexecution"></a>YieldExecution

Produit l'exécution pour qu'un autre contexte puisse s'exécuter. Si aucun autre contexte n'est disponible pour la production, le planificateur peut produire dans un autre thread du système d'exploitation.

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Notes

Cette méthode entraîne la création du planificateur par défaut du processus et/ou son attachement au contexte d'appel s'il n'existe aucun planificateur actuellement associé au contexte d'appel.

Cette fonction est nouvelle dans Visual Studio 2015 et est identique à la fonction [yield](#yield) , mais n’est pas en conflit avec la macro yield dans Windows. h.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)<br/>
[Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
