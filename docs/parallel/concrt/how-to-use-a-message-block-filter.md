---
title: 'Comment : utiliser un filtre de bloc de Message | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92de322142e56eb9907da2e19d350c3af9c8a7d9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688269"
---
# <a name="how-to-use-a-message-block-filter"></a>Comment : utiliser un filtre de bloc de message
Ce document montre comment utiliser une fonction de filtre pour permettre à un bloc de message asynchrone accepter ou rejeter un message en fonction de la charge utile de ce message.  
  
 Lorsque vous créez un objet de bloc de message comme un [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), un [concurrency::call](../../parallel/concrt/reference/call-class.md), ou un [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md), vous pouvez fournir un *fonction filter* qui détermine si le bloc de message accepte ou rejette un message. Une fonction de filtre est un moyen utile pour garantir qu’un bloc de message reçoit uniquement certaines valeurs.  
  
 Fonctions de filtrage sont importantes car elles vous permettent de connecter des blocs de messages pour former *des réseaux de flux de données*. Dans un réseau de flux de données, les blocs de messages contrôlent le flux de données en traitant uniquement les messages qui répondent aux critères spécifiques. Comparez cela au modèle de flux de contrôle, lorsque le flux de données est organisée à l’aide de structures de contrôle telles que des instructions conditionnelles, les boucles et ainsi de suite.  
  
 Ce document fournit un exemple simple d’utilisation d’un filtre de messages. Pour obtenir des exemples supplémentaires qui utilisent des filtres de messages et le modèle de flux de données à connecter des blocs de message, consultez [procédure pas à pas : création d’un Agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) et [procédure pas à pas : création d’un réseau de traitement d’Image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md) .  
  
## <a name="example"></a>Exemple  
 Considérez la fonction suivante, `count_primes`, qui illustre l’utilisation de base d’un bloc de message qui ne filtre pas les messages entrants. Le bloc de message ajoute des nombres premiers à un [std::vector](../../standard-library/vector-class.md) objet. Le `count_primes` fonction envoie plusieurs nombres pour le bloc de message, reçoit les valeurs de sortie du bloc de message et imprime ces nombres premiers dans la console.  
  
 [!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]  
  
 Le `transformer` objet traite les valeurs toutes les entrées ; Toutefois, il requiert uniquement les valeurs qui sont les premiers. Bien que l’application peut être écrite pour que l’expéditeur du message envoie uniquement des nombres premiers, la configuration requise du récepteur du message ne peut pas toujours être connue.  
  
## <a name="example"></a>Exemple  
 La fonction suivante, `count_primes_filter`, effectue la même tâche que la `count_primes` (fonction). Toutefois, le `transformer` objet dans cette version utilise une fonction de filtre pour accepter uniquement les valeurs qui sont les premiers. La fonction qui exécute l’action reçoit uniquement des nombres premiers. Par conséquent, il n’a pas d’appeler le `is_prime` (fonction).  
  
 Étant donné que la `transformer` objet reçoit uniquement des nombres premiers, la `transformer` objet lui-même peut contenir des nombres premiers. En d’autres termes, le `transformer` objet dans cet exemple n’est pas requis pour ajouter les nombres premiers à la `vector` objet.  
  
 [!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]  
  
 Le `transformer` objet traite désormais uniquement les valeurs qui sont les premiers. Dans l’exemple précédent, `transformer` objet traite tous les messages. Par conséquent, l’exemple précédent doit recevoir le même nombre de messages qu’il envoie. Cet exemple utilise le résultat de la [concurrency::send](reference/concurrency-namespace-functions.md#send) fonction pour déterminer combien de messages à recevoir de la `transformer` objet. Le `send` fonction renvoie `true` lorsque le tampon de messages accepte le message et `false` lorsque le tampon de messages rejette le message. Par conséquent, le nombre de fois que le tampon de messages accepte le message correspond au nombre de nombres premiers.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant illustre l'exemple complet. L’exemple appelle la `count_primes` (fonction) et `count_primes_filter` (fonction).  
  
 [!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `primes-filter.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /EHsc primes-Filter.cpp**  
  
## <a name="robust-programming"></a>Programmation fiable  
 Une fonction de filtre peut être une fonction lambda, un pointeur de fonction ou un objet de fonction. Chaque fonction de filtre prend l’une des formes suivantes :  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 Pour éliminer la copie inutile des données, utilisez la deuxième forme lorsque vous avez un type d’agrégation qui est transmis par valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)   
 [Procédure pas à pas : Création d’un Agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [Procédure pas à pas : Création d’un réseau de traitement d’Image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [transformer, classe](../../parallel/concrt/reference/transformer-class.md)
