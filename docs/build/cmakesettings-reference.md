---
title: Informations de référence sur le schéma CMakeSettings.json
ms.date: 11/22/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: f9c864b66df86165090b7d6d6fc9c4fc51d65a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328895"
---
# <a name="cmakesettingsjson-schema-reference"></a>Informations de référence sur le schéma CMakeSettings.json

::: moniker range="vs-2015"

Les projets CMake sont soutenus dans Visual Studio 2017 et plus tard.

::: moniker-end

::: moniker range=">=vs-2017"

Le fichier **CMakeSettings.json** contient des informations que Visual Studio utilise pour IntelliSense et pour construire les arguments de la ligne de commande qu’il passe à cmake.exe pour une *configuration* spécifiée et *l’environnement*compilateur . Une configuration spécifie les propriétés qui s’appliquent à une plate-forme spécifique et de type build, par exemple, `x86-Debug` ou `Linux-Release`. Chaque configuration spécifie un environnement qui encapsule des informations sur l’ensemble d’outils compilateur, par exemple MSVC, GCC ou Clang. CMake utilise les arguments de la ligne de commande pour régénérer le fichier *CMakeCache.txt* racine et d’autres fichiers de projet pour le projet. Les valeurs peuvent être remplacées dans les fichiers *CMakeLists.txt.*

Vous pouvez ajouter ou supprimer des configurations dans l’IDE, puis les modifier directement dans le fichier JSON ou utiliser **l’éditeur CMake Settings** (Visual Studio 2019 et plus tard). Vous pouvez basculer facilement entre les configurations dans l’IDE pour générer les différents fichiers de projet. Voir [personnaliser les paramètres de construction CMake dans Visual Studio](customize-cmake-settings.md) pour plus d’informations.

## <a name="configurations"></a>Configurations

Le `configurations` tableau contient toutes les configurations d’un projet CMake. Voir [la référence de configuration prédéfinie CMake](cmake-predefined-configuration-reference.md) pour plus d’informations sur les configurations prédéfinies. Vous pouvez ajouter n’importe quel nombre de configurations prédéfinises ou personnalisées au fichier.

Une `configuration` a les propriétés suivantes :

