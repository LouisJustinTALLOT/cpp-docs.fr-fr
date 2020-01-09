---
title: Informations de référence sur le schéma CMakeSettings.json
ms.date: 11/22/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 08ecb5bc55ead207d6e4a0029a21e737d447143b
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556732"
---
# <a name="cmakesettingsjson-schema-reference"></a>Informations de référence sur le schéma CMakeSettings.json

::: moniker range="vs-2015"

Les projets CMake sont pris en charge dans Visual Studio 2017 et versions ultérieures.

::: moniker-end

::: moniker range=">=vs-2017"

Le fichier **CMakeSettings. JSON** contient des informations que Visual Studio utilise pour IntelliSense et pour construire les arguments de ligne de commande qu’il transmet à cmake. exe pour un *environnement*de *configuration* et de compilateur spécifié. Une configuration spécifie les propriétés qui s’appliquent à une plateforme et à un type de build spécifiques, par exemple, `x86-Debug` ou `Linux-Release`. Chaque configuration spécifie un environnement, qui encapsule des informations sur l’ensemble d’outils du compilateur, par exemple MSVC, GCC ou Clang. CMake utilise les arguments de ligne de commande pour régénérer le fichier *CMakeCache. txt* racine et d’autres fichiers de projet pour le projet. Les valeurs peuvent être remplacées dans les fichiers *fichier CMakeLists. txt* . 

Vous pouvez ajouter ou supprimer des configurations dans l’IDE, puis les modifier directement dans le fichier JSON ou utiliser l' **éditeur de paramètres cmake** (Visual Studio 2019 et versions ultérieures). Vous pouvez facilement basculer entre les configurations dans l’IDE pour générer les différents fichiers projet. Pour plus d’informations, consultez [personnaliser les paramètres de build cmake dans Visual Studio](customize-cmake-settings.md) .

## <a name="configurations"></a>Configurations

Le tableau `configurations` contient toutes les configurations d’un projet CMake. Pour plus d’informations sur les configurations prédéfinies, consultez [référence de configuration](cmake-predefined-configuration-reference.md) prédéfinie cmake. Vous pouvez ajouter n’importe quel nombre de configurations prédéfinies ou personnalisées au fichier. 

Une `configuration` a les propriétés suivantes :

