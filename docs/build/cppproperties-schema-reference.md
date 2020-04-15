---
title: CppProperties.json référence
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328715"
---
# <a name="cpppropertiesjson-reference"></a>CppProperties.json référence

Les projets Open Folder qui n’utilisent pas CMake peuvent stocker les paramètres de configuration du projet pour IntelliSense dans un fichier *CppProperties.json.* (Les projets CMake utilisent un fichier [CMakeSettings.json.)](customize-cmake-settings.md) Une configuration se compose de paires de noms/valeurs et définit #include chemins, compilant commutateurs, et d’autres paramètres. Consultez [les projets Open Folder pour plus d’informations](open-folder-projects-cpp.md) sur la façon d’ajouter des configurations dans un projet Open Folder. Les sections suivantes résument les différents paramètres. Pour une description complète du schéma, naviguez vers *CppProperties_schema.json*, dont le chemin complet est donné en haut de l’éditeur de code lorsque *CppProperties.json* est ouvert.

## <a name="configuration-properties"></a>Propriétés de configuration

Une configuration peut avoir l’une des propriétés suivantes :

|||
|-|-|
|`inheritEnvironments`| Précise quels environnements s’appliquent à cette configuration.|
|`name`|Le nom de configuration qui apparaîtra dans le dropdown de configuration C|
|`includePath`|Une liste de dossiers comma-séparés qui doivent être spécifiés dans le chemin inclus (cartes à /I pour la plupart des compilateurs)|
|`defines`|Liste des macros à définir (correspond à /D dans la plupart des compilateurs)|
|`compilerSwitches`|Un ou plusieurs commutateurs supplémentaires pouvant influencer le comportement d’IntelliSense|
|`forcedInclude`|En-tête à inclure automatiquement dans chaque unité de compilation (correspond à /FI dans MSVC ou -include dans clang)|
|`undefines`|Liste des macros non définies (correspond à /U dans MSVC)|
|`intelliSenseMode`|Moteur IntelliSense à utiliser Vous pouvez spécifier l’une des variantes prédéfinies spécifiques à l’architecture pour MSVC, gcc ou Clang.|
|`environments`|Ensembles de variables définis par l’utilisateur qui se comportent comme des\< variables d’environnement dans une invite de commande et sont consultés avec le $env. VARIABLE> macro.|

### <a name="intellisensemode-values"></a>valeurs intelliSenseMode

L’éditeur de code affiche les options disponibles lorsque vous commencez à taper :

![Dossier ouvert IntelliSense](media/open-folder-intellisense-mode.png "Dossier ouvert IntelliSense")

Voici les valeurs prises en charge :

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
- linux-gcc-bras

Remarque : `msvc-x86` Les `msvc-x64` valeurs et sont prises en charge pour des raisons héritées seulement. Utilisez `windows-msvc-*` les variantes à la place.

## <a name="pre-defined-environments"></a>Environnements prédéfinis

Visual Studio fournit les environnements prédéfinis suivants pour Microsoft CMD qui cartographient l’invite correspondante de commande de développeur. Lorsque vous héritez d’un de ces environnements, vous `env` pouvez vous référer à l’une\< des variables de l’environnement en utilisant la propriété globale avec cette syntaxe macro : $-env. VARIABLE>.

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

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a>Environnements définis par l’utilisateur

Vous pouvez utiliser `environments` la propriété en option pour définir des ensembles de variables dans *CppProperties.json* soit globalement ou par configuration. Ces variables se comportent comme des variables d’environnement dans le cadre d’un\< projet Open Folder et peuvent être consultées avec le $env. VARIABLE> syntaxe à partir de *tasks.vs.json* et *launch.vs.json* après qu’ils soient définis ici. Cependant, ils ne sont pas nécessairement définis comme variables d’environnement réelles dans n’importe quelle invite de commande que Visual Studio utilise en interne.

**Visual Studio 2019 version 16.4 et plus tard:** Les variables spécifiques à la configuration définies dans *CppProperties.json* sont automatiquement `inheritEnvironments`captées par des cibles et des tâches de déboçons sans avoir à définir . Les cibles Debug sont lancées automatiquement avec l’environnement que vous spécifiez dans *CppProperties.json*.

**Visual Studio 2019 version 16.3 et plus tôt:** Lorsque vous consommez un environnement, vous `inheritsEnvironments` devez le spécifier dans la propriété même si l’environnement est défini comme faisant partie de la même configuration; la `environment` propriété spécifie le nom de l’environnement. L’exemple suivant montre une configuration d’échantillon pour permettre IntelliSense pour le CCG dans une installation MSYS2. Notez comment la configuration définit `mingw_64` et hérite `includePath` de l’environnement, et comment la propriété peut accéder à la `INCLUDE` variable.

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

Lorsque vous définissez une propriété **d’environnements** à l’intérieur d’une configuration, elle remplace toutes les variables globales du même nom.

## <a name="built-in-macros"></a>Macros intégrés

Vous avez accès aux macros intégrées suivantes à l’intérieur *de CppProperties.json*:

|||
|-|-|
|`${workspaceRoot}`| Le chemin complet vers le dossier d’espace de travail|
|`${projectRoot}`| Le chemin complet vers le dossier où *CppProperties.json* est placé|
|`${env.vsInstallDir}`| Le chemin complet vers le dossier où l’instance de fonctionnement de Visual Studio est installé|

### <a name="example"></a>Exemple

Si votre projet a un dossier inclus et comprend également *windows.h* et d’autres en-têtes communs de la SDK Windows, vous pouvez mettre à jour votre fichier de configuration *CppProperties.json* avec les éléments suivants comprend:

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

Si vous ne voyez pas l’IntelliSense que vous attendez, vous pouvez dépanner en allant à **Tools** > **Options** > **Text Editor** > **C/C-Advanced** > **Advanced** et en **définissant Enable Logging** pour **vrai**. Pour commencer, essayez de définir **le niveau d’enregistrement** à 5, et **les filtres d’enregistrement** à 8.

![la journalisation des diagnostics.](media/diagnostic-logging.png)

La sortie est acheminée vers la **fenêtre de sortie** et est visible lorsque vous choisissez Afficher la sortie **de: Visual C ' Log**. La sortie contient, entre autres choses, la liste des personnes réelles comprennent des chemins qu’IntelliSense essaie d’utiliser. Si les chemins ne correspondent pas à ceux de *CppProperties.json*, essayez de fermer le dossier et de supprimer le sous-dossier *.vs* qui contient des données de navigation en cache.

Pour résoudre les erreurs IntelliSense dues à l’absence de chemins include, ouvrez la **Liste d’erreurs** et filtrez sa sortie sur « IntelliSense uniquement » et sur le code d’erreur E1696 « Impossible d’ouvrir le fichier de code source... ».
