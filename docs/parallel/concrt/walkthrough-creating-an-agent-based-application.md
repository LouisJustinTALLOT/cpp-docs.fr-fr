---
title: 'Procédure pas à pas : création d’une application basée sur un agent'
ms.date: 11/04/2016
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 1d5e7ed085481b714423760cebf2984084626645
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509342"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Procédure pas à pas : création d’une application basée sur un agent

Cette rubrique décrit comment créer une application basée sur un agent de base. Dans cette procédure pas à pas, vous pouvez créer un agent qui lit des données à partir d’un fichier texte en mode asynchrone. L’application utilise l’algorithme de somme de contrôle Adler-32 pour calculer la somme de contrôle du contenu de ce fichier.

## <a name="prerequisites"></a>Prérequis

Vous devez comprendre les rubriques suivantes pour effectuer cette procédure pas à pas :

- [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)

- [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> Sections

Cette procédure pas à pas montre comment effectuer les tâches suivantes :

- [Créer l'application console](#createapplication)

- [Création de la classe file_reader](#createagentclass)

- [À l’aide de la classe file_reader dans l’Application](#useagentclass)

##  <a name="createapplication"></a> Création de l’Application de Console

Cette section montre comment créer une application console Visual C++ qui référence les fichiers d’en-tête qui utilise le programme.

#### <a name="to-create-a-visual-c-application-by-using-the-win32-console-application-wizard"></a>Pour créer une application Visual C++ à l’aide de l’Assistant d’Application Console Win32

1. Sur le **fichier** menu, cliquez sur **New**, puis cliquez sur **projet** pour afficher le **nouveau projet** boîte de dialogue.

1. Dans le **nouveau projet** boîte de dialogue, sélectionnez le **Visual C++** nœud dans le **types de projets** volet, puis sélectionnez **Application Console Win32** dans le **modèles** volet. Tapez un nom pour le projet, par exemple, `BasicAgent`, puis cliquez sur **OK** pour afficher le **Assistant Application Console Win32**.

1. Dans le **Assistant Application Console Win32** boîte de dialogue, cliquez sur **Terminer**.

1. Dans stdafx.h, ajoutez le code suivant.

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Le fichier d’en-tête agents.h contient la fonctionnalité de la [concurrency::agent](../../parallel/concrt/reference/agent-class.md) classe.

1. Vérifiez que l’application a été créée avec succès en créant et son exécution. Pour générer l’application, dans le **Build** menu, cliquez sur **générer la Solution**. Si l’application est générée avec succès, exécutez l’application en cliquant sur **démarrer le débogage** sur le **déboguer** menu.

[[Haut](#top)]

##  <a name="createagentclass"></a> Création de la classe file_reader

Cette section montre comment créer la `file_reader` classe. Le runtime planifie chaque agent pour effectuer le travail dans son propre contexte. Par conséquent, vous pouvez créer un agent qui exécute une tâche de façon synchrone, mais qui interagit avec d’autres composants de façon asynchrone. Le `file_reader` classe lit les données à partir d’un fichier d’entrée donné et envoie des données à partir de ce fichier à un composant cible donné.

#### <a name="to-create-the-filereader-class"></a>Pour créer la classe file_reader

1. Ajouter un nouveau fichier d’en-tête C++ à votre projet. Pour ce faire, cliquez sur le **fichiers d’en-tête** nœud **l’Explorateur de solutions**, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**. Dans le **modèles** volet, sélectionnez **fichier d’en-tête (.h)**. Dans le **ajouter un nouvel élément** boîte de dialogue, tapez `file_reader.h` dans le **nom** , puis cliquez sur **ajouter**.

1. Dans file_reader.h, ajoutez le code suivant.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. Dans file_reader.h, créez une classe nommée `file_reader` qui dérive de `agent`.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Ajoutez les membres de données suivants à la `private` section de votre classe.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   Le `_file_name` membre est le nom de fichier que l’agent lit. Le `_target` membre est un [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) que l’agent écrit le contenu du fichier à l’objet. Le `_error` membre conserve toute erreur qui se produit pendant la durée de vie de l’agent.

1. Ajoutez le code suivant pour le `file_reader` constructeurs pour la `public` section de la `file_reader` classe.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Chaque surcharge de constructeur définit la `file_reader` membres de données. La surcharge de constructeur deuxième et troisième permet à votre application d’utiliser un planificateur spécifique avec votre agent. La première surcharge utilise le planificateur par défaut avec votre agent.

1. Ajouter le `get_error` méthode à la section publique de la `file_reader` classe.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   Le `get_error` méthode récupère toute erreur qui se produit pendant la durée de vie de l’agent.

1. Implémentez le [Concurrency::agent :: Run](reference/agent-class.md#run) méthode dans la `protected` section de votre classe.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

Le `run` méthode ouvre le fichier et lit les données à partir de celui-ci. Le `run` méthode utilise la gestion des exceptions pour capturer les erreurs qui se produisent pendant le traitement du fichier.

   Chaque fois que cette méthode lit les données à partir du fichier, il appelle le [concurrency::asend](reference/concurrency-namespace-functions.md#asend) (fonction) pour envoyer ces données à la mémoire tampon cible. Il envoie la chaîne vide à sa mémoire tampon cible pour indiquer la fin du traitement.

L’exemple suivant montre le contenu complet de file_reader.h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Haut](#top)]

##  <a name="useagentclass"></a> À l’aide de la classe file_reader dans l’Application

Cette section montre comment utiliser le `file_reader` classe pour lire le contenu d’un fichier texte. Il montre également comment créer un [concurrency::call](../../parallel/concrt/reference/call-class.md) objet qui reçoit les données de ce fichier et calcule sa somme de contrôle Adler-32.

#### <a name="to-use-the-filereader-class-in-your-application"></a>Pour utiliser la classe file_reader dans votre application

1. Dans BasicAgent.cpp, ajoutez le code suivant `#include` instruction.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. Dans BasicAgent.cpp, ajoutez le code suivant `using` directives.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. Dans le `_tmain` de fonction, créez un [concurrency::event](../../parallel/concrt/reference/event-class.md) objet qui signale la fin du traitement.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Créer un `call` objet qui met à jour de la somme de contrôle lorsqu’il reçoit des données.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Cela `call` objet définit également la `event` lorsqu’il reçoit la chaîne vide pour signaler la fin du traitement de l’objet.

1. Créer un `file_reader` objet qui lit à partir du fichier test.txt et écrit le contenu de ce fichier à la `call` objet.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Démarrez l’agent et attendez qu’elle se termine.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Attendez que le `call` objet recevoir toutes les données et de fin.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Vérifiez le lecteur de fichier pour les erreurs. Si aucune erreur ne s’est produite, calculer la somme Adler-32 finale et imprimer la somme est égale à la console.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

L’exemple suivant montre le fichier BasicAgent.cpp complet.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Haut](#top)]

## <a name="sample-input"></a>Exemple d’entrée

Il s’agit de l’exemple de contenu du fichier d’entrée text.txt :

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Résultat de l'exemple

Lorsqu’il est utilisé avec l’exemple d’entrée, ce programme produit la sortie suivante :

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Programmation fiable

Pour empêcher l’accès simultané aux membres de données, nous vous recommandons d’ajouter les méthodes qui effectuent le travail à la `protected` ou `private` section de votre classe. Ajoutez uniquement des méthodes qui envoient ou reçoivent des messages vers ou à partir de l’agent à le `public` section de votre classe.

Appelez toujours le [concurrency::agent :: fait](reference/agent-class.md#done) méthode pour déplacer votre agent vers l’état terminé. En règle générale, vous appelez cette méthode avant le retour de la `run` (méthode).

## <a name="next-steps"></a>Étapes suivantes

Pour un autre exemple d’une application basée sur agent, consultez [procédure pas à pas : à l’aide de la classe join pour empêcher l’interblocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Procédure pas à pas : utilisation de la classe join pour empêcher l’interblocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)

