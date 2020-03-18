---
title: Créer et configurer un projet CMake Linux dans Visual Studio
description: Comment créer, configurer, modifier et compiler un projet CMake Linux dans Visual Studio
ms.date: 10/04/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 9c6a60162c2dbbab8e348b27d1987d7f1001bee0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419405"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Créer et configurer un projet CMake Linux

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range="vs-2019"

Pour créer un nouveau projet Linux CMake dans Visual Studio 2019 :

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Définissez le **Langage** sur **C++** et recherchez « CMake ». Choisissez ensuite **Suivant**. Entrez un **Nom** et un **Emplacement**, puis choisissez **Créer**.

Visual Studio crée un fichier CMakeLists.txt minimal avec uniquement le nom de l’exécutable et la version minimale de CMake requise. Vous pouvez modifier manuellement ce fichier à votre convenance ; Visual Studio ne remplacera jamais vos changements. Vous pouvez spécifier des arguments de ligne de commande et des variables d’environnement CMake en cliquant avec le bouton droit sur le fichier fichier CMakeLists. txt racine dans **Explorateur de solutions** et en choisissant **paramètres cmake pour Project**. Pour spécifier les options de débogage, cliquez avec le bouton droit sur le nœud du projet et choisissez **Paramètres de débogage et de lancement**.

::: moniker-end

Lorsque vous ouvrez un dossier qui contient un projet CMake existant, Visual Studio utilise des variables dans le cache CMake pour configurer IntelliSense et les builds automatiquement. Les paramètres locaux de débogage et de configuration sont stockés dans des fichiers JSON qui peuvent être partagés avec d’autres utilisateurs de Visual Studio.

Visual Studio ne modifie ni les fichiers CMakeLists.txt. Les autres personnes travaillant sur le même projet peuvent ainsi continuer à utiliser leurs outils habituels. Visual Studio régénère le cache lorsque vous enregistrez les modifications apportées à fichier CMakeLists. txt ou dans certains cas à CMakeSettings. JSON. Mais si vous utilisez une configuration de **Cache existant**, Visual Studio ne modifie pas le cache.

Pour obtenir des informations générales sur la prise en charge de CMake dans Visual Studio, consultez [Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md). Vous devez lire cet article avant de continuer.

## <a name="before-you-begin"></a>Avant de commencer

