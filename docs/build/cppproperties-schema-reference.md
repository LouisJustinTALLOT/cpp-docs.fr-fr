---
description: 'En savoir plus sur : CppProperties.jsà la référence'
title: CppProperties.jsà la référence
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: 9067a186d3ab111eda11246d06e3a9d7a164455f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163052"
---
# <a name="cpppropertiesjson-reference"></a>CppProperties.jsà la référence

Les projets de dossiers ouverts qui n’utilisent pas CMake peuvent stocker des paramètres de configuration de projet pour IntelliSense dans un *CppProperties.jssur* un fichier. (Les projets CMake utilisent un [CMakeSettings.jssur le](customize-cmake-settings.md) fichier.) Une configuration se compose de paires nom/valeur et définit #include chemins d’accès, des commutateurs de compilateur et d’autres paramètres. Consultez [ouvrir des projets de dossier pour C++](open-folder-projects-cpp.md) pour plus d’informations sur la façon d’ajouter des configurations dans un projet de dossier ouvert. Les sections suivantes résument les différents paramètres. Pour obtenir une description complète du schéma, accédez à *CppProperties_schema.jssur*, dont le chemin d’accès complet est indiqué en haut de l’éditeur de code lorsque *CppProperties.jssur* est ouvert.

## <a name="configuration-properties"></a>Propriétés de configuration

Une configuration peut avoir l’une des propriétés suivantes :

|Nom|Description|
|-|-|
|`inheritEnvironments`| Spécifie les environnements qui s’appliquent à cette configuration.|
|`name`|Nom de configuration qui s’affichera dans la liste déroulante de configuration C++|
|`includePath`|Liste séparée par des virgules des dossiers qui doivent être spécifiés dans le chemin d’accès include (correspond à/I pour la plupart des compilateurs)|
|`defines`|Liste des macros à définir (correspond à /D dans la plupart des compilateurs)|
|`compilerSwitches`|Un ou plusieurs commutateurs supplémentaires pouvant influencer le comportement d’IntelliSense|
|`forcedInclude`|En-tête à inclure automatiquement dans chaque unité de compilation (correspond à /FI dans MSVC ou -include dans clang)|
|`undefines`|Liste des macros non définies (correspond à /U dans MSVC)|
|`intelliSenseMode`|Moteur IntelliSense à utiliser Vous pouvez spécifier l’une des variantes prédéfinies spécifiques à l’architecture pour MSVC, GCC ou Clang.|
|`environments`|Ensembles de variables définis par l’utilisateur qui se comportent comme des variables d’environnement dans une invite de commandes et sont accessibles avec le $ {env. \<VARIABLE> } macrovirus.|

### <a name="intellisensemode-values"></a>valeurs intelliSenseMode

L’éditeur de code affiche les options disponibles lorsque vous commencez à taper :

![Ouvrir le dossier IntelliSense](media/open-folder-intellisense-mode.png "Ouvrir le dossier IntelliSense")

Les valeurs prises en charge sont les suivantes :

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
- Linux-GCC-ARM

Remarque : les valeurs `msvc-x86` et `msvc-x64` sont prises en charge uniquement pour des raisons d’héritage. Utilisez les `windows-msvc-*` variantes à la place.

## <a name="pre-defined-environments"></a>Environnements prédéfinis

Visual Studio fournit les environnements prédéfinis suivants pour Microsoft C++ qui sont mappés aux Invite de commandes développeur correspondants. Lorsque vous héritez de l’un de ces environnements, vous pouvez faire référence à l’une des variables d’environnement à l’aide de la propriété globale `env` avec la syntaxe de macro suivante : $ {env. \<VARIABLE> }.

|Nom de la variable|Description|
|-----------|-----------------|
|vsdev|Environnement Visual Studio par défaut|
|msvc_x86|Compiler pour x86 à l’aide d’outils x86|
|msvc_x64|Compiler pour AMD64 à l’aide d’outils 64 bits|
|msvc_arm|Compiler pour ARM à l’aide d’outils x86|
|msvc_arm64|Compiler pour ARM64 à l’aide d’outils x86|
|msvc_x86_x64|Compiler pour AMD64 à l’aide d’outils x86|
|msvc_arm_x64|Compiler pour ARM à l’aide d’outils 64 bits|
|msvc_arm64_x64|Compiler pour ARM64 à l’aide d’outils 64 bits|

