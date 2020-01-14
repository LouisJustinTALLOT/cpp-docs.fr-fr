---
title: Configurer des sessions de débogage CMake dans Visual Studio
description: Décrit comment utiliser Visual Studio pour configurer les paramètres du débogueur CMake
ms.date: 01/13/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: ff1de8241c2489e675f82f469f1cf697a72f5034
ms.sourcegitcommit: 275b71219d2a8bd5d78f87e21dd909e9968c2f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75946816"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurer des sessions de débogage CMake

::: moniker range="vs-2015"

La prise en charge native de CMake est disponible dans Visual Studio 2017 et versions ultérieures.

::: moniker-end

::: moniker range=">=vs-2017"

Toutes les cibles CMake exécutables figurent dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**. Pour démarrer une session de débogage, sélectionnez-en une et lancez le débogueur.

![Liste déroulante d’élément de démarrage CMake](media/cmake-startup-item-dropdown.png "Liste déroulante d’élément de démarrage CMake")

Vous pouvez également démarrer une session de débogage à partir de Explorateur de solutions. Tout d’abord, basculez vers la **vue cibles cmake** dans la fenêtre **Explorateur de solutions** .

![Bouton d’affichage des cibles CMake](media/cmake-targets-view.png  "Élément de menu Affichage des cibles CMake")

Ensuite, cliquez avec le bouton droit sur n’importe quel exécutable et sélectionnez Paramètres de **débogage ou** de débogage **et de lancement**. Le **débogage** démarre automatiquement le débogage de la cible sélectionnée, en fonction de votre configuration active. Les **paramètres de débogage et de lancement** ouvrent le fichier *Launch. vs. JSON* et ajoute une nouvelle configuration de débogage pour la cible sélectionnée.

## <a name="customize-debugger-settings"></a>Personnaliser les paramètres du débogueur

Vous pouvez personnaliser les paramètres du débogueur pour toute cible CMake exécutable de votre projet dans un fichier appelé *Launch. vs. JSON*. Il existe trois points d’entrée pour ce fichier :

- Sélectionnez **Déboguer > les paramètres de débogage et de lancement pour $ {activeDebugTarget}** dans le menu principal pour modifier la configuration de débogage spécifique à votre cible de débogage active. Si vous n’avez pas de cible active sélectionnée, cette option est grisée.

- Accédez à la **vue cibles** dans Explorateur de solutions. Ensuite, cliquez avec le bouton droit sur une cible de débogage et sélectionnez **paramètres de débogage et de lancement** pour modifier la configuration de débogage spécifique à votre cible sélectionnée.

- Cliquez avec le bouton droit sur fichier CMakeLists. txt racine et sélectionnez **paramètres de débogage et de lancement** pour ouvrir la boîte de dialogue **Sélectionner un débogueur** . La boîte de dialogue vous permet d’ajouter une configuration de débogage, mais vous devez spécifier manuellement la cible CMake à appeler via la propriété `projectTarget`.

Pour faire référence à une clé dans un fichier *CMakeSettings. JSON* , faites-la précéder `cmake.` dans *Launch. vs. JSON*. L’exemple suivant montre un fichier *Launch. vs. JSON* simple qui extrait la valeur de la `remoteCopySources` clé dans le fichier *CMakeSettings. JSON* pour la configuration actuellement sélectionnée :

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

Lorsque vous enregistrez le fichier *Launch. vs. JSON* , Visual Studio crée une entrée pour le nouveau nom dans la liste déroulante **élément de démarrage** . Vous pouvez modifier le fichier *Launch. vs. JSON* pour créer plusieurs configurations de débogage, pour n’importe quel nombre de cibles cmake.

## <a name="launchvsjson-reference"></a>Référence Launch. vs. JSON

Il existe de nombreuses propriétés *Launch. vs. JSON* pour prendre en charge tous vos scénarios de débogage. Les propriétés suivantes sont communes à toutes les configurations de débogage, à la fois distantes et locales :

- `projectTarget`: spécifie la cible CMake à appeler lors de la génération du projet. Visual Studio remplit cette propriété si vous entrez *Launch. vs. JSON* à partir de **déboguer > les paramètres de débogage et de lancement pour la vue $ {ActiveDebugTarget}** ou **cibles**.

- `program`: chemin d’accès complet au fichier exécutable du programme sur le système distant. Vous pouvez utiliser la macro `${debugInfo.fullTargetPath}` ici.

- `args`: arguments de ligne de commande passés au programme à déboguer.

## <a name="launchvsjson-reference-for-remote-linux-projects"></a>Référence Launch. vs. JSON pour les projets Linux distants

