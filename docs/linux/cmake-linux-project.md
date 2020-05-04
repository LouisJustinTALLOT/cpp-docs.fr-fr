---
title: Créer et configurer un projet CMake Linux dans Visual Studio
description: Comment créer, configurer, modifier et compiler un projet CMake Linux dans Visual Studio
ms.date: 05/03/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: c12e32801c992f6ba3675327b9ae537890202a4c
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765758"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Créer et configurer un projet CMake Linux

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="before-you-begin"></a>Avant de commencer

Tout d’abord, assurez-vous que vous avez installé la charge de travail de **développement Linux en C++**, y compris le composant CMake. Consultez [Installer la charge de travail Linux C++ dans Visual Studio](download-install-and-setup-the-linux-development-workload.md).

Sur le système Linux, vérifiez que les éléments suivants sont installés :

- gcc
- gdb
- rsync
- zip
- Ninja-Build

::: moniker-end

::: moniker range="vs-2019"

La prise en charge de Linux pour les projets CMake nécessite que l’ordinateur cible dispose d’une version récente de CMake. Souvent, la version offerte par le gestionnaire de package par défaut d’une distribution n’est pas assez récente pour prendre en charge toutes les fonctionnalités requises par Visual Studio. Visual Studio 2019 détecte si une version récente de CMake est installée sur le système Linux. Si aucune valeur n’est trouvée, Visual Studio affiche une barre d’informations en haut du volet de l’éditeur. Il propose d’installer CMake pour vous à [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)partir de.

La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Dans Visual Studio 2019, la version 3.14 ou ultérieure est recommandée.

::: moniker-end

::: moniker range="vs-2017"

La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Pour une variante CMake fournie par Microsoft, téléchargez les derniers binaires prégénérés [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)à l’adresse.

Les fichiers binaires sont installés `~/.vs/cmake`dans. Une fois les fichiers binaires déployés, votre projet régénère automatiquement. Si le CMake spécifié par le `cmakeExecutable` champ dans *CMakeSettings. JSON* n’est pas valide (il n’existe pas ou s’il s’agit d’une version non prise en charge) et que les fichiers binaires `cmakeExecutable` prédéfinis sont présents, Visual Studio ignore et utilise les binaires prédéfinis.

:::moniker-end

::: moniker range="vs-2019"

## <a name="create-a-new-linux-cmake-project"></a>Créer un projet CMake Linux

Pour créer un nouveau projet Linux CMake dans Visual Studio 2019 :

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Définissez le **Langage** sur **C++** et recherchez « CMake ». Choisissez ensuite **Suivant**. Entrez un **Nom** et un **Emplacement**, puis choisissez **Créer**.

Visual Studio crée un fichier *fichier CMakeLists. txt* minimal avec uniquement le nom de l’exécutable et la version cmake minimale requise. Vous pouvez modifier manuellement ce fichier à votre convenance ; Visual Studio ne remplacera jamais vos changements. Vous pouvez spécifier des arguments de ligne de commande et des variables d’environnement CMake dans ce fichier. Cliquez avec le bouton droit sur le fichier *fichier CMakeLists. txt* racine dans **Explorateur de solutions** et choisissez **paramètres cmake pour le projet**. Pour spécifier les options de débogage, cliquez avec le bouton droit sur le nœud du projet et choisissez **Paramètres de débogage et de lancement**.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="open-a-cmake-project-folder"></a>Ouvrir un dossier de projet CMake

Lorsque vous ouvrez un dossier qui contient un projet CMake existant, Visual Studio utilise des variables dans le cache CMake pour configurer automatiquement IntelliSense et les builds. Les paramètres de configuration locale et de débogage sont stockés dans des fichiers JSON. Vous pouvez éventuellement partager ces fichiers avec d’autres personnes qui utilisent Visual Studio.

Visual Studio ne modifie pas les fichiers *fichier CMakeLists. txt* . Elle est laissée seule afin que d’autres personnes travaillant sur le même projet puissent continuer à utiliser leurs outils existants. Visual Studio régénère le cache lorsque vous enregistrez les modifications apportées à *fichier CMakeLists. txt* ou dans certains cas à *CMakeSettings. JSON*. Toutefois, si vous utilisez une configuration de **cache existante** , Visual Studio ne modifie pas le cache.

Pour obtenir des informations générales sur la prise en charge de CMake dans Visual Studio, consultez [Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md). Vous devez lire cet article avant de continuer.

Pour commencer, choisissez **fichier** > **ouvrir** > le**dossier** dans le menu principal ou tapez `devenv.exe <foldername>` dans une fenêtre d’invite de [commandes développeur](../build/building-on-the-command-line.md) . Le dossier que vous ouvrez doit contenir un fichier *fichier CMakeLists. txt* , ainsi que votre code source.

L’exemple suivant montre un fichier *fichier CMakeLists. txt* et un fichier. cpp simples :

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*Fichier CMakeLists. txt*:

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Choisir une cible Linux

