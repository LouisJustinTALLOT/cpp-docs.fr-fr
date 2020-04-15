---
title: 'Procédure pas à pas : création d’une application basée sur un agent'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 20197786e3d3c2d34d29af748c1cc073902cf70d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377454"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Procédure pas à pas : création d’une application basée sur un agent

Ce sujet décrit comment créer une application de base basée sur l’agent. Dans cette procédure pas à pas, vous pouvez créer un agent qui lit les données d’un fichier texte asynchrone. L’application utilise l’algorithme de checksum Adler-32 pour calculer le checksum du contenu de ce fichier.

## <a name="prerequisites"></a>Prérequis

Vous devez comprendre les sujets suivants pour compléter cette procédure pas à pas :

- [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de message](../../parallel/concrt/message-passing-functions.md)

- [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Sections

Cette procédure pas à pas démontre comment effectuer les tâches suivantes :

- [Créer l'application console](#createapplication)

- [Création de la classe file_reader](#createagentclass)

- [Utilisation de la classe file_reader dans l’application](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>Création de l’application Console

Cette section montre comment créer une application de console CMD qui fait référence aux fichiers d’en-tête que le programme utilisera. Les étapes initiales varient selon la version de Visual Studio que vous utilisez. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Pour créer une application console CMD dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur ** C++ **, **Plateforme** sur **Windows** et **Type de projet** sur **Console**.

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page `BasicAgent` suivante, entrez comme nom pour le projet, et spécifiez l’emplacement du projet si désiré.

1. Choisissez le bouton **Créer** pour créer le projet.

1. Cliquez à droite sur le nœud de projet dans **Solution Explorer**, et choisissez **Propriétés**. Sous **Configuration Properties** > **C/CMD** > **Precompiled Headers** > **Precompiled header** choose **Create**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Pour créer une application de console CMD dans Visual Studio 2017 et plus tôt

1. Sur le menu **Du fichier,** cliquez sur **Nouveau**, puis cliquez sur **Project** pour afficher la boîte de dialogue du **nouveau projet.**

1. Dans la boîte de dialogue **New Project,** sélectionnez le nœud **Visual CMD** dans la vitre **des types de projets,** puis sélectionnez **l’application console Win32** dans la vitre **Templates.** Tapez un nom pour le `BasicAgent`projet, par exemple, , puis cliquez **sur OK** pour afficher le **Win32 Console Application Wizard**.

1. Dans la boîte de dialogue **Win32 Console Application Wizard,** cliquez sur **Finition**.

::: moniker-end

1. Dans *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt), ajoutez le code suivant :

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Le fichier d’en-tête agents.h contient la fonctionnalité de la [concurrence::classe d’agent.](../../parallel/concrt/reference/agent-class.md)

1. Vérifiez que l’application a été créée avec succès en la construisant et en l’exécutant. Pour construire l’application, sur le menu **Build,** cliquez sur **Build Solution**. Si l’application se construit avec succès, exécutez l’application en cliquant sur **Start Debugging** sur le menu **Debug.**

[[Top](#top)]

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>Création de la classe file_reader

Cette section montre comment `file_reader` créer la classe. Le temps d’exécution prévoit que chaque agent effectue des travaux dans son propre contexte. Par conséquent, vous pouvez créer un agent qui effectue le travail de façon synchrone, mais interagit avec d’autres composants asynchrone. Le `file_reader` groupe lit les données d’un fichier d’entrée donné et envoie des données de ce fichier à un composant cible donné.

#### <a name="to-create-the-file_reader-class"></a>Créer la classe file_reader

1. Ajoutez un nouveau fichier d’en-tête CMD à votre projet. Pour ce faire, cliquez à droite sur le nœud **Header Files** dans **Solution Explorer**, cliquez sur **Ajouter**, puis cliquez sur **Nouvel article**. Dans le volet **Templates,** sélectionnez **Fichier d’en-tête (.h)**. Dans la boîte de dialogue `file_reader.h` Add New **Item,** tapez dans la boîte de **nom,** puis cliquez sur **Ajouter**.

1. Dans file_reader.h, ajoutez le code suivant.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. Dans file_reader.h, créer une classe qui `file_reader` est nommé `agent`qui dérive de .

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Ajoutez les membres de `private` données suivants à la section de votre classe.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   Le `_file_name` membre est le nom de fichier que l’agent lit à partir. Le `_target` membre est une [concordance::ITarget](../../parallel/concrt/reference/itarget-class.md) objet que l’agent écrit le contenu du fichier à. Le `_error` membre détient toute erreur qui se produit pendant la vie de l’agent.

1. Ajoutez le code `file_reader` suivant pour `public` les constructeurs à la section de la `file_reader` classe.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Chaque surcharge de constructeurs définit les `file_reader` membres des données. La deuxième et troisième surcharge du constructeur permet à votre application d’utiliser un planificateur spécifique avec votre agent. La première surcharge utilise le planificateur par défaut avec votre agent.

1. Ajoutez `get_error` la méthode à la `file_reader` section publique de la classe.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   La `get_error` méthode récupère toute erreur qui se produit pendant la durée de vie de l’agent.

1. Implémentez la [concurrence ::agent:::exécuter](reference/agent-class.md#run) la méthode dans la `protected` section de votre classe.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

La `run` méthode ouvre le fichier et lit les données de celui-ci. La `run` méthode utilise le traitement des exceptions pour capturer les erreurs qui se produisent pendant le traitement des fichiers.

   Chaque fois que cette méthode lit les données du fichier, elle appelle la [concordance::asend](reference/concurrency-namespace-functions.md#asend) fonction d’envoyer ces données au tampon cible. Il envoie la chaîne vide à son tampon cible pour indiquer la fin du traitement.

L’exemple suivant montre le contenu complet de file_reader.h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Top](#top)]

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>Utilisation de la classe file_reader dans l’application

Cette section montre comment `file_reader` utiliser la classe pour lire le contenu d’un fichier texte. Il montre également comment créer une [concordance::appel](../../parallel/concrt/reference/call-class.md) objet qui reçoit ces données de fichier et calcule son chèque Adler-32.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Utiliser la classe file_reader dans votre application

1. Dans BasicAgent.cpp, ajoutez `#include` la déclaration suivante.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. Dans BasicAgent.cpp, ajoutez `using` les directives suivantes.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. Dans `_tmain` la fonction, créez une concordance : : objet [d’événement](../../parallel/concrt/reference/event-class.md) qui signale la fin du traitement.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Créez `call` un objet qui met à jour le checksum lorsqu’il reçoit des données.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Cet `call` objet définit `event` également l’objet lorsqu’il reçoit la chaîne vide pour signaler la fin du traitement.

1. Créez `file_reader` un objet qui lit à partir du fichier test.txt et écrit le contenu de ce fichier à l’objet. `call`

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Démarrez l’agent et attendez qu’il se termine.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Attendez que `call` l’objet reçoive toutes les données et terminez.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Vérifiez le lecteur de fichiers pour les erreurs. En cas d’erreur, calculez la somme finale d’Adler-32 et imprimez la somme à la console.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

L’exemple suivant montre le fichier BasicAgent.cpp complet.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Top](#top)]

## <a name="sample-input"></a>Exemple d’entrée

Il s’agit du contenu de l’échantillon du fichier d’entrée text.txt:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Exemple de sortie

Lorsqu’il est utilisé avec l’entrée de l’échantillon, ce programme produit la sortie suivante :

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Programmation fiable

Pour empêcher l’accès simultané aux membres des données, `protected` nous `private` vous recommandons d’ajouter des méthodes qui effectuent le travail à la section ou à la section de votre classe. Ajoutez uniquement des méthodes qui envoient ou `public` reçoivent des messages à l’agent ou à la section de votre classe.

Appelez toujours la [concurrence::agent::dune](reference/agent-class.md#done) méthode pour déplacer votre agent à l’état terminé. Vous appelez généralement cette méthode `run` avant de revenir de la méthode.

## <a name="next-steps"></a>Étapes suivantes

Pour un autre exemple d’une application basée sur un agent, voir [Procédure pas à pas: Utiliser l’adhésion pour prévenir l’impasse](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de message](../../parallel/concrt/message-passing-functions.md)<br/>
[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Procédure pas à pas : utilisation de la classe join pour empêcher l’interblocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
