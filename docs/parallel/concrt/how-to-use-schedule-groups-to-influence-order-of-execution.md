---
title: "Comment : utiliser des groupes de planifications pour influencer l'ordre d'exécution"
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 84829664603999893f32caab39af250059bf9788
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141916"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Comment : utiliser des groupes de planifications pour influencer l'ordre d'exécution

Dans le runtime d’accès concurrentiel, l’ordre dans lequel les tâches sont planifiées n’est pas déterministe. Toutefois, vous pouvez utiliser des stratégies de planification pour influencer l’ordre dans lequel les tâches s’exécutent. Cette rubrique montre comment utiliser des groupes de planification avec la stratégie de planificateur [Concurrency :: SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) pour influencer l’ordre dans lequel les tâches s’exécutent.

L’exemple exécute un ensemble de tâches deux fois, chacune avec une stratégie de planification différente. Les deux stratégies limitent le nombre maximal de ressources de traitement à deux. La première exécution utilise la stratégie de `EnhanceScheduleGroupLocality`, qui est la valeur par défaut, et la deuxième exécution utilise la stratégie de `EnhanceForwardProgress`. Dans le cadre de la stratégie de `EnhanceScheduleGroupLocality`, le planificateur exécute toutes les tâches d’un groupe de planification jusqu’à ce que chaque tâche se termine ou génère. Dans le cadre de la stratégie de `EnhanceForwardProgress`, le planificateur passe au groupe de planification suivant en mode tourniquet (Round Robin) après la fin ou le rendement d’une seule tâche.

Lorsque chaque groupe de planification contient des tâches associées, la stratégie de `EnhanceScheduleGroupLocality` entraîne généralement une amélioration des performances, car la localité du cache est conservée entre les tâches. La stratégie de `EnhanceForwardProgress` permet aux tâches d’avancer en progression et est utile lorsque vous avez besoin de planifier une équité entre des groupes de planification.

## <a name="example"></a>Exemple

Cet exemple définit la classe `work_yield_agent`, qui dérive de [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md). La classe `work_yield_agent` effectue une unité de travail, produit le contexte actuel, puis effectue une autre unité de travail. L’agent utilise la fonction [Concurrency :: wait](reference/concurrency-namespace-functions.md#wait) pour générer de manière coopérative le contexte actuel afin que d’autres contextes puissent s’exécuter.

Cet exemple crée quatre objets `work_yield_agent`. Pour illustrer comment définir des stratégies de planificateur pour qu’elles affectent l’ordre dans lequel les agents s’exécutent, l’exemple associe les deux premiers agents à un groupe de planification et les deux autres à un autre groupe de planification. L’exemple utilise la méthode [Concurrency :: CurrentScheduler :: CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) pour créer les objets [Concurrency :: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) . L’exemple exécute les quatre agents deux fois, chaque fois avec une stratégie de planification différente.

[!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Using EnhanceScheduleGroupLocality...
group 0,
    task 0: first loop...
group 0,
    task 1: first loop...
group 0,
    task 0: waiting...
group 1,
    task 0: first loop...
group 0,
    task 1: waiting...
group 1,
    task 1: first loop...
group 1,
    task 0: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 0,
    task 1: second loop...
group 0,
    task 0: finished...
group 1,
    task 0: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: finished...

Using EnhanceForwardProgress...
group 0,
    task 0: first loop...
group 1,
    task 0: first loop...
group 0,
    task 0: waiting...
group 0,
    task 1: first loop...
group 1,
    task 0: waiting...
group 1,
    task 1: first loop...
group 0,
    task 1: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 1,
    task 0: second loop...
group 0,
    task 0: finished...
group 0,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: finished...
```

Les deux stratégies produisent la même séquence d’événements. Toutefois, la stratégie qui utilise `EnhanceScheduleGroupLocality` démarre les deux agents qui font partie du premier groupe de planification avant de démarrer les agents qui font partie du second groupe. La stratégie qui utilise `EnhanceForwardProgress` démarre un agent à partir du premier groupe, puis démarre le premier agent dans le deuxième groupe.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `scheduling-protocol.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc scheduling-protocol. cpp**

## <a name="see-also"></a>Voir aussi

[Groupes de planification](../../parallel/concrt/schedule-groups.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)
