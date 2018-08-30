---
title: Projets Ouvrir un dossier dans Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 06/01/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4444e70ec158d7afa35c3955bbef9af4bfa12f2
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131321"
---
# <a name="open-folder-projects-in-visual-c"></a>Projets Ouvrir un dossier dans Visual C++

Dans Visual Studio 2017 et ultérieur, la fonctionnalité « Ouvrir un dossier » vous permet d’ouvrir un dossier de fichiers sources et de commencer immédiatement à coder en bénéficiant des avantages suivants : IntelliSense, navigation, refactorisation, débogage, etc. Aucun fichier .sln ou .vcxproj n’est chargé. Si nécessaire, vous pouvez spécifier des tâches personnalisées ou générer et lancer des paramètres par le biais de fichiers .json simples. Grâce à la technologie Ouvrir un dossier, Visual C++ prend non seulement en charge des collections souples de fichiers, mais aussi la quasi-totalité des systèmes de génération : CMake, Ninja, QMake (pour les projets de Qt), gyp, SCons, Gradle, Buck, make, etc. 

Pour utiliser Ouvrir un dossier, sélectionnez *Fichier | Ouvrir | Dossier* à partir du menu principal ou appuyez sur *Ctrl + Maj + Alt + O*. L’Explorateur de solutions affiche immédiatement tous les fichiers dans le dossier. Vous pouvez cliquer sur n’importe quel fichier pour le modifier. En arrière-plan, Visual Studio démarre l’indexation des fichiers pour activer les fonctionnalités IntelliSense, de navigation et de refactorisation. Au fil des modifications, créations, déplacements et suppressions de fichiers, Visual Studio effectue automatiquement le suivi des modifications et met à jour en permanence son index IntelliSense. 
  
