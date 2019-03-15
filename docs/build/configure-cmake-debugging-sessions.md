---
title: Configurer des sessions de débogage CMake dans Visual Studio
ms.date: 03/05/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 9a4dd009544a4590c336697ba2162eec45718869
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826079"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurer des sessions de débogage CMake

Toutes les cibles CMake exécutables figurent dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**. Pour démarrer une session de débogage, sélectionnez-en une et lancez le débogueur.

![Liste déroulante d’éléments de démarrage CMake](media/cmake-startup-item-dropdown.png "Liste déroulante d’éléments de démarrage CMake")

Vous pouvez également démarrer une session de débogage à partir des menus de CMake.

## <a name="customize-debugger-settings"></a>Personnaliser les paramètres du débogueur

Pour personnaliser les paramètres du débogueur pour toutes les cibles CMake exécutables dans votre projet, cliquez avec le bouton droit sur le fichier CMakeLists.txt et sélectionnez **Paramètres de débogage et de lancement**. Quand vous sélectionnez une cible CMake dans le sous-menu, un fichier appelé `launch.vs.json` est créé. Ce fichier est prérempli avec les informations de la cible CMake que vous avez sélectionnée et vous permet de spécifier des paramètres supplémentaires comme les arguments de programme ou le type de débogueur. Pour référencer une clé dans un fichier `CMakeSettings.json`, préfacez-la avec `cmake.` dans `launch.vs.json`. L’exemple suivant montre un fichier `launch.vs.json` simple qui intègre la valeur de la clé `remoteCopySources` dans le fichier `CMakeSettings.json` pour la configuration actuellement sélectionnée :

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Dès que vous enregistrez le fichier `launch.vs.json`, une entrée est créée dans la liste déroulante **Élément de démarrage** avec le nouveau nom. En modifiant le fichier `launch.vs.json`, vous pouvez créer autant de configurations de débogage que vous voulez pour n’importe quel nombre de cibles CMake.

## <a name="support-for-cmakesettings-variables"></a>Prise en charge des variables CMakeSettings

 `Launch.vs.json` prend en charge les variables déclarées dans `CMakeSettings.json` (voir ci-dessous) et applicables à la configuration actuellement sélectionnée. Ce fichier a également une clé nommée `currentDir`, qui définit le répertoire actuel de l’application de lancement :

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Quand vous exécutez l’application, la valeur de `currentDir` ressemble à

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```
## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)<br/>
[Se connecter à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Personnaliser les paramètres de génération CMake](customize-cmake-settings.md)<br/>
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)<br/>