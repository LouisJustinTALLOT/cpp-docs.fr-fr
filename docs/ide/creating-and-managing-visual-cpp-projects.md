---
title: Création et gestion de projets Visual C++
ms.date: 11/04/2016
f1_keywords:
- vcprojects
- creatingmanagingVC
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: e511ef597e64a3782ce7a3ce650db065e9299cdd
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744325"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>Création et gestion de projets Visual C++ basés sur MSBuild

MSBuild est le système de génération natif de Visual C++ et souvent le meilleur choix pour les applications UWP et les applications de bureau qui utilisent des bibliothèques MFC ou ATL. MSBuild est étroitement intégré à l’IDE Visual Studio et au système de projet, mais vous pouvez également l’utiliser à partir de la ligne de commande. À partir de Visual Studio 2017, Visual C++ prend en charge [CMake et d’autres systèmes autres que MSBuild via la fonctionnalité Ouvrir le dossier](non-msbuild-projects.md).

Un projet MSBuild a un fichier projet au format XML (.vcxproj) qui spécifie tous les fichiers et toutes les ressources nécessaires à la compilation du programme, ainsi que d’autres paramètres de configuration, par exemple la plateforme cible (x86, x64 ou ARM) et si vous générez une version Release ou Debug du programme. Un projet (ou de nombreux projets) sont contenus dans une *solution*. Par exemple, une solution peut contenir plusieurs projets de DLL Win32 et une seule application console Win32 qui utilise ces DLL. Quand vous générez le projet, le moteur MSBuild consomme le fichier projet. En outre, il produit le fichier exécutable et/ou toute autre sortie personnalisée que vous avez spécifiée.

Vous pouvez créer des projets Visual C++ en choisissant **Fichier &#124; Nouveau &#124; Projet**, en vérifiant que Visual C++ est sélectionné dans le volet gauche, puis en choisissant des éléments dans la liste des modèles de projet du volet central. Quand vous cliquez sur un modèle, bien souvent un Assistant s’affiche pour vous permettre de définir diverses propriétés de projet avant la création du projet. Vous pouvez afficher et modifier ces propriétés ultérieurement à l’aide des pages de propriétés du projet (**Projet &#124; Propriétés**).

Vous pouvez également créer des projets comme suit :

- Choisissez **Fichier &#124; Nouveau &#124; Projet à partir de code existant**, puis suivez les instructions pour ajouter des fichiers de code source existants. Cette option est la plus appropriée pour les projets relativement petits et simples, 25 fichiers de code source tout au plus, avec peu ou pas de dépendances complexes.

- Démarrez avec un makefile, puis choisissez le modèle de projet Makefile sous l'onglet Général.

- Créez un projet vide (sous l’onglet **Général**), puis ajoutez manuellement les fichiers de code source en cliquant avec le bouton droit sur le nœud de projet dans l’Explorateur de solutions et en choisissant **Ajouter &#124; Élément existant**.

- using the [Win32 Application Wizard](../windows/win32-application-wizard.md).

## <a name="in-this-section"></a>Dans cette section

[Types de projets Visual C++](../ide/visual-cpp-project-types.md)<br>
Décrit les types de projets MSBuild qui sont disponibles dans Visual C++.

[Types de fichiers créés pour les projets Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
Décrit les types de fichiers utilisés avec divers types de projets MSBuild.

[Création de projets de bureau à l’aide des Assistants Application](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
Explique comment utiliser les Assistants pour créer des projets en Visual C++.

[Utilisation des propriétés de projet](../ide/working-with-project-properties.md)<br>
Explique comment utiliser les pages de propriétés et les feuilles de propriétés pour spécifier les paramètres de votre projet.

[Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
Explique comment ajouter des classes, des méthodes, des variables et d'autres éléments à votre projet pour ajouter des fonctionnalités.

[Guide pratique pour organiser des fichiers de sortie de projet pour les générations](../ide/how-to-organize-project-output-files-for-builds.md)<br>
Explique comment organiser les fichiers de sortie de projet.

## <a name="related-sections"></a>Rubriques connexes

[Génération de programmes C/C++](../build/building-c-cpp-programs.md)<br>
Fournit des liens vers des rubriques qui décrivent comment générer votre programme à partir de la ligne de commande ou de l'environnement de développement intégré de Visual Studio.

## <a name="see-also"></a>Voir aussi

[Kit de développement logiciel Visual Studio](https://msdn.microsoft.com/vstudio/extend)