Les propriétés suivantes sont spécifiques aux **configurations de débogage distant**. Vous pouvez également [Envoyer des commandes directement à gdb](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands) et [activer la journalisation MIEngine](https://github.com/microsoft/MIEngine/wiki/Logging). Ces propriétés vous permettent de voir les commandes qui sont envoyées à gdb, le résultat renvoyé par gdb, ainsi que la durée de chaque commande.

- `cwd`: répertoire de travail actuel pour la recherche de dépendances et d’autres fichiers sur l’ordinateur distant. La macro `${debugInfo.defaultWorkingDirectory}` peut être utilisée. La valeur par défaut est la racine de l’espace de travail distant, sauf si elle est remplacée dans *fichier CMakeLists. txt*. Cette propriété est utilisée uniquement pour les configurations distantes. `currentDir` est utilisé pour définir le répertoire actif de l’application de lancement pour un projet local.

- `environment`: variables d’environnement supplémentaires à ajouter à l’environnement pour le programme avec la syntaxe suivante :

```json
  "environment": [
      {
        "name": "ENV1",
        "value": "envvalue1"
      },
      {
        "name": "ENV2",
        "value": "envvalue2"
      }
    ]
```

- `pipeArgs`: arguments de ligne de commande passés au programme canal pour configurer la connexion. Le programme pipe est utilisé pour relayer les entrées/sorties standard entre Visual Studio et gdb. La commande `${debuggerCommand}` lance gdb sur le système distant et peut être modifiée en :

  - Exportez la valeur de l’affichage de la variable d’environnement sur votre système Linux. Dans l’exemple suivant, cette valeur est `:1`.

  ```json
  "pipeArgs": [
      "/s",
      "${debugInfo.remoteMachineId}",
      "/p",
      "${debugInfo.parentProcessId}",
      "/c",
      "export DISPLAY=:1;${debuggerCommand}",
      "--tty=${debugInfo.tty}"
    ],
  ```

  - Exécutez un script avant l’exécution de gdb. Vérifiez que les autorisations d’exécution sont définies sur votre script.

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`: valeur booléenne qui spécifie s’il faut arrêter dès que le processus est lancé. La valeur par défaut est False.

- `visualizerFile`: [fichier. natvis](/visualstudio/debugger/create-custom-views-of-native-objects) à utiliser lors du débogage de ce processus. Cette option n’est pas compatible avec l’impression gdb. Définissez également `showDisplayString` lorsque vous définissez cette propriété.

- `showDisplayString`: valeur booléenne qui active la chaîne d’affichage lorsqu’un `visualizerFile` est spécifié. L’affectation de la valeur `true` à cette option peut entraîner une baisse des performances lors du débogage.

- `setupCommands`: une ou plusieurs commandes gdb à exécuter, pour configurer le débogueur sous-jacent.

- `externalConsole`: valeur booléenne qui spécifie si une console est lancée pour l’élément débogué.

- `miDebuggerPath`: chemin d’accès complet à gdb. Quand il n’est pas spécifié, Visual Studio recherche d’abord le débogueur.

::: moniker-end

::: moniker range="vs-2017"

- `remoteMachineName`: système Linux distant qui héberge gdb et le programme à déboguer.

::: moniker-end

::: moniker range="vs-2019"

Les propriétés suivantes peuvent être utilisées pour séparer votre **système de génération distant** de votre **système de débogage distant**. Pour plus d’informations, consultez [spécifier des ordinateurs différents pour la génération et le débogage](../linux/deploy-run-and-debug-your-linux-project.md#cmake-projects).

- `remoteMachineName`: système Linux distant qui héberge gdb et le programme à déboguer. Cette entrée n’a pas besoin de correspondre au système Linux distant utilisé pour la build spécifiée dans *CMakeSettings. JSON*. Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes stockées dans le [Gestionnaire de connexions](../linux/connect-to-your-remote-linux-computer.md).

- `disableDeploy`: indique si la séparation de build/débogage est désactivée. Lorsqu’elle est activée, cette fonctionnalité permet à la génération et au débogage de se produire sur deux ordinateurs distincts.

- `deployDirectory`: répertoire sur l’ordinateur de débogage distant (spécifié par `remoteMachineName`) dans lequel l’exécutable sera copié.

- `deploy`: un tableau de paramètres de déploiement avancés. Vous devez configurer ces paramètres uniquement lorsque vous souhaitez un contrôle plus granulaire du processus de déploiement. Par défaut, seuls les fichiers nécessaires pour le processus à déboguer sont déployés sur la machine de débogage distante.

  - `sourceMachine`: ordinateur à partir duquel le fichier ou le répertoire sera copié. Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes stockées dans le gestionnaire de connexions.

  - `targetMachine`: ordinateur sur lequel le fichier ou le répertoire sera copié. Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes stockées dans le gestionnaire de connexions.

  - `sourcePath`: emplacement du fichier ou du répertoire sur `sourceMachine`.

  - `targetPath`: emplacement du fichier ou du répertoire sur `targetMachine`.

  - `deploymentType`: description du type de déploiement. `LocalRemote` et `RemoteRemote` sont pris en charge. `LocalRemote` correspond à la copie à partir du système de fichiers local vers le système distant spécifié par `remoteMachineName` dans *Launch. vs. JSON*. `RemoteRemote` correspond à la copie à partir du système de génération distant spécifié dans *CMakeSettings. JSON* vers le système distant différent spécifié dans *Launch. vs. JSON*.

  - `executable`: indique si le fichier déployé est un fichier exécutable.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="attach-to-a-remote-process"></a>Attacher à un processus distant

Vous pouvez attacher à un processus en cours d’exécution sur votre système Linux en définissant `processId` sur l’ID de processus auquel le débogueur doit être attaché. Pour plus d’informations, consultez [résoudre les problèmes liés à l’attachement à des processus à l’aide de gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

::: moniker-end

::: moniker range="vs-2019"

## <a name="debug-on-linux-using-gdbserver"></a>Débogage sur Linux à l’aide de gdbserver

Visual Studio 2019 version 16,5 Preview 1 ou une version ultérieure prend en charge le débogage à distance des projets CMake avec gdbserver. Pour plus d’informations, consultez [débogage de projets cmake Linux avec gdbserver](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Voir aussi

[Projets cmake dans Visual Studio](cmake-projects-in-visual-studio.md)\
[Configurer un projet cmake Linux](../linux/cmake-linux-project.md)\
[Connectez-vous à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)\
[Personnaliser les paramètres de build CMake](customize-cmake-settings.md)\
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)\
[Déployez, exécutez et déboguez votre projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
