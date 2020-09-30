---
title: Configurer un projet CMake Linux dans Visual Studio
description: Comment configurer les paramètres de CMake Linux dans Visual Studio
ms.date: 08/08/2020
ms.openlocfilehash: 32c851791402b59c941ae088fa637d3d9953dd1b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504726"
---
# <a name="configure-a-linux-cmake-project-in-visual-studio"></a>Configurer un projet CMake Linux dans Visual Studio

::: moniker range="vs-2015"
La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur. Pour consulter la documentation de ces versions, définissez la liste déroulante **version** située au-dessus de la table des matières dans **Visual Studio 2017** ou **Visual Studio 2019**.
::: moniker-end

::: moniker range=">=vs-2017"
Cette rubrique explique comment ajouter une configuration Linux à un projet CMake qui cible soit un système Linux distant, soit un sous-système Windows pour Linux (WSL). Il poursuit la série qui a commencé par [créer un projet Linux cmake dans Visual Studio](cmake-linux-project.md). Si vous utilisez MSBuild, consultez [configurer un projet MSBuild Linux dans Visual Studio](configure-a-linux-project.md) .

## <a name="add-a-linux-configuration"></a>Ajouter une configuration Linux

Une configuration peut être utilisée pour cibler différentes plateformes (Windows, WSL, un système distant) avec le même code source. Une configuration est également utilisée pour définir vos compilateurs, passer des variables d’environnement et personnaliser le mode d’appel de CMake. L' *CMakeSettings.jssur* le fichier spécifie une partie ou l’ensemble des propriétés listées dans [personnaliser les paramètres cmake](../build/customize-cmake-settings.md), ainsi que des propriétés supplémentaires qui contrôlent les paramètres de génération sur l’ordinateur Linux distant.
::: moniker-end

::: moniker range="vs-2017"
Pour modifier les paramètres de cmake par défaut dans Visual Studio 2017, choisissez **cmake**  >  **modifier les paramètres de cmake**  >  **CMakeLists.txt** dans le menu principal. Ou cliquez avec le bouton droit sur *CMakeLists.txt* dans **Explorateur de solutions** puis choisissez **modifier les paramètres cmake**. Visual Studio crée ensuite un *CMakeSettings.jssur* le fichier dans le dossier racine de votre projet. Pour apporter des modifications, ouvrez le fichier et modifiez-le directement. Pour plus d’informations, consultez [personnaliser les paramètres cmake](../build/customize-cmake-settings.md).

La configuration par défaut pour Linux-Debug dans Visual Studio 2017 (et Visual Studio 2019 version 16,0) ressemble à ceci :

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
Pour modifier les paramètres de CMake par défaut dans Visual Studio 2019, dans la barre d’outils principale, ouvrez la liste déroulante **configuration** , puis choisissez **gérer les configurations**.

![CMake gérer les configurations](../build/media/vs2019-cmake-manage-configurations.png "Liste déroulante des configurations CMake")

Cette commande ouvre l' **éditeur de paramètres cmake**, que vous pouvez utiliser pour modifier la *CMakeSettings.jssur* le fichier dans le dossier racine de votre projet. Vous pouvez également ouvrir le fichier avec l’éditeur JSON en cliquant sur le bouton **modifier JSON** dans l’éditeur. Pour plus d’informations, consultez [Personnaliser les paramètres CMake](../build/customize-cmake-settings.md).

La configuration de débogage Linux par défaut dans Visual Studio 2019 version 16,1, et versions ultérieures, ressemble à ceci :

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

Dans Visual Studio 2019 version 16,6 ou ultérieure, le Ninja est le générateur par défaut pour les configurations ciblant un système distant ou WSL. Pour plus d’informations, consultez ce billet sur le blog de l' [équipe C++](https://devblogs.microsoft.com/cppblog/linux-development-with-visual-studio-first-class-support-for-gdbserver-improved-build-times-with-ninja-and-updates-to-the-connection-manager/).

::: moniker-end
::: moniker range=">=vs-2017"
Pour plus d’informations sur ces paramètres, consultez la [Référence de CMakeSettings.json](../build/cmakesettings-reference.md).

Quand vous effectuez une génération :

