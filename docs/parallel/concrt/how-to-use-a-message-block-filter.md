---
description: 'En savoir plus sur : Comment : utiliser un filtre de bloc de message'
title: 'Comment : utiliser un filtre de bloc de message'
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 3c07aa7f12ed952d5256ba8fc7f53b619edefb7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172586"
---
# <a name="how-to-use-a-message-block-filter"></a>Comment : utiliser un filtre de bloc de message

Ce document montre comment utiliser une fonction de filtre pour permettre à un bloc de message asynchrone d’accepter ou de rejeter un message en fonction de la charge utile de ce message.

Lorsque vous créez un objet de bloc de message tel qu’un [accès concurrentiel :: unbounded_buffer](reference/unbounded-buffer-class.md), un [accès concurrentiel :: Call](../../parallel/concrt/reference/call-class.md)ou un [Concurrency :: transformer](../../parallel/concrt/reference/transformer-class.md), vous pouvez fournir une *fonction de filtre* qui détermine si le bloc de message accepte ou rejette un message. Une fonction de filtre est un moyen utile de garantir qu’un bloc de message ne reçoit que certaines valeurs.

Les fonctions de filtre sont importantes car elles vous permettent de connecter des blocs de messages pour former des *réseaux de flux* de données. Dans un réseau de flux de données, les blocs de messages contrôlent le flux de données en traitant uniquement les messages qui répondent à des critères spécifiques. Comparez cela au modèle de contrôle de workflow, où le workflow de données est régulé à l’aide de structures de contrôle telles que des instructions conditionnelles, des boucles, etc.

Ce document fournit un exemple de base de l’utilisation d’un filtre de messages. Pour obtenir des exemples supplémentaires qui utilisent des filtres de messages et le modèle de flux de données pour connecter des blocs de messages, consultez [procédure pas à pas : création d’un agent de flux](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) de données et [procédure pas à pas : création d’un réseau Image-Processing](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

## <a name="example-count_primes-function"></a>Exemple : count_primes fonction

Considérons la fonction suivante, `count_primes` , qui illustre l’utilisation de base d’un bloc de message qui ne filtre pas les messages entrants. Le bloc de message ajoute des nombres premiers à un objet [std :: Vector](../../standard-library/vector-class.md) . La `count_primes` fonction envoie plusieurs numéros au bloc de message, reçoit les valeurs de sortie du bloc de message, puis imprime les nombres premiers dans la console.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

L' `transformer` objet traite toutes les valeurs d’entrée ; Toutefois, il ne requiert que les valeurs premières. Bien que l’application puisse être écrite de manière à ce que l’expéditeur du message envoie uniquement des nombres premiers, les exigences du récepteur du message ne peuvent pas toujours être connues.

## <a name="example-count_primes_filter-function"></a>Exemple : count_primes_filter fonction

La fonction suivante, `count_primes_filter` , effectue la même tâche que la `count_primes` fonction. Toutefois, l' `transformer` objet de cette version utilise une fonction de filtre pour accepter uniquement les valeurs premières. La fonction qui exécute l’action reçoit uniquement les nombres premiers ; par conséquent, il n’est pas nécessaire d’appeler la `is_prime` fonction.

Étant donné que l' `transformer` objet reçoit uniquement des nombres premiers, l' `transformer` objet lui-même peut contenir les nombres premiers. En d’autres termes, l' `transformer` objet de cet exemple n’est pas obligatoire pour ajouter les nombres premiers à l' `vector` objet.

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

L' `transformer` objet traite désormais uniquement les valeurs premières. Dans l’exemple précédent, l' `transformer` objet traite tous les messages. Par conséquent, l’exemple précédent doit recevoir le même nombre de messages qu’il envoie. Cet exemple utilise le résultat de la fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) pour déterminer le nombre de messages à recevoir de l' `transformer` objet. La `send` fonction retourne **`true`** lorsque la mémoire tampon du message accepte le message et **`false`** lorsque la mémoire tampon du message rejette le message. Par conséquent, le nombre de fois que la mémoire tampon du message accepte le message correspond au nombre de nombres premiers.

## <a name="example-finished-message-block-filter-code-sample"></a>Exemple : exemple de code de filtre de bloc de message terminé

L'exemple de code suivant illustre l'exemple complet. L’exemple appelle la `count_primes` fonction et la `count_primes_filter` fonction.

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `primes-filter.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc primes-Filter. cpp**

## <a name="robust-programming"></a>Programmation fiable

Une fonction de filtre peut être une fonction lambda, un pointeur de fonction ou un objet de fonction. Chaque fonction de filtre prend l’une des formes suivantes :

```Output
bool (T)
bool (T const &)
```

Pour éliminer la copie inutile des données, utilisez la deuxième forme lorsque vous avez un type d’agrégat qui est transmis par valeur.

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Procédure pas à pas : création d’un agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Procédure pas à pas : création d’un réseau Image-Processing](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer, classe](../../parallel/concrt/reference/transformer-class.md)