Tout d’abord, assurez-vous que vous avez installé la charge de travail de **développement Linux en C++** , y compris le composant CMake. Consultez [Installer la charge de travail Linux C++ dans Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

Sur le système Linux, vérifiez que les éléments suivants sont installés : 

- gcc
- gdb
- rsync
- zip 

::: moniker range="vs-2019"

Pour les projets CMake, la prise en charge de Linux nécessite qu’une version récente de CMake soit installée sur l’ordinateur cible. Souvent, la version proposée par le gestionnaire de package par défaut d’une distribution n’est pas assez récente pour prendre en charge toutes les fonctionnalités requises par Visual Studio. Visual Studio 2019 détecte si une version récente de CMake est installée sur le système Linux. Si aucune n’est trouvée, Visual Studio affiche une barre d’informations en haut du volet de l’éditeur qui vous propose de l’installer pour vous à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Dans Visual Studio 2019, la version 3.14 ou ultérieure est recommandée.

::: moniker-end

::: moniker range="vs-2017"

La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Pour une variante de CMake fournie par Microsoft, téléchargez les fichiers binaires prédéfinis les plus récents à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

Les binaires seront installés dans `~/.vs/cmake`. Après le déploiement des binaires, le projet se régénère automatiquement. Notez que, si le fichier CMake spécifié par le champ `cmakeExecutable` dans `CMakeSettings.json` n’est pas valide (n’existe pas ou correspond à une version non prise en charge) et que des binaires prédéfinis sont présents, Visual Studio ignore `cmakeExecutable` et utilise les binaires prédéfinis.

:::moniker-end

## <a name="open-a-folder"></a>Ouvrir un dossier

Pour commencer, choisissez **Fichier** > **Ouvrir** > **Dossier** dans le menu principal ou tapez `devenv.exe <foldername>` en ligne de commande. Le dossier que vous ouvrez doit contenir un fichier CMakeLists.txt, ainsi que votre code source.
L’exemple suivant montre un fichier CMakeLists.txt et un fichier .cpp simples :

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists.txt :

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Choisir une cible Linux

Dès que le dossier est ouvert, Visual Studio analyse le fichier CMakeLists.txt et spécifie la cible Windows **x86-Debug**. Pour cibler un système Linux distant, remplacez les paramètres du projet par **Linux-Debug** ou **Linux-Release**. (Consultez [Configurer les paramètres CMake pour Linux](#configure_cmake_linux) ci-dessous.)

::: moniker range="vs-2019"

Pour cibler le sous-système Windows pour Linux, cliquez sur **Gérer les configurations** dans la liste déroulante de configurations dans la barre d’outils principale. Appuyez ensuite sur le bouton **Ajouter une configuration** et choisissez **WSL-Debug** ou **WSL-Release** si vous utilisez GCC, ou les variantes Clang, si vous utilisez l’ensemble d’outils Clang/LLVM. 

**Visual Studio 2019 version 16.1** Quand vous ciblez WSL, aucune copie de sources ou d’en-têtes n’est nécessaire, car le compilateur sur Linux a un accès direct au système de fichiers Windows où se trouvent vos fichiers source. (Dans Windows version 1903 et versions ultérieures, les applications Windows peuvent aussi accéder aux fichiers d’en-tête Linux directement, mais Visual Studio ne tire pas encore parti de cette fonctionnalité).

::: moniker-end

Pour les cibles distantes, Visual Studio choisit par défaut le premier système distant de la liste sous **Outils** > **Options** > **Multiplateforme** > **Gestionnaire de connexions**. Si aucune connexion distante n’est trouvée, vous êtes invité à en créer une. Pour plus d’informations, consultez [Se connecter à un ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

Si vous spécifiez une cible Linux distante, votre source est copiée sur le système distant.

Une fois que vous sélectionnez une cible, CMake s’exécute automatiquement sur le système Linux afin de générer le cache CMake pour votre projet. 

![Générer le cache CMake sur Linux](media/cmake-linux-1.png "Générer le cache CMake sur Linux")

Pour fournir la prise en charge des fonctionnalités IntelliSense pour les en-têtes sur les systèmes Linux distants, Visual Studio les copie automatiquement de la machine Linux vers un répertoire de votre machine Windows locale. Pour plus d’informations, consultez [IntelliSense pour les en-têtes distants](configure-a-linux-project.md#remote_intellisense).

## <a name="debug_cmake_project"></a> Déboguer le projet CMake

Pour déboguer votre code sur le système cible de débogage spécifié, définissez un point d’arrêt, sélectionnez la cible CMake comme élément de démarrage dans le menu de barre d’outils à côté des paramètres du projet, puis choisissez **&#x23f5; Démarrer** dans la barre d’outils ou appuyez sur F5.

Pour personnaliser les arguments de ligne de commande de votre programme, appuyez sur le bouton **Changer les cibles** en haut de **l’Explorateur de solutions**, puis choisissez **Vue des cibles**. Puis cliquez avec le bouton droit sur la cible et sélectionnez **Paramètres de débogage et de lancement**. Un fichier de configuration launch.vs.json contenant des informations sur votre programme s’ouvre ou est créé. Pour spécifier l’emplacement des fichiers sources, ajoutez une propriété **sourceFileMap** au fichier, comme illustré dans cet exemple :

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Pour spécifier des arguments supplémentaires, ajoutez-les au tableau JSON `args`. Pour plus d’informations, consultez [Projets Dossier ouvert pour C++](../build/open-folder-projects-cpp.md) et [Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md).

## <a name="configure_cmake_linux"></a> Configurer les paramètres CMake pour Linux

Dans un projet CMake Linux, le fichier CMakeSettings.json peut inclure toutes les propriétés listées dans [Personnaliser les paramètres CMake](../build/customize-cmake-settings.md) ainsi que des propriétés supplémentaires qui contrôlent les paramètres de build sur la machine Linux distante. 

::: moniker range="vs-2019"

Pour changer les paramètres CMake par défaut dans Visual Studio 2019, dans la barre d’outils principale, ouvrez la liste déroulante **Configuration**, puis choisissez **Gérer les configurations**. 

![CMake gérer les configurations](../build/media/vs2019-cmake-manage-configurations.png "Liste déroulante des configurations CMake")

L’**éditeur de paramètres CMake** apparaît et vous permet de modifier le fichier `CMakeSettings.json` situé dans le dossier projet racine. Vous pouvez aussi ouvrir le fichier directement en cliquant sur le bouton **Modifier JSON** dans l’éditeur. Pour plus d’informations, consultez [Personnaliser les paramètres CMake](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Pour changer les paramètres CMake par défaut dans Visual Studio 2017, choisissez **CMake | Changer les paramètres CMake | CMakeLists.txt** dans le menu principal, ou cliquez avec le bouton droit sur CMakeSettings.txt dans l’**Explorateur de solutions**, puis choisissez **Changer les paramètres CMake**. Visual Studio crée ensuite un fichier `CMakeSettings.json` dans votre dossier projet racine. Vous pouvez ouvrir ce fichier à l’aide de l’éditeur de **paramètres CMake**, ou le modifier directement. Pour plus d’informations, consultez [Personnaliser les paramètres CMake](../build/customize-cmake-settings.md).

L’exemple suivant montre la configuration par défaut définie pour Linux-Debug dans Visual Studio 2017 (et Visual Studio 2019 version 16.0) sur la base de l’exemple de code précédent :

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range="vs-2019"

La configuration de débogage de Linux par défaut dans Visual Studio 2019 16.1 et versions ultérieures est illustrée ici :

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```
::: moniker-end

Pour plus d’informations sur ces paramètres, consultez la [Référence de CMakeSettings.json](../build/cmakesettings-reference.md).


## <a name="optional-settings"></a>Paramètres facultatifs

Vous pouvez utiliser les paramètres facultatifs suivants pour plus de contrôle :

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Ces options vous permettent d’exécuter des commandes sur le système Linux avant et après la build, et avant la génération CMake. Les valeurs peuvent correspondre à n’importe quelle commande valide sur le système distant. La sortie est redirigée vers Visual Studio.



## <a name="see-also"></a>Voir aussi

[Utilisation des propriétés de projet](../build/working-with-project-properties.md)<br/>
[Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Se connecter à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md)<br/>
[Personnaliser les paramètres CMake](../build/customize-cmake-settings.md)<br/>
[Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](../build/cmake-predefined-configuration-reference.md)<br/>