- Si vous ciblez un système distant, Visual Studio choisit le premier système distant dans la liste sous **Outils** > **options** > Gestionnaire de connexions **multiplateformes** > **Connection Manager** par défaut pour les cibles distantes.
- Si aucune connexion distante n’est trouvée, vous êtes invité à en créer une. Pour plus d’informations, consultez [Se connecter à un ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

## <a name="choose-a-linux-target"></a>Choisir une cible Linux

Quand vous ouvrez un dossier de projet CMake, Visual Studio analyse le fichier *CMakeLists.txt* et spécifie une cible Windows **x86-Debug**. Pour cibler un système Linux distant, vous devez modifier les paramètres du projet en fonction de votre compilateur Linux. Par exemple, si vous utilisez GCC sur Linux et que vous compilez avec les informations de débogage, vous avez choisi :  **Linux-GCC-Debug** ou **Linux-GCC-Release**.

Si vous spécifiez une cible Linux distante, votre source est copiée sur le système distant.

Une fois que vous avez sélectionné une cible, CMake s’exécute automatiquement sur le système Linux pour générer le cache CMake pour votre projet :

![Générer le cache CMake sur Linux](media/cmake-linux-1.png "Générer le cache CMake sur Linux")

::: moniker-end
::: moniker range="vs-2019"

### <a name="target-windows-subsystem-for-linux"></a>Sous-système Windows cible pour Linux

Si vous ciblez le sous-système Windows pour Linux (WSL), vous n’avez pas besoin d’ajouter une connexion à distance.

Pour cibler WSL, sélectionnez **gérer les configurations** dans la liste déroulante Configuration de la barre d’outils principale :

![CMake gérer les configurations](../build/media/vs2019-cmake-manage-configurations.png "Liste déroulante des configurations CMake")

La fenêtre **CMakeSettings.jssur** s’affiche.

![Ajouter une configuration](media/cmake-linux-configurations.png "Ajouter une configuration aux paramètres de CMake")

Appuyez sur **Ajouter une configuration** (bouton vert +), puis sélectionnez **Linux-GCC-Debug** ou **Linux-GCC-Release** si vous utilisez gcc. Utilisez les variantes Clang si vous utilisez l’ensemble d’outils Clang/LLVM.  Appuyez sur **Select** , puis sur **CTRL + S** pour enregistrer la configuration.

**Visual Studio 2019 version 16,1** Quand vous ciblez WSL, Visual Studio n’a pas besoin de copier les fichiers sources et de conserver deux copies synchrones de votre arborescence de génération, car le compilateur sur Linux a un accès direct à vos fichiers sources dans le système de fichiers Windows monté.
::: moniker-end
::: moniker range=">=vs-2017"

### <a name="intellisense"></a>IntelliSense

IntelliSense IntelliSense précis requiert l’accès aux en-têtes C++ référencés par vos fichiers sources C++. Visual Studio utilise automatiquement les en-têtes référencés par un projet CMake de Linux vers Windows pour fournir une expérience IntelliSense complète. Pour plus d’informations, consultez [IntelliSense pour les en-têtes distants](configure-a-linux-project.md#remote_intellisense).

### <a name="locale-setting"></a>Paramètres régionaux

Les paramètres de langue de Visual Studio ne sont pas propagés aux cibles Linux, car Visual Studio ne gère pas ou ne configure pas les packages installés. Les messages affichés dans la fenêtre sortie, tels que les erreurs de build, s’affichent à l’aide de la langue et des paramètres régionaux de la cible Linux. Vous devez configurer vos cibles Linux pour les paramètres régionaux souhaités.

## <a name="additional-settings"></a>Paramètres supplémentaires

Utilisez les paramètres suivants pour exécuter des commandes sur le système Linux avant et après la génération, et avant la génération de CMake. Les valeurs peuvent correspondre à n’importe quelle commande valide sur le système distant. La sortie est redirigée vers Visual Studio.

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

## <a name="next-steps"></a>Étapes suivantes

[Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md?toc=/cpp/linux/toc.json&bc=/cpp/_breadcrumb/toc.json)

## <a name="see-also"></a>Voir aussi

[Utilisation des propriétés de projet](../build/working-with-project-properties.md)<br/>
[Personnaliser les paramètres CMake](../build/customize-cmake-settings.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
