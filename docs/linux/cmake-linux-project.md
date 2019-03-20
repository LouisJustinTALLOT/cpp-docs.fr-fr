---
title: Configurer un projet CMake Linux dans Visual Studio
description: Comment configurer un projet CMake Linux dans Visual Studio
ms.date: 11/01/2018
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 22de2f7a7b5374f781a032f5152610d7a97feb16
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57815864"
---
# <a name="configure-a-linux-cmake-project"></a>Configurer un projet CMake Linux

Quand vous ouvrez un dossier qui contient un projet CMake, Visual Studio utilise les métadonnées générées par CMake pour configurer IntelliSense et les builds automatiquement. Les paramètres locaux de débogage et de configuration sont stockés dans des fichiers JSON qui peuvent être partagés avec d’autres utilisateurs de Visual Studio. 

Visual Studio ne modifie ni les fichiers CMakeLists.txt ni le cache CMake initial. Les autres personnes travaillant sur le même projet peuvent ainsi continuer à utiliser leurs outils habituels.  

## <a name="before-you-begin"></a>Avant de commencer

Tout d’abord, assurez-vous que vous avez installé la charge de travail de **développement Linux en C++**, y compris le composant CMake. Consultez [Installer la charge de travail Linux C++ dans Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Pour une variante de CMake fournie par Microsoft, téléchargez les fichiers binaires prédéfinis les plus récents à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

Cette rubrique suppose que vous avez lu [CMake Tools pour Visual Studio](../build/cmake-projects-in-visual-studio.md). 

> [!NOTE]
> La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Pour une variante de CMake fournie par Microsoft, téléchargez les fichiers binaires prédéfinis les plus récents à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases). Dans Visual Studio 2019, les binaires prédéfinis peuvent être déployés automatiquement (voir [Télécharger des binaires CMake prédéfinis](#download-prebuilt-cmake-binaries)).

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

Par défaut, Visual Studio choisit le premier système distant de la liste sous **Outils** > **Options** > **Multiplateforme** > **Gestionnaire de connexions**. Si aucune connexion distante n’est trouvée, vous êtes invité à en créer une. Pour plus d’informations, consultez [Se connecter à un ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

Une fois que vous avez spécifié une cible Linux, votre source est copiée sur la machine Linux. Ensuite, CMake est exécuté sur la machine Linux pour générer le cache CMake de votre projet.

![Générer le cache CMake sur Linux](media/cmake-linux-1.png "Générer le cache CMake sur Linux")

**Visual Studio 2017 15.7 et versions ultérieures :**<br/>
Pour fournir la prise en charge des fonctionnalités IntelliSense pour les en-têtes distants, Visual Studio les copie automatiquement de la machine Linux vers un répertoire de votre machine Windows locale. Pour plus d’informations, consultez [IntelliSense pour les en-têtes distants](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Déboguer le projet

Pour déboguer votre code sur le système distant, définissez un point d’arrêt, sélectionnez la cible CMake comme élément de démarrage dans le menu de barre d’outils à côté des paramètres du projet, puis choisissez **&#x23f5; Démarrer** dans la barre d’outils ou appuyez sur F5.

Pour personnaliser les arguments de ligne de commande de votre programme, cliquez sur l’exécutable dans **Explorateur de solutions** et sélectionnez **Paramètres de débogage et de lancement**. Un fichier de configuration launch.vs.json contenant des informations sur votre programme s’ouvre ou est créé. Pour spécifier des arguments supplémentaires, ajoutez-les au tableau JSON `args`. Pour plus d’informations, consultez [Projets Dossier ouvert pour C++](../build/open-folder-projects-cpp.md) et [Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a>Configurer les paramètres CMake pour Linux

Dans un projet CMake Linux, le fichier CMakeSettings.json peut inclure toutes les propriétés listées dans [Personnaliser les paramètres CMake](../build/customize-cmake-settings.md) ainsi que des propriétés supplémentaires qui contrôlent les paramètres de build sur la machine Linux distante. Pour changer les paramètres CMake par défaut, choisissez **CMake | Changer les paramètres CMake | CMakeLists.txt** dans le menu principal, ou cliquez avec le bouton droit sur CMakeSettings.txt dans **l’Explorateur de solutions** et choisissez **Changer les paramètres CMake**. Visual Studio crée ensuite un fichier `CMakeSettings.json` dans votre dossier projet racine. Vous pouvez ouvrir ce fichier à l’aide de l’éditeur de **paramètres CMake**, ou le modifier directement. 

L’exemple suivant montre la configuration par défaut définie pour Linux-Debug sur la base de l’exemple de code précédent :

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
Le tableau suivant récapitule les paramètres  :

|Paramètre|Description|
|-----------|-----------------|
|`name`|Cette valeur peut être n’importe quelle valeur de votre choix.|
|`remoteMachineName`|Spécifie le système distant à cibler, s’il y a plusieurs systèmes distants disponibles. IntelliSense est activé pour ce champ afin de vous permettre de sélectionner le système approprié.|
|`remoteCMakeListsRoot`|Spécifie l’emplacement où vos sources de projet doivent être copiées sur le système distant.|
|`remoteBuildRoot`|Spécifie l’emplacement où la sortie de build doit être générée sur le système distant. Cette sortie est également copiée sur le système local, à l’emplacement spécifié par `buildRoot`.|
|`remoteInstallRoot` et `installRoot`| Similaires à `remoteBuildRoot` et `buildRoot`, sauf qu’ils sont utilisés dans le cas d’une installation de CMake.|
|`remoteCopySources`|Spécifie si vos sources locales sont copiées ou non sur la machine distante. Vous pouvez lui affecter la valeur false si vous avez beaucoup de fichiers et si vous synchronisez déjà les sources vous-même.|
|`remoteCopyOutputVerbosity`| Spécifie le niveau de détail de l’étape de copie, pour les besoins de diagnostic des erreurs.|
|`remoteCopySourcesConcurrentCopies`| Spécifie le nombre de processus générés pour effectuer la copie.|
|`remoteCopySourcesMethod`| La valeur peut être `rsync` ou `sftp`.|
|`remoteCopySourcesExclusionList`| Spécifie les fichiers qui ne doivent pas être copiés sur la machine distante.|
|`rsyncCommandArgs`|Contrôle la méthode rsync de copie.|
|`remoteCopyBuildOutput`| Spécifie si la sortie de build distante est copiée ou non dans votre dossier de build local.|

Vous pouvez spécifier ces paramètres facultatifs pour effectuer un contrôle plus précis :

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

Ces options vous permettent d’exécuter des commandes sur le système distant avant et après la build, et avant la génération CMake. Les valeurs peuvent correspondre à n’importe quelle commande valide sur le système distant. La sortie est redirigée vers Visual Studio.

## <a name="download-prebuilt-cmake-binaries"></a>Télécharger les fichiers binaires CMake prédéfinis

Votre distribution Linux peut avoir une version antérieure de CMake. La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Pour une variante de CMake fournie par Microsoft, téléchargez les fichiers binaires prédéfinis les plus récents à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

**Visual Studio 2019**<br/>
Si aucun fichier CMake valide n’est trouvé sur l’ordinateur distant, une barre d’informations apparaît : elle offre la possibilité de déployer automatiquement les binaires CMake prédéfinis. Les binaires seront installés dans `~/.vs/cmake`. Après le déploiement des binaires, le projet se régénère automatiquement. Notez que, si le fichier CMake spécifié par le champ `cmakeExecutable` dans `CMakeSettings.json` n’est pas valide (n’existe pas ou correspond à une version non prise en charge) et que des binaires prédéfinis sont présents, Visual Studio ignore `cmakeExecutable` et utilise les binaires prédéfinis.

## <a name="see-also"></a>Voir aussi

[Utilisation des propriétés de projet](../build/working-with-project-properties.md)<br/>
[Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Se connecter à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md)<br/>
[Personnaliser les paramètres CMake](../build/customize-cmake-settings.md)<br/>
[Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](../build/cmake-predefined-configuration-reference.md)<br/>