Quand la charge de travail Linux est installée, les environnements suivants sont disponibles pour cibler à distance Linux et WSL :

|Nom de la variable|Description|
|-----------|-----------------|
|linux_x86|Cibler Linux x86 à distance|
|linux_x64|Cibler Linux x64 à distance|
|linux_arm|Cibler Linux ARM à distance|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a> Environnements définis par l’utilisateur

Vous pouvez éventuellement utiliser la `environments` propriété pour définir des ensembles de variables dans *CppProperties.js* , soit globalement, soit par configuration. Ces variables se comportent comme des variables d’environnement dans le contexte d’un projet de dossier ouvert et sont accessibles à l’aide de la fonction $ {env. \<VARIABLE> } la syntaxe de *tasks.vs.jssur* et *launch.vs.jssur* après qu’elles ont été définies ici. Toutefois, ils ne sont pas nécessairement définis comme des variables d’environnement réelles dans une invite de commandes que Visual Studio utilise en interne.

**Visual Studio 2019 version 16,4 et versions ultérieures :** Les variables spécifiques à la configuration définies dans *CppProperties.jssur* sont automatiquement récupérées par les cibles de débogage et les tâches sans qu’il soit nécessaire de définir `inheritEnvironments` . Les cibles de débogage sont lancées automatiquement avec l’environnement que vous spécifiez dans *CppProperties.js*.

**Visual Studio 2019 version 16,3 et versions antérieures :** Lorsque vous consommez un environnement, vous devez le spécifier dans la `inheritsEnvironments` propriété même si l’environnement est défini dans le cadre de la même configuration ; la `environment` propriété spécifie le nom de l’environnement. L’exemple suivant montre un exemple de configuration pour l’activation d’IntelliSense pour GCC dans une installation MSYS2. Notez comment la configuration définit et hérite de l' `mingw_64` environnement, et comment la `includePath` propriété peut accéder à la `INCLUDE` variable.

```json
"configurations": [
    {

      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath ,": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**",
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR};",
          "environment": "mingw_64"
        }
      ]
    }
  ]
```

Lorsque vous définissez une propriété d' **environnement** à l’intérieur d’une configuration, elle remplace toutes les variables globales du même nom.

## <a name="built-in-macros"></a>Macros intégrées

Vous avez accès aux macros intégrées suivantes dans *CppProperties.jssur*:

|Macro|Description|
|-|-|
|`${workspaceRoot}`| Chemin d’accès complet au dossier de l’espace de travail|
|`${projectRoot}`| Chemin d’accès complet au dossier dans lequel *CppProperties.js* est placé|
|`${env.vsInstallDir}`| Le chemin d’accès complet au dossier où l’instance en cours d’exécution de Visual Studio est installée|

### <a name="example"></a>Exemple

Si votre projet contient un dossier include et inclut également *Windows. h* et d’autres en-têtes courants de la SDK Windows, vous pouvez mettre à jour votre *CppProperties.jsdans* le fichier de configuration avec les éléments suivants :

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

Si vous ne voyez pas la fonctionnalité IntelliSense que vous attendez, vous pouvez résoudre les problèmes en accédant à **Outils**  >  **options**  >  **éditeur de texte**  >  **C/C++**  >  **avancé** et en définissant **activer la journalisation** sur **`true`** . Pour commencer, essayez de définir le **niveau de journalisation** sur 5 et les **filtres de journalisation** sur 8.

![la journalisation des diagnostics.](media/diagnostic-logging.png)

La sortie est dirigée vers le **fenêtre Sortie** et est visible lorsque vous choisissez **afficher la sortie à partir de : journal des Visual C++**. La sortie contient, entre autres choses, la liste des chemins d’accès include réels que IntelliSense tente d’utiliser. Si les chemins d’accès ne correspondent pas à ceux de *CppProperties.jssur*, essayez de fermer le dossier et de supprimer le sous-dossier *. vs* qui contient les données de navigation mises en cache.

Pour résoudre les erreurs IntelliSense dues à l’absence de chemins include, ouvrez la **Liste d’erreurs** et filtrez sa sortie sur « IntelliSense uniquement » et sur le code d’erreur E1696 « Impossible d’ouvrir le fichier de code source... ».
