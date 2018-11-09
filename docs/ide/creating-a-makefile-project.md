---
title: Création d’un projet Makefile C++
ms.date: 10/19/2018
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 0c64f6df342e82e3ea5409e2b07af1e591747d7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494846"
---
# <a name="creating-a-c-makefile-project"></a>Création d’un projet Makefile C++

Un *makefile* est un fichier texte qui contient des instructions indiquant comment compiler et lier (ou *générer*) un ensemble de fichiers de code source C++. Un programme *make* lit le makefile et appelle un compilateur, un éditeur de liens et éventuellement d’autres programmes pour rendre un fichier exécutable. L’implémentation par Microsoft du programme *make* est appelée **NMAKE**. (Visual Studio utilise par défaut le système MSBuild basé sur des fichiers .vcxproj. C’est ce qui est créé par **Fichier | Nouveau | Projet**.)

Si vous avez un projet makefile existant, ces choix vous sont proposés si vous voulez le coder et/ou le déboguer dans l’IDE Visual Studio :

- Créez un projet Makefile dans Visual Studio qui utilise votre makefile existant pour générer votre code dans l’IDE. (Vous n’aurez pas toutes les fonctionnalités de l’IDE que vous obtenez avec un projet MSBuild natif.) Consultez [Pour créer un projet Makefile](#create_a_makefile_project) ci-dessous.
- Utilisez l’Assistant **Créer un projet à partir de fichiers de code existants** pour créer un projet MSBuild natif à partir de votre code source. Pour plus d’informations, consultez [Guide pratique pour créer un projet C++ à partir d’un code existant](how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 et ultérieur** : utilisez la fonctionnalité **Ouvrir un dossier** pour ouvrir un projet makefile sans le convertir en projet MSBuild. Pour plus d’informations, consultez [Open Folder projects in Visual C++](non-msbuild-projects.md).

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Pour créer un projet Makefile avec le modèle de projet Makefile

Dans Visual Studio 2017 et les versions ultérieures, le modèle de projet Makefile est disponible quand la charge de travail de développement d’applications de bureau C++ est installée.

Suivez l’Assistant pour spécifier les commandes et l’environnement utilisés par votre makefile. Vous pouvez ensuite utiliser ce projet pour générer votre code dans l’environnement de développement Visual Studio.

Par défaut, le projet makefile n’affiche aucun fichier dans l’Explorateur de solutions. Le projet makefile spécifie les paramètres de génération qui sont reflétés dans la page de propriétés du projet.

Le fichier de sortie que vous spécifiez dans le projet n'a pas d'incidence sur le nom que le script génère ; il déclare uniquement une intention. Votre makefile contrôle toujours le processus de génération et spécifie les cibles de génération.

1. Dans la page de démarrage de Visual Studio, tapez « makefile » dans la zone de recherche **Nouveau projet**. Ou dans la boîte de dialogue **Nouveau projet**, développez **Visual C++** > **Général** (Visual Studio 2015) ou **Autre** (Visual Studio 2017), puis sélectionnez **Projet Makefile** dans le volet Modèles pour ouvrir l’Assistant Projet.

1. Dans la page [Paramètres de l’application](../ide/application-settings-makefile-project-wizard.md), indiquez les informations relatives à la ligne de commande, à la sortie, au nettoyage et à la regénération pour les builds Debug et Retail.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir le projet que vous venez de créer dans **l’Explorateur de solutions**.

Vous pouvez afficher et modifier les propriétés du projet dans sa page de propriétés. Pour obtenir des informations sur l’affichage de la page de propriétés, consultez [Définition des propriétés de projets Visual C++](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Voir aussi

[Projet Makefile (Assistant)](../ide/makefile-project-wizard.md)<br/>
[Caractères spéciaux dans un makefile](../build/special-characters-in-a-makefile.md)<br/>
[Contenu d’un makefile](../build/contents-of-a-makefile.md)<br/>
