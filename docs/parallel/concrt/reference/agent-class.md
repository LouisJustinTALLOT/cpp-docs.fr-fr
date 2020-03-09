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
ms.openlocfilehash: f0092f5f90bbdf253c09dbdc80849c3db472212f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882936"
---
# <a name="agent-class"></a>agent, classe

Classe destinée à être utilisée comme classe de base pour tous les agents indépendants. Elle est utilisée pour masquer l'état des autres agents et interagir par transmission de messages.

## <a name="syntax"></a>Syntaxe

```cpp
class agent;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[agent](#ctor)|Surchargé. Construit un agent.|
|[~ agent, destructeur](#dtor)|Détruit l’agent.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[cancel](#cancel)|Déplace un agent des États `agent_created` ou `agent_runnable` vers l’État `agent_canceled`.|
|[start](#start)|Déplace un agent de l’État `agent_created` vers l’État `agent_runnable`, et planifie son exécution.|
|[statut](#status)|Source synchrone d’informations d’état de l’agent.|
|[status_port](#status_port)|Source asynchrone d’informations d’état de l’agent.|
|[qu'](#wait)|Attend qu’un agent termine sa tâche.|
|[wait_for_all](#wait_for_all)|Attend que tous les agents spécifiés terminent leurs tâches.|
|[wait_for_one](#wait_for_one)|Attend la fin de la tâche de l’un des agents spécifiés.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[done](#done)|Déplace un agent dans l’État `agent_done`, indiquant que l’agent est terminé.|
|[run](#run)|Représente la tâche principale d’un agent. `run` doit être substitué dans une classe dérivée, et spécifie ce que l’agent doit faire après son démarrage.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [agents asynchrones](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`agent`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="ctor"></a>agent

Construit un agent.

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche d’exécution de l’agent est planifiée.

*_PGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche d’exécution de l’agent est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PGroup` .

## <a name="dtor"></a>~ agent

Détruit l’agent.

```cpp
virtual ~agent();
```

### <a name="remarks"></a>Notes

Il s’agit d’une erreur de destruction d’un agent qui n’est pas dans un état terminal (`agent_done` ou `agent_canceled`). Cela peut être évité en attendant que l’agent atteigne un état terminal dans le destructeur d’une classe qui hérite de la classe `agent`.

## <a name="cancel"></a>Annuler

Déplace un agent des États `agent_created` ou `agent_runnable` vers l’État `agent_canceled`.

```cpp
bool cancel();
```

### <a name="return-value"></a>Valeur de retour

**true** si l’agent a été annulé ; sinon, **false** . Un agent ne peut pas être annulé s’il a déjà démarré ou s’est déjà terminé.

## <a name="done"></a>cas

Déplace un agent dans l’État `agent_done`, indiquant que l’agent est terminé.

```cpp
bool done();
```

### <a name="return-value"></a>Valeur de retour

**true** si l’agent est déplacé vers l’État `agent_done` ; sinon, **false** . Un agent qui a été annulé ne peut pas être déplacé vers l’État `agent_done`.

### <a name="remarks"></a>Notes

Cette méthode doit être appelée à la fin de la méthode `run`, lorsque vous savez que l’exécution de votre agent est terminée.

## <a name="run"></a>Utilisez

Représente la tâche principale d’un agent. `run` doit être substitué dans une classe dérivée, et spécifie ce que l’agent doit faire après son démarrage.

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>Notes

L’état de l’agent est remplacé par `agent_started` juste avant que cette méthode soit appelée. La méthode doit appeler `done` sur l’agent avec un état approprié avant de retourner, et peut ne pas lever d’exceptions.

## <a name="start"></a>activer

Déplace un agent de l’État `agent_created` vers l’État `agent_runnable`, et planifie son exécution.

```cpp
bool start();
```

### <a name="return-value"></a>Valeur de retour

**true** si l’agent a démarré correctement ; sinon, **false** . Impossible de démarrer un agent qui a été annulé.

## <a name="status"></a>statu

Source synchrone d’informations d’état de l’agent.

```cpp
agent_status status();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’état actuel de l’agent. Notez que cet état retourné peut changer immédiatement après avoir été retourné.

## <a name="status_port"></a>status_port

Source asynchrone d’informations d’état de l’agent.

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Valeur de retour

Retourne une source de message qui peut envoyer des messages concernant l’état actuel de l’agent.

## <a name="wait"></a>qu'

Attend qu’un agent termine sa tâche.

```cpp
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*_PAgent*<br/>
Pointeur vers l’agent à attendre.

*_Timeout*<br/>
Durée maximale d’attente, en millisecondes.

### <a name="return-value"></a>Valeur de retour

`agent_status` de l’agent lorsque l’attente se termine. Il peut s’agir de `agent_canceled` ou `agent_done`.

### <a name="remarks"></a>Notes

Une tâche de l’agent est terminée lorsque l’agent entre les États `agent_canceled` ou `agent_done`.

Si le paramètre `_Timeout` a une valeur autre que la constante `COOPERATIVE_TIMEOUT_INFINITE`, l’exception [operation_timed_out](operation-timed-out-class.md) est levée si l’intervalle de temps spécifié expire avant que l’agent n’ait terminé sa tâche.

## <a name="wait_for_all"></a>wait_for_all

Attend que tous les agents spécifiés terminent leurs tâches.

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*count*<br/>
Nombre de pointeurs d’agent présents dans le tableau `_PAgents`.

*_PAgents*<br/>
Tableau de pointeurs vers les agents à attendre.

*_PStatus*<br/>
Pointeur vers un tableau d’États de l’agent. Chaque valeur d’état représente l’état de l’agent correspondant lorsque la méthode est retournée.

*_Timeout*<br/>
Durée maximale d’attente, en millisecondes.

### <a name="remarks"></a>Notes

Une tâche de l’agent est terminée lorsque l’agent entre les États `agent_canceled` ou `agent_done`.

Si le paramètre `_Timeout` a une valeur autre que la constante `COOPERATIVE_TIMEOUT_INFINITE`, l’exception [operation_timed_out](operation-timed-out-class.md) est levée si l’intervalle de temps spécifié expire avant que l’agent n’ait terminé sa tâche.

## <a name="wait_for_one"></a>wait_for_one

Attend la fin de la tâche de l’un des agents spécifiés.

```cpp
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*count*<br/>
Nombre de pointeurs d’agent présents dans le tableau `_PAgents`.

*_PAgents*<br/>
Tableau de pointeurs vers les agents à attendre.

*_Status*<br/>
Référence à une variable où l’état de l’agent sera placé.

*_Index*<br/>
Référence à une variable dans laquelle l’index de l’agent sera placé.

*_Timeout*<br/>
Durée maximale d’attente, en millisecondes.

### <a name="remarks"></a>Notes

Une tâche de l’agent est terminée lorsque l’agent entre les États `agent_canceled` ou `agent_done`.

Si le paramètre `_Timeout` a une valeur autre que la constante `COOPERATIVE_TIMEOUT_INFINITE`, l’exception [operation_timed_out](operation-timed-out-class.md) est levée si l’intervalle de temps spécifié expire avant que l’agent n’ait terminé sa tâche.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
