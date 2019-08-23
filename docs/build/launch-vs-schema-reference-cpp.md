---
title: informations de référence sur le schéma Launch.C++vs. JSON ()
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 362a329289107f74cca2f20af62c8a28b4192575
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69978459"
---
# <a name="launchvsjson-schema-reference-c"></a>informations de référence sur le schéma Launch.C++vs. JSON ()

Utilisez le fichier *Launch. vs. JSON* pour configurer les paramètres de débogage. Pour créer le fichier. Cliquez avec le bouton droit sur un fichier exécutable dans **Explorateur de solutions** et choisissez **paramètres de débogage et de lancement**. Choisissez l’option qui correspond le mieux à votre projet, puis utilisez les propriétés suivantes pour modifier la configuration en fonction des besoins:

## <a name="default-properties"></a>Propriétés par défaut

||||
|-|-|-|
|**Propriété**|**Type**|**Description**|
|`name`|string|Spécifie le nom de l’entrée dans la liste déroulante cible de débogage.|
|`type`|string|Spécifie si le projet est une dll ou. exe (par défaut,. exe)|
|`project`|string|Spécifie le chemin d’accès relatif au fichier projet.|
|`projectTarget`|string|Spécifie la cible facultative appelée lors de `project`la génération. Il `projectTarget` doit déjà exister et correspondre au nom figurant dans la liste déroulante **cible** de débogage.|
|`debugType`|string|Spécifie le mode de débogage en fonction du type de code (natif, managé ou mixte). Cela sera détecté automatiquement, sauf si ce paramètre est défini. Valeurs autorisées: «Native», «Managed», «mixed».|
|`inheritEnvironments`|array|Spécifie un ensemble de variables d’environnement héritées de plusieurs sources. Vous pouvez définir des variables dans des fichiers comme CMakeSettings. JSON ou CppProperties. JSON et les mettre à disposition du contexte de débogage|
|`args`|array|Spécifie les arguments de ligne de commande passés au programme lancé.|
|`currentDir`|string|Spécifie le chemin d’accès complet au répertoire de la cible de génération. Cela sera détecté automatiquement, sauf si ce paramètre est défini.|
|`noDebug`|booléenne|Spécifie s’il faut déboguer le programme lancé. La valeur par défaut de ce paramètre `false` est si elle n’est pas spécifiée.|
|`stopOnEntry`|booléenne|Spécifie s’il faut arrêter une prochaine fois que le processus est lancé et que le débogueur est attaché. La valeur par défaut de ce paramètre `false`est.|
|`remoteMachine`|string|Spécifie le nom de l’ordinateur distant sur lequel le programme est lancé.|
|`env`|array| Spécifie une liste de valeurs clés de variables d’environnement personnalisées. env: {"myEnv": "myVal"}.|
|`portName`|string|Spécifie le nom du port lors de l’attachement à un processus en cours d’exécution.|
|`buildConfigurations`|array| Paire clé-valeur qui spécifie le nom du mode de génération à appliquer aux configurations. Par exemple, `Debug` ou `Release` et les configurations à utiliser en fonction du mode de génération sélectionné.

## <a name="c-linux-properties"></a>C++Propriétés Linux

