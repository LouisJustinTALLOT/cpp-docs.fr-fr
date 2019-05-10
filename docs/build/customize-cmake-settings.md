---
title: Personnaliser des paramètres de génération CMake dans Visual Studio
ms.date: 04/25/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: 20ed066f71a5c8c3acb00ef5923fa5c9f16ac229
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877154"
---
# <a name="customize-cmake-build-settings"></a>Personnaliser des paramètres de génération CMake

::: moniker range="vs-2019"

Dans Visual Studio 2019 et versions ultérieures, vous pouvez ajouter des configurations et personnaliser leurs paramètres à l’aide de la **éditeur de paramètres CMake**. L’éditeur est destiné à être une alternative plus simple à modifier manuellement le fichier CMakeSettings.json, mais si vous préférez modifier directement le fichier, vous pouvez cliquer sur le **JSON modifier** lien dans le coin supérieur droit de l’éditeur. 

Pour ouvrir l’éditeur, cliquez sur le **Configuration** liste déroulante dans la barre d’outils principale et choisissez **gérer les Configurations**.

![Liste déroulante des configurations CMake](media/vs2019-cmake-manage-configurations.png)

Maintenant vous voyez la **éditeur de paramètres** avec les configurations installées sur la gauche. 

![Éditeur de paramètres de CMake](media/cmake-settings-editor.png)

Visual Studio fournit deux configurations par défaut : `x64-Debug` et `x86-Debug`. Vous pouvez ajouter des configurations supplémentaires en cliquant sur le signe plus vert. Les paramètres que vous voyez dans l’éditeur peuvent varier selon la configuration est sélectionnée.

Les options que vous choisissez dans l’éditeur sont écrits dans un fichier appelé CMakeSettings.json. Ce fichier fournit des arguments de ligne de commande et les variables d’environnement qui sont passées à CMake lorsque vous générez les projets. Visual Studio ne modifie jamais CMakeLists.txt automatiquement ; à l’aide de CMakeSettings.json, vous pouvez personnaliser la génération via Visual Studio tout en conservant les fichiers de projet CMake intactes afin que d’autres personnes de votre équipe puissent les utiliser avec les outils qu’ils utilisent.

## <a name="cmake-general-settings"></a>Paramètres généraux de CMake

Les paramètres suivants sont disponibles sous le **général** titre :

### <a name="configuration-name"></a>Nom de la configuration

Correspond à la **nom** paramètre. Il s’agit du nom qui apparaît dans le C++ liste déroulante configuration. Vous pouvez utiliser le `${name}` macro pour composer des autres valeurs de propriété telles que des chemins d’accès.


### <a name="configuration-type"></a>Type de configuration

Correspond à la **le type de configuration** paramètre. Définit le type de configuration de build pour le générateur sélectionné. Les valeurs actuellement prises en charge sont « Debug », « MinSizeRel », « Release » et « RelWithDebInfo ».

### <a name="toolset"></a>Ensemble d'outils

Correspond à la **inheritedEnvironments** paramètre. Définit l’environnement du compilateur qui sera utilisé pour générer la configuration sélectionnée. Valeurs prises en charge varient selon le type de configuration. Pour créer un environnement personnalisé, cliquez sur le **JSON modifier** lien dans le coin supérieur droit de l’éditeur de paramètres et de modifier directement le fichier CMakeSettings.json.

### <a name="cmake-toolchain-file"></a>Fichier de chaîne d’outils CMake

Chemin d’accès au fichier de chaîne d’outils CMake. Seront passés à CMake en tant que «-DCMAKE_TOOLCHAIN_FILE = \<filepath > ».

### <a name="build-root"></a>Racine de build

Correspond à **buildRoot**. Mappe à **-DCMAKE_BINARY_DIR** basculer et spécifie où le cache CMake sera créé. Si le dossier n’existe pas, il est créé.

## <a name="command-arguments"></a>Les arguments de la commande

Les paramètres suivants sont disponibles sous le **arguments de la commande** titre :

### <a name="cmake-command-arguments"></a>Arguments de la commande CMake

Correspond à **cmakeCommandArgs**. Spécifie tous les commutateurs que vous souhaitez passer à CMake.exe.

### <a name="build-command-arguments"></a>Arguments de commande de génération

Correspond à **buildCommandArgs**: Spécifie le système de génération des commutateurs supplémentaires à passer au sous-jacent. Par exemple, si vous passez -v quand vous utilisez le générateur Ninja, cela oblige Ninja à sortir des lignes de commande.


### <a name="ctest-command-arguments"></a>Arguments de commande CTest

Correspond à**ctestCommandArgs**: Spécifie les commutateurs supplémentaires à passer à CTest lors de l’exécution des tests.

## <a name="general-settings-for-remote-builds"></a>Paramètres généraux pour les builds à distance

Pour les configurations, telles que Linux qui utilisent des builds distantes, les paramètres suivants sont également disponibles :

### <a name="rsync-command-arguments"></a>arguments de commande rsync

Fournir les arguments de commande à passer à rsync. 

## <a name="cmake-variables-and-cache"></a>Cache et les variables de CMake

Ces paramètres permettent de définir les variables CMake et enregistrez-les dans CMakeSettings.json. Ils seront passés à CMake au moment de la génération et remplacent toutes les valeurs peuvent être dans le fichier CMakeLists.txt. Vous pouvez utiliser cette section de la même façon que vous pouvez utiliser le CMakeGUI pour afficher une liste de toutes les variables CMake disponibles pour le modifier. Cliquez sur le **enregistrer et générer le cache** bouton pour afficher une liste de toutes les variables CMake disponibles pour modifier, y compris les variables avancées (par le CMakeGUI). Vous pouvez filtrer la liste par nom de variables. 

