---
title: Configurer des sessions de débogage CMake dans Visual Studio
description: Décrit comment utiliser Visual Studio pour configurer les paramètres de débbuggeur CMake.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 8364e5b3dd3316a4ed7e754a104a14373040aa6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328843"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurer des sessions de débogage CMake

::: moniker range="vs-2015"

Native CMake support est disponible dans Visual Studio 2017 et plus tard. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end

::: moniker range=">=vs-2017"

Toutes les cibles CMake exécutables figurent dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**. Sélectionnez-en un pour démarrer une session de débogage et lancer le débbugger.

![Baisse de l’article de démarrage de CMake](media/cmake-startup-item-dropdown.png "Baisse de l’article de démarrage de CMake")

Vous pouvez également commencer une session de déboçon de Solution Explorer. Tout d’abord, passez à **CMake Targets View** dans la fenêtre **Solution Explorer.**

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png  "CMake Cibles Voir l’élément du menu")

Ensuite, cliquez à droite sur un **Debug**exécutable et sélectionné . Cette commande commence automatiquement à débogage de la cible sélectionnée en fonction de votre configuration active.

## <a name="customize-debugger-settings"></a>Personnaliser les paramètres du débogueur

Vous pouvez personnaliser les paramètres de débogénaires pour n’importe quelle cible CMake exécutable dans votre projet. Ils se trouvent dans un fichier de configuration appelé *launch.vs.json*, situé dans un *`.vs`* dossier dans votre racine de projet. Un fichier de configuration de lancement est utile dans la plupart des scénarios de débogage, car vous pouvez configurer et enregistrer vos détails de configuration débogage. Il y a trois points d’entrée à ce fichier :

- **Menu Debug:** Sélectionnez **Debug > Paramètres de débog et de lancement pour $-activeDebugTarget du** menu principal pour personnaliser la configuration de débogé spécifique à votre cible de débogé active. Si vous n’avez pas une cible de débogé, cette option est grisée.

![Point d’entrée du menu Debug](media/cmake-debug-menu.png "Point d’entrée du menu Debug")

- **Vue des cibles :** Naviguez vers **La vue des cibles** dans Solution Explorer. Ensuite, cliquez à droite sur une cible de débogé et **sélectionnez Add Debug Configuration** pour personnaliser la configuration de débogé spécifique à la cible sélectionnée.

![Cibles afficher le point d’entrée](media/cmake-targets-add-debug-configuration.png "Cibles afficher le point d’entrée")

- **Racine CMakeLists.txt:** Cliquez à droite sur une racine *CMakeLists.txt* et sélectionnez **Add Debug Configuration** pour ouvrir la boîte de dialogue **Select a Debugger.** Le dialogue vous permet d’ajouter *n’importe quel* type de configuration de débogs, `projectTarget` mais vous devez spécifier manuellement la cible CMake à invoquer via la propriété.

![Sélectionnez une boîte de dialogue de débbugger](media/cmake-select-a-debugger.png "Sélectionnez une boîte de dialogue de débbugger")

Vous pouvez modifier le fichier *launch.vs.json* pour créer des configurations de déboçon pour n’importe quel nombre de cibles CMake. Lorsque vous enregistrez le fichier, Visual Studio crée une entrée pour chaque nouvelle configuration dans le **dropdown Startup Item.**

## <a name="reference-keys-in-cmakesettingsjson"></a>Clés de référence dans CMakeSettings.json

Pour faire référence à n’importe quelle clé dans un `cmake.` fichier *CMakeSettings.json,* prépendez-lui dans *launch.vs.json*. L’exemple suivant montre un fichier *simple de lancement.vs.json* qui tire dans la valeur de la `remoteCopySources` clé dans le fichier *CMakeSettings.json* pour la configuration actuellement sélectionnée :

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