||||
|-|-|-|
|**Propriété**|**Type**|**Description**|
|`program`|string|Chemin d’accès complet à l’exécutable du programme sur l’ordinateur distant. Lorsque vous utilisez cmake, la `${debugInfo.fullTargetPath}` macro peut être utilisée comme valeur de ce champ.|
|`processId`|integer|ID de processus facultatif auquel le débogueur doit être attaché.|
|`sourceFileMap`|objet|Mappages de fichiers sources facultatifs passés au moteur de débogage. Format: `{ "\<Compiler source location>": "\<Editor source location>" }` ou `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. Exemple: `{ "/home/user/foo": "C:\\foo" }` ou `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Consultez [options de mappage de fichier source](#source_file_map_options).|
|`additionalProperties`|string|L’un des sourceFileMapOptions. (Voir ci-dessous.)|
|`MIMode`|string|Indique le type de débogueur de console compatible MI auquel le MIDebugEngine se connectera. Les valeurs autorisées sont «gdb», «lldb».|
|`args`|array|Arguments de ligne de commande passés au programme.|
|`environment`|array|Variables d’environnement à ajouter à l’environnement pour le programme. Exemple: [{"Name": "squid", "value": "clamation"}].|
|`targetArchitecture`|string|Architecture du programme débogué. Cela sera détecté automatiquement, sauf si ce paramètre est défini. Les valeurs autorisées sont x86, ARM, arm64, mips, x64, amd64, x86_64.|
|`visualizerFile`|string|fichier. natvis à utiliser lors du débogage de ce processus. Cette option n’est pas compatible avec GDB Pretty Printing. Consultez «showDisplayString» si vous utilisez ce paramètre.|
|`showDisplayString`|booléenne|Quand un visualizerFile est spécifié, showDisplayString active la chaîne d’affichage. L’activation de cette option peut entraîner une baisse des performances lors du débogage.|
|`remoteMachineName`|string|L’ordinateur Linux distant qui héberge gdb et le programme à déboguer. Utilisez le gestionnaire de connexions pour l’ajout de nouvelles machines Linux. Lorsque vous utilisez cmake, la `${debugInfo.remoteMachineName}` macro peut être utilisée comme valeur de ce champ.|
|`cwd`|string|Répertoire de travail de la cible sur la machine distante. Lorsque vous utilisez cmake, la `${debugInfo.defaultWorkingDirectory}` macro peut être utilisée comme valeur de ce champ. La valeur par défaut est la racine de l’espace de travail distant, sauf si elle a été remplacée dans le fichier *fichier CMakeLists. txt* .|
|`miDebuggerPath`|string|Chemin d’accès au débogueur MI (par exemple, gdb). Quand il n’est pas spécifié, il recherche d’abord le débogueur dans PATH.|
|`miDebuggerServerAddress`|string|Adresse réseau du serveur du débogueur compatible MI auquel se connecter. Exemple: localhost: 1234.|
|`setupCommands`|array|Une ou plusieurs commandes GDB/LLDB à exécuter afin de configurer le débogueur sous-jacent. Exemple : `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Consultez [lancer les commandes de configuration](#launch_setup_commands).|
|`customLaunchSetupCommands`|array|S’il est fourni, cela remplace les commandes par défaut utilisées pour lancer une cible avec d’autres commandes. Par exemple, il peut s’agir de «-Target-Attach» afin d’effectuer un attachement à un processus cible. Une liste de commandes vide remplace les commandes Launch sans rien, ce qui peut être utile si le débogueur est fourni à des options de démarrage en tant qu’options de ligne de commande. Exemple : `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|string|Commande à exécuter après la configuration complète du débogueur, pour provoquer l’exécution du processus cible. Les valeurs autorisées sont "exec-Run", "exec-continue", "none". La valeur par défaut est «exec-Run».|
|`debugServerPath`|string|Chemin complet facultatif pour déboguer le serveur à lancer. La valeur par défaut est null.|
|`debugServerArgs`|string|Arguments de serveur de débogage facultatifs. La valeur par défaut est null.|
|`filterStderr`|booléenne|Recherchez dans le flux STDERR le modèle Démarré par le serveur et log stderr pour déboguer la sortie. La valeur par défaut est `false`.|
|`coreDumpPath`|string|Chemin complet facultatif d’un fichier d’image mémoire de base pour le programme spécifié. La valeur par défaut est null.|
externalConsole|booléenne|Si la valeur est true, une console est lancée pour l’élément débogué. Si `false`la condition est, aucune console n’est lancée. La valeur par défaut est `false`. REMARQUE : Cette option est ignorée dans certains cas pour des raisons techniques.|
|`pipeTransport`|string|Le cas échéant, cela indique au débogueur qu’il doit se connecter à un ordinateur distant à l’aide d’un autre exécutable en tant que canal qui relaie les entrées/sorties standard entre Visual Studio et le débogueur MI (par exemple, gdb). Valeurs autorisées: une ou plusieurs [options de transport de canal](#pipe_transport_options).|


## <a name="launch_setup_commands"></a>Lancer les commandes d’installation

Utilisé avec la `setupCommands` propriété:

||||
|-|-|-|
|`text`|string|Commande du débogueur à exécuter.|
|`description`|string|Description facultative de la commande.|
|`ignoreFailures`|booléenne|Si la valeur est true, les échecs de la commande doivent être ignorés. La valeur par défaut est `false`.|

## <a name = "pipe_transport_options"></a>Options de transport de canal

Utilisé avec la `pipeTransport` propriété:

||||
|-|-|-|
|`pipeCwd`|string|Chemin d’accès complet au répertoire de travail du programme de canal.|
|`pipeProgram`|string|Commande de canal qualifié complet à exécuter.|
|`pipeArgs`|array|Arguments de ligne de commande passés au programme canal pour configurer la connexion.|
|`debuggerPath`|string|Le chemin d’accès complet au débogueur sur l’ordinateur cible, par exemple/usr/bin/gdb.|
|`pipeEnv`|objet|Variables d’environnement passées au programme pipe.|
|`quoteArgs`|booléenne|Si des arguments individuels contiennent des caractères (tels que des espaces ou des tabulations), doivent-ils être placés entre guillemets? Si `false`la condition est, la commande du débogueur n’est plus automatiquement placée entre guillemets. La valeur par défaut est `true`.|

## <a name="source_file_map_options"></a>Options de mappage de fichier source

Utilisez avec la `sourceFileMap` propriété:

||||
|-|-|-|
|`editorPath`|string|Emplacement du code source de l’éditeur à localiser.|
|`useForBreakpoints`|booléenne|Lors de la définition de points d’arrêt, ce mappage de source doit être utilisé. Si `false`la valeur est, seuls le nom de fichier et le numéro de ligne sont utilisés pour définir des points d’arrêt. Si `true`la valeur est, les points d’arrêt sont définis avec le chemin d’accès complet au fichier et le numéro de ligne uniquement lorsque ce mappage de source est utilisé. Sinon, seul le nom de fichier et le numéro de ligne seront utilisés lors de la définition de points d’arrêt. La valeur par défaut est `true`.|
