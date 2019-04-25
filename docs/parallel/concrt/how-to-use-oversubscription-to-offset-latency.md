---
title: 'Procédure : Utiliser le surabonnement pour compenser la latence'
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: d74a081f71f044cab90a8e6fdc64530eaaf87ed8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159936"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Procédure : Utiliser le surabonnement pour compenser la latence

Le surabonnement peut améliorer l’efficacité globale de certaines applications qui contiennent des tâches qui ont une grande quantité de latence. Cette rubrique montre comment utiliser le surabonnement pour compenser la latence provoquée par la lecture des données à partir d’une connexion réseau.

## <a name="example"></a>Exemple

Cet exemple utilise le [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) pour télécharger des fichiers à partir de serveurs HTTP. Le `http_reader` dérive de la classe [concurrency::agent](../../parallel/concrt/reference/agent-class.md) et utilise passage de message pour lire de façon asynchrone les noms d’URL à télécharger.

Le `http_reader` classe utilise le [concurrency::task_group](reference/task-group-class.md) classe pour lire chaque fichier simultanément. Chaque tâche appelle le [Concurrency::Context :: Oversubscribe](reference/context-class.md#oversubscribe) méthode avec le `_BeginOversubscription` paramètre défini sur **true** pour activer le surabonnement dans le contexte actuel. Chaque tâche utilise ensuite Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md) et [CHttpFile](../../mfc/reference/chttpfile-class.md) classes pour télécharger le fichier. Enfin, chaque tâche appelle `Context::Oversubscribe` avec la `_BeginOversubscription` paramètre défini sur **false** pour désactiver le surabonnement.

Lorsque le surabonnement est activé, le runtime crée un thread supplémentaire dans lequel exécuter des tâches. Chacun de ces threads peut également augmenter le contexte actuel et ainsi créer des threads supplémentaires. Le `http_reader` classe utilise un [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objet pour limiter le nombre de threads utilisés par l’application. L’agent initialise la mémoire tampon avec un nombre fixe de valeurs de jeton. Pour chaque opération de téléchargement, l’agent lit une valeur de jeton à partir de la mémoire tampon avant l’opération démarre, puis réécrit cette valeur dans la mémoire tampon une fois l’opération terminée. Lorsque la mémoire tampon est vide, l’agent attend qu’une des opérations de téléchargement à écrire une valeur dans la mémoire tampon.

L’exemple suivant limite le nombre de tâches simultanées à deux fois le nombre de threads matériels disponibles. Cette valeur est un bon point de départ à utiliser lorsque vous testez le surabonnement. Vous pouvez utiliser une valeur qui correspond à un environnement de traitement particulier ou modifier cette valeur pour répondre à la charge de travail de façon dynamique.

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

Cet exemple produit la sortie suivante sur un ordinateur qui a quatre processeurs :

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

L’exemple peut s’exécuter plus rapidement lorsque le surabonnement est activé, car des tâches supplémentaires s’exécuter pendant que les autres tâches attendent qu’une opération latente se termine.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `download-oversubscription.cpp` et puis exécutez un de ces commandes dans un **invite de commandes Visual Studio** fenêtre.

**cl.exe /EHsc /MD /D "_AFXDLL" download-oversubscription.cpp**

**CL.exe /EHsc/MT download-oversubscription.cpp**

## <a name="robust-programming"></a>Programmation fiable

Désactivez toujours le surabonnement une fois que vous n’avez plus besoin. Considérez une fonction qui ne gère pas une exception est levée par une autre fonction. Si vous ne désactivez pas le surabonnement avant le retour de la fonction, tout travail parallèle supplémentaire sera également manquer d’abonnements pour le contexte actuel.

Vous pouvez utiliser la *Resource Acquisition Is Initialization* modèle (RAII) pour limiter le surabonnement à une portée donnée. Dans le modèle RAII, une structure de données est allouée sur la pile. Cette structure de données initialise ou acquiert une ressource lorsqu’il est créé et détruit ou libère cette ressource lorsque la structure de données est détruite. Le modèle RAII garantit que le destructeur est appelé avant la fermeture de la portée englobante. Par conséquent, la ressource est gérée correctement lorsqu’une exception est levée ou lorsqu’une fonction contient plusieurs `return` instructions.

L’exemple suivant définit une structure qui est nommée `scoped_blocking_signal`. Le constructeur de la `scoped_blocking_signal` structure Active le surabonnement et le destructeur désactive le surabonnement.

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

L’exemple suivant modifie le corps de la `download` méthode à utiliser RAII pour s’assurer que le surabonnement est désactivé avant le retour de la fonction. Cette technique garantit que le `download` méthode est protégée contre les exceptions.

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Contextes](../../parallel/concrt/contexts.md)<br/>
[Context::Oversubscribe, méthode](reference/context-class.md#oversubscribe)
