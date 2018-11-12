---
title: IDE et outils de développement Visual C++
description: L’IDE Visual Studio prend en charge le développement C++ sur Windows, Linux, Android et iOS avec un éditeur de code, un débogueur, des frameworks de tests, des analyseurs statiques et d’autres outils de programmation.
ms.date: 09/27/2018
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
ms.openlocfilehash: e24ba58cf0cf94f1505adaf056f64580b8f7829e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473357"
---
# <a name="ide-and-compiler-tools-for-visual-c-development"></a>IDE et outils du compilateur pour le développement Visual C++

Dans l’environnement de développement intégré (IDE) Visual Studio, Microsoft Visual C++ (MSVC) partage plusieurs fenêtres et outils avec d’autres langages. Beaucoup d’entre eux, y compris **l’Explorateur de solutions**, l’éditeur de code et le débogueur, sont documentés sous [IDE Visual Studio](/visualstudio/ide/visual-studio-ide). Il arrive souvent qu’une fenêtre ou un outil partagé n’ait pas tout à fait les mêmes fonctionnalités pour C++ et pour les langages .NET ou JavaScript. Quelques fenêtres ou outils sont disponibles seulement dans les éditions Visual Studio Professional ou Visual Studio Enterprise.

En plus des outils partagés dans l’IDE Visual Studio, MSVC propose plusieurs outils spécifiques pour le développement de code natif. Ces outils sont également répertoriés dans cet article. Pour obtenir la liste des outils disponibles dans chaque édition de Visual Studio, consultez [Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Créer des projets

Un *projet* est essentiellement un ensemble de fichiers de code source et des ressources comme des images ou des fichiers de données qui sont intégrés dans un fichier exécutable.

Visual Studio 2015 prend en charge les projets MSBuild. Vous pouvez télécharger des extensions Visual Studio pour d’autres systèmes de build tels que Qt ou CMake.

Visual Studio 2017 prend en charge tous les systèmes de build ou outils de build personnalisés que vous voulez utiliser, avec prise en charge complète d’IntelliSense, de la navigation et du débogage :

- **MSBuild** est le système de génération natif de Visual Studio. Quand vous sélectionnez **Fichier** > **Nouveau** > **Projet** dans le menu principal, vous voyez de nombreux types de *modèles de projet*  MSBuild qui vous aideront à développer rapidement différents types d’applications C++.

   ![Modèles de projet](media/vs2017-new-project.png "Boîte de dialogue Nouveau projet de Visual Studio 2017")

   En règle générale, vous devez utiliser ces modèles pour les nouveaux projets, sauf si vous avez une raison spécifique d’utiliser CMake ou un autre système de projet. Certains projets ont un *Assistant* qui vous guide pas à pas à travers le processus de création d’un projet. Pour plus d’informations, consultez [Création et gestion de projets basés sur MSBuild](creating-and-managing-visual-cpp-projects.md).

- **CMake** est un système de génération multiplateforme intégré dans l’IDE Visual Studio quand vous installez une charge de travail Développement Desktop en C++. Pour plus d’informations, consultez [CMake projects in Visual C++](cmake-tools-for-visual-cpp.md).
- Tous les autres systèmes de génération C++, notamment un ensemble libre de fichiers, sont pris en charge via la fonctionnalité **Ouvrir le dossier**. Vous créez des fichiers JSON simples pour appeler votre programme de génération et configurer des sessions de débogage. Pour plus d’informations, consultez [Open Folder projects in Visual C++](non-msbuild-projects.md).

## <a name="add-to-source-control"></a>Ajouter au contrôle de code source

Le contrôle de code source vous permet de coordonner le travail entre plusieurs développeurs, d’isoler le travail en cours du code de production, et de sauvegarder votre code source. Visual Studio prend en charge Git et [Team Foundation Version Control \(TFVC\)](/azure/devops/repos/tfvc/) par le biais de sa fenêtre **Team Explorer**.

![Team Explorer](media/vs2017-team-explorer.png "Visual Studio 2017 Team Explorer")

Pour plus d’informations sur l’intégration de Git avec les dépôts dans Azure, consultez [Partager votre code avec Visual Studio 2017 et Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017). Pour plus d’informations sur l’intégration de Git avec GitHub, consultez [Extension GitHub pour Visual Studio](https://visualstudio.github.com/).

## <a name="create-user-interfaces-with-designers"></a>Créer des interfaces utilisateur avec les concepteurs

Si votre programme a une interface utilisateur, vous pouvez utiliser un concepteur pour y placer rapidement des contrôles, tels que des boutons, des zones de liste, et ainsi de suite. Quand vous faites glisser un contrôle à partir de la fenêtre Boîte à outils et que vous le déposez sur l’aire de conception, Visual Studio génère les ressources et le code nécessaires pour que tout fonctionne. Vous écrivez ensuite le code pour personnaliser l’apparence et le comportement.

![Concepteur et Boîte à outils](media/vs2017-toolbox-designer.png "Concepteur et Boîte à outils de Visual Studio 2017")

Pour plus d’informations sur la conception d’une interface utilisateur pour une application de plateforme Windows universelle, consultez [Concevoir une interface utilisateur](https://developer.microsoft.com/windows/design).

Pour plus d’informations sur la création d’une interface utilisateur pour une application MFC, consultez [Applications de bureau MFC](../mfc/mfc-desktop-applications.md). Pour plus d’informations sur les programmes Windows Win32, consultez [Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Écrire du code

Une fois que vous avez créé un projet, tous les fichiers projet s’affichent dans la fenêtre **Explorateur de solutions**. (Une *solution* est un conteneur logique pour un ou plusieurs projets associés.) Quand vous cliquez sur un fichier .h ou .cpp dans **l’Explorateur de solutions**, le fichier s’ouvre dans l’éditeur de code.

![Explorateur de solutions et éditeur de code](media/vs2017-solution-explorer-code-editor.png "Explorateur de solutions et éditeur de code de Visual Studio 2017")

L'éditeur de code est un traitement de texte spécialisé pour le code source C++. Il colore selon une certaine codification les mots clés du langage, les noms des méthodes et des variables, ainsi que les autres éléments de votre code pour rendre le code plus lisible et plus facile à comprendre.

Pour plus d’informations, consultez [Écriture et refactorisation de code](writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Ajouter et modifier des ressources

Le terme *ressource* correspond à des éléments comme des boîtes de dialogue, des icônes, des chaînes localisables, des écrans de démarrage, des chaînes de connexion de base de données ou des données arbitraires que vous voulez inclure dans le fichier exécutable.

Pour plus d’informations sur l’ajout et la modification de ressources dans les projets Desktop C++ natifs, consultez [Utilisation de fichiers de ressources](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Générer (compiler et lier)

Choisissez **Générer** > **Générer la solution** dans la barre de menus ou entrez la combinaison de touches Ctrl + Maj + B pour compiler et lier un projet. Les erreurs et les avertissements de génération sont signalés dans la liste des erreurs (Ctrl+\\, E). La fenêtre **Sortie** (Alt+2) montre les informations du processus de génération.

![Fenêtre Sortie et Liste d’erreurs](media/vs2017-output-error-list.png "Fenêtre Sortie et Liste d’erreurs dans Visual Studio 2017") Pour plus d’informations sur les configurations MSBuild, consultez [Utilisation des propriétés de projet](working-with-project-properties.md) et [Génération de projets C++ dans Visual Studio](building-cpp-projects-in-visual-studio.md).

Vous pouvez également utiliser le compilateur (cl.exe) et de nombreux autres outils autonomes liés à la génération, comme NMAKE et LIB, directement à partir de la ligne de commande. Pour plus d’informations, consultez [Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md) et [Informations de référence sur la génération C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Débogage

Vous pouvez démarrer le débogage en appuyant sur **F5**. L’exécution s’arrête sur les points d’arrêt que vous avez définis. Vous pouvez également parcourir le code ligne par ligne, voir les valeurs de variables ou registres et même, dans certains cas, modifier le code et continuer le débogage sans recompiler. L’illustration suivante montre une session de débogage dans laquelle l’exécution est arrêtée sur un point d’arrêt. Les valeurs des membres de la structure de données sont visibles dans la **fenêtre Espion**.

![Session de débogage](media/vs2017-debug-watch.png "Session de débogage dans Visual Studio 2017")

Pour plus d’informations, consultez [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Tester

Visual Studio inclut des frameworks de tests unitaires pour le code C++ natif et pour C++/CLI. Boost.Test, Google Test et CTest sont également pris en charge. Exécutez vos tests à partir de la fenêtre **Explorateur de tests** :

![Explorateur de tests](media/cpp-test-explorer-passed.png "Explorateur de tests Visual Studio 2017")

Pour plus d’informations, consultez [Vérification du code à l’aide de tests unitaires](/visualstudio/test/unit-test-your-code) et [Écrire des tests unitaires pour C/C++ dans Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analyze

Visual Studio inclut des outils d’analyse statique du code qui peuvent détecter des problèmes potentiels dans votre code source. Ces outils incluent une implémentation des vérificateurs de règles [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md). Pour plus d’informations, consultez [Vue d’ensemble de l’analyse de code pour C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Déployer des applications terminées

Vous pouvez déployer des applications de bureau classiques et des applications UWP sur les clients par le biais du Microsoft Store. Le déploiement de la bibliothèque CRT est géré automatiquement en arrière-plan. Pour plus d’informations, consultez [Publier des applications et des jeux Windows](/windows/uwp/publish/).

Vous pouvez également déployer une application de bureau C++ native sur un autre ordinateur. Pour plus d’informations, consultez [Déploiement des applications de bureau](deploying-native-desktop-applications-visual-cpp.md).

Pour plus d’informations sur le déploiement d’un programme C++/CLI, consultez [Guide de déploiement pour les développeurs](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="related-articles"></a>Articles connexes

|||
|-|-|
|[Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)|Affiche toutes les fonctionnalités disponibles dans les différentes éditions de Visual Studio.|
|[Création et gestion de projets basés sur MSBuild](creating-and-managing-visual-cpp-projects.md)|Fournit une vue d’ensemble des projets C++ basés sur MSBuild dans Visual Studio et des liens vers d’autres articles qui expliquent comment les créer et les gérer.|
|[Projets CMake dans Visual C++](cmake-tools-for-visual-cpp.md).|Décrit comment générer des projets CMake ou d’autres projets non-MSBuild en Visual C++.|
|[Génération de programmes C/C++](../build/building-c-cpp-programs.md)|Décrit comment générer des projets C++.|
|[Déploiement des applications de bureau](deploying-native-desktop-applications-visual-cpp.md)|Fournit une vue d'ensemble du déploiement pour les applications C++ et des liens vers d'autres articles qui décrivent le déploiement en détail.|
|[Guide du portage et de la mise à niveau de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Informations détaillées sur la mise à niveau d’applications C++ qui ont été créées dans des versions antérieures de Visual Studio et sur la migration des applications qui ont été créées avec des outils autres que Visual Studio.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Décrit les principales fonctionnalités de Visual C++ dans Visual Studio et fournit un lien vers le reste de la documentation Visual C++.|