- `addressSanitizerEnabled`: `true` si le programme compile avec Address Sanitizer (Expérimental sur Windows). Sur Linux, compilez avec -fno-omit-frame-pointer et compiler niveau d’optimisation -Os ou -Oo pour les meilleurs résultats.
- `addressSanitizerRuntimeFlags`: drapeaux en temps d’exécution passés à AddressSanitizer via la variable ASAN_OPTIONS environnement. Format: drapeau1-valeur: flag2-value2.
- `buildCommandArgs` : spécifie des commutateurs de build natifs passés à CMake après --build --. Par exemple, si vous passez -v quand vous utilisez le générateur Ninja, cela oblige Ninja à sortir des lignes de commande. Consultez [Arguments de ligne de commande Ninja](#ninja) pour plus d’informations sur les commandes Ninja.
- `buildRoot` : spécifie le répertoire dans lequel CMake génère les scripts de génération pour le générateur choisi.  Cartes à **-DCMAKE_BINARY_DIR** commutateur et spécifie où *CMakeCache.txt* sera créé. Si le dossier n’existe pas, il est créé. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `cacheGenerationCommand`: spécifie un outil et des arguments de ligne de commande, par exemple *gencache.bat debug* pour générer le cache. La commande est exécutée à partir de la coque dans l’environnement spécifié pour la configuration lorsque l’utilisateur demande explicitement la régénération, ou un fichier CMakeLists.txt ou CMakeSettings.json est modifié.
- `cacheRoot` : spécifie le chemin d’un cache CMake. Cet annuaire doit contenir un fichier *CMakeCache.txt* existant.
- `clangTidyChecks`: liste d’avertissements séparés par les virgules qui seront transmises à clang-tidy; wildcards sont autorisés et «-» préfixe supprimera les contrôles.
- `cmakeCommandArgs`: spécifie d’autres options de ligne de commande transmises à CMake lorsqu’elles sont invoquées pour générer les fichiers du projet.
- `cmakeToolchain` : spécifie le fichier de chaîne d’outils. Celui-ci est passé à CMake à l’aide de -DCMAKE_TOOLCHAIN_FILE.
- `codeAnalysisRuleset` : spécifie l’ensemble de règles à utiliser lors de l’exécution de l’analyse du code. Il peut s’agir d’un chemin complet ou du nom d’un fichier d’ensemble de règles installé par Visual Studio.
- `configurationType` : spécifie la configuration du type de build pour le générateur sélectionné. Possibilités :

  - Débogage
  - Libérer
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs` : spécifie des options de ligne de commande supplémentaires passées à CTest pendant l’exécution des tests.
- `description` : description de cette configuration qui apparaît dans les menus.
- `enableClangTidyCodeAnalysis`: utilisez Clang-Tidy pour l’analyse de code.
- `enableMicrosoftCodeAnalysis`: utilisez des outils d’analyse de code Microsoft pour l’analyse de code.
- `generator` : spécifie le générateur CMake à utiliser pour cette configuration. Possibilités :
  
  **Visual Studio 2019 uniquement :**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 et plus tard:**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix Makefiles
  - Ninja

Comme Ninja est conçu pour des vitesses de génération rapides plutôt que pour la flexibilité et la fonctionnalité, il est défini par défaut. Toutefois, certains projets CMake peuvent ne pas pouvoir être générés correctement avec Ninja. Si cela se produit, vous pouvez demander à CMake de générer des projets Visual Studio à la place.

Pour spécifier un générateur Visual Studio dans Visual Studio 2017, ouvrez le menu principal en choisissant **CMake Modifier les paramètres CMake**. Supprimer "Ninja" et tapez "V". Cela active IntelliSense, qui vous permet de choisir le générateur souhaité.

Pour spécifier un générateur De studio visuel dans Visual Studio 2019, cliquez à droite sur le fichier *CMakeLists.txt* dans **Solution Explorer** et choisissez **CMake Settings pour le projet** > **Show Advanced Settings** > **CMake Generator**.

Quand la configuration active spécifie un générateur Visual Studio, MSBuild.exe est appelé par défaut avec des arguments `-m -v:minimal`. Pour personnaliser la construction, à l’intérieur du fichier *CMakeSettings.json,* vous pouvez spécifier d’autres [arguments de ligne de commande MSBuild](../build/reference/msbuild-visual-cpp-overview.md) à transmettre au système de construction via la `buildCommandArgs` propriété :

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `installRoot` : spécifie le répertoire dans lequel CMake génère les cibles d’installation pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `inheritEnvironments` : spécifie un ou plusieurs environnements de compilation dont dépend cette configuration. Il peut s’agir de tout environnement personnalisé ou de l’un des environnements prédéfinis. Pour plus d’informations, consultez [Environnements](#environments).
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

- `name` : nomme la configuration.  Voir [la référence de configuration prédéfinie CMake](cmake-predefined-configuration-reference.md) pour plus d’informations sur les configurations prédéfinies.
- `wslPath`: le chemin vers le lanceur d’une instance de Windows Subsystem pour Linux.

### <a name="additional-settings-for-cmake-linux-projects"></a>Paramètres supplémentaires pour les projets CMake Linux

- `remoteMachineName` : spécifie le nom de la machine Linux distante qui héberge CMake, les builds et le débogueur. Utilisez le gestionnaire de connexions pour l’ajout de nouvelles machines Linux. Les macros prises en charge incluent `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity` : spécifie le niveau de détail de l’opération de copie de la source vers la machine distante. Valeurs possibles : « Normal », « Détaillé » ou « Diagnostic ».
- `remoteCopySourcesConcurrentCopies`: précise le nombre de copies simultanées utilisées lors de la synchronisation des sources à la machine à distance (sftp seulement).
- `remoteCopySourcesMethod` : spécifie la méthode de copie des fichiers sur la machine distante. Valeurs possibles : « rsync » ou « sftp ».
- `remoteCMakeListsRoot` : spécifie le répertoire de la machine distante qui contient le projet CMake. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteBuildRoot` : spécifie le répertoire de la machine distante dans lequel CMake génère les scripts de génération pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteInstallRoot` : spécifie le répertoire de la machine distante dans lequel CMake génère les cibles d’installation pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` et `${env.VARIABLE}` où `VARIABLE` est une variable d’environnement définie au niveau du système, de l’utilisateur ou de la session.
- `remoteCopySources`: `boolean` Un qui précise si Visual Studio doit copier des fichiers sources à la machine à distance. La valeur par défaut est true. Affectez la valeur false si vous gérez vous-même la synchronisation des fichiers.
- `remoteCopyBuildOutput`: `boolean` Un qui précise s’il faut copier les sorties de construction à partir du système distant.
- `remoteCopyAdditionalIncludeDirectories`: D’autres répertoires à copier à partir de la machine à distance pour soutenir IntelliSense. Format comme "/path1;/path2...".
- `remoteCopyExcludeDirectories`: Inclure des répertoires pas à copier à partir de la machine à distance. Format comme "/path1;/path2...".
- `remoteCopyUseCompilerDefaults`: Précise s’il faut utiliser la définition par défaut du compilateur et inclure des chemins pour IntelliSense. Ne devrait être faux que si les compilateurs utilisés pour ne pas soutenir les arguments de style gcc.
- `rsyncCommandArgs` : spécifie un ensemble d’options de ligne de commande supplémentaires passées à rsync.
- `remoteCopySourcesExclusionList`: `array` Une liste de chemins à exclure lors de la copie des fichiers sources : un chemin peut être le nom d’un fichier/annuaire, ou un chemin par rapport à la racine de la copie. Les caractères génériques \\\"*\\\" et \\\"?\\\" peuvent être utilisés à des fins de correspondance à des modèles Glob.
- `cmakeExecutable` : spécifie le chemin complet de l’exécutable du programme CMake, avec le nom de fichier et l’extension.
- `remotePreGenerateCommand`: spécifie la commande de courir avant d’exécuter CMake pour analyser le fichier *CMakeLists.txt.*
- `remotePrebuildCommand` : spécifie la commande à exécuter sur la machine distante avant la génération.
- `remotePostbuildCommand` : spécifie la commande à exécuter sur la machine distante après la génération.
- `variables` : contient une paire nom-valeur de variables CMake qui sont passées sous la forme **-D** *_nom_=_valeur_* à CMake. Si vos instructions de construction de projet CMake spécifient l’ajout de toutes variables directement au fichier *CMakeCache.txt,* il est recommandé de les ajouter ici à la place. L’exemple suivant indique comment spécifier les paires nom-valeur pour l’ensemble d’outils MSVC 14.14.26428 :

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

Notez que si vous `"type"`ne `"STRING"` définissez pas le , le type sera supposé par défaut.

- `remoteCopyOptimizations`: **Visual Studio 2019 version 16.5 ou plus tard** propriétés pour contrôler la copie source à la cible distante. Les optimisations sont activées par défaut. Inclut `remoteCopyUseOptimizations`, `rsyncSingleDirectoryCommandArgs` et `remoteCopySourcesMaxSmallChange`.

## <a name="environments"></a><a name="environments"></a>Environnements

Un *environnement* résume les variables de l’environnement qui sont définies dans le processus que Visual Studio utilise pour invoquer cmake.exe. Pour les projets MSVC, les variables sont celles qui sont définies dans une [invite de commande de développeur](building-on-the-command-line.md) pour une plate-forme spécifique. Par exemple, `msvc_x64_x64` l’environnement est le même que l’exécution **de l’invite de commande de développeur pour VS 2017** ou **Developer Command Prompt pour VS 2019** avec les arguments **-arch-amd64 -host_arch-amd64.** Vous pouvez `env.{<variable_name>}` utiliser la syntaxe dans *CMakeSettings.json* pour référencer les variables individuelles de l’environnement, par exemple pour construire des chemins vers les dossiers.  Les environnements prédéfinis suivants sont fournis :

- linux_arm: Cible ARM Linux à distance.
- linux_x64: Cible x64 Linux à distance.
- linux_x86: Cible x86 Linux à distance.
- msvc_arm: Ciblez ARM Windows avec le compilateur MSVC.
- msvc_arm_x64: Ciblez ARM Windows avec le compilateur MSVC 64 bits.
- msvc_arm64: Cible ARM64 Windows avec le compilateur MSVC.
- msvc_arm64_x64: Cible ARM64 Windows avec le compilateur MSVC 64 bits.
- msvc_x64: Cible x64 Windows avec le compilateur MSVC.
- msvc_x64_x64: Cible x64 Windows avec le compilateur MSVC 64 bits.
- msvc_x86: Ciblez x86 Windows avec le compilateur MSVC.
- msvc_x86_x64: Cible x86 Windows avec le compilateur MSVC 64 bits.

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>Accès aux variables de l’environnement de CMakeLists.txt

À partir d’un fichier CMakeLists.txt, toutes `$ENV{variable_name}`les variables de l’environnement sont référencées par la syntaxe . Pour voir les variables disponibles pour un environnement, ouvrez l’invite de commande correspondante et tapez `SET`. Certaines des informations contenues dans les variables de l’environnement sont également disponibles par le biais de variables d’introspection du système CMake, mais vous trouverez peut-être plus pratique d’utiliser la variable de l’environnement. Par exemple, la version compilateur MSVC ou la version Windows SDK sont facilement récupérées grâce aux variables de l’environnement.

### <a name="custom-environment-variables"></a>Variables d’environnement personnalisées

Dans `CMakeSettings.json`, vous pouvez définir des variables d’environnement personnalisées globalement ou par configuration dans le `environments` tableau. Un environnement personnalisé est un moyen pratique de regrouper un ensemble de propriétés que vous pouvez utiliser à la place d’un environnement prédéfini, ou d’étendre ou de modifier un environnement prédéfini. Chaque élément dans le tableau `environments` comprend ce qui suit :

- `namespace` : nomme l’environnement afin que ses variables puissent être référencées à partir d’une configuration sous la forme `namespace.variable`. L’objet de `env` l’environnement par défaut est `%USERPROFILE%`appelé et est peuplé de certaines variables de l’environnement du système, y compris .
- `environment` : identifie de façon unique ce groupe de variables. Permet au groupe d’être hérité plus tard dans une entrée `inheritEnvironments`.
- `groupPriority`: Un intégrant qui spécifie la priorité de ces variables lors de leur évaluation. Les éléments dont la valeur est élevée sont évalués en premier.
- `inheritEnvironments`: Un éventail de valeurs qui spécifient l’ensemble d’environnements hérités par ce groupe. Cette fonctionnalité vous permet d’hériter les environnements par défaut et de créer des variables d’environnement personnalisées qui sont passées à CMake.exe quand il s’exécute.

**Visual Studio 2019 version 16.4 et plus tard:** Les cibles Debug sont automatiquement lancées avec l’environnement que vous spécifiez dans *CMakeSettings.json*. Vous pouvez remplacer ou ajouter des variables de l’environnement sur une base par cible ou par tâche dans [launch.vs.json](launch-vs-schema-reference-cpp.md) et [tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

L’exemple suivant définit une variable globale, **BuildDir**, qui est héritée dans les configurations x86-Debug et de x64-Debug. Chaque configuration utilise la variable pour spécifier la valeur de la propriété **buildRoot** pour cette configuration. Notez également la façon dont chaque configuration utilise la propriété **inheritEnvironments** pour spécifier une variable qui s’applique uniquement à cette configuration.

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
      // Since this configuration doesn't modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="macros"></a>Macros

Les macros suivantes peuvent être utilisées dans *CMakeSettings.json*:

- `${workspaceRoot}`- le chemin complet du dossier d’espace de travail
- `${workspaceHash}` : Hachage de l’emplacement de l’espace de travail. Utile pour créer un identificateur unique pour l’espace de travail actuel (par exemple, à utiliser dans les chemins de dossier)
- `${projectFile}` : Chemin complet du fichier racine CMakeLists.txt
- `${projectDir}` : Chemin complet du dossier du fichier racine CMakeLists.txt
- `${thisFile}` : Chemin complet du fichier `CMakeSettings.json`
- `${name}` : Nom de la configuration
- `${generator}` : Nom du générateur CMake utilisé dans cette configuration

Toutes les références aux macros et aux variables de l’environnement dans *CMakeSettings.json* sont étendues avant d’être transmises à la ligne de commandement cmake.exe.

## <a name="ninja-command-line-arguments"></a><a name="ninja"></a> Arguments de ligne de commande Ninja

Si les cibles ne sont pas spécifiées, génère la cible « par défaut ».

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
|   -t TOOL  | exécute un sous-outil (utilisez -t list pour obtenir la liste des sous-outils). met fin aux options de niveau supérieur. Les autres indicateurs sont transmis à l’outil|
|   -w FLAG  | ajuste les avertissements (utiliser -w list pour obtenir la liste des avertissements)|

::: moniker-end
