---
title: Configurer des sessions de débogage CMake dans Visual Studio
description: Décrit comment utiliser Visual Studio pour configurer les paramètres du débogueur CMake.
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

La prise en charge native de CMake est disponible dans Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end

::: moniker range=">=vs-2017"

Toutes les cibles CMake exécutables figurent dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**. Sélectionnez-en un pour démarrer une session de débogage et lancer le débogueur.

![Liste déroulante d’élément de démarrage CMake](media/cmake-startup-item-dropdown.png "Liste déroulante d’élément de démarrage CMake")

Vous pouvez également démarrer une session de débogage à partir de Explorateur de solutions. Tout d’abord, basculez vers la **vue cibles cmake** dans la fenêtre **Explorateur de solutions** .

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png  "Élément de menu Affichage des cibles CMake")

Ensuite, cliquez avec le bouton droit sur un exécutable et sélectionnez **Déboguer**. Cette commande démarre automatiquement le débogage de la cible sélectionnée en fonction de votre configuration active.

## <a name="customize-debugger-settings"></a>Personnaliser les paramètres du débogueur

Vous pouvez personnaliser les paramètres du débogueur pour toute cible CMake exécutable dans votre projet. Ils se trouvent dans un fichier de configuration nommé *Launch. vs. JSON*, situé dans *`.vs`* un dossier à la racine de votre projet. Un fichier de configuration de lancement est utile dans la plupart des scénarios de débogage, car vous pouvez configurer et enregistrer les détails de l’installation du débogage. Il existe trois points d’entrée pour ce fichier :

- **Menu Déboguer :** Sélectionnez **Déboguer > paramètres de débogage et de lancement pour $ {activeDebugTarget}** dans le menu principal pour personnaliser la configuration de débogage spécifique à votre cible de débogage active. Si aucune cible de débogage n’est sélectionnée, cette option est grisée.

![Point d’entrée du menu Débogage](media/cmake-debug-menu.png "Point d’entrée du menu Débogage")

- **Affichage des cibles :** Accédez à la **vue cibles** dans Explorateur de solutions. Ensuite, cliquez avec le bouton droit sur une cible de débogage et sélectionnez **Ajouter une configuration de débogage** pour personnaliser la configuration de débogage spécifique à la cible sélectionnée.

![Point d’entrée de la vue cibles](media/cmake-targets-add-debug-configuration.png "Point d’entrée de la vue cibles")

- **Racine fichier CMakeLists. txt :** Cliquez avec le bouton droit sur un *fichier CMakeLists. txt* racine et sélectionnez **Ajouter une configuration de débogage** pour ouvrir la boîte de dialogue **Sélectionner un débogueur** . La boîte de dialogue vous permet d’ajouter *n’importe quel* type de configuration de débogage, mais vous devez spécifier manuellement la `projectTarget` cible cmake à appeler via la propriété.

![Sélectionner une boîte de dialogue du débogueur](media/cmake-select-a-debugger.png "Sélectionner une boîte de dialogue du débogueur")

Vous pouvez modifier le fichier *Launch. vs. JSON* pour créer des configurations de débogage pour n’importe quel nombre de cibles cmake. Lorsque vous enregistrez le fichier, Visual Studio crée une entrée pour chaque nouvelle configuration dans la liste déroulante **élément de démarrage** .

## <a name="reference-keys-in-cmakesettingsjson"></a>Clés de référence dans CMakeSettings. JSON

Pour faire référence à une clé dans un fichier *CMakeSettings. JSON* , ajoutez `cmake.` -la au début dans *Launch. vs. JSON*. L’exemple suivant montre un fichier *Launch. vs. JSON* simple qui extrait la valeur de la `remoteCopySources` clé dans le fichier *CMakeSettings. JSON* pour la configuration actuellement sélectionnée :

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

Les **variables d’environnement** définies dans *CMakeSettings. JSON* peuvent également être utilisées dans Launch. vs. JSON à `${env.VARIABLE_NAME}`l’aide de la syntaxe. Dans Visual Studio 2019 version 16,4 et versions ultérieures, les cibles de débogage sont automatiquement lancées à l’aide de l’environnement que vous spécifiez dans *CMakeSettings. JSON*. Vous pouvez annuler la définition d’une variable d’environnement en lui affectant la **valeur null**.

## <a name="launchvsjson-reference"></a>Référence Launch. vs. JSON

Il existe de nombreuses propriétés *Launch. vs. JSON* pour prendre en charge tous vos scénarios de débogage. Les propriétés suivantes sont communes à toutes les configurations de débogage, à la fois distantes et locales :

- `projectTarget`: Spécifie la cible CMake à appeler lors de la génération du projet. Visual Studio remplit cette propriété si vous entrez *Launch. vs. JSON* à partir du **menu Déboguer** ou de la **vue cibles**. Cette valeur doit correspondre au nom d’une cible de débogage existante figurant dans la liste déroulante **élément de démarrage** .

- `env`: Variables d’environnement supplémentaires à ajouter à l’aide de la syntaxe suivante :

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: Arguments de ligne de commande passés au programme à déboguer.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Référence Launch. vs. JSON pour les projets distants et WSL

