---
title: agent, classe
ms.date: 11/04/2016
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
ms.openlocfilehash: ad096eea3467346d85ce4249e910915cbd73488d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560249"
---
# <a name="agent-class"></a>agent, classe

Classe destinée à être utilisée comme classe de base pour tous les agents indépendants. Elle est utilisée pour masquer l'état des autres agents et interagir par transmission de messages.

## <a name="syntax"></a>Syntaxe

```
class agent;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[agent](#ctor)|Surchargé. Construit un agent.|
|[~ agent, destructeur](#dtor)|Détruit l’agent.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[cancel](#cancel)|Déplace un agent à partir de le le `agent_created` ou `agent_runnable` États à la `agent_canceled` état.|
|[start](#start)|Déplace un agent à partir de la `agent_created` l’état le `agent_runnable` d’état et il planifie l’exécution de.|
|[status](#status)|Une source synchrone d’informations d’état de l’agent.|
|[status_port](#status_port)|Source asynchrone d’informations d’état de l’agent.|
|[attente](#wait)|Attend qu’un agent effectuer sa tâche.|
|[wait_for_all](#wait_for_all)|Attend que tous les agents spécifiés pour effectuer leurs tâches.|
|[wait_for_one](#wait_for_one)|Attend que l’un des agents spécifiés ait terminé sa tâche.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[Terminé](#done)|Déplace un agent dans le `agent_done` état indiquant que l’agent a terminé.|
|[run](#run)|Représente la tâche principale d’un agent. `run` doit être substituée dans une classe dérivée et spécifie ce que l’agent doit faire après qu’elle a été démarré.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Agents asynchrones](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`agent`

## <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> Agent

Construit un agent.

```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Le `Scheduler` de l’objet dans lequel la tâche d’exécution de l’agent est planifiée.

*_PGroup*<br/>
Le `ScheduleGroup` de l’objet dans lequel la tâche d’exécution de l’agent est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PGroup` .

##  <a name="dtor"></a> ~ agent

Détruit l’agent.

```
virtual ~agent();
```

### <a name="remarks"></a>Notes

C’est une erreur pour détruire un agent qui n’est pas dans un état terminal (soit `agent_done` ou `agent_canceled`). Cela peut être évité en attendant que l’agent atteigne un état terminal dans le destructeur d’une classe qui hérite de la `agent` classe.

##  <a name="cancel"></a> Annuler

Déplace un agent à partir de le le `agent_created` ou `agent_runnable` États à la `agent_canceled` état.

```
bool cancel();
```

### <a name="return-value"></a>Valeur de retour

**true** si l’agent a été annulée, **false** dans le cas contraire. Un agent ne peut pas être annulé si elle a déjà démarré ou est déjà terminée.

##  <a name="done"></a> Terminé

Déplace un agent dans le `agent_done` état indiquant que l’agent a terminé.

```
bool done();
```

### <a name="return-value"></a>Valeur de retour

**true** si l’agent est déplacé vers le `agent_done` état, **false** dans le cas contraire. Impossible de déplacer un agent qui a été annulé à la `agent_done` état.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée à la fin de la `run` méthode, lorsque vous savez que l’exécution de votre agent est terminée.

##  <a name="run"></a> exécuter

Représente la tâche principale d’un agent. `run` doit être substituée dans une classe dérivée et spécifie ce que l’agent doit faire après qu’elle a été démarré.

```
virtual void run() = 0;
```

### <a name="remarks"></a>Notes

L’état de l’agent est passé à `agent_started` juste avant que cette méthode est appelée. La méthode doit appeler `done` sur l’agent avec un état approprié avant de retourner et ne peut pas lever des exceptions.

##  <a name="start"></a> Démarrer

Déplace un agent à partir de la `agent_created` l’état le `agent_runnable` d’état et il planifie l’exécution de.

```
bool start();
```

### <a name="return-value"></a>Valeur de retour

**true** si l’agent a démarré correctement, **false** dans le cas contraire. Impossible de démarrer un agent qui a été annulé.

##  <a name="status"></a> État

Une source synchrone d’informations d’état de l’agent.

```
agent_status status();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’état actuel de l’agent. Notez que cet état retourné peut changer immédiatement après avoir été retourné.

##  <a name="status_port"></a> status_port

Source asynchrone d’informations d’état de l’agent.

```
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Valeur de retour

Retourne une source de message qui peut envoyer des messages sur l’état actuel de l’agent.

##  <a name="wait"></a> attente

Attend qu’un agent effectuer sa tâche.

```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*_PAgent*<br/>
Pointeur vers l’agent à attendre.

*_Délai*<br/>
La durée maximale d’attente, en millisecondes.

### <a name="return-value"></a>Valeur de retour

Le `agent_status` de l’agent lors de l’attente se termine. Il peut s’agir `agent_canceled` ou `agent_done`.

### <a name="remarks"></a>Notes

Une tâche d’agent est terminée lorsque l’agent passe le `agent_canceled` ou `agent_done` États.

Si le paramètre `_Timeout` a une valeur autre que la constante `COOPERATIVE_TIMEOUT_INFINITE`, l’exception [operation_timed_out](operation-timed-out-class.md) est levée si le délai spécifié expire avant que l’agent a terminé sa tâche.

##  <a name="wait_for_all"></a> wait_for_all

Attend que tous les agents spécifiés pour effectuer leurs tâches.

```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*count*<br/>
Le nombre de pointeurs d’agent présents dans le tableau `_PAgents`.

*_PAgents*<br/>
Un tableau de pointeurs vers les agents à attendre.

*_PStatus*<br/>
Pointeur vers un tableau d’états d’agent. Chaque valeur d’état représentera l’état de l’agent correspondant lorsque la méthode est retournée.

*_Délai*<br/>
La durée maximale d’attente, en millisecondes.

### <a name="remarks"></a>Notes

Une tâche d’agent est terminée lorsque l’agent passe le `agent_canceled` ou `agent_done` États.

Si le paramètre `_Timeout` a une valeur autre que la constante `COOPERATIVE_TIMEOUT_INFINITE`, l’exception [operation_timed_out](operation-timed-out-class.md) est levée si le délai spécifié expire avant que l’agent a terminé sa tâche.

##  <a name="wait_for_one"></a> wait_for_one

Attend que l’un des agents spécifiés ait terminé sa tâche.

```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*count*<br/>
Le nombre de pointeurs d’agent présents dans le tableau `_PAgents`.

*_PAgents*<br/>
Un tableau de pointeurs vers les agents à attendre.

*_État*<br/>
Une référence à une variable où l’état de l’agent sera placé.

*_Index*<br/>
Une référence à une variable où l’index de l’agent sera placé.

*_Délai*<br/>
La durée maximale d’attente, en millisecondes.

### <a name="remarks"></a>Notes

Une tâche d’agent est terminée lorsque l’agent passe le `agent_canceled` ou `agent_done` États.

Si le paramètre `_Timeout` a une valeur autre que la constante `COOPERATIVE_TIMEOUT_INFINITE`, l’exception [operation_timed_out](operation-timed-out-class.md) est levée si le délai spécifié expire avant que l’agent a terminé sa tâche.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
