---
title: Personnaliser des paramètres de génération CMake dans Visual Studio
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: c6bd1404799ccc9ad6b689646cd066849d48fca8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328680"
---
# <a name="customize-cmake-build-settings"></a>Personnaliser des paramètres de génération CMake

::: moniker range="vs-2019"

Dans Visual Studio 2019 et ultérieur, vous pouvez ajouter des configurations et personnaliser leurs paramètres à l’aide de l’**éditeur de paramètres CMake**. L’éditeur est destiné à être une alternative plus simple à l’édition manuelle du fichier *CMakeSettings.json,* mais si vous préférez modifier le fichier directement, vous pouvez cliquer sur le lien **Edit JSON** en haut à droite de l’éditeur.

Pour ouvrir l’éditeur, cliquez sur la liste déroulante **Configuration** dans la barre d’outils principale et choisissez **Gérer les configurations**.

![Liste déroulante des configurations CMake](media/vs2019-cmake-manage-configurations.png)

Maintenant, vous voyez l’**éditeur de paramètres**, avec les configurations installées sur la gauche.

![Éditeur de paramètres CMake](media/cmake-settings-editor.png)

Visual Studio `x64-Debug` fournit une configuration par défaut. Vous pouvez ajouter des configurations supplémentaires en cliquant sur le signe vert plus. Les paramètres que vous voyez dans l’éditeur peuvent varier en fonction de la configuration sélectionnée.

Les options que vous choisissez dans l’éditeur sont écrites à un fichier appelé *CMakeSettings.json*. Ce fichier fournit des arguments de ligne de commande et des variables d’environnement qui sont passés à CMake quand vous générez les projets. Visual Studio ne modifie jamais *automatiquement CMakeLists.txt;* en utilisant *CMakeSettings.json,* vous pouvez personnaliser la construction via Visual Studio tout en laissant les fichiers du projet CMake intacts afin que d’autres membres de votre équipe puissent les consommer avec tous les outils qu’ils utilisent.

## <a name="cmake-general-settings"></a>Paramètres généraux CMake

Les paramètres suivants sont disponibles sous le titre **Général** :

### <a name="configuration-name"></a>Nom de la configuration

Correspond au paramètre **name**. Ce nom apparaît dans le décrochage de configuration C. Vous pouvez utiliser la macro `${name}` pour composer d’autres valeurs de propriété telles que des chemins.

### <a name="configuration-type"></a>Type de configuration

Correspond au paramètre **configurationType**. Définit le type de configuration de build du générateur sélectionné. Les valeurs actuellement prises en charge sont « Debug », « MinSizeRel », « Release » et « RelWithDebInfo ». Il cartes à [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html).

### <a name="toolset"></a>Ensemble d'outils

Correspond au paramètre **inheritedEnvironments**. Définit l’environnement compilateur qui est utilisé pour construire la configuration sélectionnée. Les valeurs prises en charge varient selon le type de configuration. Pour créer un environnement personnalisé, choisissez le lien **Edit JSON** dans le coin supérieur droit de l’éditeur Paramètres, et modifiez directement le fichier *CMakeSettings.json.*

### <a name="cmake-toolchain-file"></a>Fichier de chaîne d’outils CMake

Chemin vers le [fichier de chaîne d’outils CMake](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html). Ce chemin est passé à CMake comme \<"-DCMAKE_TOOLCHAIN_FILE - filepath>". Les fichiers de chaîne d’outils spécifient l’emplacement des compilateurs et des utilitaires de chaîne à outils, ainsi que d’autres informations relatives à la plate-forme cible et au compilateur. Par défaut, Visual Studio utilise le [fichier de chaîne d’outils vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) si ce paramètre n’est pas spécifié.

### <a name="build-root"></a>Racine de build

Correspond à **buildRoot**. Cartes pour [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html), et précise où créer le cache CMake. Le dossier spécifié est créé s’il n’existe pas.

## <a name="command-arguments"></a>Arguments de la commande

Les paramètres suivants sont disponibles sous le titre **Arguments de la commande**  :

### <a name="cmake-command-arguments"></a>Arguments de commande CMake

