---
title: Projets CMake dans Visual Studio
ms.date: 03/27/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 479179d94a0534f5f0c790fea18e281053b686e2
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565293"
---
# <a name="cmake-projects-in-visual-studio"></a>Projets CMake dans Visual Studio

CMake est un outil open source multiplateforme utilisé pour définir des processus de génération qui s’exécutent sur plusieurs plateformes. Cet article part du principe que vous connaissez déjà CMake. Pour en savoir plus, consultez [Générer, tester et empaqueter votre logiciel avec CMake](https://cmake.org/).

Dans Visual Studio 2015, les utilisateurs de Visual Studio peuvent utiliser un [générateur CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) pour générer des fichiers projet MSBuild, consommés ensuite par l’IDE pour IntelliSense, la navigation et la compilation.

Visual Studio 2017 introduit une prise en charge enrichie de CMake, notamment des [projets CMake multiplateformes](../linux/cmake-linux-project.md). Le composant **Outils Visual C++ pour CMake** utilise la fonctionnalité **Dossier ouvert** pour activer l’IDE afin de consommer des fichiers projet CMake (comme CMakeLists.txt) directement pour IntelliSense et la navigation. Les générateurs Ninja et Visual Studio sont pris en charge. Si vous utilisez un générateur Visual Studio, un fichier projet temporaire est généré et transmis à msbuild.exe, mais il n’est jamais chargé pour IntelliSense ou la navigation. Vous pouvez importer un cache CMake existant ; Visual Studio extrait des variables personnalisées et crée un préremplie automatiquement **CMakeSettings.json** fichier. 

## <a name="installation"></a>Installation

**Outils Visual C++ pour CMake** est installé par défaut dans le cadre des charges de travail **Développement Desktop en C++** et **Développement Linux en C++**.

![Composant CMake dans la charge de travail Desktop C++](media/cmake-install.png)

Pour plus d’informations, consultez [Installer la charge de travail Linux C++ dans Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Intégration à l’IDE

Quand vous choisissez **Fichier | Ouvrir | Dossier** pour ouvrir un dossier contenant un fichier CMakeLists.txt, les événements suivants se produisent :

- Visual Studio ajoute un élément de menu **CMake** au menu principal, avec des commandes pour voir et modifier les scripts CMake.

- **L’Explorateur de solutions** affiche la structure de dossiers et les fichiers.

- Visual Studio exécute CMake.exe et génère éventuellement le cache CMake pour la *configuration* par défaut, à savoir x86 Debug. La ligne de commande CMake s’affiche dans la **fenêtre Sortie**, ainsi que la sortie supplémentaire de CMake.

- En arrière-plan, Visual Studio démarre pour indexer les fichiers sources afin d’activer IntelliSense, les informations de navigation, la refactorisation et ainsi de suite. Pendant que vous travaillez, Visual Studio surveille les changements dans l’éditeur et sur le disque pour synchroniser son index avec les sources.

Vous pouvez ouvrir des dossiers avec un nombre quelconque de projets CMake. Visual Studio détecte et configure tous les fichiers CMakeLists.txt « racines » dans votre espace de travail. Les opérations CMake (configurer, générer, déboguer) ainsi que les opérations C++ IntelliSense et de navigation sont disponibles pour tous les projets CMake dans votre espace de travail.

![Projet CMake avec plusieurs racines](media/cmake-multiple-roots.png)

Vous pouvez également voir vos projets organisées logiquement par cibles. Choisissez **Targets view** (Affichage des cibles) dans la liste déroulante dans la barre d’outils de **l’Explorateur de solutions** :

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png)

Visual Studio utilise un fichier appelé **CMakeSettings.json** pour stocker les variables d’environnement ou des options de ligne de commande pour Cmake.exe. **CMakeSettings.json** permet également aux vous permettent de définir et stocker CMake plusieurs configurations de build et aisément basculer entre eux dans l’IDE. 

Sinon, utilisez le **CMakeLists.txt** tout comme vous serait dans n’importe quel projet CMake pour spécifier les fichiers sources, recherche de bibliothèques, définir les options du compilateur et éditeur de liens et spécifier autre système de génération informations connexes.

Si vous avez besoin passer des arguments à un fichier exécutable au moment du débogage, vous pouvez utiliser un autre fichier appelé **launch.vs.json**. Dans certains scénarios, Visual Studio génère automatiquement ces fichiers. Vous pouvez les modifier manuellement. Vous pouvez également créer le fichier vous-même.

> [!NOTE]
> Pour d’autres types de projets d’ouvrir le dossier, deux fichiers JSON supplémentaires sont utilisés : **CppProperties.json** et **tasks.vs.json**. Aucun des deux n’est pertinent pour les projets CMake.

## <a name="import-an-existing-cache"></a>Importer un cache existant

Quand vous importez un fichier CMakeCache.txt existant, Visual Studio extrait automatiquement des variables personnalisées à partir desquelles il crée un fichier **CMakeSettings.json** prérempli. Le cache d’origine n’est modifié en aucune façon et peut encore être utilisé à partir de la ligne de commande ou avec n’importe quel outil ou IDE qui a été utilisé pour sa génération. La nouvelle **CMakeSettings.json** fichier est placé à côté de la racine du projet CMakeLists.txt. Visual Studio génère un nouveau cache en fonction du fichier de paramètres. Vous pouvez remplacer la génération automatique du cache dans la boîte de dialogue **Outils | Options | CMake | Général**.

Le contenu du cache n’est pas importé en totalité.  Des propriétés comme le générateur et l’emplacement des compilateurs sont remplacées par les valeurs par défaut qui fonctionnent avec l’IDE.

### <a name="to-import-an-existing-cache"></a>Pour importer un cache existant

1. Dans le menu principal, choisissez **Fichier | Ouvrir | CMake** :

   ![Ouvrir CMake](media/cmake-file-open.png "Fichier, Ouvrir, CMake")

   Cette opération lance l’Assistant **Importer CMake à partir du cache**.

2. Accédez au fichier CMakeCache.txt à importer, puis cliquez sur **OK**. L’Assistant **Importer un projet CMake à partir du cache** apparaît :

   ![Importer un cache CMake](media/cmake-import-wizard.png "Ouvrir l’Assistant Importer un cache CMake")

   Une fois l’Assistant terminé, vous pouvez voir le nouveau fichier CMakeCache.txt dans **l’Explorateur de solutions** à côté du fichier CMakeLists.txt racine dans votre projet.

## <a name="building-cmake-projects"></a>Génération de projets CMake

Pour générer un projet CMake, vous avez ces possibilités :

1. Dans la barre d’outils généraux, recherchez le **Configurations** déroulante ; il affiche généralement « Linux-Debug » ou « x64-Debug » par défaut. Sélectionnez la configuration souhaitée et appuyez sur **F5**, ou cliquez sur le **exécuter** (triangle vert) la barre d’outils. Le projet est d’abord généré automatiquement, comme une solution Visual Studio.

1. Cliquez avec le bouton droit sur CMakeLists.txt et sélectionnez **Générer** dans le menu contextuel. Si vous avez plusieurs cibles dans votre structure de dossiers, vous pouvez choisir de générer toutes les cibles ou une seule cible spécifique.

1. Dans le menu principal, sélectionnez **Générer | Générer la solution** (**F7** ou **Ctrl + Maj + B**). Vérifiez qu’une cible CMake est déjà sélectionnée dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**.

![Commande de menu de génération CMake](media/cmake-build-menu.png "Commande de menu de génération CMake")

Vous pouvez personnaliser les configurations de build, les variables d’environnement, les arguments de ligne de commande et les autres paramètres sans modifier le fichier CMakeLists.txt à l’aide de la **CMakeSettings.json** fichier. Pour plus d’informations, consultez [Personnaliser les paramètres CMake](customize-cmake-settings.md).

Comme attendu, les résultats de génération sont affichés dans la **fenêtre sortie** et la **Liste des erreurs**.

![Erreurs de génération CMake](media/cmake-build-errors.png "Erreurs de génération CMake")

Dans un dossier avec plusieurs cibles de génération, vous pouvez choisir l’élément **Générer** dans le menu **CMake** ou le menu contextuel de **CMakeLists.txt** pour spécifier la cible CMake à générer. Quand vous appuyez sur **Ctrl + Maj + B** dans un projet CMake, le document actif est généré.

## <a name="debugging-cmake-projects"></a>Débogage de projets CMake

Pour déboguer un projet CMake, choisissez la configuration souhaitée et appuyez sur **F5**, ou appuyez sur le bouton **Exécuter** dans la barre d’outils. Si le bouton **Exécuter** indique « Sélectionner un élément de démarrage », sélectionnez la flèche déroulante et choisissez la cible à exécuter. (Dans un projet CMake, l’option « Document actif » est uniquement valide pour les fichiers .cpp.)

![Bouton d’exécution de CMake](media/cmake-run-button.png "Bouton d’exécution de CMake")

Les commandes **Exécuter** ou **F5** génèrent d’abord le projet si des modifications ont été apportées depuis la dernière génération.

Vous pouvez personnaliser un CMake session de débogage en définissant des propriétés le **launch.vs.json** fichier. Pour plus d’informations, consultez [Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md).


## <a name="editing-cmakeliststxt-files"></a>Modification des fichiers CMakeLists.txt

Pour modifier un fichier CMakeLists.txt, cliquez avec le bouton droit sur le fichier dans **l’Explorateur de solutions** et choisissez **Ouvrir**. Si vous modifiez le fichier, une barre d’état jaune s’affiche pour vous informer qu’IntelliSense va effectuer la mise à jour et vous donne la possibilité d’annuler l’opération de mise à jour. Pour plus d’informations sur CMakeLists.txt, consultez la [documentation de CMake](https://cmake.org/documentation/).

   ![Modification du fichier CMakeLists.txt](media/cmake-cmakelists.png "Modification du fichier CMakeLists.txt")

Dès que vous enregistrez le fichier, l’étape de configuration s’exécute à nouveau automatiquement et affiche les informations dans la fenêtre **Sortie**. Les erreurs et les avertissements sont affichés dans la **Liste des erreurs** ou la fenêtre **Sortie**. Double-cliquez sur une erreur dans la **Liste des erreurs** pour accéder à la ligne concernée dans CMakeLists.txt.

   ![Erreurs du fichier CMakeLists.txt](media/cmake-cmakelists-error.png "Erreurs du fichier CMakeLists.txt")


## <a name="cmake-configure-step"></a>Étape de configuration CMake

Lorsque des modifications importantes sont apportées à la **CMakeSettings.json** ou aux fichiers CMakeLists.txt, Visual Studio exécute automatiquement à nouveau le CMake l’étape de configuration. Si l’étape de configuration se termine sans erreur, les informations collectées sont disponibles dans C++ IntelliSense et les services de langage, et également dans les opérations de génération et de débogage.

Quand plusieurs projets CMake utilisent le même nom de configuration CMake (par exemple, x86-Debug), ils sont tous configurés et générés (dans son propre dossier racine de build) quand cette configuration est sélectionnée. Vous pouvez déboguer les cibles de tous les projets CMake qui participent à cette configuration CMake.

   ![Élément de menu CMake Générer uniquement](media/cmake-build-only.png "Élément de menu CMake Générer uniquement")

Pour limiter les builds et déboguer des sessions pour un sous-ensemble des projets dans l’espace de travail, créer une nouvelle configuration avec un nom unique dans le **CMakeSettings.json** de fichiers et l’appliquer à ces projets uniquement. Quand cette configuration est sélectionnée, les commandes de génération et de débogage IntelliSense sont activées uniquement pour les projets spécifiés.

## <a name="troubleshooting-cmake-cache-errors"></a>Résolution des erreurs de cache CMake

Si vous avez besoin de plus d’informations sur l’état du cache CMake pour diagnostiquer un problème, ouvrez le menu principal de **CMake** ou le menu contextuel de **CMakeLists.txt** dans **l’Explorateur de solutions** pour exécuter l’une des commandes suivantes :

- **Afficher le cache** ouvre le fichier CMakeCache.txt à partir du dossier racine de build dans l’éditeur. (Toutes les modifications que vous apportez ici à CMakeCache.txt sont effacées si vous nettoyez le cache. Pour apporter des modifications conservées une fois que le cache est nettoyé, voir [paramètres CMake personnaliser](customize-cmake-settings.md).)

- **Ouvrir le dossier de cache** ouvre une fenêtre de l’Explorateur dans le dossier racine de build.

- **Nettoyer le cache** supprime le dossier racine de build pour que la prochaine étape de configuration CMake démarre à partir d’un cache propre.

- **Générer le cache** force l’exécution de l’étape de génération même si Visual Studio considère l’environnement comme étant à jour.

La génération automatique du cache peut être désactivée dans la boîte de dialogue **Outils | Options | CMake | Général**.

## <a name="single-file-compilation"></a>Compilation de fichier unique

Pour générer un fichier unique dans un projet CMake, cliquez avec le bouton droit sur le fichier dans l’**Explorateur de solutions** et choisissez **Compiler**. Vous pouvez également générer le fichier qui est actuellement ouvert dans l’éditeur à l’aide du menu CMake principal :

![Compilation de fichier unique CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Exécuter CMake à partir de la ligne de commande

Si vous avez installé CMake à partir de Visual Studio Installer, vous pouvez l’exécuter à partir de la ligne de commande en suivant les étapes suivantes :

1. Exécutez le fichier vsdevcmd.bat approprié (x86/x64). Pour plus d’informations, consultez [Génération à partir de la ligne de commande](building-on-the-command-line.md).

1. Revenez à votre dossier de sortie.

1. Exécutez CMake pour générer/configurer votre application.
  
## <a name="see-also"></a>Voir aussi

[Tutoriel : Créer des projets multiplateforme C++ dans Visual Studio](get-started-linux-cmake.md)<br/>
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)<br/>
[Se connecter à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Personnaliser les paramètres de génération CMake](customize-cmake-settings.md)<br/>
[Référence CMakeSettings.json](cmakesettings-reference.md)<br/>
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)<br/>