## <a name="cmake-projects"></a>Projets CMake
CMake est intégré à l’IDE Visual Studio sous le nom « Outils Visual C++ pour CMake », un composant de la charge de travail de bureau C++. Pour plus d’informations, consultez [Visual C++ Tools pour CMake](cmake-tools-for-visual-cpp.md).
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>Projets QMake qui ciblent le framework Qt
Vous pouvez soit utiliser Outils Visual C++ pour CMake pour cibler Qt afin de générer des projets Qt, soit utiliser l’[extension Qt Visual Studio](https://download.qt.io/development_releases/vsaddin/) pour Visual Studio 2015 ou Visual Studio 2017.

## <a name="gyp-cons-scons-buck-etc"></a>gyp, Cons, SCons, Buck, etc.
Quel que soit le système de génération que vous utilisez dans Visual C++, vous pouvez tirer parti des avantages de l’IDE et du débogueur Visual C++. Quand vous ouvrez le dossier racine de votre projet, Visual C++ utilise l’heuristique pour indexer les fichiers sources pour IntelliSense et la navigation. Vous pouvez fournir des indications sur la structure de votre code en modifiant le fichier CppProperties.json. De la même façon, vous pouvez configurer votre programme de génération en modifiant le fichier launch.vs.json. 

## <a name="configuring-open-folder-projects"></a>Configuration de projets Ouvrir un dossier
Les trois fichiers JSON suivants vous permettent de personnaliser un projet Ouvrir un dossier :
|||
|-|-|
|CppProperties.json|Spécifiez les informations de configuration personnalisées pour la navigation. Si nécessaire, créez ce fichier dans votre dossier de projet racine.|
|launch.vs.json|Spécifiez les arguments de la ligne de commande. Accessible via l’option **Paramètres de débogage et de lancement** du menu contextuel de l’**Explorateur de solutions**.|
|tasks.vs.json|Spécifiez les commandes de génération personnalisée et les commutateurs de compilation. Accessible via l’option **Configurer les tâches** du menu contextuel de l’**Explorateur de solutions**.|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>Configurer IntelliSense avec CppProperties.json
Le comportement d’IntelliSense et de la navigation varie en partie selon la configuration de build active, qui définit les chemins #include, les commutateurs du compilateur et d’autres paramètres. Par défaut, Visual Studio fournit les configurations Debug et Release. Dans certains projets, vous devrez peut-être créer une configuration personnalisée pour permettre aux fonctionnalités IntelliSense et de navigation de comprendre parfaitement votre code. Pour définir une nouvelle configuration, créez un fichier appelé CppProperties.json dans le dossier racine. Voici un exemple :

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
Une configuration peut avoir l’une des propriétés suivantes :

|||  
|-|-| 
|`name`|Nom de configuration qui apparaît dans la liste déroulante des configurations C++|
|`includePath`|Liste des dossiers à spécifier dans le chemin include (correspond à /I dans la plupart des compilateurs)|
|`defines`|Liste des macros à définir (correspond à /D dans la plupart des compilateurs)|
|`compilerSwitches`|Un ou plusieurs commutateurs supplémentaires pouvant influencer le comportement d’IntelliSense|
|`forcedInclude`|En-tête à inclure automatiquement dans chaque unité de compilation (correspond à /FI dans MSVC ou -include dans clang)|
|`undefines`|Liste des macros non définies (correspond à /U dans MSVC)|
|`intelliSenseMode`|Moteur IntelliSense à utiliser Vous pouvez spécifier des variantes spécifiques à l’architecture pour MSVC, gcc ou Clang :
- msvc-x86 (valeur par défaut)
- msvc-x64
- msvc-arm
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- Linux-x64
- Linux-x86
- Linux-arm
- gccarm

#### <a name="environment-variables"></a>Variables d’environnement
CppProperties.json prend en charge le développement de variables d’environnement système pour les chemins include et d’autres valeurs de propriété. La syntaxe est `${env.FOODIR}` pour développer une variable d’environnement `%FOODIR%`. Les variables suivantes définies par le système sont également prises en charge :

|Nom de la variable|Description|  
|-----------|-----------------|
|vsdev|Environnement Visual Studio par défaut|
|msvc_x86|Compiler pour x86 à l’aide d’outils x86|
|msvc_arm|Compiler pour ARM à l’aide d’outils x86|
|msvc_arm64|Compiler pour ARM64 à l’aide d’outils x86|
|msvc_x86_x64|Compiler pour AMD64 à l’aide d’outils x86|
|msvc_x64_x64|Compiler pour AMD64 à l’aide d’outils 64 bits|
|msvc_arm_x64|Compiler pour ARM à l’aide d’outils 64 bits|
|msvc_arm64_x64|Compiler pour ARM64 à l’aide d’outils 64 bits|

Quand la charge de travail Linux est installée, les environnements suivants sont disponibles pour cibler à distance Linux et WSL :

|Nom de la variable|Description|  
|-----------|-----------------|
|linux_x86|Cibler Linux x86 à distance|
|linux_x64|Cibler Linux x64 à distance|
|linux_arm|Cibler Linux ARM à distance|

Vous pouvez définir des variables d’environnement personnalisées dans CppProperties.json (globalement ou par configuration). L’exemple suivant montre comment déclarer et utiliser des variables d’environnement par défaut et personnalisées. La propriété **environments** globale déclare une variable nommée **INCLUDE** qui peut être utilisée par n’importe quelle configuration :

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
    }
  ],
 
  "configurations": [
    {
      "inheritEnvironments": [
        // Inherit the MSVC 32-bit environment and toolchain.
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x86"
    },
    {
      "inheritEnvironments": [
        // Inherit the MSVC 64-bit environment and toolchain.
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```
Vous pouvez également définir une propriété **environments** à l’intérieur d’une configuration. Ainsi, elle ne s’applique qu’à cette configuration et remplace toutes les variables globales du même nom. Dans l’exemple suivant, la configuration x64 définit une variable **INCLUDE** locale qui remplace la valeur globale :

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
    }
  ],
 
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined in the global environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\\src\\includes64"
        }
      ],
 
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined in the local environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```

Toutes les variables d’environnement par défaut et personnalisées sont également disponibles dans tasks.vs.json et launch.vs.json.

#### <a name="macros"></a>Macros
Vous avez accès aux macros intégrées suivantes à l’intérieur de CppProperties.json :
|||
|-|-|
|`${workspaceRoot}`| Chemin complet au dossier de l’espace de travail|
|`${projectRoot}`| Chemin complet au dossier où se trouve CppProperties.json|
|`${vsInstallDir}`| Chemin complet au dossier où est installée l’instance en cours d’exécution de VS 2017|

Par exemple, si votre projet a un dossier include et comprend également windows.h et d’autres en-têtes courants du SDK Windows, il peut être judicieux de mettre à jour votre fichier de configuration CppProperties.json avec les include suivants :

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\ucrt",
        "${env.NETFXSDKDir}\\include\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\shared",
        "${env.VCToolsInstallDir}include"
      ]
    }
  ]
}
```

**Remarque :** `%WindowsSdkDir%` et `%VCToolsInstallDir%` ne sont pas définies comme des variables d’environnement globales. Veillez donc à lancer devenv.exe à partir d’une « invite de commandes développeur pour VS 2017 » qui définit ces variables.

Pour résoudre les erreurs IntelliSense dues à l’absence de chemins include, ouvrez la **Liste d’erreurs** et filtrez sa sortie sur « IntelliSense uniquement » et sur le code d’erreur E1696 « Impossible d’ouvrir le fichier de code source... ». 

Vous pouvez créer autant de configurations que vous le souhaitez dans CppProperties.json. Chacune d’elles apparaît dans la liste déroulante des configurations :

```json
{
  "configurations": [
    {
      "name": "Windows",
      ...
    },
    {
      "name": "with EXTERNAL_CODECS",
      ...
    }
  ]
}
```
### <a name="define-tasks-with-tasksvsjson"></a>Définir de tâches avec tasks.vs.json
Vous pouvez automatiser les scripts de génération ou d’autres opérations externes sur les fichiers de votre espace de travail actuel en les exécutant comme des tâches directement dans l’IDE. Vous pouvez configurer une nouvelle tâche en cliquant sur un fichier ou dossier puis en sélectionnant **Configurer les tâches**. 

![Ouvrir un dossier, Configurer les tâches](media/open-folder-config-tasks.png)

Cette opération crée (ou ouvre) le fichier `tasks.vs.json` dans le dossier .vs créé par Visual Studio dans votre dossier de projet racine. Vous pouvez définir une tâche arbitraire dans ce fichier, puis l’appeler à partir du menu contextuel de **l’Explorateur de solutions**. L’exemple suivant montre un fichier tasks.vs.json qui définit une tâche unique. `taskName` définit le nom qui apparaît dans le menu contextuel. `appliesTo` définit les fichiers sur lesquels la commande peut être exécutée. La propriété `command` fait référence à la variable d’environnement COMSPEC qui identifie le chemin de la console (cmd.exe sur Windows). Vous pouvez également référencer des variables d’environnement déclarées dans CppProperties.json ou CMakeSettings.json. La propriété `args` spécifie la ligne de commande à appeler. La macro `${file}` extrait le fichier sélectionné dans **l’Explorateur de solutions**. L’exemple suivant affiche le nom du fichier .cpp actuellement sélectionné.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```
Après avoir enregistré tasks.vs.json, vous pouvez cliquer avec le bouton droit sur n’importe quel fichier .cpp contenu dans le dossier et choisir **Echo filename** à partir du menu contextuel. Le nom du fichier apparaît dans la fenêtre Sortie.



