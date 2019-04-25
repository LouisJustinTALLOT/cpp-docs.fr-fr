---
title: 'Procédure : Utiliser un filtre de bloc de Message'
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 1bfa11953d27dc7e013e715b3f58111f124caeaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321936"
---
# <a name="how-to-use-a-message-block-filter"></a>Procédure : Utiliser un filtre de bloc de Message

Ce document montre comment utiliser une fonction de filtre pour permettre à un bloc de message asynchrone accepter ou rejeter un message en fonction de la charge utile de ce message.

Lorsque vous créez un objet de bloc de message comme un [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), un [concurrency::call](../../parallel/concrt/reference/call-class.md), ou un [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md), vous pouvez fournir un *fonction filter* qui détermine si le bloc de message accepte ou rejette un message. Une fonction de filtre est un moyen utile pour garantir qu’un bloc de message reçoit uniquement certaines valeurs.

Fonctions de filtre sont importantes, car ils vous permettent de connecter des blocs de messages pour former *les réseaux de flux de données*. Dans un réseau de flux de données, les blocs de messages contrôlent le flux de données en traitant uniquement les messages qui répondent aux critères spécifiques. Comparez cela au modèle de flux de contrôle, lorsque le flux de données est organisée à l’aide de structures de contrôle telles que les instructions conditionnelles, des boucles et ainsi de suite.

Ce document fournit un exemple de base de l’utilisation d’un filtre de messages. Pour obtenir des exemples supplémentaires qui utilisent des filtres de messages et le modèle de flux de données à connecter des blocs de message, consultez [procédure pas à pas : Création d’un Agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) et [procédure pas à pas : Création d’un réseau de traitement d’Image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

## <a name="example"></a>Exemple

Considérez la fonction suivante, `count_primes`, qui illustre l’utilisation de base d’un bloc de message qui ne filtre pas les messages entrants. Le bloc de message ajoute des nombres premiers à un [std::vector](../../standard-library/vector-class.md) objet. Le `count_primes` fonction envoie plusieurs numéros au bloc de message, reçoit les valeurs de sortie à partir du bloc de message et imprime ces nombres premiers dans la console.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

Le `transformer` objet traite les valeurs toutes les entrées ; Toutefois, il requiert uniquement les valeurs qui sont les premiers. Bien que l’application peut être écrite afin que l’expéditeur du message envoie uniquement des nombres premiers, la configuration requise du récepteur de message ne peut pas toujours être connue.

## <a name="example"></a>Exemple

La fonction suivante, `count_primes_filter`, effectue la même tâche que le `count_primes` (fonction). Toutefois, le `transformer` objet dans cette version utilise une fonction de filtre pour accepter uniquement les valeurs qui sont les premiers. La fonction qui exécute l’action reçoit uniquement les nombres premiers. Par conséquent, il n’a pas d’appeler le `is_prime` (fonction).

Étant donné que le `transformer` objet reçoit uniquement les nombres premiers, la `transformer` objet lui-même peut contenir des nombres premiers. En d’autres termes, le `transformer` objet dans cet exemple n’est pas obligatoire pour ajouter les nombres premiers à la `vector` objet.

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

Le `transformer` objet traite désormais uniquement les valeurs qui sont les premiers. Dans l’exemple précédent, `transformer` objet traite tous les messages. Par conséquent, l’exemple précédent doit recevoir le même nombre de messages qu’il envoie. Cet exemple utilise le résultat de la [concurrency::send](reference/concurrency-namespace-functions.md#send) fonction permettant de déterminer combien de messages à recevoir de le `transformer` objet. Le `send` fonction renvoie **true** lorsque le tampon de messages accepte le message et **false** lorsque le tampon de messages rejette le message. Par conséquent, le nombre de fois que le tampon de messages accepte le message correspond au nombre de nombres premiers.

## <a name="example"></a>Exemple

L'exemple de code suivant illustre l'exemple complet. L’exemple appelle à la fois le `count_primes` (fonction) et le `count_primes_filter` (fonction).

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `primes-filter.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**cl.exe /EHsc primes-filter.cpp**

## <a name="robust-programming"></a>Programmation fiable

Une fonction de filtre peut être une fonction lambda, un pointeur de fonction ou un objet de fonction. Chaque fonction de filtre prend l’une des formes suivantes :

```Output
bool (T)
bool (T const &)
```

Pour éliminer la copie inutile des données, utilisez la deuxième forme lorsque vous avez un type d’agrégat qui est transmis par valeur.

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Procédure pas à pas : création d’un agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer, classe](../../parallel/concrt/reference/transformer-class.md)
