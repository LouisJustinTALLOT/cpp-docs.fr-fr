---
title: Projets CMake dans Visual Studio
description: Comment créer et générer des projets C++ à l’aide de CMake dans Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 8aa11d05aba2fe5f0e781dce2c4b801533bede26
ms.sourcegitcommit: 6acb62dae8e46d9cfaea7c564a7135b2ca037889
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97905229"
---
# <a name="cmake-projects-in-visual-studio"></a>Projets CMake dans Visual Studio

[Cmake](https://cmake.org) est un outil multiplateforme et open source permettant de définir des processus de génération qui s’exécutent sur plusieurs plateformes. Cet article suppose que vous êtes familiarisé avec CMake. Pour plus d’informations sur CMake, consultez la [documentation de cmake](https://cmake.org/cmake/help/latest/index.html#). Le [didacticiel cmake](https://cmake.org/cmake/help/latest/guide/tutorial/index.html#guide:CMake%20Tutorial) est un bon point de départ pour en savoir plus. 

> [!NOTE]
> CMake est devenu de plus en plus intégré à Visual Studio au cours des dernières versions. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="msvc-160"

Le composant **C++ cmake Tools pour Windows** utilise la fonctionnalité [ouvrir le dossier](open-folder-projects-cpp.md) pour utiliser directement les fichiers projet cmake (par exemple, *CMakeLists.txt*) à des fins d’IntelliSense et de navigation. Les générateurs Ninja et Visual Studio sont pris en charge. Si vous utilisez un générateur Visual Studio, il génère un fichier projet temporaire et le transmet à msbuild.exe. Toutefois, le projet n’est jamais chargé à des fins d’IntelliSense ou de navigation. Vous pouvez également importer un cache CMake existant.

## <a name="installation"></a>Installation

**C++ cmake Tools pour Windows** est installé dans le cadre du développement bureautique avec le développement de postes de travail **avec c++** et **Linux avec des charges de travail c++** . Pour plus d’informations, consultez [projets cmake inter-plateformes](../linux/cmake-linux-project.md).

![Capture d’écran de la liste déroulante de développement Desktop avec C plus plus sélectionnée et de l’option c plus C make Tools for Windows.](media/cmake-install-2019.png)

Pour plus d’informations, consultez [Installer la charge de travail Linux C++ dans Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Intégration à l’IDE

Lorsque vous choisissez **fichier > ouvrir > dossier** pour ouvrir un dossier contenant un fichier *CMakeLists.txt* , les événements suivants se produisent :

- Visual Studio ajoute des éléments **cmake** dans le menu **projet** , avec les commandes permettant d’afficher et de modifier les scripts cmake.

- **L’Explorateur de solutions** affiche la structure de dossiers et les fichiers.

- Visual Studio exécute cmake.exe et génère le fichier cache CMake (*CMakeCache.txt*) pour la configuration par défaut (x64 Debug). La ligne de commande CMake s’affiche dans la **fenêtre Sortie**, ainsi que la sortie supplémentaire de CMake.

- En arrière-plan, Visual Studio démarre pour indexer les fichiers sources afin d’activer IntelliSense, les informations de navigation, la refactorisation et ainsi de suite. Pendant que vous travaillez, Visual Studio surveille les changements dans l’éditeur et sur le disque pour synchroniser son index avec les sources.

Vous pouvez ouvrir des dossiers avec un nombre quelconque de projets CMake. Visual Studio détecte et configure tous les fichiers de *CMakeLists.txt* racine dans votre espace de travail. Les opérations CMake (configurer, générer, déboguer), IntelliSense C++ et la navigation sont disponibles pour tous les projets CMake dans votre espace de travail.

![Projet CMake avec plusieurs racines](media/cmake-multiple-roots.png)

Vous pouvez également voir vos projets organisées logiquement par cibles. Choisissez **Targets view** (Affichage des cibles) dans la liste déroulante dans la barre d’outils de **l’Explorateur de solutions** :

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png)

Cliquez sur le bouton **Afficher tous les fichiers** en haut de **Explorateur de solutions** pour voir toutes les sorties générées par cmake dans les dossiers *out \<config> /Build/* .

Visual Studio utilise un fichier de configuration appelé **CMakeSettings.jssur**. Ce fichier vous permet de définir et de stocker plusieurs configurations de build, et de passer facilement de l’un à l’autre dans l’IDE. Une *configuration* est une construction Visual Studio qui encapsule des paramètres spécifiques à un type de build donné. Les paramètres sont utilisés pour configurer les options de ligne de commande par défaut que Visual Studio transmet à cmake.exe. Vous pouvez également spécifier des options de CMake supplémentaires ici et définir toutes les variables supplémentaires de votre choix. Toutes les options sont écrites dans le cache CMake en tant que variables internes ou externes. Dans Visual Studio 2019, l' **éditeur de paramètres cmake** offre un moyen pratique de modifier vos paramètres. Pour plus d’informations, consultez [personnaliser les paramètres cmake](customize-cmake-settings.md).

Un paramètre `intelliSenseMode` n’est pas passé à cmake, mais il est utilisé uniquement par Visual Studio.

Utilisez le fichier **CMakeLists.txt** dans chaque dossier du projet, comme vous le feriez dans n’importe quel projet cmake. Vous pouvez spécifier des fichiers sources, Rechercher des bibliothèques, définir les options du compilateur et de l’éditeur de liens, et spécifier d’autres informations relatives au système de génération.

Pour passer des arguments à un exécutable au moment du débogage, vous pouvez utiliser un autre fichier appelé **launch.vs.jssur**. Dans certains scénarios, Visual Studio génère automatiquement ces fichiers. Vous pouvez les modifier manuellement ou même créer le fichier vous-même.

> [!NOTE]
> Pour les autres types de projets de dossiers ouverts, deux fichiers JSON supplémentaires sont utilisés : **CppProperties.jssur** et **tasks.vs.jssur**. Aucun des deux n’est pertinent pour les projets CMake.

## <a name="open-an-existing-cache"></a>Ouvrir un cache existant

Quand vous ouvrez un fichier cache CMake existant (*CMakeCache.txt*), Visual Studio ne tente pas de gérer votre cache et votre arborescence de génération pour vous. Vos outils personnalisés ou préférés ont un contrôle total sur la façon dont CMake configure votre projet. Pour ouvrir un cache existant dans Visual Studio, choisissez **fichier > ouvrir > cmake**. Ensuite, accédez à un fichier de *CMakeCache.txt* existant.

Vous pouvez ajouter un cache CMake existant à un projet ouvert. Cela s’effectue de la même façon que vous ajoutez une nouvelle configuration. Pour plus d’informations, consultez notre billet de blog sur [l’ouverture d’un cache existant dans Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Génération de projets CMake

Pour générer un projet CMake, vous avez ces possibilités :

1. Dans la barre d’outils Général, recherchez la liste déroulante **Configurations**. Il affiche probablement « x64-Debug » par défaut. Sélectionnez la configuration par défaut et appuyez sur **F5**, ou cliquez sur le bouton **exécuter** (triangle vert) dans la barre d’outils. Le projet est d’abord généré automatiquement, comme une solution Visual Studio.

1. Cliquez avec le bouton droit sur *CMakeLists.txt* , puis sélectionnez **générer** dans le menu contextuel. Si vous avez plusieurs cibles dans votre structure de dossiers, vous pouvez choisir de générer toutes les cibles ou une seule cible spécifique.

1. Dans le menu principal, sélectionnez **générer > tout générer** (**F7** ou **Ctrl + Maj + B**). Vérifiez qu’une cible CMake est déjà sélectionnée dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**.

![Commande de menu Générer CMake](media/cmake-build-menu.png "Menu de commandes de génération CMake")

Comme attendu, les résultats de génération sont affichés dans la **fenêtre sortie** et la **Liste des erreurs**.

![Erreurs de build CMake](media/cmake-build-errors.png "Erreurs de build CMake")

Dans un dossier avec plusieurs cibles de génération, vous pouvez spécifier la cible CMake à générer : choisissez l’élément de **Build** dans le menu **cmake** ou le menu contextuel *CMakeLists.txt* pour spécifier la cible. Si vous entrez **Ctrl + Maj + B** dans un projet cmake, il génère le document actif actuel.

## <a name="debugging-cmake-projects"></a>Débogage de projets CMake

Pour déboguer un projet CMake, choisissez la configuration par défaut et appuyez sur **F5**, ou appuyez sur le bouton **exécuter** de la barre d’outils. Si le bouton **exécuter** indique « sélectionner un élément de démarrage », sélectionnez la flèche déroulante. Choisissez la cible que vous souhaitez exécuter. (Dans un projet CMake, l’option « Document actif » est uniquement valide pour les fichiers .cpp.)

![CMake bouton exécuter](media/cmake-run-button.png "CMake bouton exécuter")

Les commandes **Exécuter** ou **F5** génèrent d’abord le projet si des modifications ont été apportées depuis la dernière génération. Les modifications apportées à *CMakeSettings.jssur* provoquent la régénération du cache cmake.

Vous pouvez personnaliser une session de débogage CMake en définissant des propriétés dans le fichier **launch.vs.js** . Pour plus d’informations, consultez [Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Uniquement mon code pour les projets CMake

Quand vous générez pour Windows à l’aide du compilateur MSVC, les projets CMake prennent en charge le débogage Uniquement mon code. Pour modifier le paramètre uniquement mon code, accédez à **Outils**  >  **options**  >  **débogage**  >  **général**.

## <a name="vcpkg-integration"></a>Intégration de vcpkg

Si vous avez installé [vcpkg](vcpkg.md), les projets cmake ouverts dans Visual Studio intègrent automatiquement le fichier vcpkg chaîne d’outils. Cela signifie qu’aucune configuration supplémentaire n’est requise pour utiliser vcpkg avec vos projets CMake. Cette prise en charge fonctionne pour les installations vcpkg locales et les installations vcpkg sur les systèmes distants que vous ciblez. Ce comportement est désactivé automatiquement lorsque vous spécifiez un autre chaîne d’outils dans votre configuration de paramètres CMake.

## <a name="customize-configuration-feedback"></a>Personnaliser les commentaires sur la configuration

Par défaut, la plupart des messages de configuration sont supprimés, sauf s’il existe une erreur. Vous pouvez voir tous les messages en activant cette fonctionnalité dans **Outils**  >  **options**  >  **cmake**.

   ![Configuration des options de diagnostic CMake](media/vs2019-cmake-configure-options.png "Options de diagnostic CMake")

## <a name="editing-cmakeliststxt-files"></a>Modification des fichiers CMakeLists.txt

Pour modifier un fichier de *CMakeLists.txt* , cliquez avec le bouton droit sur le fichier dans **Explorateur de solutions** puis choisissez **ouvrir**. Si vous apportez des modifications au fichier, une barre d’état jaune s’affiche et vous informe que IntelliSense est mis à jour. Elle vous donne la possibilité d’annuler l’opération de mise à jour. Pour plus d’informations sur *CMakeLists.txt*, consultez la [documentation cmake](https://cmake.org/documentation/).

   ![ Modification de fichiersCMakeLists.txt](media/cmake-cmakelists.png "Modification de fichiers CMakeLists.txt")

Dès que vous enregistrez le fichier, l’étape de configuration s’exécute à nouveau automatiquement et affiche les informations dans la fenêtre **Sortie**. Les erreurs et les avertissements sont affichés dans la **Liste des erreurs** ou la fenêtre **Sortie**. Double-cliquez sur une erreur dans le **liste d’erreurs** pour accéder à la ligne incriminée dans *CMakeLists.txt*.

   ![ Erreurs de fichierCMakeLists.txt](media/cmake-cmakelists-error.png "Erreurs de fichier CMakeLists.txt")

## <a name="cmake-configure-step"></a>Étape de configuration CMake

Lorsque vous apportez des modifications importantes à la *CMakeSettings.jssur* ou pour *CMakeLists.txt* fichiers, Visual Studio réexécute automatiquement l’étape de configuration de cmake. Si l’étape de configuration se termine sans erreur, les informations collectées sont disponibles dans C++ IntelliSense et les services de langage. Elle est également utilisée dans les opérations de génération et de débogage.

## <a name="troubleshooting-cmake-cache-errors"></a>Résolution des erreurs de cache CMake

Si vous avez besoin de plus d’informations sur l’état du cache CMake pour diagnostiquer un problème, ouvrez le menu principal du **projet** ou le menu contextuel *CMakeLists.txt* dans **Explorateur de solutions** pour exécuter l’une des commandes suivantes :

- **Afficher le cache** ouvre le fichier *CMakeCache.txt* à partir du dossier racine de build dans l’éditeur. (Toutes les modifications apportées ici pour *CMakeCache.txt* sont effacées si vous nettoyez le cache. Pour apporter des modifications qui persistent après le nettoyage du cache, consultez [personnaliser les paramètres cmake](customize-cmake-settings.md).)

- **Ouvrir le dossier de cache** ouvre une fenêtre de l’Explorateur dans le dossier racine de build.

- **Nettoyer le cache** supprime le dossier racine de build pour que la prochaine étape de configuration CMake démarre à partir d’un cache propre.

- **Générer le cache** force l’exécution de l’étape générer même si Visual Studio considère l’environnement à jour.

La génération automatique du cache peut être désactivée dans **outils > Options > boîte de dialogue CMake > général** .

## <a name="run-cmake-from-the-command-line"></a>Exécuter CMake à partir de la ligne de commande

Si vous avez installé CMake à partir de Visual Studio Installer, vous pouvez l’exécuter à partir de la ligne de commande en suivant les étapes suivantes :

1. Exécutez le fichier vsdevcmd.bat approprié (x86/x64). Pour plus d’informations, consultez [génération sur la ligne de commande](building-on-the-command-line.md).

1. Revenez à votre dossier de sortie.

1. Exécutez CMake pour générer/configurer votre application.

::: moniker-end

::: moniker range="msvc-150"

Visual Studio 2017 offre une prise en charge enrichie des CMake, y compris les [projets cmake multiplateformes](../linux/cmake-linux-project.md). Le composant **Visual C++ Tools pour cmake** utilise la fonctionnalité **ouvrir le dossier** pour permettre à l’IDE de consommer des fichiers projet CMake (tels que *CMakeLists.txt*) directement à des fins d’IntelliSense et de navigation. Les générateurs Ninja et Visual Studio sont pris en charge. Si vous utilisez un générateur Visual Studio, il génère un fichier projet temporaire et le transmet à msbuild.exe. Toutefois, le projet n’est jamais chargé à des fins d’IntelliSense ou de navigation. Vous pouvez également importer un cache CMake existant.

## <a name="installation"></a>Installation

Les **outils de Visual C++ pour cmake** sont installés dans le cadre du **développement bureautique avec** le développement en c++ et **Linux avec des charges de travail c++** .

![Capture d’écran de l’onglet composants individuels avec les outils Visual C plus pour l’ajout de la commande C.](media/cmake-install.png)

Pour plus d’informations, consultez [Installer la charge de travail Linux C++ dans Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Intégration de l’IDE

Lorsque vous choisissez **fichier > ouvrir > dossier** pour ouvrir un dossier contenant un fichier *CMakeLists.txt* , les événements suivants se produisent :

- Visual Studio ajoute un élément de menu **CMake** au menu principal, avec des commandes pour voir et modifier les scripts CMake.

- **L’Explorateur de solutions** affiche la structure de dossiers et les fichiers.

- Visual Studio exécute CMake.exe et génère éventuellement le cache CMake pour la *configuration* par défaut, à savoir x86 Debug. La ligne de commande CMake s’affiche dans la **fenêtre Sortie**, ainsi que la sortie supplémentaire de CMake.

- En arrière-plan, Visual Studio démarre pour indexer les fichiers sources afin d’activer IntelliSense, les informations de navigation, la refactorisation et ainsi de suite. Pendant que vous travaillez, Visual Studio surveille les changements dans l’éditeur et sur le disque pour synchroniser son index avec les sources.

Vous pouvez ouvrir des dossiers avec un nombre quelconque de projets CMake. Visual Studio détecte et configure tous les fichiers de *CMakeLists.txt* racine dans votre espace de travail. Les opérations CMake (configurer, générer, déboguer), IntelliSense C++ et la navigation sont disponibles pour tous les projets CMake dans votre espace de travail.

![Projet CMake avec plusieurs racines](media/cmake-multiple-roots.png)

Vous pouvez également voir vos projets organisées logiquement par cibles. Choisissez **Targets view** (Affichage des cibles) dans la liste déroulante dans la barre d’outils de **l’Explorateur de solutions** :

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png)

Visual Studio utilise un fichier appelé *CMakeSettings.js* pour stocker les variables d’environnement ou les options de ligne de commande pour Cmake.exe. *CMakeSettings.jssur* vous permet également de définir et de stocker plusieurs configurations de build cmake. Vous pouvez facilement passer de l’un à l’autre dans l’IDE.

Sinon, utilisez la *CMakeLists.txt* comme vous le feriez dans n’importe quel projet cmake pour spécifier des fichiers sources, Rechercher des bibliothèques, définir des options de compilateur et de l’éditeur de liens, et spécifier d’autres informations relatives au système de génération.

Si vous devez passer des arguments à un exécutable au moment du débogage, vous pouvez utiliser un autre fichier appelé **launch.vs.jssur**. Dans certains scénarios, Visual Studio génère automatiquement ces fichiers. Vous pouvez les modifier manuellement ou même créer le fichier vous-même.

> [!NOTE]
> Pour les autres types de projets de dossiers ouverts, deux fichiers JSON supplémentaires sont utilisés : **CppProperties.jssur** et **tasks.vs.jssur**. Aucun des deux n’est pertinent pour les projets CMake.

## <a name="import-an-existing-cache"></a>Importer un cache existant

Lorsque vous importez un fichier de *CMakeCache.txt* existant, Visual Studio extrait automatiquement les variables personnalisées et crée unCMakeSettings.jsprérempli *sur le* fichier en fonction de ces dernières. Le cache d’origine n’est pas modifié. Il peut toujours être utilisé à partir de la ligne de commande ou avec l’outil ou l’IDE utilisé pour le générer. Le nouveau  *CMakeSettings.jssur* le fichier est placé en regard de la *CMakeLists.txt* racine du projet. Visual Studio génère un nouveau cache en fonction du fichier de paramètres. Vous pouvez remplacer la génération automatique du cache dans la boîte de dialogue **outils > Options > CMake > général** .

Le contenu du cache n’est pas importé en totalité.  Des propriétés comme le générateur et l’emplacement des compilateurs sont remplacées par les valeurs par défaut qui fonctionnent avec l’IDE.

### <a name="to-import-an-existing-cache"></a>Pour importer un cache existant

1. Dans le menu principal, choisissez **fichier > ouvrir > cmake**:

   ![Ouvrir CMake](media/cmake-file-open.png "Fichier, ouvrir, CMake")

   Cette commande affiche l’Assistant **importer des cmake à partir du cache** .

2. Accédez au fichier *CMakeCache.txt* que vous souhaitez importer, puis cliquez sur **OK**. L’Assistant **Importer un projet CMake à partir du cache** apparaît :

   ![Importer un cache CMake](media/cmake-import-wizard.png "Ouvrir l’Assistant CMake Import cache")

   Une fois l’Assistant terminé, vous pouvez voir le nouveau fichier de *CMakeCache.txt* dans **Explorateur de solutions** en regard du fichier de *CMakeLists.txt* racine dans votre projet.

## <a name="building-cmake-projects"></a>Génération de projets CMake

Pour générer un projet CMake, vous avez ces possibilités :

1. Dans la barre d’outils Général, recherchez la liste déroulante **Configurations**. Elle indique probablement « Linux-Debug » ou « x64-Debug » par défaut. Sélectionnez la configuration par défaut et appuyez sur **F5**, ou cliquez sur le bouton **exécuter** (triangle vert) dans la barre d’outils. Le projet est d’abord généré automatiquement, comme une solution Visual Studio.

1. Cliquez avec le bouton droit sur le *CMakeLists.txt* , puis sélectionnez **générer** dans le menu contextuel. Si vous avez plusieurs cibles dans votre structure de dossiers, vous pouvez choisir de générer toutes les cibles ou une seule cible spécifique.

1. Dans le menu principal, sélectionnez **générer > générer la solution** (**F7** ou **Ctrl + Maj + B**). Vérifiez qu’une cible CMake est déjà sélectionnée dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**.

![Commande de menu Générer CMake](media/cmake-build-menu.png "Menu de commandes de génération CMake")

Vous pouvez personnaliser les configurations de build, les variables d’environnement, les arguments de ligne de commande et d’autres paramètres dans le *CMakeSettings.jssur* le fichier. Elle vous permet d’apporter des modifications sans modifier le fichier *CMakeLists.txt* . Pour plus d’informations, consultez [personnaliser les paramètres cmake](customize-cmake-settings.md).

Comme attendu, les résultats de génération sont affichés dans la **fenêtre sortie** et la **Liste des erreurs**.

![Erreurs de build CMake](media/cmake-build-errors.png "Erreurs de build CMake")

Dans un dossier avec plusieurs cibles de génération, vous pouvez spécifier la cible CMake à générer : choisissez l’élément de **Build** dans le menu **cmake** ou le menu contextuel *CMakeLists.txt* pour spécifier la cible. Si vous entrez **Ctrl + Maj + B** dans un projet cmake, il génère le document actif actuel.

## <a name="debugging-cmake-projects"></a>Débogage de projets CMake

Pour déboguer un projet CMake, choisissez la configuration par défaut et appuyez sur **F5**. Ou appuyez sur le bouton **exécuter** de la barre d’outils. Si le bouton **Exécuter** indique « Sélectionner un élément de démarrage », sélectionnez la flèche déroulante et choisissez la cible à exécuter. (Dans un projet CMake, l’option « Document actif » est uniquement valide pour les fichiers .cpp.)

![CMake bouton exécuter](media/cmake-run-button.png "CMake bouton exécuter")

Les commandes **Exécuter** ou **F5** génèrent d’abord le projet si des modifications ont été apportées depuis la dernière génération.

Vous pouvez personnaliser une session de débogage CMake en définissant des propriétés dans le fichier **launch.vs.js** . Pour plus d’informations, consultez [Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md).

## <a name="editing-cmakeliststxt-files"></a>Modification des fichiers CMakeLists.txt

Pour modifier un fichier de *CMakeLists.txt* , cliquez avec le bouton droit sur le fichier dans **Explorateur de solutions** puis choisissez **ouvrir**. Si vous apportez des modifications au fichier, une barre d’état jaune s’affiche et vous informe que IntelliSense est mis à jour. Elle vous donne la possibilité d’annuler l’opération de mise à jour. Pour plus d’informations sur *CMakeLists.txt*, consultez la [documentation cmake](https://cmake.org/documentation/).

   ![ Modification de fichiersCMakeLists.txt](media/cmake-cmakelists.png "Modification de fichiers CMakeLists.txt")

Dès que vous enregistrez le fichier, l’étape de configuration s’exécute à nouveau automatiquement et affiche les informations dans la fenêtre **Sortie**. Les erreurs et les avertissements sont affichés dans la **Liste des erreurs** ou la fenêtre **Sortie**. Double-cliquez sur une erreur dans le **liste d’erreurs** pour accéder à la ligne incriminée dans *CMakeLists.txt*.

   ![ Erreurs de fichierCMakeLists.txt](media/cmake-cmakelists-error.png "Erreurs de fichier CMakeLists.txt")

## <a name="cmake-configure-step"></a>Étape de configuration CMake

Lorsque des modifications importantes sont apportées à la  *CMakeSettings.jssur* ou pour *CMakeLists.txt* fichiers, Visual Studio réexécute automatiquement l’étape de configuration de cmake. Si l’étape de configuration se termine sans erreur, les informations collectées sont disponibles dans C++ IntelliSense et les services de langage. Elle est également utilisée dans les opérations de génération et de débogage.

Plusieurs projets CMake peuvent utiliser le même nom de configuration CMake (par exemple, x86-Debug). Tous sont configurés et générés (dans leur propre dossier racine de Build) lorsque cette configuration est sélectionnée. Vous pouvez déboguer les cibles de tous les projets CMake qui participent à cette configuration CMake.

   ![Élément de menu de génération CMake uniquement](media/cmake-build-only.png "Élément de menu de génération CMake uniquement")

Vous pouvez limiter les sessions de débogage et les builds à un sous-ensemble des projets de l’espace de travail. Créez une nouvelle configuration avec un nom unique dans le fichier  *CMakeSettings.js* . Ensuite, appliquez la configuration à ces projets uniquement. Lorsque cette configuration est sélectionnée, IntelliSense et les commandes de génération et de débogage s’appliquent uniquement à ces projets spécifiés.

## <a name="troubleshooting-cmake-cache-errors"></a>Résolution des erreurs de cache CMake

Si vous avez besoin de plus d’informations sur l’état du cache CMake pour diagnostiquer un problème, ouvrez le menu principal de **CMake** ou le menu contextuel de *CMakeLists.txt* dans **l’Explorateur de solutions** pour exécuter l’une des commandes suivantes :

- **Afficher le cache** ouvre le fichier  *CMakeCache.txt* à partir du dossier racine de build dans l’éditeur. (Toutes les modifications apportées ici pour  *CMakeCache.txt* sont effacées si vous nettoyez le cache. Pour apporter des modifications qui persistent après le nettoyage du cache, consultez [personnaliser les paramètres cmake](customize-cmake-settings.md).)

- **Ouvrir le dossier de cache** ouvre une fenêtre de l’Explorateur dans le dossier racine de build.

- **Nettoyer le cache** supprime le dossier racine de build pour que la prochaine étape de configuration CMake démarre à partir d’un cache propre.

- **Générer le cache** force l’exécution de l’étape générer même si Visual Studio considère l’environnement à jour.

La génération automatique du cache peut être désactivée dans **outils > Options > boîte de dialogue CMake > général** .

## <a name="single-file-compilation"></a>Compilation de fichier unique

Pour générer un fichier unique dans un projet CMake, cliquez avec le bouton droit sur le fichier dans **Explorateur de solutions**. Choisissez **compiler** dans le menu contextuel. Vous pouvez également générer le fichier actuellement ouvert dans l’éditeur à l’aide du menu principal **cmake** :

![Compilation de fichier unique CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Exécuter CMake à partir de la ligne de commande

Si vous avez installé CMake à partir de Visual Studio Installer, vous pouvez l’exécuter à partir de la ligne de commande en suivant les étapes suivantes :

1. Exécutez le fichier vsdevcmd.bat approprié (x86/x64). Pour plus d’informations, consultez [génération sur la ligne de commande](building-on-the-command-line.md) .

1. Revenez à votre dossier de sortie.

1. Exécutez CMake pour générer/configurer votre application.

::: moniker-end

::: moniker range="msvc-140"

Dans Visual Studio 2015, les utilisateurs de Visual Studio peuvent utiliser un [générateur CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) pour générer des fichiers projet MSBuild, consommés ensuite par l’IDE pour IntelliSense, la navigation et la compilation.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Didacticiel : créer des projets multiplateformes C++ dans Visual Studio](get-started-linux-cmake.md)\
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)\
[Connectez-vous à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)\
[Personnaliser les paramètres de build CMake](customize-cmake-settings.md)\
[CMakeSettings.jssur la référence de schéma](cmakesettings-reference.md)\
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)\
[Déployer, exécuter et déboguer votre projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)
