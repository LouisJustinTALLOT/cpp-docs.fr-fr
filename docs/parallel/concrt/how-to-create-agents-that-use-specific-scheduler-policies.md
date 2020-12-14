---
description: 'En savoir plus sur : Comment : créer des agents qui utilisent des stratégies de planificateur spécifiques'
title: 'Comment : créer des agents qui utilisent des stratégies de planificateur spécifiques'
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: 06a7ffaf18f3d7024f99755a0595154197c396f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333458"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Comment : créer des agents qui utilisent des stratégies de planificateur spécifiques

Un agent est un composant d’application qui fonctionne de façon asynchrone avec d’autres composants pour résoudre les tâches de calcul plus volumineuses. Un agent a généralement un cycle de vie défini et conserve l’État.

Chaque agent peut avoir des exigences d’applications uniques. Par exemple, un agent qui active l’interaction avec l’utilisateur (extraction de l’entrée ou affichage de la sortie) peut nécessiter un accès plus prioritaire aux ressources de calcul. Les stratégies de planificateur vous permettent de contrôler la stratégie que le planificateur utilise pour gérer les tâches. Cette rubrique montre comment créer des agents qui utilisent des stratégies de planificateur spécifiques.

Pour obtenir un exemple de base qui utilise des stratégies de planificateur personnalisées avec des blocs de messages asynchrones, consultez Guide pratique [pour spécifier des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

Cette rubrique utilise les fonctionnalités de la bibliothèque des agents asynchrones, comme les agents, les blocs de messages et les fonctions de transmission de messages, pour effectuer le travail. Pour plus d’informations sur la bibliothèque des agents asynchrones, consultez [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="example"></a>Exemple

L’exemple suivant définit deux classes qui dérivent de [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md): `permutor` et `printer` . La `permutor` classe calcule toutes les permutations d’une chaîne d’entrée donnée. La `printer` classe imprime les messages d’avancement sur la console. La `permutor` classe effectue une opération nécessitant beaucoup de ressources de calcul, qui peut utiliser toutes les ressources de calcul disponibles. Pour être utile, la `printer` classe doit imprimer chaque message de progression en temps opportun.

Pour fournir à la `printer` classe un accès équitable aux ressources de calcul, cet exemple utilise les étapes décrites dans [Comment : gérer une instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) pour créer une instance de planificateur qui a une stratégie personnalisée. La stratégie personnalisée spécifie que la priorité de thread est la classe de priorité la plus élevée.

Pour illustrer les avantages de l’utilisation d’un planificateur qui a une stratégie personnalisée, cet exemple exécute la tâche globale deux fois. L’exemple utilise tout d’abord le planificateur par défaut pour planifier les deux tâches. L’exemple utilise ensuite le planificateur par défaut pour planifier l' `permutor` objet et un planificateur qui a une stratégie personnalisée pour planifier l' `printer` objet.

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

Bien que les deux ensembles de tâches produisent le même résultat, la version qui utilise une stratégie personnalisée permet `printer` à l’objet de s’exécuter avec une priorité élevée afin qu’il se comporte de manière plus réactive.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `permute-strings.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc permute-Strings. cpp**

## <a name="see-also"></a>Voir aussi

[Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)