**Les variables de l’environnement** définies dans *CMakeSettings.json* peuvent également `${env.VARIABLE_NAME}`être utilisées dans launch.vs.json en utilisant la syntaxe . Dans Visual Studio 2019 version 16.4 et plus tard, les cibles de débogé sont automatiquement lancées en utilisant l’environnement que vous spécifiez dans *CMakeSettings.json*. Vous pouvez décastré une variable d’environnement en la fixant à **nulle.**

## <a name="launchvsjson-reference"></a>Référence Launch.vs.json

Il existe de nombreuses propriétés *launch.vs.json* pour soutenir tous vos scénarios de débogage. Les propriétés suivantes sont communes à toutes les configurations de débogé, à distance et locales :

- `projectTarget`: Specifie la cible CMake à invoquer lors de la construction du projet. Visual Studio autopeule cette propriété si vous entrez *launch.vs.json* à partir du **menu Debug** ou **Targets View**. Cette valeur doit correspondre au nom d’une cible de débogé existante répertoriée dans le **dropdown Startup Item.**

- `env`: Variables supplémentaires de l’environnement à ajouter à l’aide de la syntaxe :

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: Les arguments de la ligne de commandement ont été transmis au programme pour déboiffer.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Référence Launch.vs.json pour les projets distants et WSL

Dans Visual Studio 2019 version 16.6, nous avons `type: cppgdb` ajouté une nouvelle configuration de débbug de pour simplifier le débogage sur les systèmes distants et WSL. Les anciennes configurations `type: cppdbg` de débogé de sont encore prises en charge.

### <a name="configuration-type-cppgdb"></a>Type de configuration`cppgdb`

