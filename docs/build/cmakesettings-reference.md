---
title: Informations de référence sur le schéma CMakeSettings.json
ms.date: 04/25/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 80392eedd5ef50ddd9c9bcb81c1605a534088133
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877101"
---
# <a name="cmakesettingsjson-schema-reference"></a>Informations de référence sur le schéma CMakeSettings.json

Le **cmakesettings.json**' fichier contient des informations qui spécifient comment Visual Studio doit interagir avec CMake pour générer un projet pour une plateforme spécifiée. Le fichier stocke des informations telles que les variables d’environnement ou les arguments pour l’environnement cmake.exe. Vous pouvez modifier directement ou utiliser le **éditeur de paramètres de CMake**. Consultez [CMake de personnaliser les paramètres dans Visual Studio build](customize-cmake-settings.md) pour plus d’informations sur l’éditeur.

## <a name="environments"></a>Environnements

Le `environments` tableau contient une liste de `items` de type `object` qui définissent un ensemble d’outils du compilateur « environnement ». Un environnement peut être utilisé pour appliquer un ensemble de variables à une `configuration`. Chaque élément dans le tableau `environments` comprend ce qui suit :

- `namespace` : nomme l’environnement afin que ses variables puissent être référencées à partir d’une configuration sous la forme `namespace.variable`. L’objet environnement par défaut est appelé `env` et il est rempli avec certaines variables d’environnement système, notamment `%USERPROFILE%`.
- `environment` : identifie de façon unique ce groupe de variables. Permet au groupe d’être hérité plus tard dans une entrée `inheritEnvironments`.
- `groupPriority`: entier qui spécifie la priorité de ces variables lors de leur évaluation. Les éléments dont la valeur est élevée sont évalués en premier.
- `inheritEnvironments`: tableau de valeurs qui spécifient l’ensemble des environnements hérités par ce groupe. Cette fonctionnalité vous permet de hériter des environnements par défaut et créer des variables d’environnement personnalisées qui sont passées à CMake.exe lorsqu’elle est exécutée.

   ```json
   "inheritEnvironments": [ "msvc_x64_x64" ]
   ```

   L’exemple ci-dessus revient à exécuter **l’invite de commandes développeur pour VS 2017** avec les arguments **-arch=amd64 -host_arch=amd64**. Vous pouvez utiliser tout environnement personnalisé ou ces environnements prédéfinis :
 
  - linux_arm : Ciblez Linux ARM à distance.
  - linux_x64 : Ciblez Linux x64 à distance.
  - linux_x86 : Ciblez Linux x86 à distance.
  - msvc_arm : Ciblez Windows ARM avec le compilateur MSVC.
  - msvc_arm_x64 : Ciblez Windows ARM avec le compilateur MSVC 64 bits.
  - msvc_arm64 : Ciblez Windows ARM64 avec le compilateur MSVC.
  - msvc_arm64_x64 : Ciblez Windows ARM64 avec le compilateur MSVC 64 bits.
  - msvc_x64 : Ciblez Windows x64 avec le compilateur MSVC.
  - msvc_x64_x64 : Ciblez Windows x64 avec le compilateur MSVC 64 bits.
  - msvc_x86 : Ciblez Windows x86 avec le compilateur MSVC.
  - msvc_x86_x64 : Ciblez Windows x86 avec le compilateur MSVC 64 bits.

## <a name="configurations"></a>Configurations

Le tableau `configurations` se compose d’objets qui représentent des configurations CMake qui s’appliquent au fichier CMakeLists.txt dans le même dossier. Vous pouvez utiliser ces objets pour définir plusieurs configurations de build et basculer facilement de l’une à l’autre dans l’IDE. 

Une `configuration` a les propriétés suivantes :
- `name` : nomme la configuration.
- `description` : description de cette configuration qui apparaît dans les menus.
- `generator` : spécifie le générateur CMake à utiliser pour cette configuration. Possibilités :

  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix Makefiles
  - Ninja

Comme Ninja est conçu pour des vitesses de génération rapides plutôt que pour la flexibilité et la fonctionnalité, il est défini par défaut. Toutefois, certains projets CMake peuvent ne pas pouvoir être générés correctement avec Ninja. Si cela se produit, vous pouvez demander à CMake de générer un projet Visual Studio à la place.

Pour spécifier un générateur Visual Studio, ouvrez `CMakeSettings.json` à partir du menu principal en choisissant **CMake | Modifier les paramètres CMake**. Supprimez « Ninja » et tapez « V ». Cela active IntelliSense, qui vous permet de choisir le générateur souhaité.

