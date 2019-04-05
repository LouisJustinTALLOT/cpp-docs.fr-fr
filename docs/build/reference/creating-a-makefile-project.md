---
title: Créer un projet makefile de C++ dans Visual Studio
ms.date: 12/08/2018
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 9c2edfe35233672e8117d336ba40cfea497b1a22
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035596"
---
# <a name="create-a-c-makefile-project"></a>Créer un projet makefile de C++

Un *makefile* est un fichier texte qui contient des instructions indiquant comment compiler et lier (ou *générer*) un ensemble de fichiers de code source C++. Un programme *make* lit le makefile et appelle un compilateur, un éditeur de liens et éventuellement d’autres programmes pour rendre un fichier exécutable. L’implémentation Microsoft de la *rendre* programme est appelé [NMAKE](nmake-reference.md);

Si vous avez un projet makefile existant, ces choix vous sont proposés si vous voulez le coder et/ou le déboguer dans l’IDE Visual Studio :

- Créer un projet makefile dans Visual Studio qui utilise votre fichier makefile existant pour configurer un fichier .vcxproj que Visual Studio utilisera pour IntelliSense. (Vous n’aurez pas toutes les fonctionnalités de l’IDE que vous obtenez avec un projet MSBuild natif.) Consultez [Pour créer un projet Makefile](#create_a_makefile_project) ci-dessous.
- Utilisez l’Assistant **Créer un projet à partir de fichiers de code existants** pour créer un projet MSBuild natif à partir de votre code source. Le makefile d’origine ne sera pas utilisé après cela. Pour plus d'informations, voir [Procédure : créer un projet C++ à partir de code existant](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 et versions ultérieures** : Utilisez le **ouvrir le dossier** fonctionnalité pour modifier et générer un projet makefile en tant que-est sans l’intervention du système MSBuild. Pour plus d’informations, consultez [Projets Dossier ouvert pour C++](../open-folder-projects-cpp.md).

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Pour créer un projet makefile avec le modèle de projet makefile

Dans Visual Studio 2017 et les versions ultérieures, le modèle de projet Makefile est disponible quand la charge de travail de développement d’applications de bureau C++ est installée.

Suivez l’Assistant pour spécifier les commandes et l’environnement utilisés par votre makefile. Vous pouvez ensuite utiliser ce projet pour générer votre code dans Visual Studio.

Par défaut, le projet makefile n’affiche aucun fichier dans l’Explorateur de solutions. Le projet makefile spécifie les paramètres de génération qui sont reflétés dans la page de propriétés du projet.

Le fichier de sortie que vous spécifiez dans le projet n'a pas d'incidence sur le nom que le script génère ; il déclare uniquement une intention. Votre makefile contrôle toujours le processus de génération et spécifie les cibles de génération.

1. Dans la page de démarrage de Visual Studio, tapez « makefile » dans la zone de recherche **Nouveau projet**. Ou dans la boîte de dialogue **Nouveau projet**, développez **Visual C++** > **Général** (Visual Studio 2015) ou **Autre** (Visual Studio 2017), puis sélectionnez **Projet Makefile** dans le volet Modèles pour ouvrir l’Assistant Projet.

1. Dans la page **Paramètres de l’application**, indiquez les informations relatives à la ligne de commande, à la sortie, au nettoyage et à la regénération pour les builds Debug et Retail.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir le projet que vous venez de créer dans **l’Explorateur de solutions**.

Vous pouvez afficher et modifier les propriétés du projet dans sa page de propriétés. Consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md) pour plus d’informations sur l’affichage de la page de propriétés.

## <a name="makefile-project-wizard"></a>Assistant projet Makefile

Après avoir créé un projet makefile, vous pouvez afficher et modifier chacune des options suivantes dans le **Nmake** page de page de propriétés du projet.

- **Ligne de commande build :** Spécifie la ligne de commande à exécuter lorsque l’utilisateur sélectionne la Build dans le menu Générer. Affiche dans le champ de ligne de commande de Build sur la page Nmake de la page de propriétés du projet.

