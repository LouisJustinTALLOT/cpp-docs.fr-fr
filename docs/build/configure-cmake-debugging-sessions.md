---
title: Configurer des sessions de débogage CMake dans Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 41f53c0c3ea46a8a1aa11215968aaee6c13c2dea
ms.sourcegitcommit: e33126222c418daf977533ea9e2819d99e0d7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72534104"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurer des sessions de débogage CMake

Toutes les cibles CMake exécutables figurent dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**. Pour démarrer une session de débogage, sélectionnez-en une et lancez le débogueur.

![Liste déroulante d’élément de démarrage CMake](media/cmake-startup-item-dropdown.png "Liste déroulante d’élément de démarrage CMake")

Vous pouvez également démarrer une session de débogage à partir de Explorateur de solutions. Tout d’abord, basculez vers la **vue cibles cmake** dans la fenêtre **Explorateur de solutions** .

![Bouton d’affichage des cibles CMake](media/cmake-targets-view.png  "Élément de menu Affichage des cibles CMake")

Ensuite, cliquez avec le bouton droit sur n’importe quel exécutable et sélectionnez Paramètres de **débogage ou** de débogage **et de lancement**. Le **débogage** démarre automatiquement le débogage de la cible sélectionnée, en fonction de votre configuration active. Les **paramètres de débogage et de lancement** ouvrent le fichier *Launch. vs. JSON* et ajoute une nouvelle configuration de débogage pour la cible sélectionnée.

## <a name="customize-debugger-settings"></a>Personnaliser les paramètres du débogueur

Pour personnaliser les paramètres du débogueur pour toutes les cibles CMake exécutables dans votre projet, cliquez avec le bouton droit sur le fichier CMakeLists.txt et sélectionnez **Paramètres de débogage et de lancement**. (Ou sélectionnez une cible dans la **vue cibles** dans **Explorateur de solutions**.) Lorsque vous sélectionnez une cible de CMake dans le sous-menu, un fichier nommé **Launch. vs. JSON** est créé. Ce fichier est prérempli avec les informations de la cible CMake que vous avez sélectionnée et vous permet de spécifier des paramètres supplémentaires comme les arguments de programme ou le type de débogueur. Pour faire référence à une clé dans un fichier **CMakeSettings. JSON** , faites-la précéder `cmake.` dans **Launch. vs. JSON**. L’exemple suivant montre un fichier **Launch. vs. JSON** simple qui extrait la valeur de la `remoteCopySources` clé dans le fichier **CMakeSettings. JSON** pour la configuration actuellement sélectionnée :

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

Dès que vous enregistrez le fichier **Launch. vs. JSON** , une entrée est créée dans la liste déroulante de l' **élément de démarrage** avec le nouveau nom. En modifiant le fichier **Launch. vs. JSON** , vous pouvez créer autant de configurations de débogage que vous le souhaitez pour un nombre quelconque de cibles cmake.

## <a name="support-for-cmakesettings-variables"></a>Prise en charge des variables CMakeSettings

 **Launch. vs. JSON** prend en charge les variables déclarées dans **CMakeSettings. JSON** (voir ci-dessous) et qui s’appliquent à la configuration actuellement sélectionnée. Il possède également une clé nommée `currentDir`, qui définit le répertoire actif de l’application de lancement pour un projet local :

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

La clé « CWD » définit le répertoire actif de l’application de lancement pour un projet distant. La valeur par défaut est « $ {debugInfo. defaultWorkingDirectory} », qui prend la valeur 

```cmd
/var/tmp/src/bfc6f7f4-4f0f-8b35-80d7-9198fa973fb9/Linux-Debug
```

## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)<br/>
[Se connecter à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Personnaliser les paramètres de génération CMake](customize-cmake-settings.md)<br/>
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)<br/>
[Déployer, exécuter et déboguer un projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)<br/>
