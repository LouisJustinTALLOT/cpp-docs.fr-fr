---
title: launch.vs.json schema reference (C)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323051"
---
# <a name="launchvsjson-schema-reference-c"></a>launch.vs.json schema reference (C)

Utilisez le fichier *launch.vs.json* pour configurer les paramètres de débogage. Pour créer le fichier. cliquez à droite sur un fichier exécutable dans **Solution Explorer** et choisissez **Debug et Paramètres de lancement**. Choisissez l’option qui correspond le plus étroitement à votre projet, puis utilisez les propriétés suivantes pour modifier la configuration au besoin. Pour plus d’informations sur le débogage des projets CMake, voir [Configure CMake séances de débogage](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Propriétés par défaut

||||
|-|-|-|
|**Propriété**|**Type**|**Description**|
|`name`|string|Précise le nom de l’entrée dans le dropdown cible Debug.|
|`type`|string|Précise si le projet est un dll ou .exe (Défauts à .exe)|
|`project`|string|Spécifie le chemin relatif vers le dossier du projet.|
|`projectTarget`|string|Spécifie la cible `project`facultative invoquée lors de la construction . Cela `projectTarget` doit exister déjà et correspondre au nom dans le **Dropdown Debug Target.**|
|`debugType`|string|Spécifie le mode de débogage selon le type de code (natif, géré ou mixte). Cela sera automatiquement détecté à moins que ce paramètre ne soit défini. Valeurs autorisées : « indigènes », « gérés », « mixtes ».|
|`inheritEnvironments`|tableau|Spécifie un ensemble de variables de l’environnement héritées de sources multiples. Vous pouvez définir certaines variables dans des fichiers comme *CMakeSettings.json* ou *CppProperties.json* et les rendre disponibles pour débug contexte.  **Visual Studio 16.4:**: Spécifier les `env.VARIABLE_NAME` variables de l’environnement sur une base par cible à l’aide de la syntaxe. Pour décastré une variable, mettez-la à "null".|
|`args`|tableau|Précise les arguments de la ligne de commandement transmis au programme lancé.|
|`currentDir`|string|Spécifie le chemin complet de l’annuaire vers la cible build. Cela sera automatiquement détecté à moins que ce paramètre ne soit défini.|
|`noDebug`|boolean|Précise s’il faut déboiffer le programme lancé. La valeur par défaut `false` de ce paramètre est si elle n’est pas spécifiée.|
|`stopOnEntry`|boolean|Précise s’il faut rompre dès le lancement du processus et que le débbuggeur s’attache. La valeur par défaut `false`pour ce paramètre est .|
|`remoteMachine`|string|Spécifie le nom de la machine à distance où le programme est lancé.|
|`env`|tableau| Spécifie une liste de valeur clé des variables de l’environnement personnalisée. env: "myEnv":"myVal".|
|`portName`|string|Spécifie le nom du port lors de l’attachement à un processus de fonctionnement.|
|`buildConfigurations`|tableau| Une paire de valeur clé qui spécifie le nom du mode de construction pour appliquer les configurations. Par `Debug` exemple, `Release` ou et les configurations à utiliser en fonction du mode de construction sélectionné.

## <a name="c-linux-properties"></a>Propriétés Linux

||||
|-|-|-|
|**Propriété**|**Type**|**Description**|
|`program`|string|Chemin complet pour programmer exécutable sur la machine à distance. Lors de l’utilisation `${debugInfo.fullTargetPath}` de CMake, la macro peut être utilisée comme valeur de ce champ.|
|`processId`|entier|ID de processus facultatif pour attacher le débagé.|
|`sourceFileMap`|object|Les cartes de fichiers sources facultatives sont passées au moteur de débogé. Format: `{ "\<Compiler source location>": "\<Editor source location>" }` `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`ou . Exemple : `{ "/home/user/foo": "C:\\foo" }` ou `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Voir [Les options de carte de fichier Source](#source_file_map_options).|
|`additionalProperties`|string|L’une des sourcesFileMapOptions. (Voir ci-dessous.)|
|`MIMode`|string|Indique le type de débbugger de console IM-activé que le MIDebugEngine se connectera à. Les valeurs autorisées sont "gdb", "lldb".|
|`args`|tableau|Les arguments de la ligne de commandement ont été transmis au programme.|
|`environment`|tableau|Variables de l’environnement à ajouter à l’environnement pour le programme. Exemple : [nom » : « calmar », « valeur » : « palourde » [ ]|
|`targetArchitecture`|string|L’architecture du débbuggee. Cela sera automatiquement détecté à moins que ce paramètre ne soit défini. Les valeurs autorisées sont x86, bras, bras64, mips, x64, amd64, x86_64.|
|`visualizerFile`|string|.natvis fichier à utiliser lors de débogage de ce processus. Cette option n’est pas compatible avec GDB assez d’impression. Voir "showDisplayString" si vous utilisez ce paramètre.|
|`showDisplayString`|boolean|Lorsqu’un visualiseurfile est spécifié, showDisplayString active la chaîne d’affichage. L’allumage de cette option peut entraîner des performances plus lentes pendant le débogage.|
|`remoteMachineName`|string|La machine Linux à distance qui héberge gdb et le programme de déboiffer. Utilisez le gestionnaire de connexions pour l’ajout de nouvelles machines Linux. Lors de l’utilisation `${debugInfo.remoteMachineName}` de CMake, la macro peut être utilisée comme valeur de ce champ.|
|`cwd`|string|Le répertoire de travail de la cible sur la machine à distance. Lors de l’utilisation `${debugInfo.defaultWorkingDirectory}` de CMake, la macro peut être utilisée comme valeur de ce champ. La valeur par défaut est la racine d’espace de travail à distance, sauf si elle est remplacée dans le fichier *CMakeLists.txt.*|
|`miDebuggerPath`|string|Le chemin vers le débâche IM(comme le gdb). Lorsqu’il n’est pas spécifié, il cherchera d’abord PATH pour le débbuggeur.|
|`miDebuggerServerAddress`|string|Adresse réseau du serveur de débâche IM à connecter. Exemple : localhost:1234.|
|`setupCommands`|tableau|Un ou plusieurs ordres GDB/LLDB doivent être exécutés afin de configurer le débâche sous-jacent. Exemple : `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Voir [les commandes de configuration de lancement](#launch_setup_commands).|
|`customLaunchSetupCommands`|tableau|Si vous êtes fourni, cela remplace les commandes par défaut utilisées pour lancer une cible par d’autres commandes. Par exemple, il peut s’agir d’une « fixation de cible » afin de s’attacher à un processus cible. Une liste de commande vide remplace les commandes de lancement par rien, ce qui peut être utile si le débbuggeur est fourni des options de lancement comme options de ligne de commande. Exemple : `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|string|La commande d’exécuter après le débbugger est entièrement configurée, pour faire fonctionner le processus cible. Les valeurs autorisées sont "exec-run", "exec-continue", "None". La valeur par défaut est "exec-run".|
|`debugServerPath`|string|Voie complète facultative pour déboiffer le serveur pour lancer. Par défaut à annuler.|
|`debugServerArgs`|string|Args serveur de débogé en option. Par défaut à annuler.|
|`filterStderr`|boolean|Rechercher le flux stderr pour le modèle serveur-commencé et le stderr de journal pour débocher la sortie. La valeur par défaut est `false`.|
|`coreDumpPath`|string|Voie complète facultative vers un fichier de décharge de base pour le programme spécifié. Par défaut à annuler.|
externalConsole|boolean|Si c’est vrai, une console est lancée pour le débbuggee. Si `false`, aucune console n’est lancée. La valeur par défaut est `false`. REMARQUE : Cette option est ignorée dans certains cas pour des raisons techniques.|
|`pipeTransport`|string|Lorsque vous êtes présent, cela permet au débâmeur de se connecter à un ordinateur distant en utilisant un autre exécutable comme un tuyau qui relaiera l’entrée/sortie standard entre Visual Studio et le débâche IM (comme le gdb). Valeurs autorisées : une ou plusieurs [options de transport de tuyaux.](#pipe_transport_options)|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>Commandes d’installation de lancement

Utilisé avec `setupCommands` la propriété:

||||
|-|-|-|
|`text`|string|Le débagé debugger commande d’exécuter.|
|`description`|string|Description facultative pour la commande.|
|`ignoreFailures`|boolean|Si c’est vrai, les échecs de la commande doivent être ignorés. La valeur par défaut est `false`.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>Options de transport de tuyaux

Utilisé avec `pipeTransport` la propriété:

||||
|-|-|-|
|`pipeCwd`|string|Le chemin entièrement qualifié vers l’annuaire de travail pour le programme de pipe.|
|`pipeProgram`|string|La commande de tuyau entièrement qualifiée pour exécuter.|
|`pipeArgs`|tableau|Les arguments de la ligne de commande sont passés au programme de tuyauterie pour configurer la connexion.|
|`debuggerPath`|string|Le chemin complet vers le débbugger sur la machine cible, par exemple /usr/bin/gdb.|
|`pipeEnv`|object|Les variables de l’environnement sont passées au programme de canalisations.|
|`quoteArgs`|boolean|Si les arguments individuels contiennent des caractères (tels que des espaces ou des onglets), devrait-il être cité? Si `false`, la commande de débogénaire ne sera plus automatiquement citée. La valeur par défaut est `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>Options de carte de fichier source

Utilisation avec `sourceFileMap` la propriété:

||||
|-|-|-|
|`editorPath`|string|L’emplacement du code source pour l’éditeur à localiser.|
|`useForBreakpoints`|boolean|Lors du réglage des points d’arrêt, cette cartographie source doit être utilisée. Si `false`, seul le nom de fichier et le numéro de ligne est utilisé pour définir les points de rupture. Si `true`, les points de rupture seront définis avec le chemin complet vers le fichier et le numéro de ligne seulement lorsque cette cartographie source est utilisée. Dans le cas contraire, il suffit de nom de fichier et de numéro de ligne sera utilisé lors de la configuration des points de rupture. La valeur par défaut est `true`.|
