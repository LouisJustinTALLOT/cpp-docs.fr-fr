---
title: Configurer un projet CMake Linux dans Visual Studio
description: Comment configurer un projet CMake Linux dans Visual Studio
ms.date: 07/20/2018
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 32d69e28c0991adc6117b7f9496eeb1022943ef2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585040"
---
# <a name="configure-a-linux-cmake-project"></a>Configurer un projet CMake Linux

**Visual Studio 2017 15.4 et versions ultérieures**<br/>
Quand vous installez la charge de travail Linux C++ pour Visual Studio, la prise en charge de CMake pour Linux est sélectionnée par défaut. Vous pouvez maintenant utiliser votre base de code CMake existante sans avoir à la convertir en projet Visual Studio. Si votre base de code est multiplateforme, vous pouvez cibler Windows et Linux à partir de Visual Studio.

Cette rubrique suppose que vous avez une connaissance de base de la prise en charge de CMake dans Visual Studio. Pour plus d’informations, consultez [Visual C++ Tools pour CMake](../ide/cmake-tools-for-visual-cpp.md). Pour plus d’informations sur la solution CMake proprement dite, consultez [Build, Test and Package Your Software With CMake](https://cmake.org/).

> [!NOTE]
> La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Pour une variante de CMake fournie par Microsoft, téléchargez les fichiers binaires prédéfinis les plus récents à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

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
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Choisir une cible Linux

Dès que le dossier est ouvert, Visual Studio analyse le fichier CMakeLists.txt et spécifie la cible Windows **x86-Debug**. Pour spécifier une cible Linux, remplacez les paramètres du projet par **Linux-Debug** ou **Linux-Release**.

Par défaut, Visual Studio choisit le premier système distant de la liste sous **Outils** > **Options** > **Multiplateforme** > **Gestionnaire de connexions**. Si aucune connexion distante n’est trouvée, vous êtes invité à en créer une.

Une fois que vous avez spécifié une cible Linux, votre source est copiée sur la machine Linux. Ensuite, CMake est exécuté sur la machine Linux pour générer le cache CMake de votre projet.

![Générer le cache CMake sur Linux](media/cmake-linux-1.png "Générer le cache CMake sur Linux")

**Visual Studio 2017 15.7 et versions ultérieures :**<br/>
Pour assurer la prise en charge IntelliSense des en-têtes distants, Visual Studio les copie automatiquement dans un répertoire de votre ordinateur Windows local. Pour plus d’informations, consultez [IntelliSense pour les en-têtes distants](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Déboguer le projet

Pour déboguer votre code sur le système distant, définissez un point d’arrêt, sélectionnez la cible CMake comme élément de démarrage dans le menu de barre d’outils à côté des paramètres du projet, puis choisissez **&#x23f5; Démarrer** dans la barre d’outils ou appuyez sur F5.

Pour personnaliser les arguments de ligne de commande de votre programme, cliquez sur l’exécutable dans **Explorateur de solutions** et sélectionnez **Paramètres de débogage et de lancement**. Un fichier de configuration launch.vs.json contenant des informations sur votre programme s’ouvre ou est créé. Pour spécifier des arguments supplémentaires, ajoutez-les au tableau JSON `args`. Pour plus d’informations, consultez [Open Folder projects in Visual C++](../ide/non-msbuild-projects.md).

## <a name="configure-cmake-settings-for-linux"></a>Configurer les paramètres CMake pour Linux

Pour changer les paramètres CMake par défaut, choisissez **CMake | Changer les paramètres CMake | CMakeLists.txt** dans le menu principal, ou cliquez avec le bouton droit sur CMakeSettings.txt dans **l’Explorateur de solutions** et choisissez **Changer les paramètres CMake**. Visual Studio crée ensuite un fichier dans votre dossier appelé `CMakeSettings.json`, qui contient les configurations par défaut affichées dans l’élément de menu des paramètres du projet. L’exemple suivant montre la configuration par défaut définie pour Linux-Debug sur la base de l’exemple de code précédent :

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

La valeur `name` spécifie un nom de votre choix. La valeur `remoteMachineName` spécifie le système distant à cibler, s’il y a plusieurs systèmes distants disponibles. IntelliSense est activé pour ce champ afin de vous permettre de sélectionner le système approprié. Le champ `remoteCMakeListsRoot` spécifie l’emplacement où vos sources de projet doivent être copiées sur le système distant. Le champ `remoteBuildRoot` spécifie l’emplacement où la sortie de la génération doit être copiée sur le système distant. Cette sortie est également copiée sur le système local, à l’emplacement spécifié par `buildRoot`. Les champs `remoteInstallRoot` et `installRoot` sont similaires à `remoteBuildRoot` et `buildRoot`. Toutefois, ils s’appliquent durant une installation de cmake. L’entrée `remoteCopySources` contrôle si vos sources locales sont copiées ou non sur la machine distante. Vous pouvez lui affecter la valeur false si vous avez beaucoup de fichiers et si vous synchronisez déjà les sources vous-même. La valeur `remoteCopyOutputVerbosity` contrôle le niveau de détail de l’étape de copie, au cas où vous auriez besoin de diagnostiquer les erreurs. L’entrée `remoteCopySourcesConcurrentCopies` contrôle le nombre de processus générés pour effectuer la copie. La valeur `remoteCopySourcesMethod` peut être rsync ou sftp. Le champ `remoteCopySourcesExclusionList` vous permet de contrôler ce qui est copié sur la machine distante. La valeur `rsyncCommandArgs` vous permet de contrôler la méthode de copie rsync. Le champ `remoteCopyBuildOutput` contrôle si la sortie de build distante est copiée ou non dans votre dossier de build local.

Il existe également des paramètres facultatifs qui vous permettent d’exercer un contrôle plus important :

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

Ces options vous permettent d’exécuter des commandes sur la boîte distante avant et après la build, et avant la génération CMake. Il peut s’agir de n’importe quelle commande valide sur la boîte distante. La sortie est redirigée vers Visual Studio.

## <a name="download-prebuilt-cmake-binaries"></a>Télécharger les fichiers binaires CMake prédéfinis

Votre distribution Linux peut avoir une version antérieure de CMake. La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Pour une variante de CMake fournie par Microsoft, téléchargez les fichiers binaires prédéfinis les plus récents à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

## <a name="see-also"></a>Voir aussi

[Utilisation des propriétés de projet](../ide/working-with-project-properties.md)<br/>
[Visual C++ Tools pour CMake](../ide/cmake-tools-for-visual-cpp.md)