Correspond à **cmakeCommandArgs**. Spécifie toutes les options de ligne de [commande](https://cmake.org/cmake/help/latest/manual/cmake.1.html) supplémentaires passées à CMake.exe.

### <a name="build-command-arguments"></a>Arguments de commande de build

Correspond à **buildCommandArgs**. Spécifie des commutateurs supplémentaires pour passer au système de construction sous-jacent. Par exemple, `-v` passer lors de l’utilisation du générateur Ninja oblige Ninja à la sortie des lignes de commandement.

### <a name="ctest-command-arguments"></a>Arguments de commande CTest

Correspond à **ctestCommandArgs**. Spécifie [d’autres options](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) de ligne de commande pour passer au CTest lors de l’exécution des tests.

## <a name="general-settings-for-remote-builds"></a>Paramètres généraux pour les builds distantes

Pour les configurations telles que Linux qui utilisent des builds distantes, les paramètres suivants sont également disponibles :

### <a name="rsync-command-arguments"></a>Arguments de commande rsync

D’autres options de ligne de commande sont passées à [rsync](https://download.samba.org/pub/rsync/rsync.html), un outil de copie de fichiers rapide et polyvalent.

## <a name="cmake-variables-and-cache"></a>Variables et cache CMake

Ces paramètres vous permettent de définir les variables CMake et de les enregistrer dans *CMakeSettings.json*. Ils sont passés à CMake au moment de la construction, et l’emporter sur toutes les valeurs sont dans le fichier *CMakeLists.txt.* Vous pouvez utiliser cette section de la même façon que l’interface CMakeGUI pour afficher la liste de toutes les variables CMake modifiables. Cliquez sur le bouton **Enregistrer et générer le cache** pour voir la liste de toutes les variables CMake modifiables, y compris les variables avancées (par le biais de l’interface CMakeGUI). Vous pouvez filtrer la liste par nom variable.

Correspond aux **variables**. Contient une paire de variables CMake de valeur nominale transmises sous forme de valeur * _de nom_=* **-D** à CMake. Si vos instructions de construction de projet CMake spécifient l’ajout de toutes les variables directement au fichier de cache CMake, nous vous recommandons de les ajouter ici à la place.

## <a name="advanced-settings"></a>Paramètres avancés

### <a name="cmake-generator"></a>Générateur CMake

Correspond au **générateur**. Cartes à l’interrupteur **CMake-G,** et spécifie le [générateur CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) à utiliser. Cette propriété peut également être utilisée en tant que macro, `${generator}`, quand vous rédigez d’autres valeurs de propriétés. Visual Studio prend actuellement en charge les générateurs CMake suivants :

- « Ninja »
- « Unix Makefiles »
- « Visual Studio 16 2019 »
- « Visual Studio 16 2019 Win64 »
- « Visual Studio 16 2019 ARM »
- « Visual Studio 15 2017 »
- « Visual Studio 15 2017 Win64 »
- « Visual Studio 15 2017 ARM »
- « Visual Studio 14 2015 »
- « Visual Studio 14 2015 Win64 »
- « Visual Studio 14 2015 ARM »
  
Parce que Ninja est conçu pour les vitesses de construction rapide au lieu de la flexibilité et la fonction, il est défini comme la valeur par défaut. Toutefois, certains projets CMake peuvent ne pas pouvoir être générés correctement avec Ninja. Si cela se produit, vous pouvez demander à CMake de générer un projet Visual Studio à la place.

### <a name="intellisense-mode"></a>Mode IntelliSense

Le mode IntelliSense utilisé par le moteur IntelliSense. Si aucun mode n’est sélectionné, Visual Studio héritera de l’outil spécifié.  

### <a name="install-directory"></a>Répertoire d’installation

Le répertoire dans lequel CMake installe des cibles. Cartes à [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="cmake-executable"></a>Exécutable CMake

Le chemin complet vers le programme CMake exécutable, y compris le nom du fichier et l’extension. Il vous permet d’utiliser une version personnalisée de CMake avec Visual Studio. Pour les builds distantes, spécifiez l’emplacement CMake sur l’ordinateur distant.

Pour les configurations telles que Linux qui utilisent des builds distantes, les paramètres suivants sont également disponibles :

### <a name="remote-cmakeliststxt-root"></a>Racine CMakeLists.txt distante

L’annuaire sur la machine à distance qui contient le fichier *CMakeLists.txt* racine.

### <a name="remote-install-root"></a>Racine d’installation distante

Répertoire de l’ordinateur distant dans lequel CMake installe les cibles. Cartes à [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="remote-copy-sources"></a>Copier les sources sur la machine distante

Précise s’il faut copier des fichiers sources à la machine à distance, et vous permet de spécifier s’il faut utiliser rsync ou sftp.

## <a name="directly-edit-cmakesettingsjson"></a>Modifier CMakeSettings.json directement

Vous pouvez également modifier directement *CMakeSettings.json* pour créer des configurations personnalisées. L’**éditeur de paramètres** a un bouton **Modifier JSON** en haut à droite qui ouvre le fichier en vue de sa modification.

L’exemple suivant illustre une configuration, que vous pouvez utiliser comme point de départ :

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

JSON IntelliSense vous aide à modifier le fichier *CMakeSettings.json* :

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

L’éditeur JSON vous informe également lorsque vous choisissez des paramètres incompatibles.

Pour plus d’informations sur chacune des propriétés dans le fichier, consultez [Informations de référence sur le schéma CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 fournit plusieurs configurations CMake qui définissent la manière d’appeler CMake.exe pour créer le cache CMake d’un projet donné. Pour ajouter une nouvelle configuration, cliquez sur la liste déroulante de configuration dans la barre d’outils et choisissez **Gérer les configurations** :

   ![Gérer les configurations CMake](media/cmake-manage-configurations.png)

Vous pouvez choisir dans la liste des configurations prédéfinies :

   ![Configurations CMake prédéfinies](media/cmake-configurations.png)

La première fois que vous sélectionnez une configuration, Visual Studio crée un fichier *CMakeSettings.json* dans le dossier racine de votre projet. Ce fichier est utilisé pour recréer le fichier de cache CMake, par exemple, après une opération **Clean**.

Pour ajouter une configuration supplémentaire, cliquez à droite *sur CMakeSettings.json* et choisissez **Add Configuration**.

   ![Configuration CMake Add](media/cmake-add-configuration.png "Configuration D’ajout de CMake")

Vous pouvez également modifier le fichier en utilisant l’**éditeur de paramètres CMake**. Cliquez à droite sur *CMakeSettings.json* dans **Solution Explorer** et choisissez **Edit CMake Paramètres**. Ou sélectionnez **Gérer les configurations** dans la liste déroulante de configuration en haut de la fenêtre de l’éditeur.

Vous pouvez également modifier directement *CMakeSettings.json* pour créer des configurations personnalisées. L’exemple suivant illustre une configuration, que vous pouvez utiliser comme point de départ :

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

JSON IntelliSense vous aide à modifier le fichier *CMakeSettings.json* :

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Pour plus d’informations sur chacune des propriétés dans le fichier, consultez [Informations de référence sur le schéma CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)<br/>
[Se connecter à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)
