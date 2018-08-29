---
title: Créer un projet d’application console C++ | Microsoft Docs
description: Créer une application de console Hello World dans Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7875d0e5c142304077ddcd3f7a1f5554da6d6248
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131034"
---
# <a name="create-a-c-console-app-project"></a>Créer un projet d’application console C++

Le habituel point de départ pour un programmeur C++ est un « Hello, world ! » application qui s’exécute sur la ligne de commande. C’est ce que vous allez créer dans Visual Studio dans cette étape.

## <a name="prerequisites"></a>Prérequis

- Visual Studio avec le développement bureautique dotées de la charge de travail C++ installé et en cours d’exécution sur votre ordinateur. S’il n’est pas encore installé, consultez [prise en charge de l’installation de C++ dans Visual Studio 2017](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Créer votre projet d’application

Visual Studio organise le code des applications dans des *projets*, et vos projets dans des *solutions*. Un projet contient toutes les options, les configurations et les règles utilisées pour créer vos applications et gère la relation entre tous les fichiers du projet et des fichiers externes. Pour créer votre application, tout d’abord, vous allez créer un nouveau projet et solution.

1. Dans Visual Studio, ouvrez le **fichier** menu et choisissez **Nouveau > projet** pour ouvrir le **nouveau projet** boîte de dialogue.

   ![Ouvrez la boîte de dialogue Nouveau projet](../build/media/vscpp-file-new-project.gif "ouvrir la boîte de dialogue Nouveau projet")

1. Dans le **nouveau projet** boîte de dialogue, sélectionnez **installé**, **Visual C++** si elle n’est pas déjà sélectionné, puis choisissez le **projet vide** modèle. Dans le **nom** , entrez *HelloWorld*. Choisissez **OK** pour créer le projet.

   ![Nommer et créer le projet](../build/media/vscpp-concierge-project-name-callouts.png "nom et créer le projet")

Visual Studio crée un nouveau projet vide, prêt à spécialisés pour le type d’application que vous souhaitez créer et ajouter vos fichiers de code source. Vous allez faire maintenant.

[J’ai rencontré un problème.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Rendre votre projet d’une application console

Visual Studio peut créer toutes sortes d’applications et composants pour Windows et d’autres plateformes. Le **projet vide** modèle n’est pas spécifique sur le type d’application, il crée. Pour créer un *application console*, un qui s’exécute dans une console ou une fenêtre d’invite de commandes, vous devez indiquer à Visual Studio pour générer votre application pour utiliser le sous-système de la console.

1. Dans Visual Studio, ouvrez le **projet** menu et choisissez **propriétés** pour ouvrir le **Pages de propriétés HelloWorld** boîte de dialogue.

1. Dans le **Pages de propriétés** boîte de dialogue, sous **propriétés de Configuration**, sélectionnez **l’éditeur de liens**, **système**, puis choisissez suivant pour la zone d’édition le **sous-système** propriété. Dans le menu déroulant qui s’affiche, sélectionnez **Console (/ SUBSYSTEM : CONSOLE)**. Choisissez **OK** pour enregistrer vos modifications.

   ![Ouvrez la boîte de dialogue Pages de propriétés](../build/media/vscpp-properties-linker-subsystem.gif "ouvrir la boîte de dialogue Pages de propriétés")

Visual Studio sait maintenant pour générer votre projet doit être exécuté dans une fenêtre de console. Ensuite, vous allez ajouter un fichier de code source et entrez le code de votre application.

[J’ai rencontré un problème.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Ajoutez un fichier de code source

1. Dans **l’Explorateur de solutions**, sélectionnez le projet HelloWorld. Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément** pour ouvrir le **ajouter un nouvel élément** boîte de dialogue.

1. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Visual C++** sous **installé** s’il n’est pas déjà sélectionné. Dans le volet central, sélectionnez **fichier C++ (.cpp)**. Modifier le **nom** à *HelloWorld.cpp*. Choisissez **ajouter** pour fermer la boîte de dialogue et créer le fichier.

   ![Ajoutez un fichier source pour HelloWorld.cpp](../build/media/vscpp-add-new-item.gif "ajouter un fichier source pour HelloWorld.cpp")

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

   ![Hello dans l’éditeur de code World](../build/media/vscpp-hello-world-editor.png "dans l’éditeur de code Hello World")

Lorsque le code ressemble à ceci dans l’éditeur, vous êtes prêt à passer à l’étape suivante et générer votre application.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Générer et exécuter un projet C++](vscpp-step-2-build.md)

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

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />