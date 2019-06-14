---
title: Prise en charge de la fonctionnalité Dossier ouvert pour les systèmes de génération C++ dans Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 8856a5b1782c75c5a59dfdc93a8203627059ea12
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042723"
---
# <a name="open-folder-projects-for-c"></a>Projets Dossier ouvert pour C++

Dans Visual Studio 2017 et ultérieur, la fonctionnalité « Ouvrir un dossier » vous permet d’ouvrir un dossier de fichiers sources et de commencer immédiatement à coder en bénéficiant des avantages suivants : IntelliSense, navigation, refactorisation, débogage, etc. Aucun fichier .sln ou .vcxproj n’est chargé. Si nécessaire, vous pouvez spécifier des tâches personnalisées ou générer et lancer des paramètres par le biais de fichiers .json simples. Pour des informations générales sur la fonctionnalité Dossier ouvert, consultez [Développer du code dans Visual Studio sans projets ni solutions](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

CMake est intégré dans l’IDE Visual Studio en tant que composant de la C++ charge de travail de bureau. Pour plus d’informations, consultez [Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md). Pour tout autre système de génération, vous pouvez utiliser la fonctionnalité Dossier ouvert. Cette dernière dissocie efficacement l’éditeur de code, le débogueur et les analyseurs du système de génération et de l’ensemble d’outils du compilateur. Vous pouvez utiliser l’éditeur de code C++ avec ses riches fonctionnalités IntelliSense, les analyseurs de code et le débogueur de Visual Studio avec n’importe quel système de génération, notamment CMake, Ninja, QMake (pour des projets Qt), gyp, SCons, Gradle, Buck, make, etc. Il fonctionne même avec un seul fichier ou une collection libre de fichiers sans aucun système de génération.

Pour utiliser Ouvrir un dossier, sélectionnez **Fichier | Ouvrir | Dossier** à partir du menu principal ou appuyez sur **Ctrl + Maj + Alt + O**. L’Explorateur de solutions affiche immédiatement tous les fichiers dans le dossier. Vous pouvez cliquer sur n’importe quel fichier pour le modifier. En arrière-plan, Visual Studio démarre l’indexation des fichiers pour activer les fonctionnalités IntelliSense, de navigation et de refactorisation. Au fil des modifications, créations, déplacements et suppressions de fichiers, Visual Studio effectue automatiquement le suivi des modifications et met à jour en permanence son index IntelliSense. 

## <a name="qmake-projects-that-target-the-qt-framework"></a>Projets QMake qui ciblent le framework Qt

Vous pouvez utiliser CMake pour générer des projets de Qt, ou vous pouvez utiliser la [Qt Visual Studio Extension](https://download.qt.io/development_releases/vsaddin/) pour Visual Studio 2015 ou Visual Studio 2017.

## <a name="gyp-cons-scons-buck-etc"></a>gyp, Cons, SCons, Buck, etc.

Quel que soit le système de génération que vous utilisez dans Visual Studio, vous pouvez tirer parti des avantages de l’IDE et du débogueur C++. Quand vous ouvrez le dossier racine de votre projet, l’éditeur de code C++ utilise l’heuristique pour indexer les fichiers sources pour IntelliSense et la navigation. Vous pouvez fournir des indications sur la structure de votre code en modifiant le fichier CppProperties.json. De la même façon, vous pouvez configurer et appeler votre programme de génération en modifiant le fichier launch.vs.json.

## <a name="configuring-open-folder-projects"></a>Configuration de projets Ouvrir un dossier

Les trois fichiers JSON suivants vous permettent de personnaliser un projet Ouvrir un dossier :

| | |
|-|-|
|CppProperties.json|Spécifiez les informations de configuration personnalisées pour la navigation. Si nécessaire, créez ce fichier dans votre dossier de projet racine. (Non utilisé dans les projets CMake.)|
|tasks.vs.json|Spécifiez les commandes de génération personnalisée et les commutateurs de compilation. Accessible via l’option **Configurer les tâches** du menu contextuel de l’**Explorateur de solutions**.|
|launch.vs.json|Spécifiez des arguments de ligne de commande pour le débogueur. Accessible via l’option **Paramètres de débogage et de lancement** du menu contextuel de l’**Explorateur de solutions**.|

### <a name="configure-intellisense-and-browsing-hints-with-cpppropertiesjson"></a>Configurer IntelliSense et parcourir les conseils avec CppProperties.json

Le comportement d’IntelliSense et de la navigation varie en partie selon la configuration de build active, qui définit les chemins #include, les commutateurs du compilateur et d’autres paramètres. Par défaut, Visual Studio fournit les configurations Debug et Release. Les projets CMake utilisent le fichier CMakeSettings.json et les fichiers CMakeLists.txt à cet effet. Dans les autres types de projets Dossier ouvert, vous devrez peut-être créer une configuration personnalisée pour permettre aux fonctionnalités IntelliSense et de navigation de comprendre parfaitement votre code. Pour définir une nouvelle configuration, créez un fichier appelé CppProperties.json dans le dossier racine. Voici un exemple :

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "windows-msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
Pour plus d’informations, consultez [Informations de référence sur le schéma CppProperties](cppproperties-schema-reference.md).

### <a name="define-build-tasks-with-tasksvsjson"></a>Définir des tâches de génération avec tasks.vs.json

Vous pouvez automatiser les scripts de génération ou d’autres opérations externes sur les fichiers de votre espace de travail actuel en les exécutant comme des tâches directement dans l’IDE. Vous pouvez configurer une nouvelle tâche en cliquant sur un fichier ou dossier puis en sélectionnant **Configurer les tâches**.

![Ouvrir un dossier, Configurer les tâches](media/open-folder-config-tasks.png)

Cela crée (ou en ouvre) le **tasks.vs.json** fichier dans le dossier .vs, ce qui crée de Visual Studio dans votre dossier projet racine. Vous pouvez définir une tâche arbitraire dans ce fichier, puis l’appeler à partir du menu contextuel de **l’Explorateur de solutions**. L’exemple suivant montre un fichier tasks.vs.json qui définit une tâche unique. `taskName` définit le nom qui apparaît dans le menu contextuel. `appliesTo` définit les fichiers sur lesquels la commande peut être exécutée. La propriété `command` fait référence à la variable d’environnement COMSPEC qui identifie le chemin de la console (cmd.exe sur Windows). Vous pouvez également référencer des variables d’environnement déclarées dans CppProperties.json ou CMakeSettings.json. La propriété `args` spécifie la ligne de commande à appeler. La macro `${file}` extrait le fichier sélectionné dans **l’Explorateur de solutions**. L’exemple suivant affiche le nom du fichier .cpp actuellement sélectionné.

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

Pour plus d’informations, consultez [Informations de référence sur le schéma Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurer les paramètres de débogage avec launch.vs.json

Pour personnaliser les arguments de ligne de commande de votre programme, cliquez sur l’exécutable dans **Explorateur de solutions** et sélectionnez **Paramètres de débogage et de lancement**. Ceci ouvrira une existante **launch.vs.json** fichier, ou si aucune n’existe, il créera un nouveau fichier prérempli avec les informations sur le programme que vous avez sélectionné.

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
