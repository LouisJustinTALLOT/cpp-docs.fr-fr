---
title: Prise en charge de la fonctionnalité Dossier ouvert pour les systèmes de génération C++ dans Visual Studio
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 9264aa4bf77de406bdde9042ef9ec4251763f721
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320959"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Prise en charge de la fonctionnalité Dossier ouvert pour les systèmes de génération C++ dans Visual Studio

::: moniker range="vs-2015"

La fonctionnalité ouvrir le dossier est disponible dans Visual Studio 2017 et versions ultérieures.

::: moniker-end

::: moniker range=">=vs-2017"

Dans Visual Studio 2017 et ultérieur, la fonctionnalité « Ouvrir un dossier » vous permet d’ouvrir un dossier de fichiers sources et de commencer immédiatement à coder en bénéficiant des avantages suivants : IntelliSense, navigation, refactorisation, débogage, etc. Au fil des modifications, créations, déplacements et suppressions de fichiers, Visual Studio effectue automatiquement le suivi des modifications et met à jour en permanence son index IntelliSense. Aucun fichier .sln ou .vcxproj n’est chargé. Si nécessaire, vous pouvez spécifier des tâches personnalisées ou générer et lancer des paramètres par le biais de fichiers .json simples. Cette fonctionnalité vous permet d’intégrer n’importe quel système de génération tiers dans Visual Studio. Pour des informations générales sur la fonctionnalité Dossier ouvert, consultez [Développer du code dans Visual Studio sans projets ni solutions](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake et QT

CMake est intégré à l’IDE de Visual Studio en tant que composant de la charge de travail de bureau C++. Le flux de travail pour CMake n’est pas identique au flux de travail décrit dans cet article. Si vous utilisez CMake, consultez [projets cmake dans Visual Studio](cmake-projects-in-visual-studio.md). Vous pouvez également utiliser CMake pour générer des projets QT, ou vous pouvez utiliser l' [extension Visual Studio QT](https://download.qt.io/development_releases/vsaddin/) pour visual studio 2015 ou visual studio 2017.

## <a name="other-build-systems"></a>Autres systèmes de génération

Pour utiliser l’IDE de Visual Studio avec un système de génération ou un ensemble d’outils du compilateur qui n’est pas directement pris en charge à partir du menu principal, sélectionnez **fichier | Ouvrir | Ou appuyez** sur **Ctrl + Maj + Alt + O**. Accédez au dossier qui contient vos fichiers de code source. Pour générer le projet, configurer IntelliSense et définir des paramètres de débogage, vous ajoutez trois fichiers JSON :

| | |
|-|-|
|CppProperties.json|Spécifiez les informations de configuration personnalisées pour la navigation. Si nécessaire, créez ce fichier dans votre dossier de projet racine. (Non utilisé dans les projets CMake.)|
|tasks.vs.json|Spécifiez les commandes de génération personnalisées. Accessible via l’option **Configurer les tâches** du menu contextuel de l’**Explorateur de solutions**.|
|launch.vs.json|Spécifiez des arguments de ligne de commande pour le débogueur. Accessible via l’option **Paramètres de débogage et de lancement** du menu contextuel de l’**Explorateur de solutions**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Configurer la navigation du code avec CppProperties. JSON

Pour que les fonctionnalités IntelliSense et de navigation telles que **atteindre la définition** fonctionnent correctement, Visual Studio doit savoir quel compilateur vous utilisez, où se trouvent les en-têtes système, et où se trouvent les fichiers include supplémentaires s’ils ne se trouvent pas directement dans le dossier que vous avez ouvert (le dossier de l’espace de travail). Pour spécifier une configuration, vous pouvez choisir **gérer les configurations** dans la liste déroulante de la barre d’outils principale :

![Liste déroulante gérer les configurations](media/manage-configurations-dropdown.png)

Visual Studio propose les configurations par défaut suivantes :

![Configurations par défaut](media/default-configurations.png)

Si, par exemple, vous choisissez **x64-Debug**, Visual Studio crée un fichier appelé *CppProperties. JSON* dans le dossier racine de votre projet :

```json
{
  "configurations": [
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
    }
  ]
}
```

Cette configuration hérite des variables d’environnement du Invite de commandes développeur Visual Studio [x64](building-on-the-command-line.md). L’une de ces variables `INCLUDE` est et vous pouvez y faire référence ici à l' `${env.INCLUDE}` aide de la macro. La `includePath` propriété indique à Visual Studio où rechercher toutes les sources dont il a besoin pour IntelliSense. Dans ce cas, il indique « Rechercher dans tous les répertoires spécifiés par la variable d’environnement INCLUDe », ainsi que tous les répertoires de l’arborescence de dossiers de travail active. La `name` propriété est le nom qui s’affiche dans la liste déroulante, et peut être tout ce que vous aimez. La `defines` propriété fournit des indications à IntelliSense lorsqu’il rencontre des blocs de compilation conditionnelle. La `intelliSenseMode` propriété fournit des indications supplémentaires basées sur le type de compilateur. Plusieurs options sont disponibles pour MSVC, GCC et Clang.

> [!NOTE]
> Si Visual Studio semble ignorer les paramètres dans *CppProperties. JSON*, essayez d’ajouter une exception à votre fichier *. gitignore* comme suit : `!/CppProperties.json`.

## <a name="default-configuration-for-mingw-w64"></a>Configuration par défaut de MinGW-W64

Si vous ajoutez la configuration MinGW-W64, le JSON se présente comme suit :

```json
{
  {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.BIN_ROOT};${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
    }
}
```

Notez le `environments` bloc. Il définit des propriétés qui se comportent comme des variables d’environnement et qui sont disponibles non seulement dans le fichier *CppProperties. JSON* , mais également dans les autres fichiers de configuration *Task. vs. JSON* et *Launch. vs. JSON*. La `Mingw64` configuration hérite de `mingw_w64` l’environnement et utilise sa `INCLUDE` propriété pour spécifier la valeur de `includePath`. Vous pouvez ajouter d’autres chemins d’accès à cette propriété de tableau en fonction des besoins.

La `intelliSenseMode` propriété est définie sur une valeur appropriée pour GCC. Pour plus d’informations sur toutes ces propriétés, consultez [référence de schéma CppProperties](cppproperties-schema-reference.md).

Lorsque tout fonctionne correctement, IntelliSense s’affiche à partir des en-têtes GCC quand vous pointez sur un type :

![IntelliSense GCC](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Activer les diagnostics IntelliSense

Si vous ne voyez pas la fonctionnalité IntelliSense que vous attendez, vous pouvez résoudre les problèmes en accédant à **Outils** > **options** > **éditeur** > de texte**C/C++** > **avancé** et en affectant à **activer la journalisation** la **valeur true**. Pour commencer, essayez de définir le **niveau de journalisation** sur 5 et les **filtres de journalisation** sur 8.

![la journalisation des diagnostics.](media/diagnostic-logging.png)

La sortie est dirigée vers le **fenêtre Sortie** et est visible quand vous choisissez **afficher la sortie à partir de : Journal de Visual C++*. La sortie contient, entre autres choses, la liste des chemins d’accès include réels que IntelliSense tente d’utiliser. Si les chemins d’accès ne correspondent pas à ceux figurant dans *CppProperties. JSON*, essayez de fermer le dossier et de supprimer le sous-dossier *. vs* qui contient les données de navigation mises en cache.

### <a name="define-build-tasks-with-tasksvsjson"></a>Définir des tâches de génération avec tasks.vs.json

Vous pouvez automatiser les scripts de génération ou d’autres opérations externes sur les fichiers de votre espace de travail actuel en les exécutant comme des tâches directement dans l’IDE. Vous pouvez configurer une nouvelle tâche en cliquant sur un fichier ou dossier puis en sélectionnant **Configurer les tâches**.

![Ouvrir un dossier, Configurer les tâches](media/configure-tasks.png)

Cela crée (ou ouvre) le fichier *Tasks. vs. JSON* dans le dossier. vs que Visual Studio crée dans le dossier de votre projet racine. Vous pouvez définir une tâche arbitraire dans ce fichier, puis l’appeler à partir du menu contextuel de **l’Explorateur de solutions**. Pour continuer l’exemple GCC, l’extrait de code suivant montre un fichier *Tasks. vs. JSON* complet avec une tâche unique qui appelle *g + +. exe* pour générer un projet. Supposons que le projet contienne un seul fichier appelé *Hello. cpp*.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

Le fichier JSON est placé dans le sous-dossier *. vs* . Pour afficher ce dossier, cliquez sur le bouton **Afficher tous les fichiers** en haut de **Explorateur de solutions**. Vous pouvez exécuter cette tâche en cliquant avec le bouton droit sur le nœud racine dans **Explorateur de solutions** et en choisissant **générer Hello**. Lorsque la tâche se termine, vous devez voir un nouveau fichier *Hello. exe* dans **Explorateur de solutions**.

Vous pouvez définir plusieurs types de tâches. L’exemple suivant montre un *fichier Tasks. vs. JSON* qui définit une tâche unique. `taskLabel` définit le nom qui apparaît dans le menu contextuel. `appliesTo` définit les fichiers sur lesquels la commande peut être exécutée. La `command` propriété fait référence à la variable d’environnement COMSPEC, qui identifie le chemin d’accès de la console (*cmd. exe* sur Windows). Vous pouvez également référencer des variables d’environnement déclarées dans CppProperties.json ou CMakeSettings.json. La propriété `args` spécifie la ligne de commande à appeler. La macro `${file}` extrait le fichier sélectionné dans **l’Explorateur de solutions**. L’exemple suivant affiche le nom du fichier .cpp actuellement sélectionné.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

Après avoir enregistré *Tasks. vs. JSON*, vous pouvez cliquer avec le bouton droit sur n’importe quel fichier *. cpp* dans le dossier, choisir **echo filename** dans le menu contextuel et afficher le nom de fichier affiché dans la fenêtre sortie.

Pour plus d’informations, consultez [Informations de référence sur le schéma Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurer les paramètres de débogage avec launch.vs.json

Pour personnaliser les arguments de ligne de commande et les instructions de débogage de votre programme, cliquez avec le bouton droit sur le fichier exécutable dans **Explorateur de solutions** et sélectionnez **paramètres de débogage et de lancement**. Cela ouvre un fichier *Launch. vs. JSON* existant, ou s’il n’en existe aucun, il crée un nouveau fichier avec un ensemble de paramètres de lancement minimal. Tout d’abord, vous avez le choix du type de session de débogage que vous souhaitez configurer. Pour déboguer un projet MinGw-W64, nous choisissons le **lancement de C/C++ pour MinGw/Cygwin (GDB)**. Cela permet de créer une configuration de lancement pour l’utilisation de *gdb. exe* , avec quelques hypothèses sur les valeurs par défaut. L’une de ces valeurs par `MINGW_PREFIX`défaut est. Vous pouvez substituer le chemin d’accès littéral (comme indiqué ci-dessous) `MINGW_PREFIX` ou vous pouvez définir une propriété dans *CppProperties. JSON*:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

Pour démarrer le débogage, choisissez l’exécutable dans la liste déroulante déboguer, puis cliquez sur la flèche verte :

![Lancer le débogueur](media/launch-debugger-gdb.png)

Vous devez voir s’afficher la boîte de dialogue **initialisation du débogueur** , puis une fenêtre de console externe qui exécute votre programme.

Pour plus d’informations, consultez [référence de schéma Launch. vs. JSON](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Lancement d’autres exécutables

Vous pouvez définir des paramètres de lancement pour tous les exécutables sur votre ordinateur. L’exemple suivant lance *7za* et spécifie des arguments supplémentaires, en les ajoutant `args` au tableau JSON :

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

::: moniker-end
