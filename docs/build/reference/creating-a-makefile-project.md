---
description: 'En savoir plus sur : créer un projet Makefile C++'
title: Créer un projet Makefile C++ dans Visual Studio
ms.date: 08/05/2019
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects [C++]
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 16b678d5ab8866f2875c20d7016657373d100f7b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196956"
---
# <a name="create-a-c-makefile-project"></a>Créer un projet Makefile C++

Un *makefile* est un fichier texte qui contient des instructions indiquant comment compiler et lier (ou *générer*) un ensemble de fichiers de code source C++. Un programme *make* lit le makefile et appelle un compilateur, un éditeur de liens et éventuellement d’autres programmes pour rendre un fichier exécutable. L’implémentation Microsoft du programme *Make* est appelée [NMAKE](nmake-reference.md).

Si vous avez un projet makefile existant, ces choix vous sont proposés si vous voulez le coder et/ou le déboguer dans l’IDE Visual Studio :

- Créez un projet Makefile dans Visual Studio qui utilise votre Makefile existant pour configurer un fichier .vcxproj que Visual Studio utilisera pour IntelliSense. (Vous ne disposez pas de toutes les fonctionnalités IDE que vous obtiendrez avec un projet MSBuild natif.) Consultez [pour créer un projet Makefile](#create_a_makefile_project) ci-dessous.
- Utilisez l’Assistant **Créer un projet à partir de fichiers de code existants** pour créer un projet MSBuild natif à partir de votre code source. Le Makefile d’origine ne sera pas utilisé après cela. Pour plus d’informations, consultez [Guide pratique pour créer un projet C++ à partir d’un code existant](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 et versions ultérieures**: utilisez la fonctionnalité **ouvrir un dossier** pour modifier et générer un projet Makefile tel quel, sans aucune implication du système MSBuild. Pour plus d’informations, consultez [Projets Dossier ouvert pour C++](../open-folder-projects-cpp.md).
- **Visual Studio 2019 et versions ultérieures**: créez un projet Makefile UNIX pour Linux.

## <a name="a-namecreate_a_makefile_project-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Pour créer un projet Makefile avec le modèle de projet Makefile

Dans Visual Studio 2017 et les versions ultérieures, le modèle de projet Makefile est disponible quand la charge de travail de développement d’applications de bureau C++ est installée.

Suivez l’Assistant pour spécifier les commandes et l’environnement utilisés par votre makefile. Vous pouvez ensuite utiliser ce projet pour générer votre code dans Visual Studio.

Par défaut, le projet makefile n’affiche aucun fichier dans l’Explorateur de solutions. Le projet makefile spécifie les paramètres de génération qui sont reflétés dans la page de propriétés du projet.

Le fichier de sortie que vous spécifiez dans le projet n'a pas d'incidence sur le nom que le script génère ; il déclare uniquement une intention. Votre makefile contrôle toujours le processus de génération et spécifie les cibles de génération.

::: moniker range="msvc-160"

### <a name="to-create-a-makefile-project-in-visual-studio-2019"></a>Pour créer un projet Makefile dans Visual Studio 2019

1. Dans le menu principal de Visual Studio, choisissez **fichier**  >  **nouveau**  >  **projet** et tapez « Makefile » dans la zone de recherche. Sinon, dans la boîte de dialogue **Nouveau projet**, développez **Visual C++** > **Général** (Visual Studio 2015) ou **Autre** (Visual Studio 2017), puis choisissez entre les deux options selon si vous ciblez Windows ou Linux.

1. **Windows uniquement**: dans la page **paramètres de configuration de débogage** , fournissez les informations de commande, de sortie, de nettoyage et de régénération pour les builds de débogage et de vente au détail. Cliquez sur **Suivant** si vous souhaitez spécifier différents paramètres pour une configuration Release.

1. Cliquez sur **Terminer** pour fermer la boîte de dialogue et ouvrir le projet que vous venez de créer dans l’**Explorateur de solutions**.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-a-makefile-project-in-visual-studio-2015-or-visual-studio-2017"></a>Pour créer un projet Makefile dans Visual Studio 2015 ou Visual Studio 2017

1. Dans la page de démarrage de Visual Studio, tapez « makefile » dans la zone de recherche **Nouveau projet**. Ou dans la boîte de dialogue **Nouveau projet**, développez **Visual C++** > **Général** (Visual Studio 2015) ou **Autre** (Visual Studio 2017), puis sélectionnez **Projet Makefile** dans le volet Modèles pour ouvrir l’Assistant Projet.

1. Dans la page **Paramètres de l’application**, indiquez les informations relatives à la ligne de commande, à la sortie, au nettoyage et à la regénération pour les builds Debug et Retail.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir le projet que vous venez de créer dans **l’Explorateur de solutions**.

::: moniker-end

Vous pouvez afficher et modifier les propriétés du projet dans sa page de propriétés. Consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md) pour plus d’informations sur l’affichage de la page de propriétés.

## <a name="makefile-project-wizard"></a>Assistant Projet Makefile

Une fois que vous avez créé un projet Makefile, vous pouvez afficher et modifier chacune des options suivantes dans la page **Nmake** de la page de propriétés du projet.

- **Ligne de commande de build :** Spécifie la ligne de commande à exécuter lorsque l’utilisateur sélectionne générer dans le menu Générer. Cette option est affichée dans le champ Ligne de commande Build de la page Nmake de la page de propriétés du projet.

- **Sortie :** Spécifie le nom du fichier qui contiendra la sortie de la ligne de commande. Par défaut, cette option est basée sur le nom du projet. Cette option est affichée dans le champ Sortie de la page Nmake de la page de propriétés du projet.

- **Commandes Clean :** Spécifie la ligne de commande à exécuter lorsque l’utilisateur sélectionne nettoyer dans le menu Générer. Cette option est affichée dans le champ Ligne de commande Clean de la page Nmake de la page de propriétés du projet.

- **Ligne de commande Rebuild :** Spécifie la ligne de commande à exécuter lorsque l’utilisateur sélectionne régénérer dans le menu Générer. Cette option est affichée dans le champ Ligne de commande Rebuild All de la page Nmake de la page de propriétés du projet.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Comment : activer IntelliSense pour des projets Makefile

IntelliSense ne fonctionne pas dans les projets Makefile quand des paramètres de projet, ou options du compilateur, sont incorrectement configurés. Suivez ces étapes pour configurer des projets Makefile afin qu’IntelliSense fonctionne comme prévu :

1. Ouvrez la boîte de dialogue **Pages de propriétés**. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Sélectionnez la page de propriétés **NMake**, puis modifiez les propriétés figurant sous **IntelliSense** à votre convenance.

   - Définissez la propriété **Définitions de préprocesseur** pour définir n’importe quel symbole de préprocesseur dans votre projet Makefile. Pour plus d’informations, consultez [/D (Définitions de préprocesseur)](d-preprocessor-definitions.md).

   - Définissez la propriété **Chemin de recherche Include** de façon à spécifier la liste des répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références de fichier passées aux directives de préprocesseur dans votre projet Makefile. Pour plus d’informations, consultez [/I (Autres répertoires Include)](i-additional-include-directories.md).

   - Pour les projets qui sont générés à l’aide de CL.EXE depuis une fenêtre Commande, définissez la variable d’environnement **INCLUDE** de façon à spécifier les répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références de fichier passées aux directives de préprocesseur dans votre projet Makefile.

   - Définissez la propriété **Fichiers Include forcés** pour spécifier les fichiers d’en-tête à traiter lors de la génération de votre projet Makefile. Pour plus d’informations, consultez [/FI (Nom du fichier Include imposé)](fi-name-forced-include-file.md).

   - Définissez la propriété **Chemin de recherche des assemblys** pour spécifier la liste des répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références aux assemblys .NET dans votre projet. Pour plus d’informations, consultez [/AI (Spécifier les répertoires des métadonnées)](ai-specify-metadata-directories.md).

   - Définissez la propriété **Utilisation forcée des assemblys** pour spécifier les assemblys .NET à traiter lors de la génération de votre projet Makefile. Pour plus d’informations, consultez [/FU (Nom du fichier #using imposé)](fu-name-forced-hash-using-file.md).

   - Définissez la propriété **options supplémentaires** pour spécifier les commutateurs de compilateur supplémentaires utilisés par IntelliSense lors de l’analyse des fichiers C++.

1. Cliquez sur **OK** pour fermer les pages de propriétés.

1. Utilisez la commande **Enregistrer tout** pour enregistrer les paramètres modifiés du projet.

La prochaine fois que vous ouvrez votre projet Makefile dans l’environnement de développement Visual Studio, exécutez les commandes **Nettoyer la solution**, puis **Générer la solution** sur votre projet Makefile. IntelliSense doit fonctionner correctement dans l’IDE.

## <a name="see-also"></a>Voir aussi

[Utilisation d’IntelliSense](/visualstudio/ide/using-intellisense)<br>
[Référence NMAKE](nmake-reference.md)<br>
[Guide pratique pour créer un projet C++ à partir d’un code existant](../how-to-create-a-cpp-project-from-existing-code.md)<br>
[Caractères spéciaux dans un Makefile](special-characters-in-a-makefile.md)<br/>
[Contenu d’un Makefile](contents-of-a-makefile.md)<br/>
