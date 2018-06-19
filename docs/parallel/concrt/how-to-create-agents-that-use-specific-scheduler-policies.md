---
title: 'Comment : créer des Agents qui utilisent des stratégies de planificateur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9efa40d24ed4eaee5b9fd3995a4cf9ed696eb39a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685734"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Comment : créer des agents qui utilisent des stratégies de planificateur spécifiques
Un agent est un composant d’application qui fonctionne de façon asynchrone avec d’autres composants pour effectuer des tâches de calcul supérieure. En règle générale, un agent a un cycle de vie fixe et conserve l’état.  
  
 Chaque agent peut avoir des spécifications d’application uniques. Par exemple, un agent qui permet l’interaction utilisateur (récupération d’entrée ou affichage de sortie) peut-être nécessiter un accès de priorité plus élevé aux ressources de calcul. Stratégies de planificateur vous permettent de contrôler la stratégie utilisée par le planificateur lorsqu’il gère des tâches. Cette rubrique montre comment créer des agents qui utilisent des stratégies de planificateur spécifiques.  
  
 Pour obtenir un exemple de base qui utilise des stratégies de planificateur personnalisé avec les blocs de messages asynchrones, consultez [Comment : spécifier des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
 Cette rubrique utilise les fonctionnalités à partir de la bibliothèque d’Agents asynchrones, telles que les agents, les blocs de messages et les fonctions de passage de messages, pour effectuer le travail. Pour plus d’informations sur la bibliothèque d’Agents asynchrones, consultez [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit deux classes qui dérivent de [concurrency::agent](../../parallel/concrt/reference/agent-class.md): `permutor` et `printer`. La `permutor` classe calcule toutes les permutations d’une chaîne d’entrée donnée. La `printer` classe imprime les messages de progression sur la console. La `permutor` classe effectue une opération gourmande en ressources, ce qui peut utiliser toutes les ressources informatiques disponibles. Pour être utile, la `printer` classe doit imprimer chaque message de progression en temps voulu.  
  
 Pour fournir la `printer` accès juste de classe aux ressources de calcul, cet exemple utilise les étapes décrites dans [Comment : gérer une Instance du planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) pour créer une instance du planificateur ayant une stratégie personnalisée. La stratégie personnalisée spécifie la priorité de thread pour la classe de priorité la plus élevée.  
  
 Pour illustrer les avantages de l’utilisation d’un planificateur ayant une stratégie personnalisée, cet exemple effectue la tâche globale deux fois. L’exemple utilise d’abord le planificateur par défaut pour planifier les deux tâches. L’exemple utilise ensuite le planificateur par défaut pour planifier la `permutor` objet et un planificateur ayant une stratégie personnalisée pour planifier le `printer` objet.  
  
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
  
 Bien que les deux ensembles de tâches produisent le même résultat, la version qui utilise une stratégie personnalisée permet le `printer` objet s’exécute avec une priorité élevée afin que la meilleure réactivité.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `permute-strings.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /EHsc permute-strings.cpp**  
  
## <a name="see-also"></a>Voir aussi  
 [Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)   
 [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)   
 

