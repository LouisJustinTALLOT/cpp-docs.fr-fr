---
title: 'Procédure pas à pas : Utilisation du Runtime d’accès concurrentiel dans une Application COM | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd9f665f77ca5ae5311b034ee7afef6241ac489
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692546"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Procédure pas à pas : utilisation du runtime d'accès concurrentiel routage dans une application COM
Ce document montre comment utiliser le Runtime d’accès concurrentiel dans une application qui utilise le modèle COM (Component Object).  
  
## <a name="prerequisites"></a>Prérequis  
 Lisez les documents suivants avant de commencer cette procédure pas à pas :  
  
- [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
- [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)  
  
- [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)  
  
- [Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)  
  
 Pour plus d’informations sur COM, consultez [modèle COM (Component Object)](http://msdn.microsoft.com/library/windows/desktop/ms680573).  
  
## <a name="managing-the-lifetime-of-the-com-library"></a>La gestion de la durée de vie de la bibliothèque COM  
 Bien que l’utilisation de COM avec le Runtime d’accès concurrentiel suit les mêmes principes que tout autre mécanisme d’accès concurrentiel, les instructions suivantes peuvent vous aider à utiliser ces bibliothèques ensemble efficacement.  
  
-   Un thread doit appeler [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) avant d’utiliser la bibliothèque COM.  
  
-   Un thread peut appeler `CoInitializeEx` plusieurs fois, tant qu’il fournit les mêmes arguments à chaque appel.  
  
-   Pour chaque appel à `CoInitializeEx`, un thread doit également appeler [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715). En d’autres termes, les appels à `CoInitializeEx` et `CoUninitialize` doit être équilibrée.  
  
-   Pour basculer d’un thread cloisonné vers un autre, un thread doit complètement libérer la bibliothèque COM avant d’appeler `CoInitializeEx` avec la nouvelle spécification de threading.  
  
 Autres principes COM s’appliquent lorsque vous utilisez COM avec le Runtime d’accès concurrentiel. Par exemple, une application qui crée un objet dans un thread unique cloisonné (STA) et marshale l’objet à un autre cloisonnement doit également fournir une boucle de message pour traiter les messages entrants. Souvenez-vous aussi que marshaling d’objets entre des cloisonnements peut diminuer les performances.  
  
### <a name="using-com-with-the-parallel-patterns-library"></a>Utilisation de COM avec la bibliothèque de modèles parallèles  
 Lorsque vous utilisez COM avec un composant dans les modèles de bibliothèque parallèles (PPL), par exemple, un groupe de tâches ou un algorithme parallèle, appelez `CoInitializeEx` avant d’utiliser la bibliothèque COM pendant chaque tâche ou itération et appel `CoUninitialize` avant la fin de chaque tâche ou itération . L’exemple suivant montre comment gérer la durée de vie de la bibliothèque COM avec un [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objet.  
  
 [!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]  
  
 Il se peut que vous devez vous assurer que la bibliothèque COM est libérée correctement lorsqu’un tâche ou un algorithme parallèle est annulé ou lorsque le corps de la tâche lève une exception. Pour garantir que la tâche appelle `CoUninitialize` avant de quitter, utilisez un `try-finally` bloc ou *Resource Acquisition Is Initialization* modèle (RAII). L’exemple suivant utilise un `try-finally` bloc pour libérer la bibliothèque COM lorsque la tâche se termine ou est annulée, ou lorsqu’une exception est levée.  
  
 [!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]  
  
 L’exemple suivant utilise le modèle RAII pour définir le `CCoInitializer` (classe), qui gère la durée de vie de la bibliothèque COM dans une étendue donnée.  
  
 [!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]  
  
 Vous pouvez utiliser la `CCoInitializer` classe pour libérer automatiquement la bibliothèque COM lorsque la tâche se termine, comme suit.  
  
 [!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]  
  
 Pour plus d’informations sur l’annulation du Runtime d’accès concurrentiel, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).  
  
### <a name="using-com-with-asynchronous-agents"></a>Utilisation de COM avec les Agents asynchrones  

 Lorsque vous utilisez COM avec les agents asynchrones, appelez `CoInitializeEx` avant d’utiliser la bibliothèque COM dans le [Concurrency::agent :: Run](reference/agent-class.md#run) méthode pour votre agent. Appelez ensuite `CoUninitialize` avant la `run` retourne de la méthode. N’utilisez pas de routines de gestion COM dans le constructeur ou un destructeur de votre agent et ne substituez pas la [Concurrency::agent :: Start](reference/agent-class.md#start) ou [concurrency::agent :: fait](reference/agent-class.md#done) méthodes, car ces méthodes sont appelée à partir d’un autre thread que le `run` (méthode).  

  
 L’exemple suivant montre une classe de base de l’agent, nommée `CCoAgent`, qui gère la bibliothèque COM dans le `run` (méthode).  
  
 [!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]  
  
 Un exemple complet est fourni plus loin dans cette procédure pas à pas.  
  
### <a name="using-com-with-lightweight-tasks"></a>Utilisation de COM avec les tâches légères  
 Le document [du Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md) décrit le rôle des tâches légères dans le Runtime d’accès concurrentiel. Vous pouvez utiliser COM avec une tâche légère comme vous le feriez avec toute routine de thread que vous passez à la `CreateThread` fonction dans l’API Windows. L'exemple suivant le démontre.  
  
 [!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]  
  
## <a name="an-example-of-a-com-enabled-application"></a>Un exemple d’une Application COM  
 Cette section montre une application COM complète qui utilise le `IScriptControl` interface pour exécuter un script qui calcule le n<sup>th</sup> nombre de Fibonacci. Cet exemple appelle d’abord le script à partir du thread principal et utilise ensuite la bibliothèque de modèles parallèles et les agents pour appeler le script simultanément.  
  
 Considérez la fonction d’assistance suivante, `RunScriptProcedure`, qui appelle une procédure dans un `IScriptControl` objet.  
  
 [!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]  
  
 Le `wmain` fonction crée un `IScriptControl` d’objet, ajoute le code de script qui calcule le n<sup>th</sup> nombre de Fibonacci, puis appelle la `RunScriptProcedure` fonction à exécuter ce script.  
  
 [!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]  
  
### <a name="calling-the-script-from-the-ppl"></a>Appel du Script à partir de la bibliothèque de modèles parallèles  

 La fonction suivante, `ParallelFibonacci`, utilise le [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme pour appeler le script en parallèle. Cette fonction utilise la `CCoInitializer` classe pour gérer la durée de vie de la bibliothèque COM pendant chaque itération de la tâche.  

  
 [!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]  
  
 Pour utiliser le `ParallelFibonacci` fonctionne avec l’exemple, ajoutez le code suivant avant la `wmain` fonction renvoie.  
  
 [!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]  
  
### <a name="calling-the-script-from-an-agent"></a>Appel du Script à partir d’un Agent  
 L’exemple suivant illustre la `FibonacciScriptAgent` (classe), qui appelle une procédure de script pour calculer le n<sup>th</sup> nombre de Fibonacci. La `FibonacciScriptAgent` classe utilise message passant à recevoir du programme principal, valeurs d’entrée à la fonction de script. Le `run` méthode gère la durée de vie de la bibliothèque COM tout au long de la tâche.  
  
 [!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]  
  
 La fonction suivante, `AgentFibonacci`, crée plusieurs `FibonacciScriptAgent` des objets et utilise le message de transmission pour envoyer plusieurs valeurs d’entrée à ces objets.  
  
 [!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]  
  
 Pour utiliser le `AgentFibonacci` fonctionne avec l’exemple, ajoutez le code suivant avant la `wmain` fonction renvoie.  
  
 [!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]  
  
### <a name="the-complete-example"></a>Exemple complet  
 Le code suivant montre l’exemple complet, qui utilise des algorithmes parallèles et des agents asynchrones pour appeler une procédure de script qui calcule les nombres de Fibonacci.  
  
 [!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]  
  
 L’exemple produit la sortie suivante.  
  
```Output  
Main Thread:  
fib(15) = 610  
 
Parallel Fibonacci:  
fib(15) = 610  
fib(10) = 55  
fib(16) = 987  
fib(18) = 2584  
fib(11) = 89  
fib(17) = 1597  
fib(19) = 4181  
fib(12) = 144  
fib(13) = 233  
fib(14) = 377  
 
Agent Fibonacci:  
fib(30) = 832040  
fib(22) = 17711  
fib(10) = 55  
fib(12) = 144  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `parallel-scripts.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /EHsc parallel-scripts.cpp /link ole32.lib**  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas Runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)   
 [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)   
 [Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)   
 [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)

