---
title: Générer et exécuter un projet d’application console C++
description: Générer et exécuter une application de console Hello World dans Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.devlang: C++
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: 89681b4f6b2ff2780cc8dc1947e2ad758d294b48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467832"
---
# <a name="build-and-run-a-c-console-app-project"></a>Générer et exécuter un projet d’application console C++

Lorsque vous avez créé un projet d’application console C++ et entré votre code, vous pouvez générer exécutez-le dans Visual Studio et puis l’exécuter comme une application autonome à partir de la ligne de commande.

## <a name="prerequisites"></a>Prérequis

- Visual Studio avec le développement bureautique dotées de la charge de travail C++ installé et en cours d’exécution sur votre ordinateur. S’il n’est pas encore installé, suivez les étapes de [prise en charge de l’installation de C++ dans Visual Studio](../build/vscpp-step-0-installation.md).

- Créer un « Hello, World ! » projet et entrez son code source. Si vous n’avez pas fait, suivez les étapes de [créer un projet d’application console C++](../build/vscpp-step-1-create.md).

Si Visual Studio ressemble à ceci, vous êtes prêt à générer et exécuter votre application :

   ![Prêt à générer le nouveau projet](../build/media/vscpp-ready-to-build.png "prêt à générer le nouveau projet")

## <a name="build-and-run-your-code-in-visual-studio"></a>Générer et exécuter votre code dans Visual Studio

1. Pour générer votre projet, choisissez **générer la Solution** à partir de la **Build** menu. Le **sortie** fenêtre affiche les résultats du processus de génération.

   ![Générez le projet](../build/media/vscpp-build-solution.gif "générer le projet")

1. Pour exécuter le code, sur la barre de menus, choisissez **déboguer**, **démarrer sans débogage**.

   ![Démarrer le projet](../build/media/vscpp-start-without-debugging.gif "démarrer le projet")

   Une fenêtre de console s’ouvre, puis exécute votre application. Lorsque vous démarrez une application console dans Visual Studio, elle s’exécute votre code, puis imprime « appuyez sur n’importe quelle touche pour continuer. . ." Pour vous donner une chance pour afficher la sortie.

Félicitations ! Vous avez créé votre premier « Hello, world ! » application de console dans Visual Studio ! Appuyez sur une touche pour fermer la fenêtre de console et revenir à Visual Studio.

[J’ai rencontré un problème.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Exécutez votre code dans une fenêtre de commande

En règle générale, vous exécutez des applications de console à l’invite de commandes, pas dans Visual Studio. Une fois que votre application est générée par Visual Studio, vous pouvez l’exécuter à partir de n’importe quelle fenêtre de commande. Voici comment rechercher et exécuter votre nouvelle application dans une fenêtre d’invite de commandes.

1. Dans **l’Explorateur de solutions**avec le bouton droit pour ouvrir le menu contextuel et sélectionnez la solution HelloWorld. Choisissez **ouvrir le dossier dans l’Explorateur de fichiers** pour ouvrir un **Explorateur de fichiers** fenêtre dans le dossier de solution HelloWorld.

1. Dans le **Explorateur de fichiers** fenêtre, ouvrez le dossier de débogage. Il contient votre application, HelloWorld.exe et quelques autres fichiers de débogage. Sélectionnez HelloWorld.exe, maintenez la touche MAJ enfoncée et avec le bouton droit pour ouvrir le menu contextuel. Choisissez **copier en tant que chemin d’accès** pour copier le chemin d’accès à votre application dans le Presse-papiers.

1. Pour ouvrir une fenêtre d’invite de commandes, appuyez sur Windows-R pour ouvrir la **exécuter** boîte de dialogue. Entrez *cmd.exe* dans le **Open** zone de texte, puis choisissez **OK** d’exécuter une fenêtre d’invite de commandes.

1. Dans la fenêtre d’invite de commandes, avec le bouton droit pour coller le chemin d’accès à votre application dans l’invite de commandes. Appuyez sur ENTRÉE pour exécuter votre application.

   ![Exécutez l’application à l’invite de commande](../build/media/vscpp-run-in-cmd.gif "à l’invite de commande, exécutez l’application")

Félicitations, vous venez de créer et exécuter une application console dans Visual Studio.

[J’ai rencontré un problème.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez créé et exécuter cette application simple, vous êtes prêt pour les projets plus complexes. Consultez [à l’aide de l’IDE Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md) pour plus de procédures pas à pas qui explorent les fonctionnalités de Visual C++ dans Visual Studio.

## <a name="troubleshooting-guide"></a>Guide de dépannage

Accédez à cette page pour les solutions aux problèmes courants lorsque vous créez votre premier projet C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Générer et exécuter votre code dans les problèmes de Visual Studio

Si les soulignements ondulés rouges s’affichent sous quoi que ce soit dans l’éditeur de code source, la build peut avoir des erreurs ou avertissements. Vérifiez que votre code correspond à l’exemple de l’orthographe, des signes de ponctuation et des cas.

[Retour.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Exécutez votre code dans une fenêtre de commande problèmes

Vous pouvez également accéder au dossier de débogage de solutions en ligne de commande pour exécuter votre application. Vous ne pouvez pas exécuter votre application à partir d’autres annuaires sans spécifier le chemin d’accès à l’application. Toutefois, vous pouvez copier votre application vers un autre répertoire et exécutez-le à partir de là.

Si vous ne voyez pas **copier en tant que chemin d’accès** dans le menu contextuel, faire disparaître le menu, puis maintenez la touche MAJ enfoncée pendant que vous l’ouvrez à nouveau. Il s’agit juste pour des raisons pratiques. Vous pouvez également copier le chemin d’accès au dossier à partir de la barre de recherche de l’Explorateur de fichiers et collez-la dans la **exécuter** boîte de dialogue, puis entrez le nom de votre fichier exécutable à la fin. Il s’agit d’un typage plus un peu, mais il a le même résultat.

[Retour.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