Dès que vous ouvrez le dossier, Visual Studio analyse le fichier *fichier CMakeLists. txt* et spécifie une cible Windows **x86-Debug**. Pour cibler un système Linux distant, remplacez les paramètres du projet par **Linux-Debug** ou **Linux-Release**. (Consultez [Configurer les paramètres CMake pour Linux](#configure_cmake_linux) ci-dessous.)

::: moniker-end

::: moniker range="vs-2019"

Pour cibler le sous-système Windows pour Linux, cliquez sur **gérer les configurations** dans la liste déroulante Configuration de la barre d’outils principale. Appuyez ensuite sur le bouton **Ajouter une configuration** et sélectionnez **WSL-Debug** ou **WSL-Release** si vous utilisez gcc. Utilisez les variantes Clang si vous utilisez l’ensemble d’outils Clang/LLVM.

**Visual Studio 2019 version 16,1** Quand vous ciblez WSL, aucune copie de sources ou d’en-têtes n’est nécessaire. Cela est dû au fait que le compilateur sur Linux a un accès direct à vos fichiers sources dans le système de fichiers Windows. (Dans Windows 10 version 1903 et versions ultérieures, les applications Windows peuvent également accéder directement aux fichiers d’en-tête Linux. Visual Studio ne tire pas encore parti de cette fonctionnalité.)

::: moniker-end

::: moniker range=">=vs-2017"

Visual Studio choisit le premier système distant dans la liste sous **Outils** > **options** > **Gestionnaire de connexions** **multiplateformes** > par défaut pour les cibles distantes. Si aucune connexion distante n’est trouvée, vous êtes invité à en créer une. Pour plus d’informations, consultez [Se connecter à un ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

Si vous spécifiez une cible Linux distante, votre source est copiée sur le système distant.

Une fois que vous sélectionnez une cible, CMake s’exécute automatiquement sur le système Linux afin de générer le cache CMake pour votre projet.

![Générer le cache CMake sur Linux](media/cmake-linux-1.png "Générer le cache CMake sur Linux")

Pour fournir la prise en charge des fonctionnalités IntelliSense pour les en-têtes sur les systèmes Linux distants, Visual Studio les copie automatiquement de la machine Linux vers un répertoire de votre machine Windows locale. Pour plus d’informations, consultez [IntelliSense pour les en-têtes distants](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-cmake-project"></a><a name="debug_cmake_project"></a> Déboguer le projet CMake

Pour déboguer votre code sur le système cible spécifié, définissez un point d’arrêt. Sélectionnez la cible CMake comme élément de démarrage dans le menu de la barre d’outils en regard du paramètre projet. Choisissez ensuite **&#x23f5; démarrer** dans la barre d’outils, ou appuyez sur **F5**.

Pour personnaliser les arguments de ligne de commande de votre programme, appuyez sur le bouton **commutateur des cibles** en haut de **Explorateur de solutions** puis choisissez **affichage des cibles**. Puis cliquez avec le bouton droit sur la cible et sélectionnez **Paramètres de débogage et de lancement**. Cette commande ouvre ou crée un fichier de configuration *Launch. vs. JSON* qui contient des informations sur votre programme. Pour spécifier l’emplacement des fichiers sources, ajoutez une propriété **sourceFileMap** au fichier, comme illustré dans cet exemple :

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Pour spécifier des arguments supplémentaires, ajoutez-les au tableau JSON `args`. Pour plus d’informations, consultez [Projets Dossier ouvert pour C++](../build/open-folder-projects-cpp.md) et [Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a><a name="configure_cmake_linux"></a>Configurer les paramètres CMake pour Linux

Un fichier *CMakeSettings. JSON* dans un projet Linux cmake peut spécifier toutes les propriétés énumérées dans [personnaliser les paramètres du cmake](../build/customize-cmake-settings.md), ainsi que des propriétés supplémentaires qui contrôlent les paramètres de génération sur l’ordinateur Linux distant.

::: moniker-end

::: moniker range="vs-2019"

Pour modifier les paramètres de CMake par défaut dans Visual Studio 2019, dans la barre d’outils principale, ouvrez la liste déroulante **configuration** , puis choisissez **gérer les configurations**.

![CMake gérer les configurations](../build/media/vs2019-cmake-manage-configurations.png "Liste déroulante des configurations CMake")

Cette commande affiche l' **éditeur de paramètres cmake**, que vous pouvez utiliser pour modifier le fichier *CMakeSettings. JSON* dans le dossier racine de votre projet. Vous pouvez aussi ouvrir le fichier directement en cliquant sur le bouton **Modifier JSON** dans l’éditeur. Pour plus d’informations, consultez [Personnaliser les paramètres CMake](../build/customize-cmake-settings.md).

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

::: moniker range="vs-2017"

Pour modifier les paramètres de cmake par défaut dans Visual Studio 2017, choisissez **cmake** > **modifier les paramètres** > cmake**fichier CMakeLists. txt** dans le menu principal. Ou cliquez avec le bouton droit sur *CMakeSettings. txt* dans **Explorateur de solutions** , puis choisissez **modifier les paramètres cmake**. Visual Studio crée ensuite un nouveau fichier *CMakeSettings. JSON* dans le dossier racine de votre projet. Vous pouvez ouvrir ce fichier à l’aide de l’éditeur de **paramètres CMake**, ou le modifier directement. Pour plus d’informations, consultez [personnaliser les paramètres cmake](../build/customize-cmake-settings.md).

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

::: moniker range=">=vs-2017"

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
[Informations de référence sur la configuration prédéfinie de CMake](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
