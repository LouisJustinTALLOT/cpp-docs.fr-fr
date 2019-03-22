---
title: Informations de référence sur le schéma CMakeSettings.json
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 893bc5c8efe3fdae80a4a0de8204d391baa63d07
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356112"
---
# <a name="cmakesettingsjson-schema-reference"></a>Informations de référence sur le schéma CMakeSettings.json

Le **cmakesettings.json**' fichier contient des informations qui spécifient comment Visual Studio doit interagir avec CMake pour générer un projet pour une plateforme spécifiée. Utilisez ce fichier pour stocker des informations comme des variables d’environnement ou des arguments pour l’environnement cmake.exe.

## <a name="environments"></a>Environnements

Le tableau `environments` contient la liste des `items` de type `object` qui définissent un « environnement ». Un environnement peut être utilisé pour appliquer un ensemble de variables à une `configuration`. Chaque élément dans le tableau `environments` comprend ce qui suit :

- `namespace` : nomme l’environnement afin que ses variables puissent être référencées à partir d’une configuration sous la forme `namespace.variable`. L’objet environnement par défaut est appelé `env` et il est rempli avec certaines variables d’environnement système, notamment `%USERPROFILE%`.
- `environment` : identifie de façon unique ce groupe de variables. Permet au groupe d’être hérité plus tard dans une entrée `inheritEnvironments`.
- `groupPriority`: entier qui spécifie la priorité de ces variables lors de leur évaluation. Les éléments dont la valeur est élevée sont évalués en premier.
- `inheritEnvironments`: tableau de valeurs qui spécifient l’ensemble des environnements hérités par ce groupe. Vous pouvez utiliser tout environnement personnalisé ou ces environnements prédéfinis :
 
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

- `configurationType` : spécifie la configuration du type de build pour le générateur sélectionné. Possibilités :
 
  - Débogage
  - Édition
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments` : spécifie un ou plusieurs environnements dont dépend cette configuration. Il peut s’agir de tout environnement personnalisé ou de l’un des environnements prédéfinis.
- `buildRoot` : spécifie le répertoire dans lequel CMake génère les scripts de génération pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `installRoot` : spécifie le répertoire dans lequel CMake génère les cibles d’installation pour le générateur choisi. Les macros prises en charge incluent `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `cmakeCommandArgs` : spécifie des options de ligne de commande supplémentaires passées à CMake quand celui-ci est appelé pour générer le cache.
- `cmakeToolchain` : spécifie le fichier de chaîne d’outils. Celui-ci est passé à CMake à l’aide de -DCMAKE_TOOLCHAIN_FILE.
- `buildCommandArgs` : spécifie des commutateurs de build natifs passés à CMake après --build --.
- `ctestCommandArgs` : spécifie des options de ligne de commande supplémentaires passées à CTest pendant l’exécution des tests.
- `codeAnalysisRuleset` : spécifie l’ensemble de règles à utiliser lors de l’exécution de l’analyse du code. Il peut s’agir d’un chemin complet ou du nom d’un fichier d’ensemble de règles installé par Visual Studio.
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
- `variables`: `array` qui spécifie les variables passées à CMake sous la forme -Dname1=value1 -Dname2=value2, et ainsi de suite. 


