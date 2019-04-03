---
title: Créer un projet d’application console C++
description: Créer une application console Hello World dans Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 739da0b6e5400117c0b09a3d4c3335bd44529a25
ms.sourcegitcommit: b72a10a7b12e722fd91a17406b91b270026f763a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2019
ms.locfileid: "58898776"
---
# <a name="create-a-c-console-app-project"></a>Créer un projet d’application console C++

Habituellement, le programmeur C++ commence par créer une application « Hello, world ! » qu’il exécute sur la ligne de commande. C’est ce que vous allez créer dans Visual Studio dans cette étape.

## <a name="prerequisites"></a>Prérequis

- Vous devez installer puis exécuter Visual Studio ainsi que la charge de travail Développement Desktop en C++ sur votre ordinateur. S’il n’est pas encore installé, consultez [prise en charge de l’installation de C++ dans Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Créer un projet d’application

Visual Studio organise le code des applications dans des *projets*, et vos projets dans des *solutions*. Un projet contient l’ensemble des options, configurations et règles qui sont utilisées pour créer vos applications. De plus, il gère les relations qui existent entre tous les fichiers du projet et les fichiers externes. Pour créer votre application, commencez par créer un projet et une solution.

::: moniker range=">=vs-2019"

1. Dans Visual Studio, ouvrez le **fichier** menu et choisissez **New** > **projet** pour ouvrir le **créer un nouveau projet** boîte de dialogue. Sélectionnez le **application Console** modèle, puis choisissez **suivant**.

   ![Créer un nouveau projet](media/vs2019-choose-console-app.png "ouvrir la créer une boîte de dialogue Nouveau projet")

1. Dans le **configurer votre nouveau projet** boîte de dialogue, entrez *HelloWorld* dans le **nom_projet** zone d’édition. Choisissez **créer** pour créer le projet.

   ![Nommer et créer le projet](media/vs2019-configure-new-project-hello-world.png "nom et créer le projet")

   Visual Studio crée un nouveau projet, vous pouvez ajouter et modifier votre code source. Par défaut, le modèle d’application de Console remplit dans votre code source avec une application « Hello World » :

   ![Projet de World Hello dans l’IDE](media/vs2019-hello-world-code.png "projet Hello World dans l’IDE")

   Lorsque le code ressemble à ceci dans l’éditeur, vous êtes prêt à passer à l’étape suivante et générer votre application.

::: moniker-end

::: moniker range="<=vs-2017"

1. Dans Visual Studio, ouvrez le **fichier** menu et choisissez **Nouveau > projet** pour ouvrir le **nouveau projet** boîte de dialogue.

   ![Ouvrez la boîte de dialogue Nouveau projet](media/vscpp-file-new-project.gif "ouvrir la boîte de dialogue Nouveau projet")

1. Dans le **nouveau projet** boîte de dialogue, sélectionnez **installé**, **Visual C++** si elle n’est pas déjà sélectionné, puis choisissez le **projet vide** modèle. Dans le **nom** , entrez *HelloWorld*. Choisissez **OK** pour créer le projet.

   ![Nommer et créer le projet](media/vscpp-concierge-project-name-callouts.png "nom et créer le projet")

Visual Studio crée un nouveau projet vide, prêt à spécialisés pour le type d’application que vous souhaitez créer et ajouter vos fichiers de code source. Vous allez faire maintenant.

[J’ai rencontré un problème.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Rendre votre projet d’une application console

Visual Studio peut créer toutes sortes d’applications et composants pour Windows et d’autres plateformes. Le **projet vide** modèle n’est pas spécifique sur le type d’application, il crée. Pour créer un *application console*, un qui s’exécute dans une console ou une fenêtre d’invite de commandes, vous devez indiquer à Visual Studio pour générer votre application pour utiliser le sous-système de la console.

1. Dans Visual Studio, ouvrez le **projet** menu et choisissez **propriétés** pour ouvrir le **Pages de propriétés HelloWorld** boîte de dialogue.

1. Dans le **Pages de propriétés** boîte de dialogue, sous **propriétés de Configuration**, sélectionnez **l’éditeur de liens**, **système**, puis choisissez suivant pour la zone d’édition le **sous-système** propriété. Dans le menu déroulant qui s’affiche, sélectionnez **Console (/ SUBSYSTEM : CONSOLE)**. Choisissez **OK** pour enregistrer vos modifications.

   ![Ouvrez la boîte de dialogue Pages de propriétés](media/vscpp-properties-linker-subsystem.gif "ouvrir la boîte de dialogue Pages de propriétés")

Visual Studio sait maintenant pour générer votre projet doit être exécuté dans une fenêtre de console. Ensuite, vous allez ajouter un fichier de code source et entrez le code de votre application.

[J’ai rencontré un problème.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Ajoutez un fichier de code source

1. Dans **l’Explorateur de solutions**, sélectionnez le projet HelloWorld. Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément** pour ouvrir le **ajouter un nouvel élément** boîte de dialogue.

1. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Visual C++** sous **installé** s’il n’est pas déjà sélectionné. Dans le volet central, sélectionnez **fichier C++ (.cpp)**. Modifier le **nom** à *HelloWorld.cpp*. Choisissez **ajouter** pour fermer la boîte de dialogue et créer le fichier.

   ![Ajoutez un fichier source pour HelloWorld.cpp](media/vscpp-add-new-item.gif "ajouter un fichier source pour HelloWorld.cpp")

Visual studio crée un fichier de code source vide et s’ouvre dans une fenêtre d’éditeur, prête à entrer votre code source.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Ajoutez le code au fichier source

1. Copiez ce code dans la fenêtre d’éditeur HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Dans la fenêtre d’éditeur, le code doit ressembler à ceci :

   ![Hello dans l’éditeur de code World](media/vscpp-hello-world-editor.png "dans l’éditeur de code Hello World")

Lorsque le code ressemble à ceci dans l’éditeur, vous êtes prêt à passer à l’étape suivante et générer votre application.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Générer et exécuter un projet C++](vscpp-step-2-build.md)

::: moniker range="<=vs-2017"

## <a name="troubleshooting-guide"></a>Guide de dépannage

Accédez à cette page pour les solutions aux problèmes courants lorsque vous créez votre premier projet C++.

### <a name="create-your-app-project-issues"></a>Créer des problèmes de projet de votre application

Si le **nouveau projet** boîte de dialogue n’affiche pas un **Visual C++** entrée sous **installé**, votre copie de Visual Studio ne possède pas le **Desktop développement en C++** charge de travail installée. Vous pouvez exécuter le programme d’installation directement à partir de la **nouveau projet** boîte de dialogue. Choisissez le **ouvrir Visual Studio Installer** lien pour démarrer le programme d’installation à nouveau. Si le **contrôle de compte d’utilisateur** boîte de dialogue demande des autorisations, choisissez **Oui**. Dans le programme d’installation, assurez-vous que le **développement Desktop en C++** charge de travail est activée, puis choisissez **OK** pour mettre à jour votre installation de Visual Studio.

Si un autre projet portant le même nom existe déjà, choisissez un autre nom pour votre projet, ou supprimer le projet existant et réessayez. Pour supprimer un projet existant, supprimez le dossier de solution (le dossier qui contient le fichier helloworld.sln) dans l’Explorateur de fichiers.

[Revenir en arrière](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Rendre votre projet d’un problème d’application de console

Si vous ne voyez pas **l’éditeur de liens** répertoriés sous **propriétés de Configuration**, choisissez **Annuler** pour fermer la **Pages de propriétés** boîte de dialogue, puis Assurez-vous que le **HelloWorld** projet est sélectionné dans **l’Explorateur de solutions**, pas la solution ou un autre fichier ou dossier, avant d’essayer à nouveau.

Le contrôle de liste déroulante n’apparaît pas dans le **sous-système** zone d’édition de propriété jusqu'à ce que vous sélectionnez la propriété. Vous pouvez le sélectionner à l’aide du pointeur, ou vous pouvez appuyer sur Tab pour passer en revue les contrôles de boîte de dialogue jusqu'à ce que **sous-système** est mis en surbrillance. Choisissez le contrôle de liste déroulante ou appuyez sur Alt + bas pour l’ouvrir.

[Retour](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Ajouter un problème de fichier de code source

Il est OK si vous nommez le fichier de code source différents. Toutefois, n’ajoutez pas plus d’un fichier de code source qui contient le même code à votre projet.

Si vous avez ajouté un type de fichier incorrect à votre projet, par exemple, un fichier d’en-tête, supprimez-le et réessayez. Pour supprimer le fichier, sélectionnez-le dans **l’Explorateur de solutions** et appuyez sur la touche SUPPR.

[Revenir en arrière](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Ajoutez le code pour les problèmes de fichier source

Si vous avez fermé accidentellement la fenêtre Éditeur de source code fichier, pour l’ouvrir à nouveau, double-cliquez sur HelloWorld.cpp dans le **l’Explorateur de solutions** fenêtre.

Si les soulignements ondulés rouges s’affichent sous quoi que ce soit dans l’éditeur de code source, vérifiez que votre code correspond à l’exemple de l’orthographe, des signes de ponctuation et des cas. Cas est significatif dans le code C++.

[Revenir en arrière](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