Dans Visual Studio 2019 version 16,6, nous avons ajouté une nouvelle configuration Debug `type: cppgdb` de pour simplifier le débogage sur les systèmes distants et les WSL. Les anciennes configurations de débogage de `type: cppdbg` sont toujours prises en charge.

### <a name="configuration-type-cppgdb"></a>Type de configuration`cppgdb`

- `name`: Nom convivial permettant d’identifier la configuration dans la liste déroulante **élément de démarrage** .
- `project`: Spécifie le chemin d’accès relatif au fichier projet. Normalement, vous n’avez pas besoin de modifier ce chemin d’accès lors du débogage d’un projet CMake.
- `projectTarget`: Spécifie la cible CMake à appeler lors de la génération du projet. Visual Studio remplit cette propriété si vous entrez *Launch. vs. JSON* à partir du **menu Déboguer** ou de la **vue cibles**. Cette valeur cible doit correspondre au nom d’une cible de débogage existante figurant dans la liste déroulante **élément de démarrage** .
- `debuggerConfiguration`: Indique le jeu de valeurs par défaut de débogage à utiliser. Dans Visual Studio 2019 version 16,6, la seule option valide est `gdb`. Les versions antérieures prennent `gdbserver`également en charge.
- `args`: Arguments de ligne de commande passés au démarrage au programme en cours de débogage.
- `env`: Autres variables d’environnement passées au programme en cours de débogage. Par exemple : `{"DISPLAY": "0.0"}`.
- `processID`: ID de processus Linux à attacher. Utilisé uniquement lors de l’attachement à un processus distant. Pour plus d’informations, consultez [résoudre les problèmes liés à l’attachement à des processus à l’aide de gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Options supplémentaires pour la `gdb` configuration

- `program`: La valeur par `"${debugInfo.fullTargetPath}"`défaut est. Chemin d’accès UNIX à l’application à déboguer. Obligatoire uniquement s’il est différent de l’exécutable cible dans l’emplacement de génération ou de déploiement.
- `remoteMachineName`: La valeur par `"${debugInfo.remoteMachineName}"`défaut est. Nom du système distant qui héberge le programme à déboguer. Obligatoire uniquement s’il est différent du système de génération. Doit avoir une entrée existante dans le [Gestionnaire de connexions](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes existantes.
- `cwd`: La valeur par `"${debugInfo.defaultWorkingDirectory}"`défaut est. Chemin d’accès UNIX au répertoire sur le système distant où `program` est exécuté. Le répertoire doit exister.
- `gdbpath`: La valeur par `/usr/bin/gdb`défaut est. Chemin d’accès UNIX complet `gdb` au utilisé pour le débogage. Obligatoire uniquement si vous utilisez une version personnalisée `gdb`de.
- `preDebugCommand`: Commande Linux à exécuter immédiatement avant d’appeler `gdb`. `gdb`ne démarre pas tant que la commande n’est pas terminée. Vous pouvez utiliser l’option pour exécuter un script avant l’exécution de `gdb`.

#### <a name="deployment-options"></a>Options de déploiement

Utilisez les options suivantes pour séparer votre ordinateur de build (défini dans CMakeSettings. Json) de votre ordinateur de débogage distant.

- `remoteMachineName`: Ordinateur de débogage distant. Obligatoire uniquement s’il est différent de l’ordinateur de Build. Doit avoir une entrée existante dans le [Gestionnaire de connexions](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes existantes.
- `disableDeploy`: La valeur par `false`défaut est. Indique si la séparation de build/débogage est désactivée. Quand `false`cette option est activée, cette option permet de générer et de déboguer sur deux ordinateurs distincts.
- `deployDirectory`: Chemin d’accès UNIX complet au répertoire `remoteMachineName` sur lequel l’exécutable est copié.
- `deploy`: Un tableau de paramètres de déploiement avancés. Vous devez configurer ces paramètres uniquement lorsque vous souhaitez un contrôle plus granulaire du processus de déploiement. Par défaut, seuls les fichiers nécessaires au débogage du processus sont déployés sur l’ordinateur de débogage distant.
  - `sourceMachine`: Ordinateur à partir duquel le fichier ou le répertoire est copié. Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes stockées dans le gestionnaire de connexions. Lors de la génération en mode natif sur WSL, cette option est ignorée.
  - `targetMachine`: Ordinateur sur lequel le fichier ou le répertoire est copié. Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes stockées dans le gestionnaire de connexions.
  - `sourcePath`: Emplacement du fichier ou du répertoire `sourceMachine`sur.
  - `targetPath`: Emplacement du fichier ou du répertoire `targetMachine`sur.
  - `deploymentType`: Description du type de déploiement. `LocalRemote`et `RemoteRemote` sont pris en charge. `LocalRemote`signifie la copie à partir du système de fichiers local vers le système `remoteMachineName` distant spécifié par dans *Launch. vs. JSON*. `RemoteRemote`signifie la copie à partir du système de génération distant spécifié dans *CMakeSettings. JSON* vers le système distant différent spécifié dans *Launch. vs. JSON*.
  - `executable`: Indique si le fichier déployé est un exécutable.

### <a name="execute-custom-gdb-commands"></a>Exécuter des `gdb` commandes personnalisées

Visual Studio prend en charge l' `gdb` exécution de commandes personnalisées pour interagir directement avec le débogueur sous-jacent. Pour plus d’informations, consultez [exécution de `gdb` commandes lldb personnalisées](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands).

### <a name="enable-logging"></a>Activation de la journalisation

Activez la journalisation MIEngine pour voir les commandes qui `gdb`sont envoyées à `gdb` , la sortie renvoyée et la durée de chaque commande. [En savoir plus](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Type de configuration`cppdbg`

Les options suivantes peuvent être utilisées lors du débogage sur un système distant ou WSL à l' `cppdbg` aide du type de configuration. Dans Visual Studio 2019 version 16,6 ou ultérieure, le type `cppgdb` de configuration est recommandé.

- `name`: Nom convivial permettant d’identifier la configuration dans la liste déroulante **élément de démarrage** .

- `project`: Spécifie le chemin d’accès relatif au fichier projet. Normalement, vous n’avez pas besoin de modifier cette valeur lors du débogage d’un projet CMake.

- `projectTarget`: Spécifie la cible CMake à appeler lors de la génération du projet. Visual Studio remplit cette propriété si vous entrez *Launch. vs. JSON* à partir du **menu Déboguer** ou de la **vue cibles**. Cette valeur doit correspondre au nom d’une cible de débogage existante figurant dans la liste déroulante **élément de démarrage** .

- `args`: Arguments de ligne de commande passés au démarrage au programme en cours de débogage.

- `processID`: ID de processus Linux à attacher. Utilisé uniquement lors de l’attachement à un processus distant. Pour plus d’informations, consultez [résoudre les problèmes liés à l’attachement à des processus à l’aide de gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: La valeur par `"${debugInfo.fullTargetPath}"`défaut est. Chemin d’accès UNIX à l’application à déboguer. Obligatoire uniquement s’il est différent de l’exécutable cible dans l’emplacement de génération ou de déploiement.

- `remoteMachineName`: La valeur par `"${debugInfo.remoteMachineName}"`défaut est. Nom du système distant qui héberge le programme à déboguer. Obligatoire uniquement s’il est différent du système de génération. Doit avoir une entrée existante dans le [Gestionnaire de connexions](../linux/connect-to-your-remote-linux-computer.md). Appuyez sur **Ctrl + Espace** pour afficher la liste de toutes les connexions distantes existantes.

- `cwd`: La valeur par `"${debugInfo.defaultWorkingDirectory}"`défaut est. Chemin d’accès UNIX complet au répertoire sur le système distant `program` où est exécuté. Le répertoire doit exister.

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

- `pipeArgs`: Tableau d’arguments de ligne de commande passés au programme canal pour configurer la connexion. Le programme pipe est utilisé pour relayer les entrées/sorties standard entre Visual `gdb`Studio et. La majeure partie de ce tableau **n’a pas besoin d’être personnalisée lors du** débogage de projets cmake. L’exception est `${debuggerCommand}`, qui se lance `gdb` sur le système distant. Il peut être modifié en :

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

  - Exécutez un script avant l’exécution de `gdb`. Vérifiez que les autorisations d’exécution sont définies sur votre script.

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

- `visualizerFile`: [Fichier. natvis](/visualstudio/debugger/create-custom-views-of-native-objects) à utiliser lors du débogage de ce processus. Cette option est incompatible avec `gdb` l’impression simple. Définissez `showDisplayString` également lorsque vous définissez cette propriété.

- `showDisplayString`: Valeur booléenne qui active la chaîne d’affichage lorsqu' `visualizerFile` un est spécifié. L’affectation de la `true` valeur à cette option peut entraîner une baisse des performances lors du débogage.

- `setupCommands`: Une ou plusieurs `gdb` commandes à exécuter, pour configurer le débogueur sous-jacent.

- `miDebuggerPath`: Chemin d’accès complet `gdb`à. Quand il n’est pas spécifié, Visual Studio recherche d’abord le débogueur.

- Enfin, toutes les options de déploiement définies pour le `cppgdb` type de configuration peuvent également être utilisées `cppdbg` par le type de configuration.

### <a name="debug-using-gdbserver"></a>Déboguer à l’aide de`gdbserver`

Vous pouvez configurer la `cppdbg` configuration pour déboguer à l’aide `gdbserver`de. Pour plus d’informations et pour obtenir un exemple de configuration de lancement, consultez le billet de blog de l’équipe Microsoft C++ intitulé [débogage de projets cmake Linux avec `gdbserver` ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)\
[Configurer un projet CMake Linux](../linux/cmake-linux-project.md)\
[Connectez-vous à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)\
[Personnaliser les paramètres de build CMake](customize-cmake-settings.md)\
[Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)\
[Déployer, exécuter et déboguer votre projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
