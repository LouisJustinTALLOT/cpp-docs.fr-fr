---
title: 'Procédure pas à pas : Utilisation de l’runtime d’accès concurrentiel dans une application COM'
ms.date: 04/25/2019
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: 23488522287ab5767c88cd3a3e90c09392634f46
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512099"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Procédure pas à pas : Utilisation de l’runtime d’accès concurrentiel dans une application COM

Ce document montre comment utiliser le runtime d’accès concurrentiel dans une application qui utilise le modèle COM (Component Object Model).

## <a name="prerequisites"></a>Prérequis

Lisez les documents suivants avant de commencer cette procédure pas à pas:

- [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)

- [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)

- [Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

Pour plus d’informations sur COM, consultez [modèle COM (Component Object Model)](/windows/win32/com/component-object-model--com--portal).

## <a name="managing-the-lifetime-of-the-com-library"></a>Gestion de la durée de vie de la bibliothèque COM

Bien que l’utilisation de COM avec le runtime d’accès concurrentiel respecte les mêmes principes que tout autre mécanisme d’accès concurrentiel, les instructions suivantes peuvent vous aider à utiliser ces bibliothèques ensemble efficacement.

- Un thread doit appeler [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) avant d’utiliser la bibliothèque com.

- Un thread peut appeler `CoInitializeEx` plusieurs fois tant qu’il fournit les mêmes arguments à chaque appel.

- Pour chaque appel à `CoInitializeEx`, un thread doit également appeler [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize). En d’autres termes, les `CoInitializeEx` appels `CoUninitialize` à et doivent être équilibrés.

- Pour passer d’un cloisonnement de thread à un autre, un thread doit libérer complètement la bibliothèque com avant `CoInitializeEx` d’appeler avec la nouvelle spécification de Threading.

D’autres principes COM s’appliquent lorsque vous utilisez COM avec l’runtime d’accès concurrentiel. Par exemple, une application qui crée un objet dans un thread cloisonné (STA) et marshale cet objet vers un autre cloisonnement doit également fournir une boucle de message pour traiter les messages entrants. Souvenez-vous également que le marshaling d’objets entre les cloisonnements peut réduire les performances.

### <a name="using-com-with-the-parallel-patterns-library"></a>Utilisation de COM avec la bibliothèque de modèles parallèles

Quand vous utilisez com avec un composant dans la bibliothèque de modèles parallèles (PPL), par exemple un groupe de tâches ou un algorithme parallèle, appelez `CoInitializeEx` avant d’utiliser la bibliothèque com pendant chaque tâche ou itération, et appelez `CoUninitialize` avant la fin de chaque tâche ou itération. . L’exemple suivant montre comment gérer la durée de vie de la bibliothèque COM avec un objet [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) .

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

Vous devez vous assurer que la bibliothèque COM est correctement libérée lors de l’annulation d’une tâche ou d’un algorithme parallèle ou lorsque le corps de la tâche lève une exception. Pour garantir que la tâche appelle `CoUninitialize` avant de se fermer, utilisez un `try-finally` modèle de bloc ou le modèle RAII ( *Resource Acquisition Is Initialization* ). L’exemple suivant utilise un `try-finally` bloc pour libérer la bibliothèque COM lorsque la tâche se termine ou est annulée, ou lorsqu’une exception est levée.

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

L’exemple suivant utilise le modèle RAII pour définir la `CCoInitializer` classe, qui gère la durée de vie de la bibliothèque com dans une étendue donnée.

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

Vous pouvez utiliser la `CCoInitializer` classe pour libérer automatiquement la bibliothèque COM lorsque la tâche se termine, comme suit.

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

Pour plus d’informations sur l’annulation dans la runtime d’accès concurrentiel, consultez [annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md).

### <a name="using-com-with-asynchronous-agents"></a>Utilisation de COM avec des agents asynchrones

Quand vous utilisez com avec des agents asynchrones `CoInitializeEx` , appelez avant d’utiliser la bibliothèque com dans la méthode Concurrency [:: agent:: Run](reference/agent-class.md#run) pour votre agent. Appelez `CoUninitialize` ensuite avant que `run` la méthode ne retourne. N’utilisez pas de routines de gestion COM dans le constructeur ou le destructeur de votre agent, et ne substituez pas l' [accès concurrentiel:: agent:: Start](reference/agent-class.md#start) ou Concurrency [:: agent::d une](reference/agent-class.md#done) méthode, car ces méthodes sont appelées à partir d’un thread différent de celui de la `run` méthode.

L’exemple suivant montre une classe d’agent de base `CCoAgent`, nommée, qui gère la bibliothèque COM `run` dans la méthode.

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

Un exemple complet est fourni plus loin dans cette procédure pas à pas.

### <a name="using-com-with-lightweight-tasks"></a>Utilisation de COM avec des tâches légères

Le document [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md) décrit le rôle des tâches légères dans le runtime d’accès concurrentiel. Vous pouvez utiliser com avec une tâche légère, comme vous le feriez avec n’importe quelle routine de thread `CreateThread` que vous transmettez à la fonction dans l’API Windows. L'exemple suivant le démontre.

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>Exemple d’application COM

Cette section présente une application com complète qui utilise l' `IScriptControl` interface pour exécuter un script qui calcule le n<sup>ième</sup> nombre de Fibonacci. Cet exemple appelle d’abord le script du thread principal, puis utilise la PPL et les agents pour appeler le script simultanément.

Considérez la fonction d’assistance suivante `RunScriptProcedure`,, qui appelle une procédure dans `IScriptControl` un objet.

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

La `wmain` fonction crée un `IScriptControl` objet, y ajoute le code de script qui calcule le n<sup>ième</sup> nombre de Fibonacci, puis appelle `RunScriptProcedure` la fonction pour exécuter ce script.

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>Appel du script à partir de la bibliothèque de modèles parallèles

La fonction suivante, `ParallelFibonacci`, utilise l’algorithme Concurrency [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour appeler le script en parallèle. Cette fonction utilise la `CCoInitializer` classe pour gérer la durée de vie de la bibliothèque com lors de chaque itération de la tâche.

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

Pour utiliser la `ParallelFibonacci` fonction avec l’exemple, ajoutez le code suivant avant le `wmain` retour de la fonction.

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>Appel du script à partir d’un agent

L’exemple suivant illustre la `FibonacciScriptAgent` classe, qui appelle une procédure de script pour calculer le n<sup>ième</sup> nombre de Fibonacci. La `FibonacciScriptAgent` classe utilise le passage de messages pour recevoir, du programme principal, des valeurs d’entrée à la fonction de script. La `run` méthode gère la durée de vie de la bibliothèque com tout au long de la tâche.

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

La fonction suivante, `AgentFibonacci`, crée plusieurs `FibonacciScriptAgent` objets et utilise le passage de message pour envoyer plusieurs valeurs d’entrée à ces objets.

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

Pour utiliser la `AgentFibonacci` fonction avec l’exemple, ajoutez le code suivant avant le `wmain` retour de la fonction.

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>Exemple complet

Le code suivant illustre l’exemple complet, qui utilise des algorithmes parallèles et des agents asynchrones pour appeler une procédure de script qui calcule les nombres de Fibonacci.

[!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]

L’exemple produit l’exemple de sortie suivant.

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

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le `parallel-scripts.cpp` dans un fichier nommé, puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL. exe/EHsc Parallel-scripts. cpp/Link ole32. lib**

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)<br/>
[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
