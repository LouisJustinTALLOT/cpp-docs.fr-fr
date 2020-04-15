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

La fonction Open Folder est disponible dans Visual Studio 2017 et plus tard.

::: moniker-end

::: moniker range=">=vs-2017"

Dans Visual Studio 2017 et ultérieur, la fonctionnalité « Ouvrir un dossier » vous permet d’ouvrir un dossier de fichiers sources et de commencer immédiatement à coder en bénéficiant des avantages suivants : IntelliSense, navigation, refactorisation, débogage, etc. Au fil des modifications, créations, déplacements et suppressions de fichiers, Visual Studio effectue automatiquement le suivi des modifications et met à jour en permanence son index IntelliSense. Aucun fichier .sln ou .vcxproj n’est chargé. Si nécessaire, vous pouvez spécifier des tâches personnalisées ou générer et lancer des paramètres par le biais de fichiers .json simples. Cette fonctionnalité vous permet d’intégrer n’importe quel système de construction tiers dans Visual Studio. Pour des informations générales sur la fonctionnalité Dossier ouvert, consultez [Développer du code dans Visual Studio sans projets ni solutions](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake et Qt

CMake est intégré dans l’IDE Visual Studio en tant que composant de la charge de travail de bureau C. Le flux de travail pour CMake n’est pas identique au flux de travail décrit dans cet article. Si vous utilisez CMake, voir [les projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md). Vous pouvez également utiliser CMake pour construire des projets Qt, ou vous pouvez utiliser [l’extension Qt Visual Studio](https://download.qt.io/development_releases/vsaddin/) pour Visual Studio 2015 ou Visual Studio 2017.

## <a name="other-build-systems"></a>Autres systèmes de construction

Pour utiliser l’IDE Visual Studio avec un système de construction ou un ensemble d’outils compilateur qui n’est pas directement pris en charge à partir du menu principal **sélectionnez Fichier . Ouvert Dossier** ou appuyez sur **Ctrl - Shift et Alt et O**. Naviguez vers le dossier qui contient vos fichiers de code source. Pour construire le projet, configurer IntelliSense et définir des paramètres de débogage, vous ajoutez trois fichiers JSON :

| | |
|-|-|
|CppProperties.json|Spécifiez les informations de configuration personnalisées pour la navigation. Si nécessaire, créez ce fichier dans votre dossier de projet racine. (Non utilisé dans les projets CMake.)|
|tasks.vs.json|Spécifier les commandes de construction personnalisées. Accessible via l’option **Configurer les tâches** du menu contextuel de l’**Explorateur de solutions**.|
|launch.vs.json|Spécifiez des arguments de ligne de commande pour le débogueur. Accessible via l’option **Paramètres de débogage et de lancement** du menu contextuel de l’**Explorateur de solutions**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Configurer la navigation de code avec CppProperties.json

Pour IntelliSense et le comportement de navigation tels que **Go to Definition** pour fonctionner correctement, Visual Studio doit savoir quel compilateur vous utilisez, où les en-têtes du système sont, et où les fichiers supplémentaires comprennent sont situés s’ils ne sont pas directement dans le dossier que vous avez ouvert (le dossier d’espace de travail). Pour spécifier une configuration, vous pouvez choisir **Les configurations** de gestion à partir du décrochage de la barre d’outils principale :

![Gérer les configurations décrochez](media/manage-configurations-dropdown.png)

Visual Studio offre les configurations par défaut suivantes :

![Configurations par défaut](media/default-configurations.png)

Si, par exemple, vous choisissez **x64-Debug**, Visual Studio crée un fichier appelé *CppProperties.json* dans votre dossier de projet racine:

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

Cette configuration hérite des variables de l’environnement du Visual Studio [x64 Developer Command Prompt](building-on-the-command-line.md). Une de ces `INCLUDE` variables est et vous pouvez `${env.INCLUDE}` vous y référer ici en utilisant la macro. La `includePath` propriété indique Visual Studio où chercher toutes les sources dont il a besoin pour IntelliSense. Dans ce cas, il est dit "regardez dans tous les répertoires spécifiés par la variable de l’environnement INCLUDE, et aussi tous les répertoires dans l’arbre de dossier de travail actuel." La `name` propriété est le nom qui apparaîtra dans le décrochage, et peut être tout ce que vous voulez. La `defines` propriété fournit des conseils à IntelliSense quand il rencontre des blocs de compilation conditionnelles. La `intelliSenseMode` propriété fournit quelques conseils supplémentaires basés sur le type de compilateur. Plusieurs options sont disponibles pour MSVC, GCC et Clang.

> [!NOTE]
> Si Visual Studio semble ignorer les paramètres dans *CppProperties.json*, essayez d’ajouter `!/CppProperties.json`une exception à votre fichier *.gitignore* comme ceci: .

## <a name="default-configuration-for-mingw-w64"></a>Configuration par défaut pour MinGW-w64

Si vous ajoutez la configuration MinGW-W64, le JSON semble ceci:

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

Notez `environments` le bloc. Il définit les propriétés qui se comportent comme des variables de l’environnement et sont disponibles non seulement dans le fichier *CppProperties.json,* mais aussi dans les autres fichiers de configuration *task.vs.json* et *launch.vs.json*. La `Mingw64` configuration hérite de l’environnement, `mingw_w64` et utilise sa `INCLUDE` propriété pour spécifier la valeur pour `includePath`. Vous pouvez ajouter d’autres chemins à cette propriété de tableau au besoin.

La `intelliSenseMode` propriété est réglée à une valeur appropriée pour le CCG. Pour plus d’informations sur toutes ces propriétés, voir [CppProperties schema référence](cppproperties-schema-reference.md).

Lorsque tout fonctionne correctement, vous verrez IntelliSense à partir des en-têtes du CCG lorsque vous planez sur un type:

![CCG IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Activez les diagnostics IntelliSense

Si vous ne voyez pas l’IntelliSense que vous attendez, vous pouvez dépanner en allant à **Tools** > **Options** > **Text Editor** > **C/C-Advanced** > **Advanced** et en **définissant Enable Logging** pour **vrai**. Pour commencer, essayez de définir **le niveau d’enregistrement** à 5, et **les filtres d’enregistrement** à 8.

![la journalisation des diagnostics.](media/diagnostic-logging.png)

La sortie est acheminée vers la **fenêtre de sortie** et est visible lorsque vous choisissez la sortie*d’exposition à partir de: Visual C ' Log*. La sortie contient, entre autres choses, la liste des personnes réelles comprennent des chemins qu’IntelliSense essaie d’utiliser. Si les chemins ne correspondent pas à ceux de *CppProperties.json*, essayez de fermer le dossier et de supprimer le sous-plieur *.vs* qui contient des données de navigation en cache.

### <a name="define-build-tasks-with-tasksvsjson"></a>Définir des tâches de génération avec tasks.vs.json

Vous pouvez automatiser les scripts de génération ou d’autres opérations externes sur les fichiers de votre espace de travail actuel en les exécutant comme des tâches directement dans l’IDE. Vous pouvez configurer une nouvelle tâche en cliquant sur un fichier ou dossier puis en sélectionnant **Configurer les tâches**.

![Ouvrir un dossier, Configurer les tâches](media/configure-tasks.png)

Cela crée (ou ouvre) le fichier *tasks.vs.json* dans le dossier .vs que Visual Studio crée dans votre dossier de projet racine. Vous pouvez définir une tâche arbitraire dans ce fichier, puis l’appeler à partir du menu contextuel de **l’Explorateur de solutions**. Pour poursuivre l’exemple du CCG, l’extrait suivant montre un fichier *complet de tâches.vs.json* avec comme tâche unique qui invoque *g.exe* pour construire un projet. Supposons que le projet contient un seul fichier appelé *hello.cpp*.

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

Le fichier JSON est placé dans le sous-plieur *.vs.* Pour voir ce dossier, cliquez sur le bouton **Afficher tous les fichiers** en haut de Solution **Explorer**. Vous pouvez exécuter cette tâche en cliquant à droite sur le nœud racine dans **Solution Explorer** et en choisissant **construire bonjour**. Lorsque la tâche se termine, vous devriez voir un nouveau fichier, *hello.exe* dans **Solution Explorer**.

Vous pouvez définir de nombreux types de tâches. L’exemple suivant montre un *fichier tasks.vs.json* qui définit une seule tâche. `taskLabel` définit le nom qui apparaît dans le menu contextuel. `appliesTo` définit les fichiers sur lesquels la commande peut être exécutée. La `command` propriété se réfère à la variable d’environnement COMSPEC, qui identifie le chemin de la console *(cmd.exe* sur Windows). Vous pouvez également référencer des variables d’environnement déclarées dans CppProperties.json ou CMakeSettings.json. La propriété `args` spécifie la ligne de commande à appeler. La macro `${file}` extrait le fichier sélectionné dans **l’Explorateur de solutions**. L’exemple suivant affiche le nom du fichier .cpp actuellement sélectionné.

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

Après avoir enregistrer *les tâches.vs.json*, vous pouvez cliquer à droite sur n’importe quel fichier *.cpp* dans le dossier, choisir le nom de **fichier Echo** dans le menu contextuelle, et voir le nom de fichier affiché dans la fenêtre de sortie.

Pour plus d’informations, consultez [Informations de référence sur le schéma Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurer les paramètres de débogage avec launch.vs.json

Pour personnaliser les arguments de la ligne de commande et les instructions de débogage de votre programme, cliquez à droite sur l’exécutable dans **Solution Explorer** et sélectionnez **Debug et Paramètres de lancement**. Cela ouvrira un fichier *de lancement.vs.json* existant, ou s’il n’y en a pas, il créera un nouveau fichier avec un ensemble de paramètres de lancement minimaux. Tout d’abord, vous êtes donné un choix de quel type de session de débogé que vous voulez configurer. Pour déboguer un projet MinGw-w64, nous choisissons **le lancement C/CMD pour MinGW/Cygwin (gdb)**. Cela crée une configuration de lancement pour l’utilisation *de gdb.exe* avec quelques suppositions éclairées sur les valeurs par défaut. Une de ces `MINGW_PREFIX`valeurs par défaut est . Vous pouvez remplacer le chemin littéral (comme `MINGW_PREFIX` indiqué ci-dessous) ou vous pouvez définir une propriété dans *CppProperties.json*:

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

Pour commencer à débogage, choisissez l’exécutable dans le décrocheur, puis cliquez sur la flèche verte:

![Lancement de débbugger](media/launch-debugger-gdb.png)

Vous devriez voir le dialogue **Initializing Debugger,** puis une fenêtre de console externe qui est en cours d’exécution de votre programme.

Pour plus d’informations, voir [launch.vs.json schema reference](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Lancement d’autres exécutables

Vous pouvez définir les paramètres de lancement pour n’importe quel exécutant sur votre ordinateur. L’exemple suivant lance *7za* et spécifie `args` des arguments supplémentaires, en les ajoutant au tableau JSON :

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