- `name`: Un nom amical pour identifier la configuration dans le **dropdown Startup Item.**
- `project`: Spécifie le chemin relatif vers le dossier du projet. Normalement, vous n’avez pas besoin de changer ce chemin lorsque vous débogiez un projet CMake.
- `projectTarget`: Specifie la cible CMake à invoquer lors de la construction du projet. Visual Studio autopeule cette propriété si vous entrez *launch.vs.json* à partir du **menu Debug** ou **Targets View**. Cette valeur cible doit correspondre au nom d’une cible de débogé existante répertoriée dans le **dropdown Startup Item.**
- `debuggerConfiguration`: Indique quel ensemble de valeurs par défaut de débogage à utiliser. Dans Visual Studio 2019 version 16.6, `gdb`la seule option valable est . Les versions `gdbserver`antérieures prennent également en charge .
- `args`: Les arguments de la ligne de commandement ont transmis le démarrage au programme en cours de déboisation.
- `env`: D’autres variables de l’environnement ont été transférées au programme en cours de déboissement. Par exemple : `{"DISPLAY": "0.0"}`.
- `processID`: ID de processus Linux à joindre. Utilisé uniquement lors de l’attachement à un processus à distance. Pour plus d’informations, voir [Troubleshoot attacher aux processus utilisant GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Options supplémentaires `gdb` pour la configuration

- `program`: Défauts `"${debugInfo.fullTargetPath}"`à . Le chemin Unix vers l’application de débog. Seulement nécessaire si la cible exécutable dans l’emplacement de construction ou de déploiement.
- `remoteMachineName`: Défauts `"${debugInfo.remoteMachineName}"`à . Nom du système distant qui héberge le programme de déboiffage. Seulement nécessaire si différent du système de construction. Doit avoir une entrée existante dans le [gestionnaire de connexion](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl-Space** pour afficher une liste de toutes les connexions à distance existantes.
- `cwd`: Défauts `"${debugInfo.defaultWorkingDirectory}"`à . Le chemin Unix vers l’annuaire `program` sur le système distant où est exécuté. Le répertoire doit exister.
- `gdbpath`: Défauts `/usr/bin/gdb`à . Plein chemin Unix `gdb` à l’utilisé pour déboter. Seulement nécessaire si vous `gdb`utilisez une version personnalisée de .
- `preDebugCommand`: Une commande Linux à exécuter `gdb`immédiatement avant d’invoquer . `gdb`ne commence pas jusqu’à ce que la commande se termine. Vous pouvez utiliser l’option pour exécuter `gdb`un script avant l’exécution de .

#### <a name="deployment-options"></a>Options de déploiement

Utilisez les options suivantes pour séparer votre machine de construction (définie dans CMakeSettings.json) de votre machine à déboguer à distance.

- `remoteMachineName`: Machine à débréter à distance. Seulement nécessaire si différent de la machine de construction. Doit avoir une entrée existante dans le [gestionnaire de connexion](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl-Space** pour afficher une liste de toutes les connexions à distance existantes.
- `disableDeploy`: Défauts `false`à . Indique si la séparation entre la construction et le débogé est désactivée. Lorsque `false`, cette option permet de construire et de déboiffer de se produire sur deux machines distinctes.
- `deployDirectory`: Plein chemin Unix vers `remoteMachineName` le répertoire sur lequel l’exécuteur est copié.
- `deploy`: Un éventail de réglages de déploiement avancés. Vous n’avez qu’à configurer ces paramètres lorsque vous voulez un contrôle plus granulaire sur le processus de déploiement. Par défaut, seuls les fichiers nécessaires au débogé du processus sont déployés à distance.
  - `sourceMachine`: La machine à partir de laquelle le fichier ou l’annuaire est copié. Appuyez sur **Ctrl-Space** pour afficher une liste de toutes les connexions à distance stockées dans le gestionnaire de connexion. Lors de la construction native sur WSL, cette option est ignorée.
  - `targetMachine`: La machine à laquelle le fichier ou l’annuaire est copié. Appuyez sur **Ctrl-Space** pour afficher une liste de toutes les connexions à distance stockées dans le gestionnaire de connexion.
  - `sourcePath`: Le fichier ou `sourceMachine`l’emplacement de l’annuaire sur .
  - `targetPath`: Le fichier ou `targetMachine`l’emplacement de l’annuaire sur .
  - `deploymentType`: Une description du type de déploiement. `LocalRemote`et `RemoteRemote` sont soutenus. `LocalRemote`signifie copier du système de fichiers local `remoteMachineName` au système distant spécifié par dans *launch.vs.json*. `RemoteRemote`signifie copier à partir du système de construction à distance spécifié dans *CMakeSettings.json* aux différents systèmes distants spécifiés dans *launch.vs.json*.
  - `executable`: Indique si le fichier déployé est exécutable.

### <a name="execute-custom-gdb-commands"></a>Exécuter `gdb` des commandes personnalisées

Visual Studio prend `gdb` en charge l’exécution de commandes personnalisées pour interagir directement avec le débbuggeur sous-jacent. Pour plus d’informations, voir [Exécution des commandes lldb personnalisées `gdb` ](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands).

### <a name="enable-logging"></a>Activation de la journalisation

Activez l’enregistrement MIEngine pour voir `gdb`à `gdb` quelles commandes sont envoyées, quelles sont les sorties et combien de temps chaque commande prend. [En savoir plus](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Type de configuration`cppdbg`

Les options suivantes peuvent être utilisées lors du débogage `cppdbg` sur un système distant ou WSL en utilisant le type de configuration. Dans Visual Studio 2019 version 16.6 `cppgdb` ou plus tard, le type de configuration est recommandé.

- `name`: Un nom amical pour identifier la configuration dans le **dropdown Startup Item.**

- `project`: Spécifie le chemin relatif vers le dossier du projet. Normalement, vous n’avez pas besoin de changer cette valeur lors de la débogage d’un projet CMake.

- `projectTarget`: Specifie la cible CMake à invoquer lors de la construction du projet. Visual Studio autopeule cette propriété si vous entrez *launch.vs.json* à partir du **menu Debug** ou **Targets View**. Cette valeur doit correspondre au nom d’une cible de débogé existante répertoriée dans le **dropdown Startup Item.**

- `args`: Les arguments de la ligne de commandement ont transmis le démarrage au programme en cours de déboisation.

- `processID`: ID de processus Linux à joindre. Utilisé uniquement lors de l’attachement à un processus à distance. Pour plus d’informations, voir [Troubleshoot attacher aux processus utilisant GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: Défauts `"${debugInfo.fullTargetPath}"`à . Le chemin Unix vers l’application de débog. Seulement nécessaire si la cible exécutable dans l’emplacement de construction ou de déploiement.

- `remoteMachineName`: Défauts `"${debugInfo.remoteMachineName}"`à . Nom du système distant qui héberge le programme de déboiffage. Seulement nécessaire si différent du système de construction. Doit avoir une entrée existante dans le [gestionnaire de connexion](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl-Space** pour afficher une liste de toutes les connexions à distance existantes.

- `cwd`: Défauts `"${debugInfo.defaultWorkingDirectory}"`à . Plein chemin Unix vers le répertoire `program` sur le système distant où est exécuté. Le répertoire doit exister.

- `environment`: D’autres variables de l’environnement ont été transférées au programme en cours de déboissement. Par exemple,

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

- `pipeArgs`: Un éventail d’arguments de ligne de commande transmis au programme de tuyauterie pour configurer la connexion. Le programme de pipe est utilisé pour relayer l’entrée/sortie standard entre Visual Studio et `gdb`. La plupart de ce tableau **n’a pas besoin d’être personnalisé** lors de la débogage des projets CMake. L’exception `${debuggerCommand}`est le `gdb` , qui lance sur le système à distance. Il peut être modifié pour :

  - Exportez la valeur de l’affichage variable de l’environnement sur votre système Linux. Dans l’exemple suivant, `:1`cette valeur est .

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

  - Exécuter un script avant `gdb`l’exécution de . Assurez-vous que les autorisations d’exécution sont définies sur votre script.

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

- `stopOnEntry`: Un boolean qui précise s’il faut rompre dès le lancement du processus. La valeur par défaut est false.

- `visualizerFile`: Un [fichier .natvis](/visualstudio/debugger/create-custom-views-of-native-objects) à utiliser lors de la débogage de ce processus. Cette option est `gdb` incompatible avec une jolie impression. Également `showDisplayString` défini lorsque vous définissez cette propriété.

- `showDisplayString`: Un boolean qui permet `visualizerFile` la chaîne d’affichage lorsqu’un est spécifié. La configuration `true` de cette option peut entraîner des performances plus lentes lors du débogage.

- `setupCommands`: Une `gdb` ou plusieurs commandes pour exécuter, pour configurer le débbuggeur sous-jacent.

- `miDebuggerPath`: Le chemin `gdb`complet vers . Lorsqu’il n’est pas précisé, Visual Studio recherche PATH d’abord pour le débbugger.

- Enfin, toutes les options de `cppgdb` déploiement définies pour `cppdbg` le type de configuration peuvent également être utilisées par le type de configuration.

### <a name="debug-using-gdbserver"></a>Debug en utilisant`gdbserver`

Vous pouvez `cppdbg` configurer la configuration `gdbserver`pour déboiffer à l’aide . Vous pouvez trouver plus de détails et une configuration de lancement d’échantillon dans le microsoft C 'Team Blog post [Debugging `gdbserver`Linux CMake Projects avec ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Voir aussi

[Projets CMake en Studio Visuel](cmake-projects-in-visual-studio.md)\
[Configurer un projet Linux CMake](../linux/cmake-linux-project.md)\
[Connectez-vous à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)\
[Personnaliser les paramètres de construction CMake](customize-cmake-settings.md)\
[Configurer les sessions de débogage CMake](configure-cmake-debugging-sessions.md)\
[Déployez, exécutez et débassez votre projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
