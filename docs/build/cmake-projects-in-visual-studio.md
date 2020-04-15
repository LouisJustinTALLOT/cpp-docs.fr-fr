---
title: Projets CMake dans Visual Studio
description: Comment créer et construire des projets CMD à l’aide de CMake dans Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329159"
---
# <a name="cmake-projects-in-visual-studio"></a>Projets CMake dans Visual Studio

CMake est un outil open source multiplateforme utilisé pour définir des processus de génération qui s’exécutent sur plusieurs plateformes. Cet article suppose que vous êtes familier avec CMake. Pour en savoir plus, consultez [Générer, tester et empaqueter votre logiciel avec CMake](https://cmake.org/).

> [!NOTE]
> CMake est devenu de plus en plus intégré avec Visual Studio au cours des dernières versions. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

Les **outils CMake pour** composant Windows utilisent la fonction Open [Folder](open-folder-projects-cpp.md) pour consommer des fichiers de projet CMake (tels que *CMakeLists.txt*) directement aux fins d’IntelliSense et de navigation. Les générateurs Ninja et Visual Studio sont pris en charge. Si vous utilisez un générateur Visual Studio, il génère un fichier de projet temporaire et le transmet à msbuild.exe. Cependant, le projet n’est jamais chargé à des fins de navigation ou de navigation. Vous pouvez également importer un cache CMake existant.

## <a name="installation"></a>Installation

**Les outils CMake pour Windows** sont installés dans le cadre du **développement de bureau avec le développement C et** Linux avec des charges de travail **CMD.** Pour plus d’informations, voir [Cross-platform CMake projects](../linux/cmake-linux-project.md).

![Composant CMake dans la charge de travail Desktop C++](media/cmake-install-2019.png)

Pour plus d’informations, consultez [Installer la charge de travail Linux C++ dans Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Intégration à l’IDE

Lorsque vous choisissez **File > Open > Folder** pour ouvrir un dossier contenant un fichier *CMakeLists.txt,* les choses suivantes se produisent:

- Visual Studio ajoute des éléments **CMake** au menu **du projet,** avec des commandes pour visionner et modifier les scripts CMake.

- **L’Explorateur de solutions** affiche la structure de dossiers et les fichiers.

- Visual Studio fonctionne cmake.exe et génère le fichier de cache CMake (*CMakeCache.txt*) pour la configuration par défaut (x64 Debug). La ligne de commande CMake s’affiche dans la **fenêtre Sortie**, ainsi que la sortie supplémentaire de CMake.

- En arrière-plan, Visual Studio démarre pour indexer les fichiers sources afin d’activer IntelliSense, les informations de navigation, la refactorisation et ainsi de suite. Pendant que vous travaillez, Visual Studio surveille les changements dans l’éditeur et sur le disque pour synchroniser son index avec les sources.

Vous pouvez ouvrir des dossiers avec un nombre quelconque de projets CMake. Visual Studio détecte et configure tous les fichiers *CMakeLists.txt* «root» dans votre espace de travail. Les opérations CMake (configurer, construire, déboiffer), CMd IntelliSense et la navigation sont disponibles pour tous les projets CMake dans votre espace de travail.

![Projet CMake avec plusieurs racines](media/cmake-multiple-roots.png)

Vous pouvez également voir vos projets organisées logiquement par cibles. Choisissez **Targets view** (Affichage des cibles) dans la liste déroulante dans la barre d’outils de **l’Explorateur de solutions** :

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png)

Cliquez sur le bouton **Afficher tous les fichiers** en haut de Solution **Explorer** pour voir toute la sortie générée par CMake dans les dossiers *>\<out/build/config.*

Visual Studio utilise un fichier de configuration appelé **CMakeSettings.json**. Ce fichier vous permet de définir et de stocker plusieurs configurations de construction, et commodément basculer entre eux dans l’IDE. Une *configuration* est une construction Visual Studio qui encapsule les paramètres spécifiques à un type de construction donné. Les paramètres sont utilisés pour configurer les options de ligne de commande par défaut que Visual Studio passe à cmake.exe. Vous pouvez également spécifier des options CMake supplémentaires ici, et définir toutes les variables supplémentaires que vous aimez. Toutes les options sont écrites au cache CMake en tant que variables internes ou externes. Dans Visual Studio 2019, **l’éditeur CMake Settings** offre un moyen pratique de modifier vos paramètres. Pour plus d’informations, consultez [les paramètres Personnaliser CMake](customize-cmake-settings.md).

Un paramètre, `intelliSenseMode` n’est pas passé à CMake, mais est utilisé uniquement par Visual Studio.

Utilisez le fichier **CMakeLists.txt** dans chaque dossier de projet comme vous le feriez dans n’importe quel projet CMake. Vous pouvez spécifier des fichiers source, trouver des bibliothèques, définir des options de compilateur et de liaison, et spécifier d’autres informations liées au système de construction.

Pour passer des arguments à un exécutable au moment de déboguer, vous pouvez utiliser un autre fichier appelé **launch.vs.json**. Dans certains scénarios, Visual Studio génère automatiquement ces fichiers. Vous pouvez les modifier manuellement, ou même créer le fichier vous-même.

> [!NOTE]
> Pour d’autres types de projets Open Folder, deux fichiers JSON supplémentaires sont utilisés: **CppProperties.json** et **tasks.vs.json**. Aucun des deux n’est pertinent pour les projets CMake.

## <a name="open-an-existing-cache"></a>Ouvrez un cache existant

Lorsque vous ouvrez un fichier de cache CMake existant (*CMakeCache.txt*), Visual Studio n’essaie pas de gérer votre cache et de construire un arbre pour vous. Vos outils personnalisés ou préférés ont un contrôle total sur la façon dont CMake configure votre projet. Pour ouvrir un cache existant dans Visual Studio, choisissez **File > Open > CMake**. Ensuite, naviguez vers un fichier *CMakeCache.txt* existant.

Vous pouvez ajouter un cache CMake existant à un projet ouvert. Il est fait de la même façon que vous ajouteriez une nouvelle configuration. Pour plus d’informations, consultez notre blog sur [l’ouverture d’un cache existant dans Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Génération de projets CMake

Pour générer un projet CMake, vous avez ces possibilités :

1. Dans la barre d’outils Général, recherchez la liste déroulante **Configurations**. Il montre probablement "x64-Debug" par défaut. Sélectionnez la configuration préférée et appuyez sur **F5**, ou cliquez sur le bouton **Run** (triangle vert) sur la barre d’outils. Le projet est d’abord généré automatiquement, comme une solution Visual Studio.

1. Cliquez à droite sur *CMakeLists.txt* et **sélectionnez Build** à partir du menu context. Si vous avez plusieurs cibles dans votre structure de dossiers, vous pouvez choisir de générer toutes les cibles ou une seule cible spécifique.

1. Dans le menu principal, sélectionnez **Build > Build All** (**F7** ou **Ctrl-ShiftMD B**). Vérifiez qu’une cible CMake est déjà sélectionnée dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**.

![CMake construire la commande de menu](media/cmake-build-menu.png "CMake construire menu de commande")

Comme attendu, les résultats de génération sont affichés dans la **fenêtre sortie** et la **Liste des erreurs**.

![CMake construire des erreurs](media/cmake-build-errors.png "CMake construire des erreurs")

Dans un dossier avec plusieurs cibles de construction, vous pouvez spécifier quelle cible CMake à construire : Choisissez l’élément **Build** sur le menu **CMake** ou le menu context context *CMakeLists.txt* pour spécifier la cible. Si vous entrez **dans le cadre d’un** projet CMake, il construit le document actif actuel.

## <a name="debugging-cmake-projects"></a>Débogage de projets CMake

Pour déboguer un projet CMake, choisissez la configuration préférée et appuyez sur **F5,** ou appuyez sur le bouton **Run** dans la barre d’outils. Si le bouton **Exécuter** indique « Sélectionnez l’élément de démarrage », sélectionnez la flèche de chute. Choisissez la cible que vous souhaitez exécuter. (Dans un projet CMake, l’option « Document actif » est uniquement valide pour les fichiers .cpp.)

![Bouton D’exécution CMake](media/cmake-run-button.png "Bouton D’exécution CMake")

Les commandes **Exécuter** ou **F5** génèrent d’abord le projet si des modifications ont été apportées depuis la dernière génération. Les modifications apportées à *CMakeSettings.json* font régénérer le cache CMake.

Vous pouvez personnaliser une session de débogage CMake en définissant des propriétés dans le fichier **launch.vs.json.** Pour plus d’informations, consultez [Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Just My Code pour les projets CMake

Lorsque vous construisez pour Windows à l’aide du compilateur MSVC, les projets CMake ont un support pour Just My Code de débogage. Pour modifier le paramètre Just My Code, rendez-vous sur **Tools** > **Options** > **Debugging** > **General**.

## <a name="vcpkg-integration"></a>Intégration de Vcpkg

Si vous avez installé [vcpkg](vcpkg.md), les projets CMake ouverts dans Visual Studio intègrent automatiquement le fichier de chaîne d’outils vcpkg. Cela signifie qu’aucune configuration supplémentaire n’est nécessaire pour utiliser des vcpkg avec vos projets CMake. Ce support fonctionne à la fois pour les installations locales de vcpkg et les installations de vcpkg sur les systèmes distants que vous ciblez. Ce comportement est désactivé automatiquement lorsque vous spécifiez toute autre chaîne d’outils dans votre configuration CMake Paramètres.

## <a name="customize-configuration-feedback"></a>Personnaliser la rétroaction de configuration

Par défaut, la plupart des messages de configuration sont supprimés à moins qu’il n’y ait une erreur. Vous pouvez voir tous les messages en activant cette fonctionnalité dans **Tools** > **Options** > **CMake**.

   ![Configurer les options de diagnostic CMake](media/vs2019-cmake-configure-options.png "Options de diagnostic CMake")

## <a name="editing-cmakeliststxt-files"></a>Modification des fichiers CMakeLists.txt

Pour modifier un fichier *CMakeLists.txt,* cliquez à droite sur le fichier dans **Solution Explorer** et choisissez **Open**. Si vous modifiez le fichier, une barre d’état jaune apparaît et vous informe qu’IntelliSense mettra à jour. Il vous donne une chance d’annuler l’opération de mise à jour. Pour plus d’informations sur *CMakeLists.txt*, voir la [documentation CMake](https://cmake.org/documentation/).

   ![Édition de fichiers CMakeLists.txt](media/cmake-cmakelists.png "Édition de fichiers CMakeLists.txt")

Dès que vous enregistrez le fichier, l’étape de configuration s’exécute à nouveau automatiquement et affiche les informations dans la fenêtre **Sortie**. Les erreurs et les avertissements sont affichés dans la **Liste des erreurs** ou la fenêtre **Sortie**. Double-cliquez sur une erreur dans la **liste d’erreurs** pour naviguer vers la ligne incriminée dans *CMakeLists.txt*.

   ![Erreurs de fichier CMakeLists.txt](media/cmake-cmakelists-error.png "Erreurs de fichier CMakeLists.txt")

## <a name="cmake-configure-step"></a>Étape de configuration CMake

Lorsque vous modifiez significativement le *CMakeSettings.json* ou sur les fichiers *CMakeLists.txt,* Visual Studio rediffuse automatiquement l’étape de configuration CMake. Si l’étape configurée se termine sans erreurs, les informations collectées sont disponibles dans les services de CMd IntelliSense et de langue. Il est également utilisé dans les opérations de construction et de débogé.

## <a name="troubleshooting-cmake-cache-errors"></a>Résolution des erreurs de cache CMake

Si vous avez besoin de plus d’informations sur l’état du cache CMake pour diagnostiquer un problème, ouvrez le menu principal du **projet** ou le menu *contextal CMakeLists.txt* dans **Solution Explorer** pour exécuter l’une de ces commandes :

- **View Cache** ouvre le fichier *CMakeCache.txt* à partir du dossier racine de construction de l’éditeur. (Toutes les modifications que vous faites ici à *CMakeCache.txt* sont effacées si vous nettoyez le cache. Pour apporter des modifications qui persistent après le nettoyage du cache, voir [personnaliser les paramètres CMake](customize-cmake-settings.md).)

- **Ouvrir le dossier de cache** ouvre une fenêtre de l’Explorateur dans le dossier racine de build.

- **Nettoyer le cache** supprime le dossier racine de build pour que la prochaine étape de configuration CMake démarre à partir d’un cache propre.

- **Générer Cache** force l’étape de générer à fonctionner même si Visual Studio considère l’environnement à jour.

La génération automatique de cache peut être désactivée dans les **outils > Options > CMake >** dialogue général.

## <a name="run-cmake-from-the-command-line"></a>Exécuter CMake à partir de la ligne de commande

Si vous avez installé CMake à partir de Visual Studio Installer, vous pouvez l’exécuter à partir de la ligne de commande en suivant les étapes suivantes :

1. Exécutez le fichier vsdevcmd.bat approprié (x86/x64). Pour plus d’informations, voir [Building on the Command Line](building-on-the-command-line.md).

1. Revenez à votre dossier de sortie.

1. Exécutez CMake pour générer/configurer votre application.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 bénéficie d’un soutien riche pour CMake, y compris [des projets CMake multiplateformes.](../linux/cmake-linux-project.md) Le composant Visual CMD pour le composant **CMake** utilise la fonction **Open Folder** pour permettre à l’IDE de consommer des fichiers de projet CMake (tels que *CMakeLists.txt*) directement aux fins d’IntelliSense et de navigation. Les générateurs Ninja et Visual Studio sont pris en charge. Si vous utilisez un générateur Visual Studio, il génère un fichier de projet temporaire et le transmet à msbuild.exe. Cependant, le projet n’est jamais chargé à des fins de navigation ou de navigation. Vous pouvez également importer un cache CMake existant.

## <a name="installation"></a>Installation

**Les outils visualS CMD pour CMake** sont installés dans le cadre du **développement de bureau avec le développement C et** Linux avec des charges de travail **CMD.**

![Composant CMake dans la charge de travail Desktop C++](media/cmake-install.png)

Pour plus d’informations, consultez [Installer la charge de travail Linux C++ dans Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Intégration de l’IDE

Lorsque vous choisissez **File > Open > Folder** pour ouvrir un dossier contenant un fichier *CMakeLists.txt,* les choses suivantes se produisent:

- Visual Studio ajoute un élément de menu **CMake** au menu principal, avec des commandes pour voir et modifier les scripts CMake.

- **L’Explorateur de solutions** affiche la structure de dossiers et les fichiers.

- Visual Studio exécute CMake.exe et génère éventuellement le cache CMake pour la *configuration* par défaut, à savoir x86 Debug. La ligne de commande CMake s’affiche dans la **fenêtre Sortie**, ainsi que la sortie supplémentaire de CMake.

- En arrière-plan, Visual Studio démarre pour indexer les fichiers sources afin d’activer IntelliSense, les informations de navigation, la refactorisation et ainsi de suite. Pendant que vous travaillez, Visual Studio surveille les changements dans l’éditeur et sur le disque pour synchroniser son index avec les sources.

Vous pouvez ouvrir des dossiers avec un nombre quelconque de projets CMake. Visual Studio détecte et configure tous les fichiers *CMakeLists.txt* «root» dans votre espace de travail. Les opérations CMake (configurer, construire, déboiffer), CMd IntelliSense et la navigation sont disponibles pour tous les projets CMake dans votre espace de travail.

![Projet CMake avec plusieurs racines](media/cmake-multiple-roots.png)

Vous pouvez également voir vos projets organisées logiquement par cibles. Choisissez **Targets view** (Affichage des cibles) dans la liste déroulante dans la barre d’outils de **l’Explorateur de solutions** :

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png)

Visual Studio utilise un fichier appelé *CMakeSettings.json* pour stocker des variables de l’environnement ou des options de ligne de commande pour Cmake.exe. *CMakeSettings.json* vous permet également de définir et de stocker plusieurs configurations de construction CMake. Vous pouvez commodément basculer entre eux dans l’IDE.

Dans le cas contraire, utilisez le *CMakeLists.txt* comme vous le feriez dans n’importe quel projet CMake pour spécifier les fichiers sources, trouver des bibliothèques, définir des options de compilateur et de liaison, et spécifier d’autres informations liées au système de construction.

Si vous avez besoin de passer des arguments à un exécutable au moment de déboguer, vous pouvez utiliser un autre fichier appelé **launch.vs.json**. Dans certains scénarios, Visual Studio génère automatiquement ces fichiers. Vous pouvez les modifier manuellement, ou même créer le fichier vous-même.

> [!NOTE]
> Pour d’autres types de projets Open Folder, deux fichiers JSON supplémentaires sont utilisés: **CppProperties.json** et **tasks.vs.json**. Aucun des deux n’est pertinent pour les projets CMake.

## <a name="import-an-existing-cache"></a>Importer un cache existant

Lorsque vous importez un fichier *CMakeCache.txt* existant, Visual Studio extrait automatiquement des variables personnalisées et crée un fichier *CMakeSettings.json* pré-peuplé basé sur eux. Le cache d’origine n’est pas modifié en aucune façon. Il peut encore être utilisé à partir de la ligne de commande, ou avec n’importe quel outil ou IDE utilisé pour le générer. Le nouveau fichier *CMakeSettings.json* est placé à côté de la racine du projet *CMakeLists.txt*. Visual Studio génère un nouveau cache en fonction du fichier de paramètres. Vous pouvez remplacer la génération automatique de caches dans les **outils > Options > CMake >** dialogue général.

Le contenu du cache n’est pas importé en totalité.  Des propriétés comme le générateur et l’emplacement des compilateurs sont remplacées par les valeurs par défaut qui fonctionnent avec l’IDE.

### <a name="to-import-an-existing-cache"></a>Pour importer un cache existant

1. Parmi le menu principal, choisissez **File > Open > CMake**:

   ![Ouvrez CMake](media/cmake-file-open.png "Fichier, Ouvert, CMake")

   Cette commande évoque **l’importation CMake de Cache** assistant.

2. Naviguez vers le fichier *CMakeCache.txt* que vous souhaitez importer, puis cliquez **sur OK**. L’Assistant **Importer un projet CMake à partir du cache** apparaît :

   ![Importer une cache CMake](media/cmake-import-wizard.png "Ouvrez le magicien de cache d’importation CMake")

   Lorsque l’assistant se termine, vous pouvez voir le nouveau fichier *CMakeCache.txt* dans **Solution Explorer** à côté du fichier *CMakeLists.txt* racine dans votre projet.

## <a name="building-cmake-projects"></a>Génération de projets CMake

Pour générer un projet CMake, vous avez ces possibilités :

1. Dans la barre d’outils Général, recherchez la liste déroulante **Configurations**. Il est probablement montrant "Linux-Debug" ou "x64-Debug" par défaut. Sélectionnez la configuration préférée et appuyez sur **F5**, ou cliquez sur le bouton **Run** (triangle vert) sur la barre d’outils. Le projet est d’abord généré automatiquement, comme une solution Visual Studio.

1. Cliquez à droite sur le *CMakeLists.txt* et **sélectionnez Build** à partir du menu context. Si vous avez plusieurs cibles dans votre structure de dossiers, vous pouvez choisir de générer toutes les cibles ou une seule cible spécifique.

1. Dans le menu principal, sélectionnez **Build > Build Solution** (**F7** ou **Ctrl-Shift-B**). Vérifiez qu’une cible CMake est déjà sélectionnée dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**.

![CMake construire la commande de menu](media/cmake-build-menu.png "CMake construire menu de commande")

Vous pouvez personnaliser les configurations de construction, les variables d’environnement, les arguments de ligne de commande et d’autres paramètres dans le fichier *CMakeSettings.json.* Il vous permet d’apporter des modifications sans modifier le fichier *CMakeLists.txt.* Pour plus d’informations, consultez [les paramètres Personnaliser CMake](customize-cmake-settings.md).

Comme attendu, les résultats de génération sont affichés dans la **fenêtre sortie** et la **Liste des erreurs**.

![CMake construire des erreurs](media/cmake-build-errors.png "CMake construire des erreurs")

Dans un dossier avec plusieurs cibles de construction, vous pouvez spécifier quelle cible CMake à construire : Choisissez l’élément **Build** sur le menu **CMake** ou le menu context context *CMakeLists.txt* pour spécifier la cible. Si vous entrez **dans le cadre d’un** projet CMake, il construit le document actif actuel.

## <a name="debugging-cmake-projects"></a>Débogage de projets CMake

Pour déboiffer un projet CMake, choisissez la configuration préférée et appuyez sur **F5**. Ou, appuyez sur le bouton **Run** dans la barre d’outils. Si le bouton **Exécuter** indique « Sélectionner un élément de démarrage », sélectionnez la flèche déroulante et choisissez la cible à exécuter. (Dans un projet CMake, l’option « Document actif » est uniquement valide pour les fichiers .cpp.)

![Bouton D’exécution CMake](media/cmake-run-button.png "Bouton D’exécution CMake")

Les commandes **Exécuter** ou **F5** génèrent d’abord le projet si des modifications ont été apportées depuis la dernière génération.

Vous pouvez personnaliser une session de débogage CMake en définissant des propriétés dans le fichier **launch.vs.json.** Pour plus d’informations, consultez [Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md).

## <a name="editing-cmakeliststxt-files"></a>Modification des fichiers CMakeLists.txt

Pour modifier un fichier *CMakeLists.txt,* cliquez à droite sur le fichier dans **Solution Explorer** et choisissez **Open**. Si vous modifiez le fichier, une barre d’état jaune apparaît et vous informe qu’IntelliSense mettra à jour. Il vous donne une chance d’annuler l’opération de mise à jour. Pour plus d’informations sur *CMakeLists.txt*, voir la [documentation CMake](https://cmake.org/documentation/).

   ![Édition de fichiers CMakeLists.txt](media/cmake-cmakelists.png "Édition de fichiers CMakeLists.txt")

Dès que vous enregistrez le fichier, l’étape de configuration s’exécute à nouveau automatiquement et affiche les informations dans la fenêtre **Sortie**. Les erreurs et les avertissements sont affichés dans la **Liste des erreurs** ou la fenêtre **Sortie**. Double-cliquez sur une erreur dans la **liste d’erreurs** pour naviguer vers la ligne incriminée dans *CMakeLists.txt*.

   ![Erreurs de fichier CMakeLists.txt](media/cmake-cmakelists-error.png "Erreurs de fichier CMakeLists.txt")

## <a name="cmake-configure-step"></a>Étape de configuration CMake

Lorsque des modifications importantes sont apportées à la *CMakeSettings.json* ou aux fichiers *CMakeLists.txt,* Visual Studio rediffuse automatiquement l’étape de configuration CMake. Si l’étape configurée se termine sans erreurs, les informations collectées sont disponibles dans les services de CMd IntelliSense et de langue. Il est également utilisé dans les opérations de construction et de débogé.

Plusieurs projets CMake peuvent utiliser le même nom de configuration CMake (par exemple, x86-Debug). Tous sont configurés et construits (dans leur propre dossier de racine de construction) lorsque cette configuration est sélectionnée. Vous pouvez déboguer les cibles de tous les projets CMake qui participent à cette configuration CMake.

   ![CMake Construire Uniquement élément de menu](media/cmake-build-only.png "CMake Construire Uniquement élément de menu")

Vous pouvez limiter les builds et les sessions de débogé à un sous-ensemble des projets dans l’espace de travail. Créez une nouvelle configuration avec un nom unique dans le fichier *CMakeSettings.json.* Ensuite, appliquez la configuration à ces seuls projets. Lorsque cette configuration est sélectionnée, IntelliSense et les commandes de construction et de débogé ne s’appliquent qu’à ces projets spécifiés.

## <a name="troubleshooting-cmake-cache-errors"></a>Résolution des erreurs de cache CMake

Si vous avez besoin de plus d’informations sur l’état du cache CMake pour diagnostiquer un problème, ouvrez le menu principal de **CMake** ou le menu contextuel de *CMakeLists.txt* dans **l’Explorateur de solutions** pour exécuter l’une des commandes suivantes :

- **View Cache** ouvre le fichier *CMakeCache.txt* à partir du dossier racine de construction de l’éditeur. (Toutes les modifications que vous faites ici à *CMakeCache.txt* sont effacées si vous nettoyez le cache. Pour apporter des modifications qui persistent après le nettoyage du cache, voir [personnaliser les paramètres CMake](customize-cmake-settings.md).)

- **Ouvrir le dossier de cache** ouvre une fenêtre de l’Explorateur dans le dossier racine de build.

- **Nettoyer le cache** supprime le dossier racine de build pour que la prochaine étape de configuration CMake démarre à partir d’un cache propre.

- **Générer Cache** force l’étape de générer à fonctionner même si Visual Studio considère l’environnement à jour.

La génération automatique de cache peut être désactivée dans les **outils > Options > CMake >** dialogue général.

## <a name="single-file-compilation"></a>Compilation de fichiers uniques

Pour construire un seul fichier dans un projet CMake, cliquez à droite sur le fichier dans **Solution Explorer**. Choisissez **Compile** dans le menu pop-up. Vous pouvez également construire le fichier actuellement ouvert dans l’éditeur en utilisant le menu **CMake** principal:

![Compilation de fichier unique CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Exécuter CMake à partir de la ligne de commande

Si vous avez installé CMake à partir de Visual Studio Installer, vous pouvez l’exécuter à partir de la ligne de commande en suivant les étapes suivantes :

1. Exécutez le fichier vsdevcmd.bat approprié (x86/x64). Pour plus d’informations, voir [Construire sur la ligne de commandement](building-on-the-command-line.md) .

1. Revenez à votre dossier de sortie.

1. Exécutez CMake pour générer/configurer votre application.

::: moniker-end

::: moniker range="vs-2015"

Dans Visual Studio 2015, les utilisateurs de Visual Studio peuvent utiliser un [générateur CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) pour générer des fichiers projet MSBuild, consommés ensuite par l’IDE pour IntelliSense, la navigation et la compilation.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Tutorial : Créez des projets multiplateformes CMD dans Visual Studio](get-started-linux-cmake.md)\
[Configurer un projet Linux CMake](../linux/cmake-linux-project.md)\
[Connectez-vous à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)\
[Personnaliser les paramètres de construction CMake](customize-cmake-settings.md)\
[CMakeSettings.json schema référence](cmakesettings-reference.md)\
[Configurer les sessions de débogage CMake](configure-cmake-debugging-sessions.md)\
[Déployez, exécutez et débassez votre projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)
