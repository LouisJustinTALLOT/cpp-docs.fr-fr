---
title: Configurer des sessions de débogage CMake dans Visual Studio
description: Décrit comment utiliser Visual Studio pour configurer les paramètres du débogueur CMake.
ms.date: 12/16/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 36a4d64b987c1468caa06ed8670dfaf7d44abad3
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645104"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurer des sessions de débogage CMake

::: moniker range="msvc-140"

La prise en charge native de CMake est disponible dans Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end

::: moniker range=">=msvc-150"

Toutes les cibles CMake exécutables sont affichées dans la liste déroulante **élément de démarrage** de la barre d’outils. Sélectionnez-en un pour démarrer une session de débogage et lancer le débogueur.

![Liste déroulante d’élément de démarrage CMake](media/cmake-startup-item-dropdown.png "Liste déroulante d’élément de démarrage CMake")

Vous pouvez également démarrer une session de débogage à partir de Explorateur de solutions. Tout d’abord, basculez vers la **vue cibles cmake** dans la fenêtre **Explorateur de solutions** .

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png  "Élément de menu Affichage des cibles CMake")

Ensuite, cliquez avec le bouton droit sur un exécutable et sélectionnez **Déboguer**. Cette commande démarre automatiquement le débogage de la cible sélectionnée en fonction de votre configuration active.

## <a name="customize-debugger-settings"></a>Personnaliser les paramètres du débogueur

Vous pouvez personnaliser les paramètres du débogueur pour toute cible CMake exécutable dans votre projet. Ils se trouvent dans un fichier de configuration appelé *launch.vs.js*, situé dans un *`.vs`* dossier à la racine de votre projet. Un fichier de configuration de lancement est utile dans la plupart des scénarios de débogage, car vous pouvez configurer et enregistrer les détails de l’installation du débogage. Il existe trois points d’entrée pour ce fichier :

- **Menu Déboguer :** Sélectionnez **Déboguer > paramètres de débogage et de lancement pour $ {activeDebugTarget}** dans le menu principal pour personnaliser la configuration de débogage spécifique à votre cible de débogage active. Si aucune cible de débogage n’est sélectionnée, cette option est grisée.

![Point d’entrée du menu Débogage](media/cmake-debug-menu.png "Point d’entrée du menu Débogage")

- **Affichage des cibles :** Accédez à la **vue cibles** dans Explorateur de solutions. Ensuite, cliquez avec le bouton droit sur une cible de débogage et sélectionnez **Ajouter une configuration de débogage** pour personnaliser la configuration de débogage spécifique à la cible sélectionnée.

![Point d’entrée de la vue cibles](media/cmake-targets-add-debug-configuration.png "Point d’entrée de la vue cibles")

- **CMakeLists.txt racine :** Cliquez avec le bouton droit sur un *CMakeLists.txt* racine et sélectionnez **Ajouter une configuration de débogage** pour ouvrir la boîte de dialogue **Sélectionner un débogueur** . La boîte de dialogue vous permet d’ajouter *n’importe quel* type de configuration de débogage, mais vous devez spécifier manuellement la cible cmake à appeler via la `projectTarget` propriété.

![Sélectionner une boîte de dialogue du débogueur](media/cmake-select-a-debugger.png "Sélectionner une boîte de dialogue du débogueur")

Vous pouvez modifier la *launch.vs.jssur* le fichier pour créer des configurations de débogage pour un nombre quelconque de cibles cmake. Lorsque vous enregistrez le fichier, Visual Studio crée une entrée pour chaque nouvelle configuration dans la liste déroulante **élément de démarrage** .

## <a name="reference-keys-in-cmakesettingsjson"></a>Clés de référence dans CMakeSettings.jssur

Pour faire référence à une clé d’un *CMakeSettings.js* dans un fichier, ajoutez-le au début `cmake.` *launch.vs.js*. L’exemple suivant montre un *launch.vs.jssimple sur* un fichier qui extrait la valeur de la `remoteCopySources` clé dans le fichier *CMakeSettings.js* de la configuration actuellement sélectionnée :

