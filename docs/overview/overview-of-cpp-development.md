---
title: Présentation du développement C++ dans Visual Studio
description: L’IDE Visual Studio prend en charge le développement C++ sur Windows, Linux, Android et iOS avec un éditeur de code, un débogueur, des frameworks de tests, des analyseurs statiques et d’autres outils de programmation.
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 4e04e189b44fe61759a9422139d856ab8a09f201
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "77415710"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Présentation du développement C++ dans Visual Studio

Dans l’environnement de développement intégré (IDE) Visual Studio, Microsoft C++ (MSVC) partage plusieurs fenêtres et outils avec d’autres langages. Beaucoup d’entre eux, y compris **l’Explorateur de solutions**, l’éditeur de code et le débogueur, sont documentés sous [IDE Visual Studio](/visualstudio/get-started/visual-studio-ide). Il arrive souvent qu’une fenêtre ou un outil partagé n’ait pas tout à fait les mêmes fonctionnalités pour C++ que pour les autres langages. Quelques fenêtres ou outils sont disponibles seulement dans les éditions Visual Studio Professional ou Visual Studio Enterprise.

En plus des outils partagés dans l’IDE Visual Studio, MSVC propose plusieurs outils spécifiques pour le développement de code natif. Ces outils sont également répertoriés dans cet article. Pour obtenir la liste des outils disponibles dans chaque édition de Visual Studio, consultez [Outils et fonctionnalités C++ dans les éditions de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Créer des projets

Un *projet* n’est rien d’autre qu’un ensemble de fichiers de code source et de ressources comme des images ou des fichiers de données qui sont intégrés dans une bibliothèque ou un programme exécutable.

Visual Studio prend en charge tous les systèmes de projet ou outils de build personnalisés que vous voulez utiliser, avec prise en charge complète d’IntelliSense, de la navigation et du débogage :

- **MSBuild** est le système de projet natif de Visual Studio. Lorsque vous **sélectionnez File** > **New** > **Project** à partir du menu principal, vous voyez de nombreux types de modèles de projet *MSBuild* qui vous font démarrer rapidement en développant différents types d’applications C.

   ::: moniker range="vs-2019"

   ![Nouveaux modèles de projets](../build/media/mathclient-project-name-2019.png "Visual Studio 2019 Nouveau dialogue de projet")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![Modèles de projets](media/vs2017-new-project.png "Visual Studio 2017 Nouveau dialogue de projet")

   ::: moniker-end

   En règle générale, vous devez utiliser ces modèles pour les nouveaux projets, sauf si vous utilisez des projets CMake existants ou un autre système de projet. Pour plus d’informations, consultez [Création et gestion de projets basés sur MSBuild](../build/creating-and-managing-visual-cpp-projects.md).

- **CMake** est un système de construction multiplateforme intégré dans l’IDE Visual Studio lorsque vous installez le développement de bureau avec la charge de travail de C. Vous pouvez utiliser le modèle de projet CMake pour les nouveaux projets, ou simplement ouvrir un dossier avec un fichier CMakeLists.txt. Pour plus d’informations, consultez [Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md).

- Tout autre système de construction de C, y compris une collection de fichiers en vrac, est pris en charge via la fonction **Open Folder.** Vous créez des fichiers JSON simples pour appeler votre programme de génération et configurer des sessions de débogage. Pour plus d’informations, consultez [Projets Dossier ouvert pour C++](../build/open-folder-projects-cpp.md).

## <a name="add-to-source-control"></a>Ajouter au contrôle de code source

Le contrôle de code source vous permet de coordonner le travail entre plusieurs développeurs, d’isoler le travail en cours du code de production, et de sauvegarder votre code source. Visual Studio prend en charge Git et [Team Foundation Version Control \(TFVC\)](/azure/devops/repos/tfvc/) par le biais de sa fenêtre **Team Explorer**.

::: moniker range="vs-2019"

![Explorateur d’équipe](media/vs2019-team-explorer.png "Visual Studio 2017 Team Explorer")

::: moniker-end

::: moniker range="<=vs-2017"

![Explorateur d’équipe](media/vs2017-team-explorer.png "Visual Studio 2017 Team Explorer")

::: moniker-end

Pour plus d’informations sur l’intégration de Git avec les dépôts dans Azure, consultez [Partager votre code avec Visual Studio 2017 et Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Pour plus d’informations sur l’intégration de Git avec GitHub, consultez [Extension GitHub pour Visual Studio](https://visualstudio.github.com/).

## <a name="obtain-libraries"></a>Obtenir des bibliothèques

Utilisez le gestionnaire de package [vcpkg](../build/vcpkg.md) pour obtenir et installer des bibliothèques tierces. Plus de 900 bibliothèques open source sont actuellement disponibles dans le catalogue.

## <a name="create-user-interfaces-with-designers"></a>Créer des interfaces utilisateur avec les concepteurs

Si votre programme a une interface utilisateur, vous pouvez utiliser un concepteur pour y placer rapidement des contrôles, tels que des boutons, des zones de liste, et ainsi de suite. Quand vous faites glisser un contrôle à partir de la fenêtre Boîte à outils et que vous le déposez sur l’aire de conception, Visual Studio génère les ressources et le code nécessaires pour que tout fonctionne. Vous écrivez ensuite le code pour personnaliser l’apparence et le comportement.

![Concepteur et boîte à outils](media/vs2017-toolbox-designer.png "Visual Studio 2017 Boîte à outils et designer")

Pour plus d’informations sur la conception d’une interface utilisateur pour une application Universal Windows Platform, voir [Design et interface utilisateur](https://developer.microsoft.com/windows/design).

Pour plus d’informations sur la création d’une interface utilisateur pour une application MFC, consultez [Applications de bureau MFC](../mfc/mfc-desktop-applications.md). Pour plus d’informations sur les programmes Windows Win32, consultez [Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Écrire du code

Une fois que vous avez créé un projet, tous les fichiers projet s’affichent dans la fenêtre **Explorateur de solutions**. (Une *solution* est un conteneur logique pour un ou plusieurs projets connexes.) Lorsque vous cliquez sur un fichier .h ou .cpp dans **Solution Explorer**, le fichier s’ouvre dans l’éditeur de code.

![Solution Explorer et éditeur de code](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017 Solution Explorer et éditeur de code")

L'éditeur de code est un traitement de texte spécialisé pour le code source C++. Il colore selon une certaine codification les mots clés du langage, les noms des méthodes et des variables, ainsi que les autres éléments de votre code pour rendre le code plus lisible et plus facile à comprendre. Il fournit également des outils pour refactoriser le code, naviguer entre les différents fichiers et comprendre comment le code est structuré. Pour plus d’informations, consultez [Écriture et refactorisation de code](../ide/writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Ajouter et modifier des ressources

Un programme Windows ou DLL comprend généralement certaines *ressources,* telles que les dialogues, les icônes, les images, les chaînes localisées, les écrans d’éclaboussure, les chaînes de connexion de base de données, ou toute donnée arbitraire. Visual Studio comprend des outils pour ajouter et modifier des ressources. Pour plus d’informations, voir [Travailler avec les fichiers de ressources](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Générer (compiler et lier)

Choisissez **Build** > **Build Solution** sur la barre de menu, ou entrez la combinaison de clés **Ctrl-Shift-B** pour compiler et lier un projet. Les erreurs de construction et les avertissements sont signalés dans la liste d’erreurs (**CtrlMD\\, E**). La **fenêtre de sortie** **(Alt-2**) affiche des informations sur le processus de construction.

![Fenêtre de sortie et liste d’erreurs](media/vs2017-output-error-list.png "Visual Studio 2017 Fenêtre de sortie et liste d’erreurs")

Pour plus d’informations sur la configuration de builds, consultez [Utilisation des propriétés de projet](../build/working-with-project-properties.md) et [Projets et systèmes de build](../build/projects-and-build-systems-cpp.md).

Vous pouvez également utiliser le compilateur (cl.exe) et de nombreux autres outils autonomes liés à la génération, comme NMAKE et LIB, directement à partir de la ligne de commande. Pour plus d’informations, consultez [Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md) et [Informations de référence sur la génération C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Débogage

Vous pouvez démarrer le débogage en appuyant sur **F5**. Exécution pauses sur tous les points d’arrêt que vous avez définis (en appuyant sur **F9**). Vous pouvez également passer par le code une ligne à la fois (**F10**), afficher les valeurs des variables ou des registres, et même dans certains cas apporter des modifications dans le code et continuer à débogage sans re-compiler. L’illustration suivante montre une session de débogage dans laquelle l’exécution est arrêtée sur un point d’arrêt. Les valeurs des membres de la structure de données sont visibles dans la **fenêtre Espion**.

![Séance de débogage](media/vs2017-debug-watch.png "Séance de débogage Visual Studio 2017")

Pour plus d'informations, consultez [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Test

Visual Studio comprend le framework de tests unitaires Microsoft pour C++ et la prise en charge de Boost.Test, Google Test et CTest. Exécutez vos tests à partir de la fenêtre **Explorateur de tests** :

![Explorateur de tests](media/cpp-test-explorer-passed.png "Visual Studio 2017 Test Explorer")

Pour plus d’informations, consultez [Vérification du code à l’aide de tests unitaires](/visualstudio/test/unit-test-your-code) et [Écrire des tests unitaires pour C/C++ dans Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analyser

Visual Studio inclut des outils d’analyse statique du code qui peuvent détecter des problèmes potentiels dans votre code source. Ces outils incluent une implémentation des vérificateurs de règles [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md). Pour plus d’informations, consultez [Vue d’ensemble de l’analyse de code pour C/C++](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Déployer des applications terminées

Vous pouvez déployer des applications de bureau classiques et des applications UWP sur les clients par le biais du Microsoft Store. Le déploiement de la bibliothèque CRT est géré automatiquement en arrière-plan. Pour plus d’informations, consultez [Publier des applications et des jeux Windows](/windows/uwp/publish/).

Vous pouvez également déployer un bureau CMD natif sur un autre ordinateur. Pour plus d’informations, consultez [Déploiement d’applications de bureau](../windows/deploying-native-desktop-applications-visual-cpp.md).

Pour plus d’informations sur le déploiement d’un programme C++/CLI, consultez [Guide de déploiement pour les développeurs](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="next-steps"></a>Étapes suivantes

Explorez davantage Visual Studio en suivant l’un de ces articles d’introduction :

> [!div class="nextstepaction"]
> [Apprendre à utiliser l’éditeur de code](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [Découvrir les projets et les solutions](/visualstudio/get-started/tutorial-projects-solutions)
