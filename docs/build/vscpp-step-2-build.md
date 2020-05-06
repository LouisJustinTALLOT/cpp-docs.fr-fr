---
title: Générer et exécuter un projet d’application console C++
description: Générez et exécutez une application console Hello World dans Visual C++
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

Vous avez créé un projet d’application console C++ et entré votre code. Vous pouvez maintenant la générer et l’exécuter dans Visual Studio. Ensuite, exécutez-la en tant qu’application autonome à partir de la ligne de commande.

## <a name="prerequisites"></a>Prérequis

- Vous devez installer puis exécuter Visual Studio ainsi que la charge de travail Développement Desktop en C++ sur votre ordinateur. S’il n’est pas encore installé, suivez les étapes de la section [installer la prise en charge de C++ dans Visual Studio](vscpp-step-0-installation.md).

- Créer un « Hello, World ! » projet et entrez son code source. Si vous n’avez pas encore effectué cette étape, suivez les étapes de la section [créer un projet d’application console C++](vscpp-step-1-create.md).

Si Visual Studio ressemble à ce qui suit, vous êtes prêt à générer et exécuter votre application :

   ![Prêt à générer le nouveau projet](media/vscpp-ready-to-build.png "Prêt à générer le nouveau projet")

## <a name="build-and-run-your-code-in-visual-studio"></a>Générer et exécuter votre code dans Visual Studio

1. Pour générer le projet, choisissez **Générer la solution** dans le menu **Générer**. La fenêtre **Sortie** affiche les résultats de la génération.

   ![Créer le projet](media/vscpp-build-solution.gif "Créer le projet")

1. Pour exécuter le projet, dans la barre de menus, choisissez **Déboguer**, **Démarrer sans débogage**.

   ![Démarrer le projet](media/vscpp-start-without-debugging.gif "Démarrer le projet")

   Une fenêtre de console s’ouvre, puis exécute votre application. Lorsque vous démarrez une application console dans Visual Studio, celui-ci exécute votre code, puis affiche le message « Appuyez sur une touche pour continuer . ." afin de vous permettre de voir la sortie.

Félicitations ! Vous venez de créer votre première application console « Hello, world ! » dans Visual Studio. Appuyez sur une touche pour fermer la fenêtre de console et revenir à Visual Studio.

[J’ai rencontré un problème.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Exécuter votre code dans une fenêtre de commande

Normalement, vous exécutez des applications console à partir de l’invite de commandes, et non dans Visual Studio. Une fois que votre application est générée par Visual Studio, vous pouvez l’exécuter à partir de n’importe quelle fenêtre de commande. Voici comment rechercher et exécuter votre nouvelle application dans une fenêtre d’invite de commandes.

1. Dans **Explorateur de solutions**, sélectionnez la solution HelloWorld (pas le projet HelloWorld) et cliquez avec le bouton droit pour ouvrir le menu contextuel. Choisissez **ouvrir le dossier dans l’Explorateur de fichiers** pour ouvrir une fenêtre de l' **Explorateur de fichiers** dans le dossier de solution HelloWorld.

1. Dans la fenêtre **Explorateur de fichiers** , ouvrez le dossier débogage. Ce dossier contient votre application, *HelloWorld. exe*, et quelques autres fichiers de débogage. Maintenez la touche **MAJ** enfoncée et cliquez avec le bouton droit sur *HelloWorld. exe* pour ouvrir le menu contextuel. Choisissez **copier en tant que chemin d’accès** pour copier le chemin d’accès de votre application dans le presse-papiers.

1. Pour ouvrir une fenêtre d’invite de commandes, appuyez sur **Windows + R** pour ouvrir la boîte de dialogue **exécuter** . Entrez *cmd. exe* dans la zone de texte **ouvrir** , puis choisissez **OK** pour exécuter une fenêtre d’invite de commandes.

1. Dans la fenêtre d’invite de commandes, cliquez avec le bouton droit pour coller le chemin d’accès à votre application dans l’invite de commandes. Appuyez sur entrée pour exécuter votre application.

   ![Exécuter l’application à partir de l’invite de commandes](media/vscpp-run-in-cmd.gif "Exécuter l’application à partir de l’invite de commandes")

Félicitations, vous avez créé et exécuté une application console dans Visual Studio !

[J’ai rencontré un problème.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez créé et exécuté cette application simple, vous êtes prêt pour des projets plus complexes. Pour plus d’informations, consultez [utilisation de l’IDE Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Elle contient des procédures pas à pas détaillées qui explorent les fonctionnalités de Microsoft C++ dans Visual Studio.

## <a name="troubleshooting-guide"></a>Guide de résolution des problèmes

Venez ici pour obtenir des solutions aux problèmes courants lorsque vous créez votre premier projet C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Générer et exécuter votre code dans Visual Studio : problèmes

Si des tildes rouges s’affichent sous n’importe quoi dans l’éditeur de code source, la build peut comporter des erreurs ou des avertissements. Vérifiez que votre code correspond à l’exemple dans l’orthographe, la ponctuation et la casse.

[Retour.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Exécuter votre code dans une fenêtre de commande : problèmes

Si le chemin d’accès affiché dans l’Explorateur de fichiers se termine par * \\HelloWorld\\HelloWorld*, vous avez ouvert le *projet* HelloWorld au lieu de la *solution*HelloWorld. Vous allez être confondu avec un dossier de débogage qui ne contient pas votre application. Naviguez vers le haut d’un niveau dans l’Explorateur de fichiers pour accéder au dossier de la solution, le premier *HelloWorld* du chemin. Ce dossier contient également un dossier de débogage et vous y trouverez votre application.

Vous pouvez également accéder au dossier de débogage de la solution sur la ligne de commande pour exécuter votre application. Votre application ne s’exécutera pas à partir d’autres répertoires sans spécifier le chemin d’accès à l’application. Toutefois, vous pouvez copier votre application dans un autre répertoire et l’exécuter à partir de là. Il est également possible de la copier dans un répertoire spécifié par votre variable d’environnement PATH, puis de l’exécuter depuis n’importe où.

Si vous ne voyez pas **copier en tant que chemin d’accès** dans le menu contextuel, Faites disparaître le menu, puis maintenez la touche **MAJ** enfoncée pendant que vous l’ouvrez à nouveau. Cette commande est uniquement pour des raisons pratiques. Vous pouvez également copier le chemin d’accès au dossier à partir de la barre de recherche de l’Explorateur de fichiers et le coller dans la boîte de dialogue **exécuter** , puis entrer le nom de votre exécutable à la fin. Il s’agit simplement d’un petit nombre de frappes, mais il a le même résultat.

[Retour.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