```json
{
  "version": "0.2.1",
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

Les **variables d’environnement** définies dans *CMakeSettings.jssur* peuvent également être utilisées dans launch.vs.jsà l’aide de la syntaxe `${env.VARIABLE_NAME}` . Dans Visual Studio 2019 version 16,4 et versions ultérieures, les cibles de débogage sont automatiquement lancées à l’aide de l’environnement que vous spécifiez dans *CMakeSettings.js*. Vous pouvez annuler la définition d’une variable d’environnement en lui affectant la **valeur null**.

## <a name="launchvsjson-reference"></a>Launch.vs.jsà la référence

Il existe *de nombreuxlaunch.vs.jssur* les propriétés pour prendre en charge tous vos scénarios de débogage. Les propriétés suivantes sont communes à toutes les configurations de débogage, à la fois distantes et locales :

- `projectTarget`: Spécifie la cible CMake à appeler lors de la génération du projet. Visual Studio remplit cette propriété si vous entrez *launch.vs.js* à partir du **menu Déboguer** ou de la **vue cibles**. Cette valeur doit correspondre au nom d’une cible de débogage existante figurant dans la liste déroulante **élément de démarrage** .

- `env`: Variables d’environnement supplémentaires à ajouter à l’aide de la syntaxe suivante :

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: Arguments de ligne de commande passés au programme à déboguer.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Launch.vs.jsen référence pour les projets distants et WSL

Dans Visual Studio 2019 version 16,6, nous avons ajouté une nouvelle configuration Debug de `type: cppgdb` pour simplifier le débogage sur les systèmes distants et les WSL. Les anciennes configurations de débogage de `type: cppdbg` sont toujours prises en charge.

### <a name="configuration-type-cppgdb"></a>Type de configuration `cppgdb`

- `name`: Nom convivial permettant d’identifier la configuration dans la liste déroulante **élément de démarrage** .
- `project`: Spécifie le chemin d’accès relatif au fichier projet. Normalement, vous n’avez pas besoin de modifier ce chemin d’accès lors du débogage d’un projet CMake.
- `projectTarget`: Spécifie la cible CMake à appeler lors de la génération du projet. Visual Studio remplit cette propriété si vous entrez *launch.vs.js* à partir du **menu Déboguer** ou de la **vue cibles**. Cette valeur cible doit correspondre au nom d’une cible de débogage existante figurant dans la liste déroulante **élément de démarrage** .
- `debuggerConfiguration`: Indique le jeu de valeurs par défaut de débogage à utiliser. Dans Visual Studio 2019 version 16,6, la seule option valide est `gdb` . Visual Studio 2019 version 16,7 ou ultérieure prend également en charge `gdbserver` .
- `args`: Arguments de ligne de commande passés au démarrage au programme en cours de débogage.
- `env`: Autres variables d’environnement passées au programme en cours de débogage. Par exemple : `{"DISPLAY": "0.0"}`.
- `processID`: ID de processus Linux à attacher. Utilisé uniquement lors de l’attachement à un processus distant. Pour plus d’informations, consultez [résoudre les problèmes liés à l’attachement à des processus à l’aide de gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Options supplémentaires pour la `gdb` Configuration

- `program`: La valeur par défaut est `"${debugInfo.fullTargetPath}"` . Chemin d’accès UNIX à l’application à déboguer. Obligatoire uniquement s’il est différent de l’exécutable cible dans l’emplacement de génération ou de déploiement.
- `remoteMachineName`: La valeur par défaut est `"${debugInfo.remoteMachineName}"` . Nom du système distant qui héberge le programme à déboguer. Obligatoire uniquement s’il est différent du système de génération. Doit avoir une entrée existante dans le [Gestionnaire de connexions](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes existantes.
- `cwd`: La valeur par défaut est `"${debugInfo.defaultWorkingDirectory}"` . Chemin d’accès UNIX au répertoire sur le système distant où `program` est exécuté. Le répertoire doit exister.
- `gdbpath`: La valeur par défaut est `/usr/bin/gdb` . Chemin d’accès UNIX complet au `gdb` utilisé pour le débogage. Obligatoire uniquement si vous utilisez une version personnalisée de `gdb` .
- `preDebugCommand`: Commande Linux à exécuter immédiatement avant d’appeler `gdb` . `gdb` ne démarre pas tant que la commande n’est pas terminée. Vous pouvez utiliser l’option pour exécuter un script avant l’exécution de `gdb` .

#### <a name="additional-options-allowed-with-the-gdbserver-configuration-167-or-later"></a>Options supplémentaires autorisées avec la `gdbserver` Configuration (16,7 ou version ultérieure)

- `program`: La valeur par défaut est `"${debugInfo.fullTargetPath}"` . Chemin d’accès UNIX à l’application à déboguer. Obligatoire uniquement s’il est différent de l’exécutable cible dans l’emplacement de génération ou de déploiement.

  > [!TIP]
  > Le déploiement n’est pas encore pris en charge pour les scénarios de compilation croisée locale. Si vous effectuez une compilation croisée sur Windows (par exemple, à l’aide d’un compilateur croisé sur Windows pour créer un fichier exécutable ARM Linux), vous devez copier manuellement le fichier binaire à l’emplacement spécifié par `program` sur l’ordinateur ARM distant avant le débogage.

- `remoteMachineName`: La valeur par défaut est `"${debugInfo.remoteMachineName}"` . Nom du système distant qui héberge le programme à déboguer. Obligatoire uniquement s’il est différent du système de génération. Doit avoir une entrée existante dans le [Gestionnaire de connexions](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes existantes.
- `cwd`: La valeur par défaut est `"${debugInfo.defaultWorkingDirectory}"` . Chemin d’accès UNIX complet au répertoire sur le système distant où `program` est exécuté. Le répertoire doit exister.
- `gdbPath`: La valeur par défaut est `${debugInfo.vsInstalledGdb}` . Chemin Windows complet du `gdb` utilisé pour le débogage. La valeur par défaut est le `gdb` installé avec le développement Linux avec la charge de travail C/C++.
- `gdbserverPath`: La valeur par défaut est `usr/bin/gdbserver` . Chemin d’accès UNIX complet au `gdbserver` utilisé pour le débogage.
- `preDebugCommand`: Commande Linux à exécuter immédiatement avant le démarrage `gdbserver` . `gdbserver` ne démarre pas tant que la commande n’est pas terminée.

#### <a name="deployment-options"></a>Options de déploiement

Utilisez les options suivantes pour séparer votre ordinateur de build (défini dans CMakeSettings.js) de votre ordinateur de débogage distant.

- `remoteMachineName`: Ordinateur de débogage distant. Obligatoire uniquement s’il est différent de l’ordinateur de Build. Doit avoir une entrée existante dans le [Gestionnaire de connexions](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes existantes.
- `disableDeploy`: La valeur par défaut est **`false`** . Indique si la séparation de build/débogage est désactivée. Quand **`false`** cette option est activée, cette option permet de générer et de déboguer sur deux ordinateurs distincts.
- `deployDirectory`: Chemin d’accès UNIX complet au répertoire sur `remoteMachineName` lequel l’exécutable est copié.
- `deploy`: Un tableau de paramètres de déploiement avancés. Vous devez configurer ces paramètres uniquement lorsque vous souhaitez un contrôle plus granulaire du processus de déploiement. Par défaut, seuls les fichiers nécessaires au débogage du processus sont déployés sur l’ordinateur de débogage distant.
  - `sourceMachine`: Ordinateur à partir duquel le fichier ou le répertoire est copié. Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes stockées dans le gestionnaire de connexions. Lors de la génération en mode natif sur WSL, cette option est ignorée.
  - `targetMachine`: Ordinateur sur lequel le fichier ou le répertoire est copié. Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes stockées dans le gestionnaire de connexions.
  - `sourcePath`: Emplacement du fichier ou du répertoire sur `sourceMachine` .
  - `targetPath`: Emplacement du fichier ou du répertoire sur `targetMachine` .
  - `deploymentType`: Description du type de déploiement. `LocalRemote` et `RemoteRemote` sont pris en charge. `LocalRemote` signifie la copie à partir du système de fichiers local vers le système distant spécifié par `remoteMachineName` dans *launch.vs.jssur*. `RemoteRemote` signifie que la copie à partir du système de génération distant spécifié dans *CMakeSettings.jssur* le autre système distant spécifié dans *launch.vs.jssur*.
  - `executable`: Indique si le fichier déployé est un exécutable.

### <a name="execute-custom-gdb-commands"></a>Exécuter des `gdb` commandes personnalisées

Visual Studio prend en charge l’exécution `gdb` de commandes personnalisées pour interagir directement avec le débogueur sous-jacent. Pour plus d’informations, consultez [exécution de `gdb` commandes lldb personnalisées](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands).

### <a name="enable-logging"></a>Activation de la journalisation

Activez la journalisation MIEngine pour voir les commandes qui sont envoyées à `gdb` , `gdb` la sortie renvoyée et la durée de chaque commande. [En savoir plus](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Type de configuration `cppdbg`

Les options suivantes peuvent être utilisées lors du débogage sur un système distant ou WSL à l’aide du `cppdbg` type de configuration. Dans Visual Studio 2019 version 16,6 ou ultérieure, le type de configuration `cppgdb` est recommandé.

- `name`: Nom convivial permettant d’identifier la configuration dans la liste déroulante **élément de démarrage** .

- `project`: Spécifie le chemin d’accès relatif au fichier projet. Normalement, vous n’avez pas besoin de modifier cette valeur lors du débogage d’un projet CMake.

- `projectTarget`: Spécifie la cible CMake à appeler lors de la génération du projet. Visual Studio remplit cette propriété si vous entrez *launch.vs.js* à partir du **menu Déboguer** ou de la **vue cibles**. Cette valeur doit correspondre au nom d’une cible de débogage existante figurant dans la liste déroulante **élément de démarrage** .

- `args`: Arguments de ligne de commande passés au démarrage au programme en cours de débogage.

- `processID`: ID de processus Linux à attacher. Utilisé uniquement lors de l’attachement à un processus distant. Pour plus d’informations, consultez [résoudre les problèmes liés à l’attachement à des processus à l’aide de gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: La valeur par défaut est `"${debugInfo.fullTargetPath}"` . Chemin d’accès UNIX à l’application à déboguer. Obligatoire uniquement s’il est différent de l’exécutable cible dans l’emplacement de génération ou de déploiement.

- `remoteMachineName`: La valeur par défaut est `"${debugInfo.remoteMachineName}"` . Nom du système distant qui héberge le programme à déboguer. Obligatoire uniquement s’il est différent du système de génération. Doit avoir une entrée existante dans le [Gestionnaire de connexions](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes existantes.

- `cwd`: La valeur par défaut est `"${debugInfo.defaultWorkingDirectory}"` . Chemin d’accès UNIX complet au répertoire sur le système distant où `program` est exécuté. Le répertoire doit exister.

- `environment`: Autres variables d’environnement passées au programme en cours de débogage. Par exemple,

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

- `pipeArgs`: Tableau d’arguments de ligne de commande passés au programme canal pour configurer la connexion. Le programme pipe est utilisé pour relayer les entrées/sorties standard entre Visual Studio et `gdb` . La majeure partie de ce tableau **n’a pas besoin d’être personnalisée lors du** débogage de projets cmake. L’exception est `${debuggerCommand}` , qui se lance `gdb` sur le système distant. Il peut être modifié en :

  - Exportez la valeur de l’affichage de la variable d’environnement sur votre système Linux. Dans l’exemple suivant, cette valeur est `:1` .

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

  - Exécutez un script avant l’exécution de `gdb` . Vérifiez que les autorisations d’exécution sont définies sur votre script.

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

- `stopOnEntry`: Valeur booléenne qui spécifie s’il faut arrêter dès que le processus est lancé. La valeur par défaut est false.

- `visualizerFile`: [Fichier. natvis](/visualstudio/debugger/create-custom-views-of-native-objects) à utiliser lors du débogage de ce processus. Cette option est incompatible avec `gdb` l’impression simple. Définissez également `showDisplayString` lorsque vous définissez cette propriété.

- `showDisplayString`: Valeur booléenne qui active la chaîne d’affichage lorsqu’un `visualizerFile` est spécifié. L’affectation de la valeur à cette option **`true`** peut entraîner une baisse des performances lors du débogage.

- `setupCommands`: Une ou plusieurs `gdb` commandes à exécuter, pour configurer le débogueur sous-jacent.

- `miDebuggerPath`: Chemin d’accès complet à `gdb` . Quand il n’est pas spécifié, Visual Studio recherche d’abord le débogueur.

- Enfin, toutes les options de déploiement définies pour le `cppgdb` type de configuration peuvent également être utilisées par le `cppdbg` type de configuration.

### <a name="debug-using-gdbserver"></a>Déboguer à l’aide de `gdbserver`

Vous pouvez configurer la `cppdbg` configuration pour déboguer à l’aide de `gdbserver` . Pour plus d’informations et pour obtenir un exemple de configuration de lancement, consultez le billet de blog de l’équipe Microsoft C++ intitulé [débogage de projets cmake Linux avec `gdbserver` ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)\
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)\
[Connectez-vous à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)\
[Personnaliser les paramètres de build CMake](customize-cmake-settings.md)\
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)\
[Déployer, exécuter et déboguer votre projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
