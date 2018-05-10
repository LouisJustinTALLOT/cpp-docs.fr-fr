---
title: Configurer un projet CMake Linux dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 10/25/2107
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 43d29513b41cc89f7d4b6ba4e33365dfa60a761a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="configure-a-linux-cmake-project"></a>Configurer un projet CMake Linux
  
**Visual Studio 2017 version 15.4** Quand vous installez la charge de travail Linux C++, la prise en charge de CMake pour Linux est sélectionnée par défaut. Vous pouvez maintenant utiliser votre base de code CMake existante sans avoir à la convertir en projet Visual Studio. Si votre base de code est multiplateforme, vous pouvez cibler Windows et Linux à partir de Visual Studio. 

Cette rubrique suppose que vous avez une connaissance de base de la prise en charge de CMake dans Visual Studio. Pour plus d’informations, consultez [Visual C++ Tools pour CMake](../ide/cmake-tools-for-visual-cpp.md). Pour plus d’informations sur la solution CMake proprement dite, consultez [Build, Test and Package Your Software With CMake](https://cmake.org/).

> [!NOTE] 
> La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Si votre gestionnaire de package fournit une version antérieure de CMake, vous pouvez contourner le problème en générant CMake 3.8 à partir de la source.



## <a name="open-a-folder"></a>Ouvrir un dossier
Pour commencer, choisissez **Fichier | Ouvrir | Dossier** dans le menu principal ou tapez `devenv.exe <foldername>` dans la ligne de commande. Le dossier que vous ouvrez doit contenir un fichier CMakeLists.txt, ainsi que votre code source.
L’exemple suivant montre un fichier CMakeLists.txt et un fichier .cpp simples :

```cpp
// Hello.cpp

#include <iostream>;
 
int main(int argc, char* argv[])
{
    std::cout << "Hello" << std::endl;
}
```

CMakeLists.txt : 
```cmd
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Choisir une cible Linux
Une fois que vous avez ouvert le dossier, Visual Studio analyse le fichier CMakeLists.txt et spécifie une cible Windows de x86-Debug. Pour spécifier une cible Linux, remplacez les paramètres du projet par Linux-Debug ou Linux-Release.

Par défaut, Visual Studio choisit le premier système distant dans la liste (sous **Outils | Options | Multiplateforme | Gestionnaire de connexions**). Si aucune connexion distante n’est trouvée, vous êtes invité à en créer une.

Une fois que vous avez spécifié une cible Linux, votre source est copiée sur la machine Linux. Ensuite, CMake est exécuté sur la machine Linux pour générer le cache CMake de votre projet.  

![Générer le cache CMake sur Linux](media/cmake-linux-1.png "Générer le cache CMake sur Linux")  

## <a name="debug-the-project"></a>Déboguer le projet  
Pour déboguer votre code sur le système distant, définissez un point d’arrêt, sélectionnez la cible CMake comme élément de démarrage du menu de barre d’outils à côté des paramètres du projet, puis cliquez sur Exécuter (ou appuyez sur F5).

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
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```
La valeur `name` spécifie un nom de votre choix. La valeur `remoteMachineName` spécifie le système distant à cibler, s’il y a plusieurs systèmes distants disponibles. IntelliSense est activé pour ce champ afin de vous permettre de sélectionner le système approprié. Le champ `remoteCMakeListsRoot` spécifie l’emplacement où vos sources de projet doivent être copiées sur le système distant. Le champ `remoteBuildRoot` spécifie l’emplacement où la sortie de la génération doit être copiée sur le système distant. Cette sortie est également copiée sur le système local, à l’emplacement spécifié par `buildRoot`.

## <a name="building-a-supported-cmake-release-from-source"></a>Génération d’une version de CMake prise en charge à partir de la source
Votre machine Linux doit avoir la version 3.8 de CMake au minimum, mais également prendre en charge le mode serveur. Pour vérifier la version, exécutez la commande suivante :

```cmd
cmake --version
```

Pour vérifier que le mode serveur est activé, exécutez cette commande :

```cmd
cmake -E capabilities
```

Dans la sortie, recherchez « serverMode:true ». Notez que même lorsque vous compilez un projet CMake à partir de la source, comme cela est décrit ci-dessous, vous devez vérifier les fonctionnalités à la fin de l’opération. En effet, votre système Linux peut avoir des limitations qui empêchent l’activation du mode serveur.

Pour préparer la génération à partir de la source dans l’interpréteur de commandes de votre système Linux, vérifiez que votre gestionnaire de package est à jour et que git et cmake sont disponibles. Tout d’abord, clonez les sources CMake à partir du référentiel que nous utilisons pour la prise en charge de CMake dans Visual Studio :

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Microsoft/CMake.git
cd CMake
```

Ensuite, exécutez les commandes suivantes :

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

Les commandes ci-dessus génèrent et installent la version actuelle de CMake dans /usr/local/bin. Exécutez cette commande pour vérifier que la version utilisée est la version 3.8 ou une version ultérieure et que le serveur mode est activé :

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>Voir aussi
[Utilisation des propriétés de projet](../ide/working-with-project-properties.md)  
[Visual C++ Tools pour CMake](../ide/cmake-tools-for-visual-cpp.md)
