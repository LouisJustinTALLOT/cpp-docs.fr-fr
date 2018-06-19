---
title: Créer un projet d’application console C++ | Documents Microsoft
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
ms.openlocfilehash: 35b7b896dfb2a4c9dd37a9f59476cbc7f23c3902
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391231"
---
# <a name="create-a-c-console-app-project"></a>Créer un projet d’application console C++

Le habituel point de départ pour un programmeur C++ est un « Hello, world ! » application qui s’exécute sur la ligne de commande. C’est ce que vous allez créer dans Visual Studio dans cette étape.

## <a name="prerequisites"></a>Prérequis

- Visual Studio avec le développement de bureau dotées de la charge de travail C++ installé et en cours d’exécution sur votre ordinateur. S’il n’est pas encore installé, consultez [prise en charge de l’installation de C++ dans Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Créer votre projet d’application

Visual Studio organise le code des applications dans des *projets*, et vos projets dans des *solutions*. Un projet contient toutes les options, les configurations et les règles utilisées pour créer des applications et gère les relations entre tous les fichiers du projet et des fichiers externes. Pour créer votre application, tout d’abord, vous allez créer une solution et un nouveau projet.

1. Dans Visual Studio, ouvrez le **fichier** menu et choisissez **Nouveau > projet** pour ouvrir le **nouveau projet** boîte de dialogue.

   ![Ouvrez la boîte de dialogue Nouveau projet](../build/media/vscpp-file-new-project.gif "ouvrir la boîte de dialogue Nouveau projet")

1. Dans le **nouveau projet** boîte de dialogue, sélectionnez **installé**, **Visual C++** s’il n’est pas déjà sélectionné, puis choisissez le **projet vide** modèle. Dans le **nom** , entrez *HelloWorld*. Choisissez **OK** pour créer le projet.

   ![Nom et créer le projet](../build/media/vscpp-concierge-project-name-callouts.png "nom et créer le projet")

Visual Studio crée un nouveau projet vide, prêt à spécialiser pour le type d’application que vous souhaitez créer et ajouter vos fichiers de code source. Vous devez le faire maintenant.

[J’ai rencontré un problème.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Faire de votre projet une application console

Visual Studio peut créer toutes sortes d’applications et des composants pour Windows et d’autres plateformes. Le **projet vide** modèle n’est pas spécifique sur le type d’application, il crée. Pour créer un *application console*, un qui s’exécute dans une console ou une fenêtre d’invite de commandes, vous devez indiquer à Visual Studio pour générer votre application pour utiliser le sous-système de la console.

1. Dans Visual Studio, ouvrez le **projet** menu et choisissez **propriétés** pour ouvrir le **Pages de propriétés HelloWorld** boîte de dialogue.

1. Dans le **Pages de propriétés** boîte de dialogue, sous **propriétés de Configuration**, sélectionnez **l’éditeur de liens**, **système**, puis choisissez suivant pour la zone d’édition le **sous-système** propriété. Dans le menu déroulant qui s’affiche, sélectionnez **Console (/ SUBSYSTEM : CONSOLE)**. Choisissez **OK** pour enregistrer vos modifications.

   ![Ouvrez la boîte de dialogue Pages de propriétés](../build/media/vscpp-properties-linker-subsystem.gif "ouvrir la boîte de dialogue Pages de propriétés")

Visual Studio sait maintenant générer votre projet pour s’exécuter dans une fenêtre de console. Ensuite, vous allez ajouter un fichier de code source et entrez le code de votre application.

[J’ai rencontré un problème.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Ajoutez un fichier de code source

1. Dans **l’Explorateur de solutions**, sélectionnez le projet HelloWorld. Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément** pour ouvrir le **ajouter un nouvel élément** boîte de dialogue.

1. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Visual C++** sous **installé** s’il n’est pas déjà sélectionné. Dans le volet central, sélectionnez **fichier C++ (.cpp)**. Modifier la **nom** à *HelloWorld.cpp*. Choisissez **ajouter** pour fermer la boîte de dialogue et créer le fichier.

   ![Ajoutez un fichier source pour HelloWorld.cpp](../build/media/vscpp-add-new-item.gif "ajouter un fichier source pour HelloWorld.cpp")

Visual studio crée un fichier de code source vide et s’ouvre dans une fenêtre d’éditeur, prête à entrer votre code source.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Ajoutez le code au fichier source

1. Copiez ce code dans la fenêtre de l’éditeur HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Dans la fenêtre de l’éditeur, le code doit ressembler à ceci :

   ![Hello code World dans l’éditeur](../build/media/vscpp-hello-world-editor.png "code Hello World dans l’éditeur")

Lorsque le code ressemble à ceci dans l’éditeur, vous êtes prêt à passer à l’étape suivante et générez votre application.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Générer et exécuter un projet C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Guide de dépannage

Viens pour les solutions aux problèmes courants rencontrés lorsque vous créez votre premier projet C++.

### <a name="create-your-app-project-issues"></a>Créer des problèmes de projet de votre application

Si le **nouveau projet** boîte de dialogue n’affiche pas une **Visual C++** entrée sous **installé**, votre copie de Visual Studio ne possède pas le **Desktop développement avec C++** installé la charge de travail. Vous pouvez exécuter le programme d’installation directement à partir de la **nouveau projet** boîte de dialogue. Choisissez le **ouvrir Visual Studio Installer** lien pour démarrer le programme d’installation à nouveau. Si le **contrôle de compte d’utilisateur** boîte de dialogue demande des autorisations, choisissez **Oui**. Dans le programme d’installation, assurez-vous que le **bureau développement avec C++** la charge de travail est activée, puis choisissez **OK** pour mettre à jour votre installation de Visual Studio.

Si un autre projet portant le même nom existe déjà, choisissez un autre nom pour votre projet, ou supprimez le projet existant, puis réessayez. Pour supprimer un projet existant, supprimez le dossier de solution (le dossier qui contient le fichier helloworld.sln) dans l’Explorateur de fichiers.

[Revenir en arrière](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Faire de votre projet un problèmes d’application console

Si vous ne voyez pas **l’éditeur de liens** répertoriés sous **propriétés de Configuration**, choisissez **Annuler** pour fermer la **Pages de propriétés** boîte de dialogue, puis Assurez-vous que le **HelloWorld** projet est sélectionné dans **l’Explorateur de solutions**, pas la solution ou un autre fichier ou dossier, avant de réessayer.

Le contrôle de liste déroulante n’apparaît pas dans le **sous-système** zone d’édition de propriété jusqu'à ce que vous sélectionnez la propriété. Vous pouvez le sélectionner à l’aide du pointeur, ou vous pouvez appuyer sur Tab pour passer en revue les contrôles de boîte de dialogue tant que **sous-système** est mis en surbrillance. Sélectionnez le contrôle de liste déroulante ou appuyez sur Alt + bas pour l’ouvrir.

[Retour](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Ajouter un problèmes de fichiers de code source

Il est OK si vous nommez le fichier de code source différents. Toutefois, n’ajoutez pas plus d’un fichier de code source qui contient le même code à votre projet.

Si vous avez ajouté un type de fichier incorrect à votre projet, par exemple, un fichier d’en-tête, supprimez-le et recommencez l’opération. Pour supprimer le fichier, sélectionnez-le dans **l’Explorateur de solutions** et appuyez sur la touche SUPPR.

[Revenir en arrière](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Ajoutez le code pour les problèmes de fichier source

Si vous fermez accidentellement la fenêtre Éditeur de source code fichier, pour l’ouvrir à nouveau, double-cliquez sur HelloWorld.cpp dans le **l’Explorateur de solutions** fenêtre.

Si les soulignements ondulés rouges s’affichent sous n’importe où dans l’éditeur de code source, vérifiez que votre code correspond à l’exemple dans le cas, signes de ponctuation et l’orthographe. Cas est significatif dans le code C++.

[Revenir en arrière](#add-code-to-the-source-file).

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />