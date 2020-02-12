---
title: 'Comment : utiliser le surabonnement pour compenser la latence'
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: 02c72e7b7f0e3ec9727504d62341d945dcd0d957
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141937"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Comment : utiliser le surabonnement pour compenser la latence

Le surabonnement peut améliorer l’efficacité globale de certaines applications qui contiennent des tâches qui présentent une latence élevée. Cette rubrique explique comment utiliser le surabonnement pour compenser la latence provoquée par la lecture de données à partir d’une connexion réseau.

## <a name="example"></a>Exemple

Cet exemple utilise la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) pour télécharger des fichiers à partir de serveurs http. La classe `http_reader` dérive de [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md) et utilise le passage de messages pour lire de façon asynchrone les noms d’URL à télécharger.

La classe `http_reader` utilise la classe [Concurrency :: task_group](reference/task-group-class.md) pour lire simultanément chaque fichier. Chaque tâche appelle la méthode [Concurrency :: Context :: Oversubscribe](reference/context-class.md#oversubscribe) avec le paramètre `_BeginOversubscription` ayant la valeur **true** pour activer le surabonnement dans le contexte actuel. Chaque tâche utilise ensuite les classes Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md) et [CHttpFile](../../mfc/reference/chttpfile-class.md) pour télécharger le fichier. Enfin, chaque tâche appelle `Context::Oversubscribe` avec le paramètre `_BeginOversubscription` ayant la valeur **false** pour désactiver le surabonnement.

Lorsque le surabonnement est activé, le runtime crée un thread supplémentaire dans lequel exécuter des tâches. Chacun de ces threads peut également surabonner le contexte actuel et créer ainsi des threads supplémentaires. La classe `http_reader` utilise un objet [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) pour limiter le nombre de threads utilisés par l’application. L’agent initialise la mémoire tampon avec un nombre fixe de valeurs de jeton. Pour chaque opération de téléchargement, l’agent lit une valeur de jeton à partir de la mémoire tampon avant le démarrage de l’opération, puis réécrit cette valeur dans la mémoire tampon une fois l’opération terminée. Lorsque la mémoire tampon est vide, l’agent attend l’une des opérations de téléchargement pour réécrire une valeur dans la mémoire tampon.

L’exemple suivant limite le nombre de tâches simultanées à deux fois le nombre de threads matériels disponibles. Cette valeur est un bon point de départ à utiliser lorsque vous expérimentez le surabonnement. Vous pouvez utiliser une valeur qui correspond à un environnement de traitement particulier ou modifier dynamiquement cette valeur pour répondre à la charge de travail réelle.

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

Cet exemple produit la sortie suivante sur un ordinateur doté de quatre processeurs :

```Output
Downloading http://www.adatum.com/...
Downloading http://www.adventure-works.com/...
Downloading http://www.alpineskihouse.com/...
Downloading http://www.cpandl.com/...
Downloading http://www.cohovineyard.com/...
Downloading http://www.cohowinery.com/...
Downloading http://www.cohovineyardandwinery.com/...
Downloading http://www.contoso.com/...
Downloading http://www.consolidatedmessenger.com/...
Downloading http://www.fabrikam.com/...
Downloading http://www.fourthcoffee.com/...
Downloading http://www.graphicdesigninstitute.com/...
Downloading http://www.humongousinsurance.com/...
Downloading http://www.litwareinc.com/...
Downloading http://www.lucernepublishing.com/...
Downloading http://www.margiestravel.com/...
Downloading http://www.northwindtraders.com/...
Downloading http://www.proseware.com/...
Downloading http://www.fineartschool.net...
Downloading http://www.tailspintoys.com/...
Downloaded 1801040 bytes in 3276 ms.
```

L’exemple peut s’exécuter plus rapidement lorsque le surabonnement est activé, car des tâches supplémentaires sont exécutées alors que d’autres tâches attendent qu’une opération latente se termine.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `download-oversubscription.cpp` puis exécutez l’une des commandes suivantes dans une fenêtre d' **invite de commandes Visual Studio** .

```cmd
cl.exe /EHsc /MD /D "_AFXDLL" download-oversubscription.cpp
cl.exe /EHsc /MT download-oversubscription.cpp
```

## <a name="robust-programming"></a>Programmation fiable

Désactivez toujours le surabonnement une fois que vous n’en avez plus besoin. Prenons l’exemple d’une fonction qui ne gère pas une exception levée par une autre fonction. Si vous ne désactivez pas le surabonnement avant le retour de la fonction, tout travail parallèle supplémentaire surabonnera également le contexte actuel.

Vous pouvez utiliser le modèle RAII ( *Resource Acquisition Is Initialization* ) pour limiter le surabonnement à une étendue donnée. Dans le modèle RAII, une structure de données est allouée sur la pile. Cette structure de données Initialise ou acquiert une ressource lors de sa création et détruit ou libère cette ressource lorsque la structure de données est détruite. Le modèle RAII garantit que le destructeur est appelé avant la sortie de la portée englobante. Par conséquent, la ressource est correctement gérée lorsqu’une exception est levée ou lorsqu’une fonction contient plusieurs instructions `return`.

L’exemple suivant définit une structure nommée `scoped_blocking_signal`. Le constructeur de la structure `scoped_blocking_signal` active le surabonnement et le destructeur désactive le surabonnement.

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

L’exemple suivant modifie le corps de la méthode `download` pour utiliser RAII afin de garantir que le surabonnement est désactivé avant le retour de la fonction. Cette technique garantit que la méthode `download` est sécurisée contre les exceptions.

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Contextes](../../parallel/concrt/contexts.md)<br/>
[Context :: Oversubscribe, méthode](reference/context-class.md#oversubscribe)
