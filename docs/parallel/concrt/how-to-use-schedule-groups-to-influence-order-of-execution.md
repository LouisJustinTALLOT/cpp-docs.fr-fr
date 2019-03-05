---
title: 'Procédure : Utiliser des groupes de planification pour influencer l’ordre d’exécution'
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 99e0383fc8d16f3eeb6e43e59424ab0984ee5c14
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284357"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Procédure : Utiliser des groupes de planification pour influencer l’ordre d’exécution

Dans le Runtime d’accès concurrentiel, l’ordre dans lequel les tâches sont planifiées est non déterministe. Toutefois, vous pouvez utiliser des stratégies de planification pour influencer l’ordre dans lequel les tâches s’exécutent. Cette rubrique montre comment utiliser des groupes de planification avec le [concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) stratégie du planificateur pour influencer l’ordre dans lequel les tâches s’exécutent.

L’exemple exécute un ensemble de tâches deux fois, chacun avec une stratégie de planification différente. Les deux stratégies de limitent le nombre maximal de ressources de traitement à deux. La première exécution utilise la `EnhanceScheduleGroupLocality` stratégie, qui est la valeur par défaut, et la deuxième exécution utilise la `EnhanceForwardProgress` stratégie. Sous le `EnhanceScheduleGroupLocality` stratégie, le planificateur s’exécute toutes les tâches dans un groupe de planification jusqu'à ce que chaque tâche se termine ou qu’il génère. Sous le `EnhanceForwardProgress` stratégie, le planificateur passe au groupe de planification suivant de manière tourniquet (round-robin) après qu’une tâche se termine ou qu’il génère.

Lorsque chaque groupe de planification contient des tâches associées, le `EnhanceScheduleGroupLocality` stratégie entraîne généralement améliorer les performances car la localité de cache est conservée entre les tâches. Le `EnhanceForwardProgress` stratégie permet aux tâches de progresser et est utile lorsque vous avez besoin d’équité de planification parmi les groupes de planification.

## <a name="example"></a>Exemple

Cet exemple définit le `work_yield_agent` classe qui dérive de [concurrency::agent](../../parallel/concrt/reference/agent-class.md). Le `work_yield_agent` classe effectue une unité de travail, cède le contexte actuel, puis exécute une autre unité de travail. L’agent utilise le [concurrency::wait](reference/concurrency-namespace-functions.md#wait) fonction à céder le contexte actuel de manière coopérative afin que d’autres contextes puissent s’exécuter.

Cet exemple crée quatre `work_yield_agent` objets. Pour illustrer comment définir des stratégies de planificateur pour affecter l’ordre dans lequel les agents s’exécutent, l’exemple associe les deux premiers agents à un groupe de planification et les deux autres agents à un autre groupe de planification. L’exemple utilise le [Concurrency::CurrentScheduler :: CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) méthode pour créer le [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objets. L’exemple s’exécute tous les agents de quatre à deux fois, chaque fois avec une stratégie de planification différente.

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

Les deux stratégies produisent la même séquence d’événements. Toutefois, la stratégie qui utilise `EnhanceScheduleGroupLocality` démarre les deux agents qui font partie du premier groupe de planification avant de démarrer les agents qui font partie du second groupe. La stratégie qui utilise `EnhanceForwardProgress` démarre un agent du premier groupe, puis démarre le premier agent du second groupe.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `scheduling-protocol.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc planification-protocol.cpp**

## <a name="see-also"></a>Voir aussi

[Groupes de planification](../../parallel/concrt/schedule-groups.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)
