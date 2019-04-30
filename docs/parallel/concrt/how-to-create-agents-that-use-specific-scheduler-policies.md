---
title: 'Procédure : Créer des Agents qui utilisent des stratégies de planificateur spécifiques'
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: 5aac86801015549b5552b51c06a30f8398346a06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411368"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Procédure : Créer des Agents qui utilisent des stratégies de planificateur spécifiques

Un agent est un composant d’application qui fonctionne de façon asynchrone avec d’autres composants pour effectuer des tâches de calcul plus volumineux. En règle générale, un agent a un cycle de vie défini et gère l’état.

Chaque agent peut avoir une configuration d’application unique. Par exemple, un agent qui permet l’interaction utilisateur (récupération de l’entrée ou affichage de sortie) peut-être nécessiter un accès de priorité plus élevé aux ressources de calcul. Stratégies de planificateur vous permettent de contrôler la stratégie utilisée par le planificateur lorsqu’il gère des tâches. Cette rubrique montre comment créer des agents qui utilisent des stratégies de planificateur spécifiques.

Pour obtenir un exemple qui utilise des stratégies de planificateur personnalisé avec des blocs de messages asynchrones, consultez [Comment : Spécifier des stratégies de planificateur](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

Cette rubrique utilise la fonctionnalité à partir de la bibliothèque d’Agents asynchrones, tels que les agents, les blocs de messages et les fonctions de passage de messages, pour effectuer un travail. Pour plus d’informations sur la bibliothèque d’Agents asynchrones, consultez [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="example"></a>Exemple

L’exemple suivant définit deux classes qui dérivent de [concurrency::agent](../../parallel/concrt/reference/agent-class.md): `permutor` et `printer`. Le `permutor` classe calcule toutes les permutations d’une chaîne d’entrée donnée. Le `printer` classe imprime les messages de progression sur la console. Le `permutor` classe effectue une opération nécessitant de nombreuses ressources, ce qui peut utiliser toutes les ressources informatiques disponibles. Pour être utile, la `printer` classe doit imprimer chaque message de progression en temps voulu.

Pour fournir la `printer` classe un accès équitable aux ressources de calcul, cet exemple utilise les étapes décrites dans [Comment : Gérer une Instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) pour créer une instance de planificateur ayant une stratégie personnalisée. La stratégie personnalisée spécifie la priorité de thread pour être la classe de priorité la plus élevée.

Pour illustrer les avantages de l’utilisation d’un planificateur qui a une stratégie personnalisée, cet exemple effectue la tâche globale deux fois. L’exemple utilise d’abord le planificateur par défaut pour planifier les deux tâches. L’exemple utilise ensuite le planificateur par défaut pour planifier la `permutor` objet et un planificateur ayant une stratégie personnalisée pour planifier le `printer` objet.

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

Bien que les deux ensembles de tâches produisent le même résultat, la version qui utilise une stratégie personnalisée permet le `printer` objet s’exécute avec une priorité élevée afin qu’il se comporte de façon plus réactive.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `permute-strings.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc permute-strings.cpp**

## <a name="see-also"></a>Voir aussi

[Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)
