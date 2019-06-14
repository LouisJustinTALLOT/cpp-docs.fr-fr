---
title: Personnaliser des paramètres de génération CMake dans Visual Studio
ms.date: 05/16/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: a00b18f163758be0238a05c4d2af3195014d79b0
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042534"
---
# <a name="customize-cmake-build-settings"></a>Personnaliser des paramètres de génération CMake

::: moniker range="vs-2019"

Dans Visual Studio 2019 et ultérieur, vous pouvez ajouter des configurations et personnaliser leurs paramètres à l’aide de l’**éditeur de paramètres CMake**. L’éditeur vous évite de modifier manuellement le fichier CMakeSettings.json, mais si vous préférez modifier ce dernier directement, vous pouvez cliquer sur le lien **Modifier JSON** en haut à droite de l’éditeur. 

Pour ouvrir l’éditeur, cliquez sur la liste déroulante **Configuration** dans la barre d’outils principale et choisissez **Gérer les configurations**.

![Liste déroulante des configurations CMake](media/vs2019-cmake-manage-configurations.png)

Maintenant, vous voyez l’**éditeur de paramètres**, avec les configurations installées sur la gauche. 

![Éditeur de paramètres CMake](media/cmake-settings-editor.png)

Visual Studio fournit deux configurations par défaut : `x64-Debug` et `x86-Debug`. Vous pouvez ajouter des configurations en cliquant sur le signe plus vert. Les paramètres que vous voyez dans l’éditeur peuvent varier selon la configuration sélectionnée.

Les options que vous choisissez dans l’éditeur sont écrites dans un fichier appelé CMakeSettings.json. Ce fichier fournit des arguments de ligne de commande et des variables d’environnement qui sont passés à CMake quand vous générez les projets. Visual Studio ne modifie jamais CMakeLists.txt automatiquement ; à l’aide de CMakeSettings.json, vous pouvez personnaliser la génération par le biais de Visual Studio tout en conservant les fichiers de projet CMake intacts afin que d’autres personnes de votre équipe puissent les utiliser avec les outils de leur choix.

## <a name="cmake-general-settings"></a>Paramètres généraux CMake

Les paramètres suivants sont disponibles sous le titre **Général** :

### <a name="configuration-name"></a>Nom de configuration

Correspond au paramètre **name**. Il s’agit du nom qui apparaît dans la liste déroulante des configurations C++. Vous pouvez utiliser la macro `${name}` pour composer d’autres valeurs de propriété telles que des chemins.


### <a name="configuration-type"></a>Type de configuration

Correspond au paramètre **configurationType**. Définit le type de configuration de build du générateur sélectionné. Les valeurs actuellement prises en charge sont « Debug », « MinSizeRel », « Release » et « RelWithDebInfo ».

### <a name="toolset"></a>Ensemble d'outils

Correspond au paramètre **inheritedEnvironments**. Définit l’environnement de compilation à utiliser pour générer la configuration sélectionnée. Les valeurs prises en charge varient selon le type de configuration. Pour créer un environnement personnalisé, cliquez sur le lien **Modifier JSON** en haut à droite de l’éditeur de paramètres et modifiez directement le fichier CMakeSettings.json.

### <a name="cmake-toolchain-file"></a>Fichier de chaîne d’outils CMake

Chemin du fichier de chaîne d’outils CMake. Celui-ci est passé à CMake à l’aide de « -DCMAKE_TOOLCHAIN_FILE = \<chemin> ».

### <a name="build-root"></a>Racine de build

Correspond à **buildRoot**. Correspond au commutateur **-DCMAKE_BINARY_DIR** et spécifie où est créé le cache CMake. Si le dossier n’existe pas, il est créé.

## <a name="command-arguments"></a>Arguments de la commande

Les paramètres suivants sont disponibles sous le titre **Arguments de la commande**  :

### <a name="cmake-command-arguments"></a>Arguments de commande CMake

Correspond à **cmakeCommandArgs**. Spécifie tous les commutateurs supplémentaires que vous voulez passer à CMake.exe.

### <a name="build-command-arguments"></a>Arguments de commande de build

Correspond à **buildCommandArgs** : spécifie les commutateurs supplémentaires à passer au système de build sous-jacent. Par exemple, si vous passez -v quand vous utilisez le générateur Ninja, cela oblige Ninja à sortir des lignes de commande.


### <a name="ctest-command-arguments"></a>Arguments de commande CTest

Correspond à **ctestCommandArgs** : spécifie les commutateurs supplémentaires à passer à CTest durant l’exécution des tests.

## <a name="general-settings-for-remote-builds"></a>Paramètres généraux pour les builds distantes

Pour les configurations telles que Linux qui utilisent des builds distantes, les paramètres suivants sont également disponibles :

### <a name="rsync-command-arguments"></a>Arguments de commande rsync

Fournissent les arguments de commande à passer à rsync. 

## <a name="cmake-variables-and-cache"></a>Variables et cache CMake