#### <a name="appliesto"></a>appliesTo
Vous pouvez créer des tâches pour tout fichier ou dossier en spécifiant son nom dans le champ `appliesTo`, par exemple `"appliesTo" : "hello.cpp"`. Les masques de fichier suivants peuvent être utilisés comme valeurs :
|||
|-|-|
|`"*"`| la tâche est disponible pour tous les fichiers et dossiers dans l’espace de travail|
|`"*/"`| la tâche est disponible pour tous les dossiers dans l’espace de travail|
|`"*.cpp"`| Tâche disponible pour tous les fichiers avec l’extension .cpp dans l’espace de travail|
|`"/*.cpp"`| Tâche disponible pour tous les fichiers avec l’extension .cpp à la racine de l’espace de travail|
|`"src/*/"`| la tâche est disponible pour tous les sous-dossiers du dossier « src »|
|`"makefile"`| la tâche est disponible pour tous les fichiers makefile dans l’espace de travail|
|`"/makefile"`| la tâche est disponible uniquement dans le fichier makefile à la racine de l’espace de travail|

#### <a name="output"></a>sortie
Utilisez la propriété `output` pour spécifier l’exécutable à lancer quand vous appuyez sur **F5**. Exemple :

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>Macros pour tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Spécifie toute variable d’environnement (par exemple, ${env.PATH}, ${env.COMSPEC}, etc.) définie pour l’invite de commandes développeur. Pour plus d’informations, consultez [Invite de commandes développeur pour Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Chemin complet du dossier de l’espace de travail (par exemple, "C:\sources\hello")|
|`${file}`| Chemin complet du fichier ou dossier sur lequel exécuter cette tâche (par exemple, "C:\sources\hello\src\hello.cpp")|
|`${relativeFile}`| Chemin relatif du fichier ou dossier (par exemple, "src\hello.cpp")|
|`${fileBasename}`| Nom du fichier sans chemin ni extension (par exemple, "hello")|
|`${fileDirname}`| Chemin complet du fichier, sans le nom de fichier (par exemple, "C:\sources\hello\src")|
|`${fileExtname}`| Extension du fichier sélectionné (par exemple, ".cpp")|

#### <a name="custom-macros"></a>Macros personnalisées
Pour définir une macro personnalisée dans tasks.vs.json, ajoutez une paire nom:valeur avant les blocs de tâche. L’exemple suivant définit une macro nommée `outDir` qui est consommée dans la propriété`args` :

```json
{
"version": "0.2.1",
  "outDir": "${workspaceRoot}\\bin",
  "tasks": [
    {
      "taskName": "List outputs",
      "*",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": [
        "dir ${outDir}"
      ]
    }
  ]
```

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurer les paramètres de débogage avec launch.vs.json
Pour personnaliser les arguments de ligne de commande de votre programme, cliquez sur l’exécutable dans **Explorateur de solutions** et sélectionnez **Paramètres de débogage et de lancement**. Cette opération ouvre un fichier `launch.vs.json` existant ou, en l’absence d’un fichier, crée un fichier avec les informations sur le programme sélectionné. 

Pour spécifier des arguments supplémentaires, ajoutez-les simplement au tableau JSON `args`, comme indiqué dans l’exemple suivant :

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

Quand vous enregistrez ce fichier, la nouvelle configuration apparaît dans le menu déroulant Cible de débogage. Vous pouvez la sélectionner pour démarrer le débogueur. Vous pouvez créer autant de configurations Debug que vous le souhaitez, pour n’importe quel nombre d’exécutables. Si vous appuyez sur **F5** maintenant, le débogueur démarre et atteint tout point d’arrêt déjà défini. Toutes les fenêtres et fonctionnalités du débogueur que vous connaissez bien sont désormais disponibles.

## <a name="see-also"></a>Voir aussi
[IDE et outils de développement Visual C++](ide-and-tools-for-visual-cpp-development.md)