- `addressSDanitizerEnabled`: si `true` compile le programme avec l’adresse de nettoyage (expérimental sur Windows). Sur Linux, compilez avec-FNO-omit-frame-pointer et le niveau d’optimisation du compilateur-OS ou-oo pour obtenir de meilleurs résultats.
- `addressSanitizerRuntimeFlags`: indicateurs d’exécution passés à AddressSanitizer via la variable d’environnement ASAN_OPTIONS. Format : Indicateur1 = valeur : Indicateur2 = value2.
- `buildCommandArgs` : spécifie des commutateurs de build natifs passés à CMake après --build --. Par exemple, si vous passez -v quand vous utilisez le générateur Ninja, cela oblige Ninja à sortir des lignes de commande. Consultez [Arguments de ligne de commande Ninja](#ninja) pour plus d’informations sur les commandes Ninja.
- `buildRoot` : spécifie le répertoire dans lequel CMake génère les scripts de génération pour le générateur choisi.  Mappe sur **le commutateur-DCMAKE_BINARY_DIR** et spécifie où *CMakeCache. txt* sera créé. Si le dossier n’existe pas, il est créé. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `cacheGenerationCommand`: spécifie un outil en ligne de commande et des arguments, par exemple *gencache. bat Debug* pour générer le cache. La commande est exécutée à partir de l’interpréteur de commandes dans l’environnement spécifié pour la configuration lorsque l’utilisateur demande explicitement la régénération, ou un fichier fichier CMakeLists. txt ou CMakeSettings. JSON est modifié.
- `cacheRoot` : spécifie le chemin d’un cache CMake. Ce répertoire doit contenir un fichier *CMakeCache. txt* existant.
- `clangTidyChecks`: liste séparée par des virgules des avertissements qui seront passés à Clang-Tidy ; les caractères génériques sont autorisés et le préfixe « - » supprime les vérifications.
- `cmakeCommandArgs`: spécifie des options de ligne de commande supplémentaires passées à CMake lorsqu’il est appelé pour générer les fichiers projet.
- `cmakeToolchain` : spécifie le fichier de chaîne d’outils. Celui-ci est passé à CMake à l’aide de -DCMAKE_TOOLCHAIN_FILE.
- `codeAnalysisRuleset` : spécifie l’ensemble de règles à utiliser lors de l’exécution de l’analyse du code. Il peut s’agir d’un chemin complet ou du nom d’un fichier d’ensemble de règles installé par Visual Studio.
- `configurationType` : spécifie la configuration du type de build pour le générateur sélectionné. Possibilités :

  - Déboguer
  - Release
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs` : spécifie des options de ligne de commande supplémentaires passées à CTest pendant l’exécution des tests.
- `description` : description de cette configuration qui apparaît dans les menus.
- `enableClangTidyCodeAnalysis`: utilisez Clang-tidy pour l’analyse du code.
- `enableMicrosoftCodeAnalysis`: utilisez les outils d’analyse du code Microsoft pour l’analyse du code.
- `generator` : spécifie le générateur CMake à utiliser pour cette configuration. Possibilités :
  
  **Visual Studio 2019 uniquement :**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 et ultérieur :**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix Makefiles
  - Ninja

Comme Ninja est conçu pour des vitesses de génération rapides plutôt que pour la flexibilité et la fonctionnalité, il est défini par défaut. Toutefois, certains projets CMake peuvent ne pas pouvoir être générés correctement avec Ninja. Si cela se produit, vous pouvez demander à CMake de générer des projets Visual Studio à la place.

Pour spécifier un générateur Visual Studio dans Visual Studio 2017, ouvrez le à partir du menu principal en choisissant **cmake | Modifiez les paramètres de CMake**. Supprimez « Ninja » et tapez « V ». Cela active IntelliSense, qui vous permet de choisir le générateur souhaité.

Pour spécifier un générateur Visual Studio dans Visual Studio 2019, cliquez avec le bouton droit sur le fichier *fichier CMakeLists. txt* dans **Explorateur de solutions** et choisissez **paramètres cmake pour le projet** > **afficher les paramètres avancés** > **Générateur cmake**.

Quand la configuration active spécifie un générateur Visual Studio, MSBuild.exe est appelé par défaut avec des arguments `-m -v:minimal`. Pour personnaliser la build, à l’intérieur du fichier *CMakeSettings. JSON* , vous pouvez spécifier des [arguments de ligne de commande MSBuild](../build/reference/msbuild-visual-cpp-overview.md) supplémentaires à passer au système de génération via la propriété `buildCommandArgs` :

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

- `name` : nomme la configuration.  Pour plus d’informations sur les configurations prédéfinies, consultez [référence de configuration](cmake-predefined-configuration-reference.md) prédéfinie cmake.
- `wslPath`: chemin d’accès au lanceur d’une instance du sous-système Windows pour Linux.

### <a name="additional-settings-for-cmake-linux-projects"></a>Paramètres supplémentaires pour les projets CMake Linux

- `remoteMachineName` : spécifie le nom de la machine Linux distante qui héberge CMake, les builds et le débogueur. Utilisez le gestionnaire de connexions pour l’ajout de nouvelles machines Linux. Les macros prises en charge incluent `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity` : spécifie le niveau de détail de l’opération de copie de la source vers la machine distante. Valeurs possibles : « Normal », « Détaillé » ou « Diagnostic ».
- `remoteCopySourcesConcurrentCopies`: spécifie le nombre de copies simultanées utilisées durant la synchronisation des sources avec l’ordinateur distant (SFTP uniquement).
- `remoteCopySourcesMethod` : spécifie la méthode de copie des fichiers sur la machine distante. Valeurs possibles : « rsync » ou « sftp ».
- `remoteCMakeListsRoot` : spécifie le répertoire de la machine distante qui contient le projet CMake. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteBuildRoot` : spécifie le répertoire de la machine distante dans lequel CMake génère les scripts de génération pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteInstallRoot` : spécifie le répertoire de la machine distante dans lequel CMake génère les cibles d’installation pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` et `${env.VARIABLE}` où `VARIABLE` est une variable d’environnement définie au niveau du système, de l’utilisateur ou de la session.
- `remoteCopySources`: `boolean` qui spécifie si Visual Studio doit copier les fichiers sources sur l’ordinateur distant. La valeur par défaut est true. Affectez la valeur false si vous gérez vous-même la synchronisation des fichiers.
- `remoteCopyBuildOutput`: `boolean` qui spécifie s’il faut copier les sorties de génération à partir du système distant.
- `remoteCopyAdditionalIncludeDirectories`: autres répertoires Include à copier à partir de la machine distante pour prendre en charge IntelliSense. Format « /path1 ;/path2... ».
- `remoteCopyExcludeDirectories`: inclure les répertoires à copier à partir de la machine distante. Format « /path1 ;/path2... ».
- `remoteCopyUseCompilerDefaults`: spécifie s’il faut utiliser les paramètres par défaut du compilateur et les chemins d’accès include pour IntelliSense. Doit uniquement avoir la valeur false si les compilateurs utilisés pour ne prennent pas en charge les arguments de style GCC.
- `rsyncCommandArgs` : spécifie un ensemble d’options de ligne de commande supplémentaires passées à rsync.
- `remoteCopySourcesExclusionList`: `array` qui spécifie une liste de chemins d’accès à exclure lors de la copie des fichiers sources : un chemin d’accès peut être le nom d’un fichier/répertoire, ou un chemin d’accès relatif à la racine de la copie. Les caractères génériques \\\"*\\\" et \\\"?\\\" peuvent être utilisés à des fins de correspondance à des modèles Glob.
- `cmakeExecutable` : spécifie le chemin complet de l’exécutable du programme CMake, avec le nom de fichier et l’extension.
- `remotePreGenerateCommand`: spécifie la commande à exécuter avant d’exécuter CMake pour analyser le fichier *fichier CMakeLists. txt* .
- `remotePrebuildCommand` : spécifie la commande à exécuter sur la machine distante avant la génération.
- `remotePostbuildCommand` : spécifie la commande à exécuter sur la machine distante après la génération.
- `variables`: contient une paire nom-valeur de variables cmake qui seront **passées sous la** forme d’une  *_valeur_ de _nom_=* à cmake. Si les instructions de génération de votre projet CMake spécifient l’ajout de toutes les variables directement au fichier *CMakeCache. txt* , nous vous recommandons de les ajouter ici à la place. L’exemple suivant indique comment spécifier les paires nom-valeur pour l’ensemble d’outils MSVC 14.14.26428 :

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

Notez que si vous ne définissez pas le `"type"`, le type de `"STRING"` est supposé par défaut.

## <a name="environments"></a>Environnements

Un *environnement* encapsule les variables d’environnement qui sont définies dans le processus que Visual Studio utilise pour appeler cmake. exe. Pour les projets MSVC, les variables sont celles qui sont définies dans une [invite de commandes développeur](building-on-the-command-line.md) pour une plateforme spécifique. Par exemple, l’environnement `msvc_x64_x64` est le même que l’exécution de la **invite de commandes développeur pour vs 2017** ou **Invite de commandes développeur pour vs 2019** avec les arguments **-ARCH = amd64-host_arch = amd64** . Vous pouvez utiliser la syntaxe `env.{<variable_name>}` dans *CMakeSettings. JSON* pour référencer les variables d’environnement individuelles, par exemple pour construire des chemins d’accès aux dossiers.  Les environnements prédéfinis suivants sont fournis :

- linux_arm : ciblez Linux ARM à distance.
- linux_x64 : ciblez Linux x64 à distance.
- linux_x86 : ciblez Linux x86 à distance.
- msvc_arm : ciblez les fenêtres ARM avec le compilateur MSVC.
- msvc_arm_x64 : ciblez les fenêtres ARM avec le compilateur MSVC bits 64.
- msvc_arm64 : ciblez Windows ARM64 avec le compilateur MSVC.
- msvc_arm64_x64 : ciblez Windows ARM64 avec le compilateur MSVC 64 bits.
- msvc_x64 : ciblez Windows x64 avec le compilateur MSVC.
- msvc_x64_x64 : ciblez Windows x64 avec le compilateur MSVC 64 bits.
- msvc_x86 : ciblez Windows x86 avec le compilateur MSVC.
- msvc_x86_x64 : ciblez Windows x86 avec le compilateur MSVC bits 64.

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>Accès aux variables d’environnement à partir de fichier CMakeLists. txt

À partir d’un fichier fichier CMakeLists. txt, toutes les variables d’environnement sont référencées par la syntaxe `$ENV{variable_name}`. Pour afficher les variables disponibles pour un environnement, ouvrez l’invite de commandes correspondante et tapez `SET`. Certaines des informations contenues dans les variables d’environnement sont également disponibles par le biais des variables système CMake, mais il peut s’avérer plus pratique d’utiliser la variable d’environnement. Par exemple, la version du compilateur MSVC ou la version de SDK Windows sont facilement récupérées via les variables d’environnement.

### <a name="custom-environment-variables"></a>Variables d’environnement personnalisées

Dans `CMakeSettings.json`, vous pouvez définir des variables d’environnement personnalisées globalement ou par configuration dans le tableau `environments`. Un environnement personnalisé est un moyen pratique de regrouper un ensemble de propriétés que vous pouvez utiliser à la place d’un environnement prédéfini, ou d’étendre ou de modifier un environnement prédéfini. Chaque élément dans le tableau `environments` comprend ce qui suit :

- `namespace` : nomme l’environnement afin que ses variables puissent être référencées à partir d’une configuration sous la forme `namespace.variable`. L’objet d’environnement par défaut est appelé `env` et est rempli avec certaines variables d’environnement système, y compris `%USERPROFILE%`.
- `environment` : identifie de façon unique ce groupe de variables. Permet au groupe d’être hérité plus tard dans une entrée `inheritEnvironments`.
- `groupPriority`: entier qui spécifie la priorité de ces variables lors de leur évaluation. Les éléments dont la valeur est élevée sont évalués en premier.
- `inheritEnvironments`: tableau de valeurs qui spécifient le jeu d’environnements hérités par ce groupe. Cette fonctionnalité vous permet d’hériter les environnements par défaut et de créer des variables d’environnement personnalisées qui sont passées à CMake.exe quand il s’exécute. 

**Visual Studio 2019 version 16,4 et versions ultérieures :** Les cibles de débogage sont automatiquement lancées avec l’environnement que vous spécifiez dans *CMakeSettings. JSON*. Vous pouvez remplacer ou ajouter des variables d’environnement par cible ou par tâche dans [Launch. vs. JSON](launch-vs-schema-reference-cpp.md) et [Tasks. vs. JSON](tasks-vs-json-schema-reference-cpp.md).

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

Les macros suivantes peuvent être utilisées dans *CMakeSettings. JSON*:

- `${workspaceRoot}` : chemin d’accès complet du dossier de l’espace de travail.
- `${workspaceHash}` : Hachage de l’emplacement de l’espace de travail. Utile pour créer un identificateur unique pour l’espace de travail actuel (par exemple, à utiliser dans les chemins de dossier)
- `${projectFile}` : Chemin complet du fichier racine CMakeLists.txt
- `${projectDir}` : Chemin complet du dossier du fichier racine CMakeLists.txt
- `${thisFile}` : Chemin complet du fichier `CMakeSettings.json`
- `${name}` : Nom de la configuration
- `${generator}` : Nom du générateur CMake utilisé dans cette configuration

Toutes les références aux macros et aux variables d’environnement dans *CMakeSettings. JSON* sont développées avant d’être passées à la ligne de commande cmake. exe.

## <a name="ninja"></a> Arguments de ligne de commande Ninja

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