Ces paramètres vous permettent de définir des variables CMake et de les enregistrer dans CMakeSettings.json. Ils sont passés à CMake au moment de la génération et remplacent toutes les valeurs se trouvant éventuellement dans le fichier CMakeLists.txt. Vous pouvez utiliser cette section de la même façon que l’interface CMakeGUI pour afficher la liste de toutes les variables CMake modifiables. Cliquez sur le bouton **Enregistrer et générer le cache** pour voir la liste de toutes les variables CMake modifiables, y compris les variables avancées (par le biais de l’interface CMakeGUI). Vous pouvez filtrer la liste par nom de variables. 

Correspond à **variables** : contient une paire nom-valeur de variables CMake qui sont passées sous la forme **-D** *_nom_=_valeur_* à CMake. Si vos instructions de génération de projet CMake spécifient l’ajout des variables directement dans le fichier de cache CMake, nous vous recommandons de les ajouter ici à la place.

## <a name="advanced-settings"></a>Paramètres avancés

### <a name="cmake-generator"></a>Générateur CMake

Correspond à **generator** : correspond au commutateur **-G** CMake et spécifie le générateur à utiliser. Cette propriété peut également être utilisée en tant que macro, `${generator}`, quand vous rédigez d’autres valeurs de propriétés. Visual Studio prend actuellement en charge les générateurs CMake suivants :

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
  
  Comme Ninja est conçu pour des vitesses de génération rapides plutôt que pour la flexibilité et la fonctionnalité, il est défini par défaut. Toutefois, certains projets CMake peuvent ne pas pouvoir être générés correctement avec Ninja. Si cela se produit, vous pouvez demander à CMake de générer un projet Visual Studio à la place.

### <a name="intellisense-mode"></a>Mode IntelliSense

Pour utiliser IntelliSense avec précision, définissez ce paramètre sur la valeur appropriée pour votre projet.

### <a name="install-directory"></a>Répertoire d’installation

Répertoire dans lequel CMake installe les cibles qu’il génère.

### <a name="cmake-executable"></a>Exécutable CMake

Chemin complet de l’exécutable CMake ainsi que le nom de fichier et l’extension. Pour les builds distantes, spécifiez l’emplacement CMake sur l’ordinateur distant.

Pour les configurations telles que Linux qui utilisent des builds distantes, les paramètres suivants sont également disponibles :

### <a name="remote-cmakeliststxt-root"></a>Racine CMakeLists.txt distante

Répertoire de l’ordinateur distant qui contient le fichier CMakeLists.txt racine.

### <a name="remote-install-root"></a>Racine d’installation distante

Répertoire de l’ordinateur distant dans lequel CMake installe les cibles.

### <a name="remote-copy-sources"></a>Copier les sources sur la machine distante

Indique s’il faut copier les fichiers sources sur l’ordinateur distant et vous permet de spécifier s’il faut utiliser rsync ou sftp. 

## <a name="directly-edit-cmakesettingsjson"></a>Modifier CMakeSettings.json directement

Vous pouvez également modifier directement `CMakeSettings.json` pour créer des configurations personnalisées. L’**éditeur de paramètres** a un bouton **Modifier JSON** en haut à droite qui ouvre le fichier en vue de sa modification. 

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

JSON IntelliSense vous permet de modifier le fichier `CMakeSettings.json` :

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

De plus, l’éditeur JSON vous avertit quand vous choisissez des paramètres incompatibles.

Pour plus d’informations sur chacune des propriétés dans le fichier, consultez [Informations de référence sur le schéma CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 fournit plusieurs configurations CMake qui définissent la manière d’appeler CMake.exe pour créer le cache CMake d’un projet donné. Pour ajouter une nouvelle configuration, cliquez sur la liste déroulante de configuration dans la barre d’outils et choisissez **Gérer les configurations** :

   ![Gérer les configurations CMake](media/cmake-manage-configurations.png)

Vous pouvez choisir dans la liste des configurations prédéfinies :

   ![Configurations CMake prédéfinies](media/cmake-configurations.png)

La première fois que vous sélectionnez une configuration, Visual Studio crée un fichier `CMakeSettings.json` dans le dossier racine de votre projet. Ce fichier est utilisé pour recréer le fichier de cache CMake, par exemple, après une opération **Clean**. 

Pour ajouter une configuration supplémentaire, cliquez avec le bouton droit sur `CMakeSettings.json` et choisissez **Ajouter une configuration**. 

   ![Ajouter une configuration CMake](media/cmake-add-configuration.png "Ajouter une configuration CMake")

Vous pouvez également modifier le fichier en utilisant l’**éditeur de paramètres CMake**. Cliquez avec le bouton droit sur `CMakeSettings.json` dans l’**Explorateur de solutions** et choisissez **Modifier les paramètres CMake**. Ou sélectionnez **Gérer les configurations** dans la liste déroulante de configuration en haut de la fenêtre de l’éditeur. 

Vous pouvez également modifier directement `CMakeSettings.json` pour créer des configurations personnalisées. L’exemple illustre une configuration que vous pouvez utiliser comme point de départ :

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

Pour plus d’informations sur chacune des propriétés dans le fichier, consultez [Informations de référence sur le schéma CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)<br/>
[Se connecter à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)<br/>
