---
title: 'Procédure pas à pas : création d’une application basée sur un agent'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 4e67b3fc3363955ae02973847912c021eca95ded
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219480"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Procédure pas à pas : création d’une application basée sur un agent

Cette rubrique explique comment créer une application de base basée sur un agent. Dans cette procédure pas à pas, vous pouvez créer un agent qui lit les données d’un fichier texte de façon asynchrone. L’application utilise l’algorithme de somme de contrôle Adler-32 pour calculer la somme de contrôle du contenu de ce fichier.

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez comprendre les rubriques suivantes :

- [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)

- [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Sections

Cette procédure pas à pas montre comment effectuer les tâches suivantes :

- [Créer l'application console](#createapplication)

- [Création de la classe file_reader](#createagentclass)

- [Utilisation de la classe file_reader dans l’application](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>Création de l’application console

Cette section montre comment créer une application console C++ qui fait référence aux fichiers d’en-tête utilisés par le programme. Les étapes initiales varient en fonction de la version de Visual Studio que vous utilisez. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Pour créer une application console C++ dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur ** C++ **, **Plateforme** sur **Windows** et **Type de projet** sur **Console**.

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez `BasicAgent` comme nom pour le projet, puis spécifiez l’emplacement du projet si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet.

1. Cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions**, puis choisissez **Propriétés**. Sous **Propriétés de configuration**, en-têtes précompilés en-têtes précompilés  >  **C/C++**  >  **Precompiled Headers**  >  **Precompiled header** , choisissez **créer**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Pour créer une application console C++ dans Visual Studio 2017 et versions antérieures

1. Dans le menu **fichier** , cliquez sur **nouveau**, puis sur **projet** pour afficher la boîte de dialogue **nouveau projet** .

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez le nœud **Visual C++** dans le volet **types de projets** , puis sélectionnez **application console Win32** dans le volet **modèles** . Tapez un nom pour le projet, par exemple, `BasicAgent` , puis cliquez sur **OK** pour afficher l **'Assistant Application console Win32**.

1. Dans la boîte de dialogue **Assistant Application console Win32** , cliquez sur **Terminer**.

::: moniker-end

1. Dans *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures), ajoutez le code suivant :

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Le fichier d’en-tête agents. h contient les fonctionnalités de la classe [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md) .

1. Vérifiez que l’application a été créée avec succès en la générant et en l’exécutant. Pour générer l’application, dans le menu **générer** , cliquez sur **générer la solution**. Si l’application est générée avec succès, exécutez l’application en cliquant sur **Démarrer le débogage** dans le menu **Déboguer** .

[[Haut](#top)]

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>Création de la classe file_reader

Cette section montre comment créer la `file_reader` classe. Le runtime planifie chaque agent pour qu’il effectue le travail dans son propre contexte. Par conséquent, vous pouvez créer un agent qui effectue le travail de façon synchrone, mais interagit de façon asynchrone avec d’autres composants. La `file_reader` classe lit les données d’un fichier d’entrée donné et envoie les données de ce fichier à un composant cible donné.

#### <a name="to-create-the-file_reader-class"></a>Pour créer la classe file_reader

1. Ajoutez un nouveau fichier d’en-tête C++ à votre projet. Pour ce faire, cliquez avec le bouton droit sur le nœud **fichiers d’en-tête** dans **Explorateur de solutions**, cliquez sur **Ajouter**, puis sur **nouvel élément**. Dans le volet **modèles** , sélectionnez **fichier d’en-tête (. h)**. Dans la boîte de dialogue **Ajouter un nouvel élément** , tapez `file_reader.h` dans la zone **nom** , puis cliquez sur **Ajouter**.

1. Dans file_reader. h, ajoutez le code suivant.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. Dans file_reader. h, créez une classe nommée `file_reader` qui dérive de `agent` .

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Ajoutez les membres de données suivants à la **`private`** section de votre classe.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   Le `_file_name` membre est le nom de fichier à partir duquel l’agent lit. Le `_target` membre est un objet [Concurrency :: ITarget](../../parallel/concrt/reference/itarget-class.md) sur lequel l’agent écrit le contenu du fichier. Le `_error` membre contient une erreur qui se produit pendant la durée de vie de l’agent.

1. Ajoutez le code suivant pour les `file_reader` constructeurs à la **`public`** section de la `file_reader` classe.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Chaque surcharge de constructeur définit les `file_reader` membres de données. La deuxième et la troisième surcharge de constructeur permettent à votre application d’utiliser un planificateur spécifique avec votre agent. La première surcharge utilise le planificateur par défaut avec votre agent.

1. Ajoutez la `get_error` méthode à la section publique de la `file_reader` classe.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   La `get_error` méthode récupère toute erreur qui se produit pendant la durée de vie de l’agent.

1. Implémentez la méthode [Concurrency :: agent :: Run](reference/agent-class.md#run) dans la **`protected`** section de votre classe.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

La `run` méthode ouvre le fichier et y lit les données. La `run` méthode utilise la gestion des exceptions pour capturer les erreurs qui se produisent pendant le traitement du fichier.

   Chaque fois que cette méthode lit les données du fichier, elle appelle la fonction [Concurrency :: asend](reference/concurrency-namespace-functions.md#asend) pour envoyer ces données à la mémoire tampon cible. Elle envoie la chaîne vide à sa mémoire tampon cible pour indiquer la fin du traitement.

L’exemple suivant montre le contenu complet de file_reader. h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Haut](#top)]

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>Utilisation de la classe file_reader dans l’application

Cette section montre comment utiliser la `file_reader` classe pour lire le contenu d’un fichier texte. Il montre également comment créer un objet [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) qui reçoit ces données de fichier et calcule sa somme de contrôle Adler-32.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Pour utiliser la classe file_reader dans votre application

1. Dans BasicAgent. cpp, ajoutez l' `#include` instruction suivante.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. Dans BasicAgent. cpp, ajoutez les **`using`** directives suivantes.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. Dans la `_tmain` fonction, créez un objet [Concurrency :: Event](../../parallel/concrt/reference/event-class.md) qui signale la fin du traitement.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Créez un `call` objet qui met à jour la somme de contrôle lorsqu’il reçoit des données.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Cet `call` objet définit également l' `event` objet lorsqu’il reçoit la chaîne vide pour signaler la fin du traitement.

1. Créez un `file_reader` objet qui lit à partir du fichier test.txt et écrit le contenu de ce fichier dans l' `call` objet.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Démarrez l’agent et attendez qu’il se termine.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Attendez que l' `call` objet reçoive toutes les données et terminez.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Recherchez les erreurs dans le lecteur de fichier. Si aucune erreur ne s’est produite, calculez la somme finale de la valeur Adler-32 et imprimez la somme sur la console.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

L’exemple suivant montre le fichier BasicAgent. cpp complet.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Haut](#top)]

## <a name="sample-input"></a>Exemple d’entrée

Voici l’exemple de contenu du fichier d’entrée text.txt :

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Exemple de sortie

Lorsqu’il est utilisé avec l’exemple d’entrée, ce programme produit la sortie suivante :

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Programmation fiable

Pour empêcher l’accès simultané aux membres de données, nous vous recommandons d’ajouter des méthodes qui effectuent des tâches à la **`protected`** **`private`** section ou de votre classe. Ajoutez uniquement des méthodes qui envoient ou reçoivent des messages vers ou depuis l’agent vers la **`public`** section de votre classe.

Appelez toujours l' [accès concurrentiel :: agent ::d une](reference/agent-class.md#done) méthode pour déplacer votre agent à l’état terminé. En général, vous appelez cette méthode avant de retourner à partir de la `run` méthode.

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir un autre exemple d’application basée sur un agent, consultez [procédure pas à pas : utilisation de Join pour empêcher tout interblocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Procédure pas à pas : utilisation de Join pour empêcher un blocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
