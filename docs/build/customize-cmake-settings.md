---
title: Personnaliser des paramètres de génération CMake dans Visual Studio
ms.date: 03/05/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: 4864e094ab967a563b153fa79fd0bf5c375f40f7
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124887"
---
# <a name="customize-cmake-build-settings"></a>Personnaliser des paramètres de génération CMake

Visual Studio fournit plusieurs configurations CMake qui définissent la manière d’appeler CMake.exe pour créer le cache CMake d’un projet donné. Pour ajouter une nouvelle configuration, cliquez sur la liste déroulante de configuration dans la barre d’outils et choisissez **Gérer les configurations** :

   ![Gérer les configurations CMake](media/cmake-manage-configurations.png)

Vous pouvez choisir dans la liste des configurations prédéfinies :

   ![Configurations CMake prédéfinies](media/cmake-configurations.png)

La première fois que vous sélectionnez une configuration, Visual Studio crée un fichier `CMakeSettings.json` dans le dossier racine de votre projet. Ce fichier est utilisé pour recréer le fichier de cache CMake, par exemple, après une opération **Clean**. 

Pour ajouter une configuration supplémentaire, cliquez avec le bouton droit sur `CMakeSettings.json` et choisissez **Ajouter une configuration**. 

   ![Ajouter une configuration CMake](media/cmake-add-configuration.png "Ajouter une configuration CMake")

JSON IntelliSense vous permet de modifier le fichier `CMakeSettings.json` :

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

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

- **name** : nom qui apparaît dans la liste déroulante des configurations C++. La macro `${name}` vous permet d’utiliser cette valeur quand vous rédigez d’autres valeurs de propriétés comme des chemins. Pour obtenir un exemple, consultez la définition de **buildRoot** dans `CMakeSettings.json`.

- **generator** : correspond au commutateur **-G** CMake et spécifie le générateur à utiliser. Cette propriété peut également être utilisée en tant que macro, `${generator}`, quand vous rédigez d’autres valeurs de propriétés. Visual Studio prend actuellement en charge les générateurs CMake suivants :

  - « Ninja »
  - « Visual Studio 14 2015 »
  - « Visual Studio 14 2015 ARM »
  - « Visual Studio 14 2015 Win64 »
  - « Visual Studio 15 2017 »
  - « Visual Studio 15 2017 ARM »
  - « Visual Studio 15 2017 Win64 »

  Comme Ninja est conçu pour des vitesses de génération rapides plutôt que pour la flexibilité et la fonctionnalité, il est défini par défaut. Toutefois, certains projets CMake peuvent ne pas pouvoir être générés correctement avec Ninja. Si cela se produit, vous pouvez demander à CMake de générer un projet Visual Studio à la place.

  Pour spécifier un générateur Visual Studio, ouvrez `CMakeSettings.json` à partir du menu principal en choisissant **CMake | Modifier les paramètres CMake**. Supprimez « Ninja » et tapez « V ». Cela active IntelliSense, qui vous permet de choisir le générateur souhaité.

  Quand la configuration active spécifie un générateur Visual Studio, MSBuild.exe est appelé par défaut avec des arguments `-m -v:minimal`. Pour personnaliser la génération, dans le fichier `CMakeSettings.json`, vous pouvez spécifier des [arguments de ligne de commande MSBuild](../build/reference/msbuild-visual-cpp-overview.md) supplémentaires à passer au système de génération via la propriété `buildCommandArgs` :
    
    ```json
    "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
    ```

- **buildRoot** : correspond au commutateur **-DCMAKE_BINARY_DIR** et spécifie où est créé le cache CMake. Si le dossier n’existe pas, il est créé.

- **variables** : contient une paire nom-valeur de variables CMake qui sont passées sous la forme **-D** *_nom_=_valeur_* à CMake. Si vos instructions de génération de projet CMake spécifient l’ajout des variables directement dans le fichier de cache CMake, nous vous recommandons de les ajouter ici à la place. L’exemple suivant indique comment spécifier les paires nom-valeur pour l’ensemble d’outils MSVC 14.14.26428 :

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    }
  ]