- **Sortie :** Spécifie le nom du fichier qui doit contenir la sortie de la ligne de commande. Par défaut, cette option est basée sur le nom du projet. Affiche dans le champ de sortie sur la page Nmake de la page de propriétés du projet.

- **Commandes de nettoyage :** Spécifie la ligne de commande à exécuter lorsque l’utilisateur sélectionne nettoyer dans le menu Générer. Affiche dans le champ de ligne de commande Clean sur la page Nmake de la page de propriétés du projet.

- **Ligne de commande Rebuild :** Spécifie la ligne de commande à exécuter lorsque l’utilisateur sélectionne la reconstruction dans le menu Générer. Affiché dans la reconstruction de tous les champs de ligne de commande sur la page Nmake de la page de propriétés du projet.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Procédure : activer IntelliSense pour des projets Makefile

Échec d’IntelliSense dans les projets makefile quand certains paramètres du projet ou les options du compilateur sont configurées incorrectement. Suivez ces étapes pour configurer des projets makefile afin qu’IntelliSense fonctionne comme prévu :

1. Ouvrez la boîte de dialogue **Pages de propriétés**. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Sélectionnez la page de propriétés **NMake**, puis modifiez les propriétés figurant sous **IntelliSense** à votre convenance.

   - Définissez la propriété **Définitions de préprocesseur** pour définir n’importe quel symbole de préprocesseur dans votre projet Makefile. Pour plus d’informations, consultez [/D (Définitions de préprocesseur)](d-preprocessor-definitions.md).

   - Définissez la propriété **Chemin de recherche Include** de façon à spécifier la liste des répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références de fichier passées aux directives de préprocesseur dans votre projet Makefile. Pour plus d’informations, consultez [/I (Autres répertoires Include)](i-additional-include-directories.md).

    - Pour les projets qui sont générés à l’aide de CL.EXE depuis une fenêtre Commande, définissez la variable d’environnement **INCLUDE** de façon à spécifier les répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références de fichier passées aux directives de préprocesseur dans votre projet Makefile.

   - Définissez la propriété **Fichiers Include forcés** pour spécifier les fichiers d’en-tête à traiter lors de la génération de votre projet Makefile. Pour plus d’informations, consultez [/FI (Nom du fichier Include imposé)](fi-name-forced-include-file.md).

   - Définissez la propriété **Chemin de recherche des assemblys** pour spécifier la liste des répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références aux assemblys .NET dans votre projet. Pour plus d’informations, consultez [/AI (Spécifier les répertoires des métadonnées)](ai-specify-metadata-directories.md).

   - Définissez la propriété **Utilisation forcée des assemblys** pour spécifier les assemblys .NET à traiter lors de la génération de votre projet Makefile. Pour plus d’informations, consultez [/FU (Nom du fichier #using imposé)](fu-name-forced-hash-using-file.md).

   - Définissez la propriété **Options supplémentaires** de façon à spécifier les commutateurs du compilateur supplémentaires que doit utiliser IntelliSense lors de l’analyse de fichiers C++.

1. Cliquez sur **OK** pour fermer les pages de propriétés.

1. Utilisez la commande **Enregistrer tout** pour enregistrer les paramètres modifiés du projet.

La prochaine fois que vous ouvrez votre projet Makefile dans l’environnement de développement Visual Studio, exécutez les commandes **Nettoyer la solution**, puis **Générer la solution** sur votre projet Makefile. IntelliSense doit fonctionner correctement dans l’IDE.

## <a name="see-also"></a>Voir aussi

[Using IntelliSense](/visualstudio/ide/using-intellisense)<br>
[Référence NMAKE](nmake-reference.md)<br>
[Guide pratique pour Créer un projet C++ à partir du Code existant](../how-to-create-a-cpp-project-from-existing-code.md)
[des caractères spéciaux dans un Makefile](special-characters-in-a-makefile.md)<br/>
[Contenu d'un makefile](contents-of-a-makefile.md)<br/>
