---
title: IDE et outils de développement Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df30bdea71a890eed25f546a53e7f329fa330762
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132018"
---
# <a name="ide-and-tools-for-visual-c-development"></a>IDE et outils de développement Visual C++

Dans l’environnement de développement intégré (IDE) Visual Studio, Microsoft Visual C++ (MSVC) partage plusieurs fenêtres et outils avec d’autres langages. Beaucoup d’entre eux, y compris **l’Explorateur de solutions**, l’éditeur de code et le débogueur, sont documentés sous [IDE Visual Studio](/visualstudio/ide/visual-studio-ide). Il arrive souvent qu’une fenêtre ou un outil partagé n’ait pas tout à fait les mêmes fonctionnalités pour C++ et pour les langages .NET ou Javascript. Certaines fenêtres ou certains outils sont disponibles seulement dans Visual Studio Pro ou Visual Studio Enterprise.

En plus des outils partagés dans l’IDE Visual Studio, MSVC propose plusieurs outils spécifiques pour le développement de code natif. Ces outils sont également répertoriés dans cet article. Pour obtenir la liste des outils disponibles dans chaque édition de Visual Studio, consultez [Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="creating-a-solution-and-projects"></a>Création d'une solution et de projets

Un *projet* est essentiellement un ensemble de fichiers de code source et des ressources comme des images ou des fichiers de données qui sont intégrés dans un fichier exécutable. 

Visual Studio 2015 prend en charge les projets MSBuild. Vous pouvez télécharger des extensions Visual Studio pour d’autres systèmes de build tels que Qt ou CMake.

Visual Studio 2017 prend en charge tous les systèmes de build ou outils de build personnalisés que vous voulez utiliser, avec prise en charge complète d’IntelliSense, de la navigation et du débogage :

- MSBuild est le système de génération natif de Visual Studio et c’est souvent le meilleur choix pour les applications de plateforme Windows universelle (UWP) ou les applications de bureau Windows héritées qui utilisent MFC ou ATL. Pour plus d’informations sur les projets C++ basés sur MSBuild, consultez [Création et gestion de projets basés sur MSBuild](creating-and-managing-visual-cpp-projects.md).
- CMake est un système de génération multiplateforme intégré dans l’IDE Visual Studio quand vous installez une charge de travail Développement Desktop en C++. Pour plus d’informations, consultez [CMake projects in Visual C++](cmake-tools-for-visual-cpp.md).
- Tous les autres systèmes de génération C++, y compris un ensemble libre de fichiers, sont pris en charge via la fonctionnalité Ouvrir le dossier. Vous créez des fichiers JSON simples pour appeler votre programme de génération et configurer des sessions de débogage. Pour plus d’informations, consultez [Bring your C++ code to Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/) (Ajoutez votre code C++ dans Visual Studio).

### <a name="project-templates-msbuild"></a>Modèles de projet (MSBuild)

Visual Studio intègre plusieurs modèles pour les projets basés sur MSBuild, qui contiennent le code de démarrage et les paramètres nécessaires pour divers types de programme de base. En général, vous commencez en choisissant **Fichier** > **Nouveau projet** pour créer un projet à partir d’un modèle de projet, puis vous ajoutez de nouveaux fichiers de code source à ce projet ou vous commencez le codage dans les fichiers fournis. Pour obtenir des informations spécifiques sur les projets C++ et les Assistants Projet, consultez [Création et gestion de projets Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

### <a name="application-wizards-msbuild"></a>Assistants Application (MSBuild)

Visual Studio fournit des Assistants pour certains types de projet MSBuild quand vous choisissez **Fichier** > **Nouveau projet**. Un Assistant vous guide pas à pas à travers le processus de création d'un projet. Cela s’avère utile pour les types de projet qui ont beaucoup d’options et de paramètres. Pour plus d'informations, consultez [Création de projets Desktop à l’aide des Assistants Application](../ide/creating-desktop-projects-by-using-application-wizards.md).

## <a name="creating-user-interfaces-with-designers-msbuild"></a>Création d’interfaces utilisateur avec des concepteurs (MSBuild)

Si votre programme a une interface utilisateur, une des premières tâches à effectuer est d’y placer des contrôles, comme des boutons, des zones de liste, etc. Visual Studio inclut une aire de conception visuelle et une boîte à outils pour chaque variante des applications C++. Quel que soit le type d'application que vous créez, l'idée de base est la même : vous faites glisser un contrôle depuis la fenêtre Boîte à outils et vous le déposez sur l'aire de conception à l'emplacement souhaité. En arrière-plan, Visual Studio génère les ressources et le code requis pour que tout fonctionne. Ensuite, vous écrivez le code pour remplir les contrôles avec des données ou personnaliser leur aspect et leur comportement.

Pour plus d’informations sur la conception d’une interface utilisateur pour une application de plateforme Windows universelle, consultez [Concevoir une interface utilisateur](https://developer.microsoft.com/en-us/windows/design).

Pour plus d’informations sur la création d’une interface utilisateur pour une application MFC, consultez [Applications de bureau MFC](../mfc/mfc-desktop-applications.md). Pour plus d’informations sur les programmes Windows Win32, consultez [Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md).

## <a name="writing-and-editing-code"></a>Écriture et modification du code

### <a name="semantic-colorization"></a>Colorisation sémantique

Une fois que vous avez créé un projet, tous les fichiers projet s’affichent dans la fenêtre **Explorateur de solutions**. Quand vous cliquez sur un fichier .h ou .cpp dans **l’Explorateur de solutions**, le fichier s’ouvre dans l’éditeur de code. L'éditeur de code est un traitement de texte spécialisé pour le code source C++. Il colore selon une certaine codification les mots clés du langage, les noms des méthodes et des variables, ainsi que les autres éléments de votre code pour rendre le code plus lisible et plus facile à comprendre.

### <a name="intellisense"></a>IntelliSense

L’éditeur de code prend également en charge plusieurs fonctionnalités réunies sous le nom d’IntelliSense. Vous pouvez placer le pointeur sur une méthode et voir une documentation de base pour celui-ci. Après avoir tapé un nom de variable de classe et un « . » ou « -> », une liste des membres de l'instance de cette classe s'affiche. Si vous tapez un nom de classe, puis « :: », une liste des membres statiques s'affiche. Quand vous commencez à taper un nom de classe ou de méthode, l'éditeur de code affiche des suggestions pour compléter l'instruction. Pour plus d’informations, consultez [Utilisation d’IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="code-snippets"></a>Extraits de code

Vous pouvez utiliser des extraits de code IntelliSense pour générer des constructions de code fréquemment utilisées ou compliquées avec un raccourci clavier. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).

## <a name="navigating-code"></a>Navigation dans le code

Le menu **Affichage** permet d’accéder à de nombreuses fenêtres et de nombreux outils pour naviguer dans vos fichiers de code. Pour obtenir des informations détaillées sur ces fenêtres, consultez [Affichage de la structure du code](/visualstudio/ide/viewing-the-structure-of-code).

### <a name="solution-explorer"></a>Explorateur de solutions

Dans toutes les éditions de Visual Studio, utilisez le volet **Explorateur de solutions** pour parcourir les fichiers d’un projet. Développez une icône de fichier .h ou .cpp pour afficher les classes du fichier. Développez une classe pour voir ses membres. Double-cliquez sur un membre pour accéder à sa définition ou à son implémentation dans le fichier.

### <a name="class-view-and-code-definition-window"></a>Affichage de classes et fenêtre Définition de code

Utilisez le volet **Affichage de classes** pour voir les espaces de noms et les classes dans tous les fichiers, y compris les classes partielles. Vous pouvez développer chaque espace de noms ou chaque classe pour voir ses membres et double-cliquer sur le membre pour accéder à cet emplacement dans le fichier source. Si vous ouvrez la **fenêtre Définition de code**, vous pouvez voir la définition ou l’implémentation du type quand vous le choisissez dans **Affichage de classes**.

### <a name="object-browser"></a>Explorateur d'objets

Utilisez **l’Explorateur d’objets** pour explorer les informations sur les types dans les composants Windows Runtime (fichiers .winmd), les assemblys .NET et les bibliothèques de types COM. Il n'est pas utilisé avec les DLL Win32.

### <a name="go-to-definitiondeclaration"></a>Accéder à la définition/déclaration

Appuyez sur F12 sur un nom d'API ou une variable d'un membre pour accéder à sa définition. Si la définition se trouve dans un fichier .winmd (pour une application UWP ou du Windows Store 8.x), les informations sur le type s’affichent dans l’Explorateur d’objets. Vous pouvez également choisir **Accéder à la définition** ou **Accéder à la déclaration** en cliquant avec le bouton droit sur le nom ou le type d’une variable, puis en choisissant l’option dans le menu contextuel.

### <a name="find-all-references"></a>Rechercher toutes les références

Dans un fichier de code source, cliquez avec le bouton droit sur le nom d’un type, d’une méthode ou d’une variable, puis choisissez **Rechercher toutes les références** pour obtenir la liste de tous les emplacements dans le fichier, le projet ou la solution où le type est utilisé. **Rechercher toutes les références** fonctionne de façon intelligente et retourne seulement les instances d’une même variable, même si d’autres variables ont le même nom dans d’autres portées.

## <a name="add-and-edit-resources--msbuild"></a>Ajouter et modifier des ressources (MSBuild)

Le terme *ressource* dans le contexte d’un projet Desktop Visual Studio correspond à des éléments comme des boîtes de dialogue, des icônes, des chaînes localisables, des écrans de démarrage, des chaînes de connexion de base de données ou des données arbitraires que vous voulez inclure dans le fichier exécutable.

Pour plus d’informations sur l’ajout et la modification de ressources dans les projets Desktop C++ natifs, consultez [Utilisation de fichiers de ressources](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Générer (compiler et lier)

Choisissez **Générer** > **Générer la solution** dans la barre de menus ou entrez la combinaison de touches Ctrl + Maj + B pour compiler et lier un projet. Pour créer du code exécutable, Visual Studio utilise [MSBuild](/visualstudio/msbuild/msbuild1) ou CMake, ou l’environnement de génération que vous avez configuré via **Ouvrir le dossier**. Pour les projets MSBuild, vous définissez des options générales de génération sous **Outils** > **Options** > **Projets et solutions** et vous pouvez définir des propriétés pour des projets spécifiques sous **Projet** > **Propriétés**. Les erreurs et les avertissements de génération sont signalés dans la liste des erreurs (Ctrl+\\, E). Les projets non-MSBuild sont configurés avec des fichiers JSON que vous créez dans l’Explorateur de solutions. Quel que soit le système de génération que vous utilisez, la fenêtre **Sortie** (Alt + 2) montre les informations du processus de génération. Pour plus d’informations sur les configurations MSBuild, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md) et [Génération de projets C++ dans Visual Studio](../ide/building-cpp-projects-in-visual-studio.md).

Vous pouvez également utiliser le compilateur (cl.exe) et de nombreux autres outils autonomes liés à la génération, comme NMAKE et LIB, directement à partir de la ligne de commande. Pour plus d’informations, consultez [Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md) et [Informations de référence sur la génération C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="test"></a>Tester

Visual Studio inclut une infrastructure de tests unitaires pour le code C++ natif et pour C++/CLI. Pour plus d’informations, consultez [Vérification du code à l’aide de tests unitaires](/visualstudio/test/unit-test-your-code) et [Écriture de tests unitaires pour C/C++ avec le framework de tests unitaires Microsoft pour C++](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="analyze"></a>Analyser

Visual Studio inclut des outils d’analyse de code statique pour C++, notamment une implémentation des vérificateurs de règles [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md). Pour plus d’informations, consultez [Vue d’ensemble de l’analyse de code pour C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="debug"></a>Débogage

Vous pouvez déboguer votre programme en appuyant sur **F5** quand votre configuration de projet est définie sur Debug. Pendant le débogage, vous pouvez définir des points d’arrêt en appuyant sur **F9**, parcourir le code pas à pas en appuyant sur **F10**, voir les valeurs de variables ou registres spécifiés et même, dans certains cas, modifier le code et continuer le débogage sans recompiler. Pour plus d’informations, consultez [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="deploy-completed-applications"></a>Déployer des applications terminées

Vous déployez une application UWP pour les clients par le biais du Microsoft Store en accédant à l’option de menu **Projet** > **Store**. Le déploiement de la bibliothèque CRT est géré automatiquement en arrière-plan. Pour plus d’informations, consultez [Publier des applications et des jeux Windows](/windows/uwp/publish/). 

Quand vous déployez une application de bureau C++ native sur un autre ordinateur, vous devez installer l'application elle-même et tous les fichiers bibliothèques dont elle dépend. Il existe trois façons de déployer le runtime universel C++ (UCRT) avec une application : le déploiement central, le déploiement local ou la liaison statique. Pour plus d’informations, consultez [Déploiement d’applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md).

Pour plus d’informations sur le déploiement d’un programme C++/CLI, consultez [Guide de déploiement pour les développeurs](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="related-articles"></a>Articles connexes

|||
|-|-|
|[Outils et fonctionnalités Visual C++ dans les éditions de Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|Affiche toutes les fonctionnalités disponibles dans les différentes éditions de Visual Studio.|
|[Création et gestion de projets basés sur MSBuild](../ide/creating-and-managing-visual-cpp-projects.md)|Fournit une vue d’ensemble des projets C++ basés sur MSBuild dans Visual Studio et des liens vers d’autres articles qui expliquent comment les créer et les gérer.|
|[Projets CMake dans Visual C++](cmake-tools-for-visual-cpp.md).|Décrit comment générer des projets CMake ou d’autres projets non-MSBuild en Visual C++.|
|[Génération de programmes C/C++](../build/building-c-cpp-programs.md)|Décrit comment générer des projets C++.|
|[Déploiement des applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)|Fournit une vue d'ensemble du déploiement pour les applications C++ et des liens vers d'autres articles qui décrivent le déploiement en détail.|
|[Guide du portage et de la mise à niveau de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Informations détaillées sur la mise à niveau d’applications C++ qui ont été créées dans des versions antérieures de Visual Studio et sur la migration des applications qui ont été créées avec des outils autres que Visual Studio.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Décrit les principales fonctionnalités de Visual C++ dans Visual Studio et fournit un lien vers le reste de la documentation Visual C++.|