Quand la configuration active spécifie un générateur Visual Studio, MSBuild.exe est appelé par défaut avec des arguments `-m -v:minimal`. Pour personnaliser la génération, dans le fichier `CMakeSettings.json`, vous pouvez spécifier des [arguments de ligne de commande MSBuild](../build/reference/msbuild-visual-cpp-overview.md) supplémentaires à passer au système de génération via la propriété `buildCommandArgs` :

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `configurationType` : spécifie la configuration du type de build pour le générateur sélectionné. Possibilités :
 
  - Débogage
  - Édition
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`: Spécifie un ou plusieurs environnements de compilateur qui dépend de cette configuration. Peut être n’importe quel environnement personnalisé ou un des environnements prédéfinis.
- `buildRoot`: Spécifie le répertoire dans lequel CMake génère les scripts de compilation pour le générateur choisi.  Mappe à **-DCMAKE_BINARY_DIR** basculer et spécifie où le cache CMake sera créé. Si le dossier n’existe pas, il est créé. Les macros prises en charge sont `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `installRoot` : spécifie le répertoire dans lequel CMake génère les cibles d’installation pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `cmakeCommandArgs`: Spécifie des options de ligne de commande supplémentaires passées à CMake lorsqu’elle est appelée pour générer le cache.
- `cmakeToolchain` : spécifie le fichier de chaîne d’outils. Celui-ci est passé à CMake à l’aide de -DCMAKE_TOOLCHAIN_FILE.
- `buildCommandArgs`: Spécifie les commutateurs de build natifs passés à CMake après--build--. Par exemple, si vous passez -v quand vous utilisez le générateur Ninja, cela oblige Ninja à sortir des lignes de commande. Consultez [arguments de ligne de commande Ninja](#ninja) pour plus d’informations sur les commandes Ninja.
- `ctestCommandArgs` : spécifie des options de ligne de commande supplémentaires passées à CTest pendant l’exécution des tests.
- `codeAnalysisRuleset` : spécifie l’ensemble de règles à utiliser lors de l’exécution de l’analyse du code. Cela peut être un chemin d’accès complet ou le nom de fichier d’un fichier ruleset installé par Visual Studio.
- `intelliSenseMode` : spécifie le mode utilisé pour le calcul des informations IntelliSense. Possibilités :
 
  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-arm
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-arm
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm

- `cacheRoot` : spécifie le chemin d’un cache CMake. Ce répertoire doit contenir un fichier CMakeCache.txt existant.

### <a name="additional-settings-for-cmake-linux-projects"></a>Paramètres supplémentaires pour les projets CMake Linux. 

- `remoteMachineName` : spécifie le nom de la machine Linux distante qui héberge CMake, les builds et le débogueur. Utilisez le gestionnaire de connexions pour l’ajout de nouvelles machines Linux. Les macros prises en charge incluent `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity` : spécifie le niveau de détail de l’opération de copie de la source vers la machine distante. Valeurs possibles : « Normal », « Détaillé » ou « Diagnostic ».
- `remoteCopySourcesConcurrentCopies` : spécifie le nombre de copies simultanées utilisées durant la synchronisation des sources par rapport à la machine distante.
- `remoteCopySourcesMethod` : spécifie la méthode de copie des fichiers sur la machine distante. Valeurs possibles : « rsync » ou « sftp ».
- `remoteCMakeListsRoot` : spécifie le répertoire de la machine distante qui contient le projet CMake. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteBuildRoot` : spécifie le répertoire de la machine distante dans lequel CMake génère les scripts de génération pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteInstallRoot` : spécifie le répertoire de la machine distante dans lequel CMake génère les cibles d’installation pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` et `${env.VARIABLE}` où `VARIABLE` est une variable d’environnement définie au niveau du système, de l’utilisateur ou de la session.
- `remoteCopySources`: `boolean` qui spécifie si Visual Studio doit copier les fichiers sources sur la machine distante. La valeur par défaut est true. Affectez la valeur false si vous gérez vous-même la synchronisation des fichiers.
- `remoteCopyBuildOutput`: `boolean` qui spécifie si les sorties de build du système distant doivent être copiées.
- `rsyncCommandArgs` : spécifie un ensemble d’options de ligne de commande supplémentaires passées à rsync.
- `remoteCopySourcesExclusionList`: `array` qui spécifie la liste des chemins à exclure lors de la copie des fichiers sources (un chemin peut être le nom d’un fichier/répertoire ou un chemin relatif de la racine de la copie). Les caractères génériques \\\"*\\\" et \\\"?\\\" peuvent être utilisés à des fins de correspondance à des modèles Glob.
- `cmakeExecutable` : spécifie le chemin complet de l’exécutable du programme CMake, avec le nom de fichier et l’extension.
- `remotePreGenerateCommand` : spécifie la commande à exécuter avant d’exécuter CMake pour analyser le fichier CMakeLists.txt.
- `remotePrebuildCommand` : spécifie la commande à exécuter sur la machine distante avant la génération.
- `remotePostbuildCommand` : spécifie la commande à exécuter sur la machine distante après la génération.
- `variables`: contient une paire nom-valeur de variables CMake qui sera transmis en tant que **-D** *_nom_=_valeur_* à CMake. Si vos instructions de génération de projet CMake spécifient l’ajout des variables directement dans le fichier de cache CMake, nous vous recommandons de les ajouter ici à la place. L’exemple suivant indique comment spécifier les paires nom-valeur pour l’ensemble d’outils MSVC 14.14.26428 :

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

## <a name="environment-variables"></a>Variables d’environnement

`CMakeSettings.json` Il prend également en charge beaucoup de variables d’environnement dans un de ses propriétés mentionnées ci-dessus. La syntaxe à utiliser est `${env.FOO}` pour développer la variable d’environnement %FOO%.

Vous avez également accès aux macros intégrées dans ce fichier :

- `${workspaceRoot}` : Fournit le chemin complet du dossier de l’espace de travail
- `${workspaceHash}` : Hachage de l’emplacement de l’espace de travail. Utile pour créer un identificateur unique pour l’espace de travail actuel (par exemple, à utiliser dans les chemins de dossier)
- `${projectFile}` : Chemin complet du fichier racine CMakeLists.txt
- `${projectDir}` : Chemin complet du dossier du fichier racine CMakeLists.txt
- `${thisFile}` : Chemin complet du fichier `CMakeSettings.json`
- `${name}` : Nom de la configuration
- `${generator}` : Nom du générateur CMake utilisé dans cette configuration


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

## <a name="ninja"></a> Arguments de ligne de commande Ninja

Si les cibles ne sont pas spécifiés, génère la cible de 'default'.

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