Correspond à **variables**: contient une paire nom-valeur de variables CMake qui sera transmis en tant que **-D** *_nom_ =  _valeur_* à CMake. Si vos instructions de génération de projet CMake spécifient l’ajout des variables directement dans le fichier de cache CMake, nous vous recommandons de les ajouter ici à la place.

## <a name="advanced-settings"></a>Paramètres avancés

### <a name="cmake-generator"></a>Générateur de CMake

Correspond à **Générateur**: mappe à la CMake **: Password-g** basculer et spécifie le Générateur à utiliser. Cette propriété peut également être utilisée en tant que macro, `${generator}`, quand vous rédigez d’autres valeurs de propriétés. Visual Studio prend actuellement en charge les générateurs CMake suivants :

  - « Ninja »
  - « Unix Makefiles »
  - "Visual Studio 16 2019"
  - "Visual Studio 16 2019 Win64"
  - - "Visual Studio 16 2019 ARM"
  - « Visual Studio 15 2017 »
  - « Visual Studio 15 2017 Win64 »
  - « Visual Studio 15 2017 ARM »
  - « Visual Studio 14 2015 »
  - « Visual Studio 14 2015 Win64 »
  - « Visual Studio 14 2015 ARM »
  
  Comme Ninja est conçu pour des vitesses de génération rapides plutôt que pour la flexibilité et la fonctionnalité, il est défini par défaut. Toutefois, certains projets CMake peuvent ne pas pouvoir être générés correctement avec Ninja. Si cela se produit, vous pouvez demander à CMake de générer un projet Visual Studio à la place.

### <a name="intellisense-mode"></a>IntelliSense mode

Pour une fonctionnalité IntelliSense précise, définissez ce paramètre sur la valeur appropriée pour votre projet.

### <a name="install-directory"></a>Répertoire d’installation

Le répertoire dans lequel CMake installe les cibles auxquelles il s’appuie.

### <a name="cmake-executable"></a>Fichier exécutable CMake

Le chemin d’accès complet au fichier exécutable CMake, y compris l’extension et le nom de fichier. Pour les builds à distance, spécifiez l’emplacement de CMake sur l’ordinateur distant.

Pour les configurations, telles que Linux qui utilisent des builds distantes, les paramètres suivants sont également disponibles :

### <a name="remote-cmakeliststxt-root"></a>Racine CMakeLists.txt à distance

Le répertoire sur l’ordinateur distant qui contient le fichier CMakeLists.txt racine.

### <a name="remote-install-root"></a>Racine de l’installation à distance

Le répertoire sur l’ordinateur distant dans lequel CMake installe cibles.

### <a name="remote-copy-sources"></a>Sources de copie à distance

Spécifie s’il faut copier les fichiers sources à l’ordinateur distant et vous permet de spécifier s’il faut utiliser rsync ou sftp. 

## <a name="directly-edit-cmakesettingsjson"></a>Modifier directement CMakeSettings.json

Vous pouvez également modifier directement `CMakeSettings.json` pour créer des configurations personnalisées. Le **éditeur de paramètres** a un **JSON modifier** bouton en haut à droite qui ouvre le fichier pour modification. 

L’exemple suivant montre un exemple de configuration que vous pouvez utiliser comme point de départ :

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

JSON IntelliSense vous permet de modifier le `CMakeSettings.json` fichier :

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

L’éditeur JSON vous informe également lorsque vous choisissez des paramètres incompatibles.

Pour plus d’informations sur chacune des propriétés dans le fichier, consultez [référence du schéma CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 fournit plusieurs configurations CMake qui définissent comment les CMake.exe est appelé pour créer le cache CMake pour un projet donné. Pour ajouter une nouvelle configuration, cliquez sur la liste déroulante de configuration dans la barre d’outils et choisissez **Gérer les configurations** :

   ![Gérer les configurations CMake](media/cmake-manage-configurations.png)

Vous pouvez choisir dans la liste des configurations prédéfinies :

   ![Configurations CMake prédéfinies](media/cmake-configurations.png)

La première fois que vous sélectionnez une configuration, Visual Studio crée un fichier `CMakeSettings.json` dans le dossier racine de votre projet. Ce fichier est utilisé pour recréer le fichier de cache CMake, par exemple, après une opération **Clean**. 

Pour ajouter une configuration supplémentaire, cliquez avec le bouton droit sur `CMakeSettings.json` et choisissez **Ajouter une configuration**. 

   ![Ajouter une configuration CMake](media/cmake-add-configuration.png "Ajouter une configuration CMake")

Vous pouvez également modifier le fichier en utilisant l’**éditeur de paramètres CMake**. Cliquez avec le bouton droit sur `CMakeSettings.json` dans l’**Explorateur de solutions** et choisissez **Modifier les paramètres CMake**. Ou sélectionnez **Gérer les configurations** dans la liste déroulante de configuration en haut de la fenêtre de l’éditeur. 

Vous pouvez également modifier directement `CMakeSettings.json` pour créer des configurations personnalisées à l’exemple suivant montre un exemple de configuration que vous pouvez utiliser comme point de départ :

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

JSON IntelliSense vous permet de modifier le fichier `CMakeSettings.json` :

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Pour plus d’informations sur chacune des propriétés dans le fichier, consultez [référence du schéma CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)<br/>
[Se connecter à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)<br/>
