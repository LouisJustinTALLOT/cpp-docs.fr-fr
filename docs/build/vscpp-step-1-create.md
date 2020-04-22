---
title: Créer un projet d’application console C++
description: Créez une application de console Hello World à l’aide de Microsoft CMD dans Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749309"
---
# <a name="create-a-c-console-app-project"></a>Créer un projet d’application console C++

Habituellement, le programmeur C++ commence par créer une application « Hello, world ! » qu’il exécute sur la ligne de commande. C’est ce que vous allez créer dans Visual Studio dans cette étape.

## <a name="prerequisites"></a>Prérequis

- Vous devez installer puis exécuter Visual Studio ainsi que la charge de travail Développement Desktop en C++ sur votre ordinateur. S’il n’est pas installé, consultez [Installer la prise en charge de C++ dans Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Créer un projet d’application

Visual Studio organise le code des applications dans des *projets*, et vos projets dans des *solutions*. Un projet contient l’ensemble des options, des configurations et des règles utilisées pour créer une application. Il gère la relation entre tous les fichiers du projet et tous les fichiers externes. Pour créer votre application, commencez par créer un projet et une solution.

::: moniker range=">=vs-2019"

1. Dans Visual Studio, ouvrez le menu **Fichier** et choisissez **New > Project** pour ouvrir le dialogue Créer un nouveau **projet.** Sélectionnez le modèle **d’application console** qui a des balises **C ,** **Windows**et **Console,** puis choisissez **Next**.

   ![Création d'un projet](media/vs2019-choose-console-app.png "Ouvrez le Dialogue Créer un nouveau projet")

1. Dans le **configuré de votre nouveau dialogue de projet,** entrez *HelloWorld* dans la boîte **d’édition du nom du projet.** Choisissez **Créer** pour créer le projet.

   ![Nommez et créez le nouveau projet](media/vs2019-configure-new-project-hello-world.png "Nommez et créez le nouveau projet")

   Visual Studio crée un nouveau projet. Il est prêt pour vous d’ajouter et de modifier votre code source. Par défaut, le modèle Console App remplit votre code source d’une application "Hello World":

   ![Projet Hello World dans l’IDE](media/vs2019-hello-world-code.png "Projet Hello World dans l’IDE")

   Lorsque le code ressemble à ceci dans l’éditeur, vous êtes prêt à passer à l’étape suivante et à construire votre application.

[J’ai rencontré un problème.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. Dans Visual Studio, ouvrez le menu **Fichier** et choisissez **New > Project** pour ouvrir le dialogue du nouveau **projet.**

   ![Ouvrir la boîte de dialogue Nouveau projet](media/vscpp-file-new-project.gif "Ouvrir la boîte de dialogue Nouveau projet")

1. Dans le dialogue du **nouveau projet,** sélectionnez **Installé > Visual CMD** s’il n’est pas déjà sélectionné, puis choisissez le modèle **de projet vide.** Dans le champ **Nom,** entrez *HelloWorld*. Choisissez **OK** pour créer le projet.

   ![Nommez et créez le nouveau projet](media/vscpp-concierge-project-name-callouts.png "Nommez et créez le nouveau projet")

Visual Studio crée un nouveau projet vide. Il est prêt pour vous de vous spécialiser pour le type d’application que vous souhaitez créer et d’ajouter vos fichiers de code source. Ce sera votre prochaine tâche.

[J’ai rencontré un problème.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Faites de votre projet une application console

Visual Studio peut créer toutes sortes d’applications et de composants pour Windows et d’autres plates-formes. Le modèle **de projet vide** n’est pas spécifique sur le type d’application qu’il crée. Une *application console* est celle qui s’exécute dans une console ou une fenêtre d’invitation de commande. Pour en créer un, vous devez dire à Visual Studio de construire votre application pour utiliser le sous-système de la console.

1. Dans Visual Studio, ouvrez le menu **Du projet** et choisissez **des propriétés** pour ouvrir le dialogue **HelloWorld Property Pages.**

1. Dans le dialogue **des pages de propriété,** sélectionnez **Configuration Properties > Linker > System,** puis choisissez la boîte de modification à côté de la propriété **Subsystem.** Dans le menu de décrochage qui apparaît, sélectionnez **Console (/SUBSYSTEM:CONSOLE)**. Choisissez **OK** pour enregistrer vos modifications.

   ![Ouvrez le dialogue des pages de propriété](media/vscpp-properties-linker-subsystem.gif "Ouvrez le dialogue des pages de propriété")

Visual Studio sait maintenant construire votre projet pour fonctionner dans une fenêtre de console. Ensuite, vous ajouterez un fichier de code source et entrez le code pour votre application.

[J’ai rencontré un problème.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Ajouter un fichier de code source

1. Dans **Solution Explorer**, sélectionnez le projet HelloWorld. Sur la barre de menu, choisissez **Project**, **Ajouter un nouvel article** pour ouvrir le dialogue Add New **Item.**

1. Dans le dialogue **Add New Item,** sélectionnez **Visual CMMD** sous **Installé** s’il n’est pas déjà sélectionné. Dans la vitre centrale, sélectionnez **le fichier CMD (.cpp)**. Changer le **nom** de *HelloWorld.cpp*. Choisissez **Add** pour fermer le dialogue et créer le fichier.

   ![Ajouter un fichier source pour HelloWorld.cpp](media/vscpp-add-new-item.gif "Ajouter un fichier source pour HelloWorld.cpp")

Visual studio crée un nouveau fichier de code source vide et l’ouvre dans une fenêtre d’éditeur, prêt à entrer votre code source.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Ajouter du code au fichier source

1. Copiez ce code dans la fenêtre de l’éditeur HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Le code doit ressembler à ceci dans la fenêtre de l’éditeur:

   ![Hello World code en éditeur](media/vscpp-hello-world-editor.png "Hello World code en éditeur")

Lorsque le code ressemble à ceci dans l’éditeur, vous êtes prêt à passer à l’étape suivante et à construire votre application.

[J’ai rencontré un problème.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Construire et exécuter un projet de C](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Guide de résolution des problèmes

Venez ici pour trouver des solutions à des problèmes communs lorsque vous créez votre premier projet de C.

### <a name="create-your-app-project-issues"></a>Créez votre projet d’application : problèmes

::: moniker range="vs-2019"

Le dialogue **du nouveau projet** doit afficher un modèle **d’application console** qui a des balises C **,** **Windows**et **Console.** Si vous ne le voyez pas, il y a deux causes possibles. Il peut être filtré hors de la liste, ou il pourrait ne pas être installé. Tout d’abord, vérifiez les déposes de filtre en haut de la liste des modèles. **Réglez-les**à C , **Windows**, et **Console**. Le modèle **d’application console** CMD devrait apparaître; autrement, le **développement de bureau avec la** charge de travail de C n’est pas installé.

Pour installer **le développement de bureau avec CMD**, vous pouvez exécuter l’installateur directement à partir du dialogue New **Project.** Choisissez **l’installation plus d’outils et de fonctionnalités** lien au bas de la liste de modèle pour démarrer l’installateur. Si le dialogue **de contrôle de compte utilisateur** demande des autorisations, choisissez **Oui**. Dans l’installateur, assurez-vous que le **développement de bureau avec** la charge de travail de C est vérifié. Choisissez ensuite **Modifier** pour mettre à jour votre installation Visual Studio.

Si un autre projet du même nom existe déjà, choisissez un autre nom pour votre projet. Ou, supprimer le projet existant et essayer à nouveau. Pour supprimer un projet existant, supprimez le dossier de solution (le dossier qui contient le fichier *helloworld.sln)* dans File Explorer.

[Revenez en arrière](#create-your-app-project).

::: moniker-end

::: moniker range="vs-2017"

Si le dialogue **new Project** ne montre pas une entrée **Visual CMD** sous **Installed**, votre copie de Visual Studio n’a probablement pas le développement de bureau avec la charge de travail **CMD** installé. Vous pouvez exécuter l’installateur directement à partir du dialogue **New Project.** Choisissez le lien **Open Visual Studio Install** pour recommencer l’installateur. Si le dialogue **de contrôle de compte utilisateur** demande des autorisations, choisissez **Oui**. Mettre à jour l’installateur si nécessaire. Dans l’installateur, assurez-vous que le développement de bureau avec la charge de travail **de Cmd** est vérifié, et choisissez **OK** pour mettre à jour votre installation Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Si un autre projet du même nom existe déjà, choisissez un autre nom pour votre projet. Ou, supprimer le projet existant et essayer à nouveau. Pour supprimer un projet existant, supprimez le dossier de solution (le dossier qui contient le fichier *helloworld.sln)* dans File Explorer.

[Revenez en arrière](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Faites de votre projet une application console : problèmes

Si vous ne voyez pas **Linker** répertorié sous **Configuration Properties**, choisissez **Annuler** pour fermer le dialogue de pages **de propriété.** Assurez-vous que le projet **HelloWorld** est sélectionné dans **Solution Explorer** avant d’essayer à nouveau. Ne sélectionnez pas la solution **HelloWorld,** ou un autre élément, dans **Solution Explorer**.

Le contrôle de décrochage n’apparaît pas dans la boîte de modification de propriété **SubSystem** jusqu’à ce que vous sélectionnez la propriété. Cliquez dans la boîte d’édition pour la sélectionner. Ou, vous pouvez appuyer sur **Tab** pour cycle à travers les contrôles de dialogue jusqu’à ce que **SubSystem** est mis en évidence. Choisissez le contrôle de décrochage ou appuyez sur **Alt-Down** pour l’ouvrir.

[Retour](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Ajouter un fichier de code source : questions

C’est correct si vous donnez au fichier de code source un nom différent. Toutefois, n’ajoutez pas plus d’un fichier qui contient le même code à votre projet.

Si vous avez ajouté le mauvais type de fichier à votre projet, comme un fichier d’en-tête, supprimez-le et réessayez. Pour supprimer le fichier, sélectionnez-le dans **Solution Explorer**. Appuyez ensuite sur la clé **Supprimer.**

[Revenez en arrière](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Ajouter du code au fichier source : les problèmes

Si vous avez accidentellement fermé la fenêtre de l’éditeur de fichiers de code source, vous pouvez facilement l’ouvrir à nouveau. Pour l’ouvrir, cliquez deux fois sur HelloWorld.cpp dans la fenêtre **Solution Explorer.**

Si des gribouillis rouges apparaissent sous quoi que ce soit dans l’éditeur de code source, vérifiez que votre code correspond à l’exemple dans l’orthographe, la ponctuation et le boîtier. Le cas est significatif dans le code C.

[Revenez en arrière](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
