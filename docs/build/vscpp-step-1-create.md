---
title: Créer un projet d’application console C++
description: Créez une application console Hello World à l’aide de Microsoft C++ dans Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: ee9631ee858ca34f82b599eeabce628483d9a247
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922086"
---
# <a name="create-a-c-console-app-project"></a>Créer un projet d’application console C++

Habituellement, le programmeur C++ commence par créer une application « Hello, world ! » qu’il exécute sur la ligne de commande. C’est ce que vous allez créer dans Visual Studio au cours de cette étape.

## <a name="prerequisites"></a>Conditions préalables requises

- Vous devez installer puis exécuter Visual Studio ainsi que la charge de travail Développement Desktop en C++ sur votre ordinateur. S’il n’est pas installé, consultez [Installer la prise en charge de C++ dans Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Créer un projet d’application

Visual Studio organise le code des applications dans des *projets* , et vos projets dans des *solutions* . Un projet contient l’ensemble des options, des configurations et des règles utilisées pour créer une application. Il gère la relation entre tous les fichiers du projet et les fichiers externes. Pour créer votre application, commencez par créer un projet et une solution.

::: moniker range=">=msvc-160"

1. Dans Visual Studio, ouvrez le menu **fichier** et choisissez **nouveau > projet** pour ouvrir la boîte de dialogue **créer un nouveau projet** . Sélectionnez le modèle **application console** qui contient des balises **C++** , **Windows** et **console** , puis choisissez **suivant** .

   ![Créer un projet](media/vs2019-choose-console-app.png "Ouvrir la boîte de dialogue créer un nouveau projet")

1. Dans la boîte de dialogue **configurer votre nouveau projet** , entrez *HelloWorld* dans la zone d’édition **nom du projet** . Choisissez **créer** pour créer le projet.

   ![Capture d’écran de la boîte de dialogue Configurer votre nouveau projet avec Hello World tapé dans le champ de texte Nom du projet.](media/vs2019-configure-new-project-hello-world.png "Nommer et créer le projet")

   Visual Studio crée un nouveau projet. Vous pouvez ajouter et modifier votre code source. Par défaut, le modèle application console remplit votre code source avec une application « Hello World » :

   ![Projet de Hello World dans l’IDE](media/vs2019-hello-world-code.png "Projet de Hello World dans l’IDE")

   Quand le code ressemble à celui-ci dans l’éditeur, vous êtes prêt à passer à l’étape suivante et à générer votre application.

[J’ai rencontré un problème.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=msvc-150"

1. Dans Visual Studio, ouvrez le menu **fichier** et choisissez **nouveau > projet** pour ouvrir la boîte de dialogue **nouveau projet** .

   ![Ouvrir la boîte de dialogue Nouveau projet](media/vscpp-file-new-project.gif "Ouvrir la boîte de dialogue Nouveau projet")

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **installé > Visual C++** s’il n’est pas déjà sélectionné, puis choisissez le modèle de **projet vide** . Dans le champ **nom** , entrez *HelloWorld* . Choisissez **OK** pour créer le projet.

   ![Capture d’écran de la boîte de dialogue Nouveau projet avec installé > Visual C plus plus sélectionné et appelé, l’option de projet vide appelée out et Hellow World tape dans la zone de texte nom.](media/vscpp-concierge-project-name-callouts.png "Nommer et créer le projet")

Visual Studio crée un projet vide. Il est prêt à être spécialisé pour le type d’application que vous souhaitez créer et pour ajouter vos fichiers de code source. Il s’agit de notre prochaine tâche.

[J’ai rencontré un problème.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Faire de votre projet une application console

Visual Studio peut créer tous les types d’applications et de composants pour Windows et d’autres plateformes. Le modèle de **projet vide** n’est pas spécifique au type d’application qu’il crée. Une *application console* est une application qui s’exécute dans une console ou une fenêtre d’invite de commandes. Pour en créer un, vous devez indiquer à Visual Studio de générer votre application pour utiliser le sous-système de la console.

1. Dans Visual Studio, ouvrez le menu **projet** , puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **pages de propriétés HelloWorld** .

1. Dans la boîte de dialogue **pages de propriétés** , sélectionnez **propriétés de configuration > éditeur de liens > système** , puis choisissez la zone d’édition en regard de la propriété **sous-système** . Dans le menu déroulant qui s’affiche, sélectionnez **console (/SUBSYSTEM : console)** . Choisissez **OK** pour enregistrer vos modifications.

   ![Ouvrir la boîte de dialogue pages de propriétés](media/vscpp-properties-linker-subsystem.gif "Ouvrir la boîte de dialogue pages de propriétés")

Visual Studio sait maintenant générer votre projet pour qu’il s’exécute dans une fenêtre de console. Ensuite, vous allez ajouter un fichier de code source et entrer le code de votre application.

[J’ai rencontré un problème.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Ajouter un fichier de code source

1. Dans **Explorateur de solutions** , sélectionnez le projet HelloWorld. Dans la barre de menus, choisissez **projet** , **Ajouter un nouvel élément** pour ouvrir la boîte de dialogue **Ajouter un nouvel élément** .

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Visual C++** sous **installé** s’il n’est pas déjà sélectionné. Dans le volet central, sélectionnez **fichier C++ (. cpp)** . Remplacez le **nom** par *HelloWorld. cpp* . Choisissez **Ajouter** pour fermer la boîte de dialogue et créer le fichier.

   ![Ajouter un fichier source pour HelloWorld. cpp](media/vscpp-add-new-item.gif "Ajouter un fichier source pour HelloWorld. cpp")

Visual Studio crée un nouveau fichier de code source vide et l’ouvre dans une fenêtre de l’éditeur, prête à entrer votre code source.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Ajouter du code au fichier source

1. Copiez ce code dans la fenêtre de l’éditeur HelloWorld. cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Le code doit ressembler à ceci dans la fenêtre de l’éditeur :

   ![Hello World du code dans l’éditeur](media/vscpp-hello-world-editor.png "Hello World du code dans l’éditeur")

Quand le code ressemble à celui-ci dans l’éditeur, vous êtes prêt à passer à l’étape suivante et à générer votre application.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Générer et exécuter un projet C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Guide de résolution des problèmes

Venez ici pour obtenir des solutions aux problèmes courants lorsque vous créez votre premier projet C++.

### <a name="create-your-app-project-issues"></a>Créer votre projet d’application : problèmes

::: moniker range="msvc-160"

La boîte de dialogue **nouveau projet** doit afficher un modèle d' **application console** qui contient des balises **C++** , **Windows** et **console** . Si vous ne le voyez pas, deux causes sont possibles. Il est possible qu’il soit exclu de la liste ou qu’il ne soit pas installé. Tout d’abord, vérifiez les listes déroulantes de filtre en haut de la liste des modèles. Définissez-les sur **C++** , **Windows** et **console** . Le modèle d' **application console** C++ doit apparaître. dans le cas contraire, la charge **de travail développement Desktop en C++** n’est pas installée.

Pour installer le **développement Desktop en C++** , vous pouvez exécuter le programme d’installation directement à partir de la boîte de dialogue **nouveau projet** . Cliquez sur le lien **installer d’autres outils et fonctionnalités** en bas de la liste des modèles pour démarrer le programme d’installation. Si la boîte de dialogue **contrôle de compte d’utilisateur** demande des autorisations, choisissez **Oui** . Dans le programme d’installation, assurez-vous que la charge de travail **développement Desktop en C++** est activée. Choisissez ensuite **modifier** pour mettre à jour votre installation de Visual Studio.

Si un autre projet portant le même nom existe déjà, choisissez un autre nom pour votre projet. Ou supprimez le projet existant et réessayez. Pour supprimer un projet existant, supprimez le dossier de solution (le dossier qui contient le fichier *HelloWorld. sln* ) dans l’Explorateur de fichiers.

[Revenez en arrière](#create-your-app-project).

::: moniker-end

::: moniker range="msvc-150"

Si la boîte de dialogue **nouveau projet** n’affiche pas une entrée de **Visual C++** sous **installé** , la charge de travail **développement Desktop en C++** n’est probablement pas installée sur votre copie de Visual Studio. Vous pouvez exécuter le programme d’installation directement à partir de la boîte de dialogue **nouveau projet** . Cliquez sur le lien **ouvrir Visual Studio installer** pour redémarrer le programme d’installation. Si la boîte de dialogue **contrôle de compte d’utilisateur** demande des autorisations, choisissez **Oui** . Mettez à jour le programme d’installation si nécessaire. Dans le programme d’installation, assurez-vous que la charge de travail **développement Desktop en C++** est activée, puis choisissez **OK** pour mettre à jour votre installation de Visual Studio.

::: moniker-end

::: moniker range="<=msvc-150"

Si un autre projet portant le même nom existe déjà, choisissez un autre nom pour votre projet. Ou supprimez le projet existant et réessayez. Pour supprimer un projet existant, supprimez le dossier de solution (le dossier qui contient le fichier *HelloWorld. sln* ) dans l’Explorateur de fichiers.

[Revenez en arrière](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Faire de votre projet une application console : problèmes

Si vous ne voyez pas l' **éditeur de liens** listé sous **Propriétés de configuration** , choisissez **Annuler** pour fermer la boîte de dialogue **pages de propriétés** . Assurez-vous que le projet **HelloWorld** est sélectionné dans **Explorateur de solutions** avant de réessayer. Ne sélectionnez pas la solution **HelloWorld** , ou un autre élément, dans **Explorateur de solutions** .

Le contrôle dropdown n’apparaît pas dans la zone de modification de la propriété du **sous-système** tant que vous n’avez pas sélectionné la propriété. Cliquez dans la zone d’édition pour la sélectionner. Vous pouvez aussi appuyer sur la touche **Tab** pour parcourir les contrôles de boîte de dialogue jusqu’à ce que le **sous-système** soit mis en surbrillance. Choisissez le contrôle dropdown ou appuyez sur **Alt + Pg. suiv** pour l’ouvrir.

[Revenir](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Ajouter un fichier de code source : problèmes

C’est parfait si vous attribuez un autre nom au fichier de code source. Toutefois, n’ajoutez pas plus d’un fichier qui contient le même code à votre projet.

Si vous avez ajouté un type de fichier incorrect à votre projet, tel qu’un fichier d’en-tête, supprimez-le et réessayez. Pour supprimer le fichier, sélectionnez-le dans **Explorateur de solutions** . Appuyez ensuite sur la touche **Suppr** .

[Revenez en arrière](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Ajouter du code au fichier source : problèmes

Si vous avez fermé par erreur la fenêtre de l’éditeur du fichier de code source, vous pouvez facilement l’ouvrir à nouveau. Pour l’ouvrir, double-cliquez sur HelloWorld. cpp dans la fenêtre **Explorateur de solutions** .

Si des tildes rouges s’affichent sous n’importe quoi dans l’éditeur de code source, vérifiez que votre code correspond à l’exemple dans l’orthographe, la ponctuation et la casse. La casse est significative dans le code C++.

[Revenez en arrière](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
