---
title: Informations de référence sur le schéma CppProperties.json
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual Studio
ms.openlocfilehash: cf5cd964068ad2e3aeeaf1e057c9bf407f4985f5
ms.sourcegitcommit: b233f05adae607f75815111006a771c432df5a9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67516362"
---
# <a name="cpppropertiesjson-schema-reference"></a>Informations de référence sur le schéma CppProperties.json

Les projets Dossier ouvert qui n’utilisent pas CMake peuvent stocker des paramètres de configuration de projet dans un fichier `CppProperties.json`. (Les projets CMake utilisent un fichier [CMakeSettings.json](customize-cmake-settings.md).) L’IDE de Visual Studio utilise `CppProperties.json` pour IntelliSense et la navigation dans le code. Une configuration se compose de paires nom-valeur et définit des chemins #include, des commutateurs de compilateur et d’autres paramètres. 


## <a name="default-configurations"></a>Configurations par défaut

Visual Studio fournit des configurations prédéfinies pour les versions x86 et x64 Debug et Release. Par défaut, votre projet a une configuration x86-Debug dans `CppProperties.json`. Pour ajouter une nouvelle configuration, cliquez sur le `CppProperties.json` fichier **l’Explorateur de solutions** et choisissez **ajouter une Configuration**:

![Ouvrez le dossier - ajouter une nouvelle configuration](media/open-folder-add-config.png "ouvrir le dossier ajouter une nouvelle configuration")

Les configurations par défaut sont indiquées ici :

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
Pour les propriétés sujettes à un ensemble de valeurs autorisées, l’éditeur de code présente les options disponibles quand vous commencez à taper :

![Dossier ouvert IntelliSense](media/open-folder-intellisense-mode.png "Dossier ouvert IntelliSense")



## <a name="configuration-properties"></a>Propriétés de configuration

Une configuration peut avoir l’une des propriétés suivantes :

|||
|-|-|
|`name`|Nom de la configuration qui apparaît dans la liste déroulante des configurations C++|
|`includePath`|Liste des dossiers à spécifier dans le chemin include (correspond à /I dans la plupart des compilateurs)|
|`defines`|Liste des macros à définir (correspond à /D dans la plupart des compilateurs)|
|`compilerSwitches`|Un ou plusieurs commutateurs supplémentaires pouvant influencer le comportement d’IntelliSense|
|`forcedInclude`|En-tête à inclure automatiquement dans chaque unité de compilation (correspond à /FI dans MSVC ou -include dans clang)|
|`undefines`|Liste des macros non définies (correspond à /U dans MSVC)|
|`intelliSenseMode`|Moteur IntelliSense à utiliser Vous pouvez spécifier les variantes spécifique de l’architecture pour MSVC, gcc et Clang :<br/><br/>- windows-msvc-x86 (valeur par défaut)<br/>- windows-msvc-x64<br/>- msvc-arm<br/>- windows-clang-x86<br/>- windows-clang-x64<br/>- windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>- Linux-arm<br/>- gccarm|

Remarque : Les valeurs `msvc-x86` et `msvc-x64` sont prises en charge pour des raisons d’héritage uniquement. Utilisez le `windows-msvc-*` variantes à la place.

## <a name="custom-configurations"></a>Configurations personnalisées


Vous pouvez personnaliser toutes les configurations par défaut dans `CppProperties.json` ou créer des configurations. Chacune d’elles apparaît dans la liste déroulante des configurations :

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

## <a name="system-environment-variables"></a>Variables d’environnement système 

 `CppProperties.json` prend en charge le développement de variables d’environnement système pour les chemins include et d’autres valeurs de propriété. La syntaxe est `${env.FOODIR}` pour développer une variable d’environnement `%FOODIR%`. Les variables suivantes définies par le système sont également prises en charge :

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

## <a name="custom-environment-variables"></a>Variables d’environnement personnalisées

Vous pouvez définir des variables d’environnement personnalisées dans `CppProperties.json` (globalement ou par configuration). L’exemple suivant montre comment déclarer et utiliser des variables d’environnement par défaut et personnalisées. La propriété **environments** globale déclare une variable nommée **INCLUDE** qui peut être utilisée par n’importe quelle configuration :

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
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
      "intelliSenseMode": "windows-msvc-x86"
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
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
## <a name="per-configuration-environment-variables"></a>Variables d’environnement par configuration

Vous pouvez également définir un **environnements** propriété au sein d’une configuration. Il s’applique uniquement à cette configuration et remplace toutes les variables globales du même nom. Dans l’exemple suivant, la configuration x64 définit une variable **INCLUDE** locale qui remplace la valeur globale :

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
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
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\src\includes64"
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
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

Toutes les variables d’environnement personnalisées et par défaut sont également disponibles dans `tasks.vs.json` et `launch.vs.json`.

#### <a name="build-in-macros"></a>Macros intégrées

Vous avez accès aux macros intégrées suivantes à l’intérieur de `CppProperties.json` :

|||
|-|-|
|`${workspaceRoot}`| Chemin complet au dossier de l’espace de travail|
|`${projectRoot}`| Chemin complet du dossier où `CppProperties.json` est placé|
|`${env.vsInstallDir}`| Chemin complet du dossier où est installée l’instance en cours d’exécution de Visual Studio|

Par exemple, si votre projet a un dossier include et également windows.h et autres en-têtes communs à partir du SDK Windows, vous pouvez mettre à jour votre `CppProperties.json` inclut du fichier de configuration avec les éléments suivants :

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\ucrt",
        "${env.NETFXSDKDir}\include\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\shared",
        "${env.VCToolsInstallDir}\include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%` et `%VCToolsInstallDir%` ne sont pas définies comme des variables d’environnement globales. Veillez donc à lancer devenv.exe à partir d’une invite de commandes développeur qui définit ces variables. (Tapez « développeur » dans le menu Démarrer de Windows.)

## <a name="troubleshoot-intellisense-errors"></a>Corriger les erreurs IntelliSense

Pour résoudre les erreurs IntelliSense dues à l’absence de chemins include, ouvrez la **Liste d’erreurs** et filtrez sa sortie sur « IntelliSense uniquement » et sur le code d’erreur E1696 « Impossible d’ouvrir le fichier de code source... ».
