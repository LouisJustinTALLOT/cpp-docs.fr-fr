---
title: 'Comment : spécifier des stratégies de planificateur'
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: 1334b8dcf8b6615120d4be8db8530af60df9d668
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520027"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>Comment : spécifier des stratégies de planificateur

Stratégies de planificateur vous permettent de contrôler la stratégie utilisée par le planificateur lorsqu’il gère des tâches. Cette rubrique montre comment utiliser une stratégie du planificateur pour augmenter la priorité de thread d’une tâche qui imprime un indicateur de progression dans la console.

Pour obtenir un exemple qui utilise des stratégies de planificateur personnalisé avec des agents asynchrones, consultez [Comment : créer des Agents cette utilisation des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="example"></a>Exemple

L’exemple suivant effectue deux tâches en parallèle. La première tâche calcule le n<sup>th</sup> nombre Fibonacci. La deuxième tâche imprime un indicateur de progression dans la console.

La première tâche utilise la décomposition récursive pour calculer le nombre de Fibonacci. Autrement dit, chaque tâche de manière récursive crée des tâches subordonnées pour calculer le résultat global. Une tâche qui utilise la décomposition récursive peut utiliser toutes les ressources disponibles et ainsi priver les autres tâches. Dans cet exemple, la tâche qui imprime l’indicateur de progression ne recevront pas l’accès aux ressources de calcul en temps voulu.

Pour fournir la tâche qui imprime un progression message un accès équitable aux ressources de calcul, cet exemple utilise les étapes décrites dans [Comment : gérer une Instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) pour créer une instance de planificateur ayant une stratégie personnalisée. La stratégie personnalisée spécifie la priorité de thread pour être la classe de priorité la plus élevée.

Cet exemple utilise le [concurrency::call](../../parallel/concrt/reference/call-class.md) et [concurrency::timer](../../parallel/concrt/reference/timer-class.md) classes pour imprimer l’indicateur de progression. Ces classes ont des versions de leurs constructeurs qui prennent une référence à un [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objet qui planifie leur. L’exemple utilise le planificateur par défaut pour planifier la tâche qui calcule le nombre de Fibonacci et l’instance de planificateur pour planifier la tâche qui imprime l’indicateur de progression.

Pour illustrer les avantages de l’utilisation d’un planificateur qui a une stratégie personnalisée, cet exemple effectue la tâche globale deux fois. L’exemple utilise d’abord le planificateur par défaut pour planifier les deux tâches. L’exemple utilise ensuite le planificateur par défaut pour planifier la première tâche et un planificateur ayant une stratégie personnalisée pour planifier la deuxième tâche.

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

Bien que les deux ensembles de tâches produisent le même résultat, la version qui utilise une stratégie personnalisée permet à la tâche qui imprime l’indicateur de progression à exécuter avec une priorité élevée de sorte qu’il se comporte de façon plus réactive.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `scheduler-policy.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc scheduler-Policy.cpp**

## <a name="see-also"></a>Voir aussi

[Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)<br/>
[Guide pratique pour gérer une instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Guide pratique pour créer des agents qui utilisent des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

