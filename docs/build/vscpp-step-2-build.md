---
title: Générer et exécuter un projet d’application console C++
description: Construire et exécuter une application de console Hello World dans Visual C
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749242"
---
# <a name="build-and-run-a-c-console-app-project"></a>Générer et exécuter un projet d’application console C++

Vous avez créé un projet d’application de console CMD et entré votre code. Maintenant, vous pouvez le construire et l’exécuter dans Visual Studio. Ensuite, exécutez-le comme une application autonome à partir de la ligne de commande.

## <a name="prerequisites"></a>Prérequis

- Vous devez installer puis exécuter Visual Studio ainsi que la charge de travail Développement Desktop en C++ sur votre ordinateur. S’il n’est pas encore installé, suivez les étapes du [support Install CMD dans Visual Studio](vscpp-step-0-installation.md).

- Créez un "Bonjour, Monde!" projet et entrez son code source. Si vous n’avez pas encore franchi cette étape, suivez les étapes du [projet d’application Console CMD](vscpp-step-1-create.md).

Si Visual Studio ressemble à ceci, vous êtes prêt à construire et exécuter votre application :

   ![Prêt à construire le nouveau projet](media/vscpp-ready-to-build.png "Prêt à construire le nouveau projet")

## <a name="build-and-run-your-code-in-visual-studio"></a>Construisez et exécutez votre code dans Visual Studio

1. Pour générer le projet, choisissez **Générer la solution** dans le menu **Générer**. La fenêtre **Sortie** affiche les résultats de la génération.

   ![Construire le projet](media/vscpp-build-solution.gif "Créer le projet")

1. Pour exécuter le projet, dans la barre de menus, choisissez **Déboguer**, **Démarrer sans débogage**.

   ![Démarrer le projet](media/vscpp-start-without-debugging.gif "Démarrer le projet")

   Une fenêtre de console s’ouvre, puis exécute votre application. Lorsque vous démarrez une application console dans Visual Studio, celui-ci exécute votre code, puis affiche le message « Appuyez sur une touche pour continuer . ." afin de vous permettre de voir la sortie.

Félicitations ! Vous venez de créer votre première application console « Hello, world ! » dans Visual Studio. Appuyez sur une touche pour fermer la fenêtre de console et revenir à Visual Studio.

[J’ai rencontré un problème.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Exécutez votre code dans une fenêtre de commande

Normalement, vous exécutez des applications de console à l’invite de commande, pas dans Visual Studio. Une fois votre application construite par Visual Studio, vous pouvez l’exécuter à partir de n’importe quelle fenêtre de commande. Voici comment trouver et exécuter votre nouvelle application dans une fenêtre d’invitation de commande.

1. Dans **Solution Explorer**, sélectionnez la solution HelloWorld (et non le projet HelloWorld) et cliquez à droite pour ouvrir le menu context. Choisissez **Open Folder in File Explorer** pour ouvrir une fenêtre File **Explorer** dans le dossier de solution HelloWorld.

1. Dans la fenêtre **File Explorer,** ouvrez le dossier Debug. Ce dossier contient votre application, *HelloWorld.exe*, et un couple d’autres fichiers de débogage. Maintenez la touche **Shift** et cliquez à droite sur *HelloWorld.exe* pour ouvrir le menu context. Choisissez **Copy comme chemin** pour copier le chemin vers votre application vers le presse-papiers.

1. Pour ouvrir une fenêtre d’invite de commande, appuyez sur **Windows-R** pour ouvrir le dialogue **Run.** Entrez *cmd.exe* dans la boîte à texte **Open,** puis choisissez **OK** pour exécuter une fenêtre d’invite de commande.

1. Dans la fenêtre d’invite de commande, cliquez à droite pour coller le chemin vers votre application dans l’invite de commande. Appuyez sur Entrez pour exécuter votre application.

   ![Exécuter l’application à l’invite de commande](media/vscpp-run-in-cmd.gif "Exécuter l’application à l’invite de commande")

Félicitations, vous avez construit et exécuté une application de console dans Visual Studio!

[J’ai rencontré un problème.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez construit et exécuté cette application simple, vous êtes prêt pour des projets plus complexes. Pour plus d’informations, voir [Utiliser l’IDE Visual Studio pour le développement de bureau](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)C . Il dispose de procédures plus détaillées qui explorent les capacités de Microsoft CMD dans Visual Studio.

## <a name="troubleshooting-guide"></a>Guide de résolution des problèmes

Venez ici pour trouver des solutions à des problèmes communs lorsque vous créez votre premier projet de C.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Construisez et exécutez votre code dans Visual Studio : les problèmes

Si des gribouillis rouges apparaissent sous quoi que ce soit dans l’éditeur de code source, la version peut avoir des erreurs ou des avertissements. Vérifiez que votre code correspond à l’exemple dans l’orthographe, la ponctuation et le boîtier.

[Retour.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Exécutez votre code dans une fenêtre de commande : problèmes

Si le chemin montré dans File Explorer se termine dans * \\HelloWorld\\HelloWorld*, vous avez ouvert le *projet* HelloWorld au lieu de la *solution*HelloWorld . Vous serez confondu par un dossier Debug qui ne contient pas votre application. Naviguez jusqu’à un niveau dans File Explorer pour arriver au dossier de solution, le premier *HelloWorld* dans le chemin. Ce dossier contient également un dossier Debug, et vous y trouverez votre application.

Vous pouvez également naviguer vers la solution dossier Debug à la ligne de commande pour exécuter votre application. Votre application ne s’exécutera pas à partir d’autres répertoires sans spécifier le chemin vers l’application. Cependant, vous pouvez copier votre application à un autre répertoire et l’exécuter à partir de là. Il est également possible de le copier à un répertoire spécifié par votre variable d’environnement PATH, puis de l’exécuter de n’importe où.

Si vous ne voyez pas **Copy comme un chemin** dans le menu raccourci, rejetez le menu, puis maintenez la clé **Shift** pendant que vous l’ouvrez à nouveau. Cette commande est juste pour plus de commodité. Vous pouvez également copier le chemin vers le dossier de la barre de recherche File Explorer, et le coller dans le dialogue **Run,** puis entrer le nom de votre exécutable à la fin. C’est juste un peu plus de dactylographie, mais il a le même résultat.

[Retour.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