```

Notez que si vous ne définissez pas la `"type"`, sera considéré comme le type « STRING » par défaut.

- **cmakeCommandArgs** : Spécifie tous les commutateurs supplémentaires que vous voulez passer à CMake.exe.

- **configurationType** : Définit le type de configuration de génération du générateur sélectionné. Les valeurs actuellement prises en charge sont « Debug », « MinSizeRel », « Release » et « RelWithDebInfo ».

- **ctestCommandArgs** : spécifie les commutateurs supplémentaires à passer à CTest durant l’exécution des tests.

- **buildCommandArgs** : spécifie les commutateurs supplémentaires à passer au système de build sous-jacent. Par exemple, si vous passez -v quand vous utilisez le générateur Ninja, cela oblige Ninja à sortir des lignes de commande.

Des paramètres supplémentaires sont disponibles pour les projets Linux CMake. Consultez [Configurer un projet Linux CMake](../linux/cmake-linux-project.md).

## <a name="environment-variables"></a>Variables d’environnement

 `CMakeSettings.json` prend également en charge la consommation de variables d’environnement dans l’une des propriétés mentionnées ci-dessus. La syntaxe à utiliser est `${env.FOO}` pour développer la variable d’environnement %FOO%.
Vous avez également accès aux macros intégrées dans ce fichier :

- `${workspaceRoot}` : Fournit le chemin complet du dossier de l’espace de travail
- `${workspaceHash}` : Hachage de l’emplacement de l’espace de travail. Utile pour créer un identificateur unique pour l’espace de travail actuel (par exemple, à utiliser dans les chemins de dossier)
- `${projectFile}` : Chemin complet du fichier racine CMakeLists.txt
- `${projectDir}` : Chemin complet du dossier du fichier racine CMakeLists.txt
- `${thisFile}` : Chemin complet du fichier `CMakeSettings.json`
- `${name}` : Nom de la configuration
- `${generator}` : Nom du générateur CMake utilisé dans cette configuration

## <a name="ninja-command-line-arguments"></a>Arguments de ligne de commande Ninja

Si les cibles ne sont pas spécifiées, génère la cible « par défaut » (voir le manuel).

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Option|Description|
|--------------|------------|
| --version  | imprime la version de Ninja (« 1.7.1 »)|
|   -C DIR   | passe à DIR avant toute autre opération|
|   -f FILE  | spécifie le fichier d’entrée de génération (valeur par défaut = build.ninja)|
|   -j N     | exécute des travaux N en parallèle (valeur par défaut = 14, dérivée des processeurs disponibles)|
|   -k N     | continue jusqu’à ce que N travaux échouent (valeur par défaut = 1)|
|   -l N     | ne démarre pas de nouveaux travaux si la charge moyenne est supérieure à N|
|   -n       | test (n’exécute pas de commandes mais agit comme elles avaient réussi)|
|   -v       | affiche toutes les lignes de commande pendant la génération|
|   -d MODE  | active le débogage (utilisez -d list pour obtenir la liste des modes)|
|   -t TOOL  | exécute un sous-outil (utilisez -t list pour obtenir la liste des sous-outils). met fin à des options de niveau supérieur ; autres indicateurs sont passées à l’outil|
|   -w FLAG  | ajuste les avertissements (utiliser -w list pour obtenir la liste des avertissements)|

## <a name="inherited-environments"></a>Environnements hérités

 `CMakeSettings.json` prend en charge les environnements hérités. Cette fonctionnalité vous permet (1) d’hériter les environnements par défaut et (2) de créer des variables d’environnement personnalisées qui sont passées à CMake.exe quand il s’exécute.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

L’exemple ci-dessus revient à exécuter **l’invite de commandes développeur pour VS 2017** avec les arguments **-arch=amd64 -host_arch=amd64**.

Le tableau suivant présente les valeurs par défaut :

|Nom du contexte|Description|
|-----------|-----------------|
|vsdev|Environnement Visual Studio par défaut|
|msvc_x86|Compiler pour x86 à l’aide d’outils x86|
|msvc_arm| Compiler pour ARM à l’aide d’outils x86|
|msvc_arm64|Compiler pour ARM64 à l’aide d’outils x86|
|msvc_x86_x64|Compiler pour AMD64 à l’aide d’outils x86|
|msvc_x64_x64|Compiler pour AMD64 à l’aide d’outils 64 bits|
|msvc_arm_x64|Compiler pour ARM à l’aide d’outils 64 bits|
|msvc_arm64_x64|Compiler pour ARM64 à l’aide d’outils 64 bits|

### <a name="custom-environment-variables"></a>Variables d’environnement personnalisées

Dans `CMakeSettings.json`, vous pouvez définir des variables d’environnement personnalisées globalement ou par configuration dans la propriété **environments**. L’exemple suivant définit une variable globale, **BuildDir**, qui est héritée dans les configurations x86-Debug et de x64-Debug. Chaque configuration utilise la variable pour spécifier la valeur de la propriété **buildRoot** pour cette configuration. Notez également la façon dont chaque configuration utilise la propriété **inheritEnvironments** pour spécifier une variable qui s’applique uniquement à cette configuration.

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

Dans l’exemple suivant, la configuration x86-Debug définit sa propre valeur pour la propriété **BuildDir**. Cette valeur remplace celle définie par la propriété **BuildDir** globales pour que **BuildRoot** prenne la valeur `D:\custom-builddir\x86-Debug`.

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir"
          // This environment does not specify a namespace, hence by default "env" will be assumed.
          // "namespace" : "name" would require that this variable be referenced with "${name.BuildDir}".
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ],
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)<br/>
[Se connecter à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)<br/>
