---
title: 'Comment : spécifier des stratégies de planificateur'
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: bd5edfbdf6b0fda9c7e327dab9538bbf6b5e4b12
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142448"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>Comment : spécifier des stratégies de planificateur

Les stratégies de planificateur vous permettent de contrôler la stratégie que le planificateur utilise pour gérer les tâches. Cette rubrique montre comment utiliser une stratégie de planificateur pour augmenter la priorité des threads d’une tâche qui imprime un indicateur de progression sur la console.

Pour obtenir un exemple qui utilise des stratégies de planificateur personnalisées avec des agents asynchrones, consultez [Comment : créer des agents qui utilisent des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="example"></a>Exemple

L’exemple suivant effectue deux tâches en parallèle. La première tâche calcule le n<sup>ième</sup> nombre de Fibonacci. La deuxième tâche imprime un indicateur de progression sur la console.

La première tâche utilise la décomposition récursive pour calculer le nombre de Fibonacci. Autrement dit, chaque tâche crée de manière récursive des tâches subordonnées pour calculer le résultat global. Une tâche qui utilise la décomposition récursive peut utiliser toutes les ressources disponibles et, par conséquent, priver d’autres tâches. Dans cet exemple, la tâche qui imprime l’indicateur de progression peut ne pas recevoir un accès opportun aux ressources de calcul.

Pour fournir à la tâche qui imprime un message de progression un accès équitable aux ressources de calcul, cet exemple utilise les étapes décrites dans [Comment : gérer une instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) pour créer une instance de planificateur qui a une stratégie personnalisée. La stratégie personnalisée spécifie que la priorité de thread est la classe de priorité la plus élevée.

Cet exemple utilise les classes [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) et [Concurrency :: Timer](../../parallel/concrt/reference/timer-class.md) pour imprimer l’indicateur de progression. Ces classes ont des versions de leurs constructeurs qui prennent une référence à un objet [Concurrency :: Scheduler](../../parallel/concrt/reference/scheduler-class.md) qui les planifie. L’exemple utilise le planificateur par défaut pour planifier la tâche qui calcule le nombre de Fibonacci et l’instance du planificateur pour planifier la tâche qui imprime l’indicateur de progression.

Pour illustrer les avantages de l’utilisation d’un planificateur qui a une stratégie personnalisée, cet exemple exécute la tâche globale deux fois. L’exemple utilise tout d’abord le planificateur par défaut pour planifier les deux tâches. L’exemple utilise ensuite le planificateur par défaut pour planifier la première tâche et un planificateur qui a une stratégie personnalisée pour planifier la deuxième tâche.

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

Bien que les deux ensembles de tâches produisent le même résultat, la version qui utilise une stratégie personnalisée permet à la tâche qui imprime l’indicateur de progression de s’exécuter avec une priorité élevée afin de se comporter plus rapidement.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `scheduler-policy.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Scheduler-Policy. cpp**

## <a name="see-also"></a>Voir aussi

[Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)<br/>
[Guide pratique pour gérer une instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Guide pratique pour créer des agents qui utilisent des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
