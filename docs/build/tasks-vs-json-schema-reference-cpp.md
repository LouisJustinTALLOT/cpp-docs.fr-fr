---
title: informations de référence sur les schémas TasksC++. vs. JSON ()
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: cc6b2983d3cc3d40449357a554df5feee38c21d9
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556654"
---
# <a name="tasksvsjson-schema-reference-c"></a>informations de référence sur les schémas TasksC++. vs. JSON ()

Pour indiquer à Visual Studio comment générer votre code source dans un projet de dossier ouvert, ajoutez un fichier *Tasks. vs. JSON* . Vous pouvez définir ici une tâche arbitraire, puis l’appeler à partir du menu contextuel **Explorateur de solutions** . Les projets CMake n’utilisent pas ce fichier, car toutes les commandes de génération sont spécifiées dans *fichier CMakeLists. txt*. Pour les systèmes de génération autres que CMake, *Tasks. vs. JSON* vous permet de spécifier des commandes de génération et d’appeler des scripts de génération. Pour obtenir des informations générales sur l’utilisation de *Tasks. vs. JSON*, consultez [personnaliser les tâches de génération et de débogage pour le développement « ouvrir un dossier »](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

Une tâche a une propriété `type` qui peut avoir l’une des quatre valeurs suivantes : `default`, `launch`, `remote`ou `msbuild`. La plupart des tâches doivent utiliser `launch`, sauf si une connexion à distance est requise.

## <a name="default-properties"></a>Propriétés par défaut

Les propriétés par défaut sont disponibles pour tous les types de tâches :

||||
|-|-|-|
|**Property**|**Type**|**Description**|
|`taskLabel`|string| (Obligatoire.) Spécifie l’étiquette de tâche utilisée dans l’interface utilisateur.|
|`appliesTo`|string| (Obligatoire.) Spécifie les fichiers sur lesquels la commande peut être exécutée. L’utilisation de caractères génériques est prise en charge, par exemple : " *", "* . cpp", "/*. txt"|
|`contextType`|string| Valeurs autorisées : « Custom », « Build », « Clean », « Rebuild ». Détermine où la tâche s’affiche dans le menu contextuel. La valeur par défaut est « Custom ».|
|`output`|string| Spécifie une balise de sortie pour votre tâche.|
|`inheritEnvironments`|Tableau .| Spécifie un ensemble de variables d’environnement héritées de plusieurs sources. Vous pouvez définir des variables dans des fichiers comme *CMakeSettings. JSON* ou *CppProperties. JSON* et les mettre à disposition du contexte de tâche. **Visual Studio 16,4 :** : spécifiez les variables d’environnement pour chaque tâche à l’aide de la syntaxe `env.VARIABLE_NAME`. Pour annuler la définition d’une variable, affectez-lui la valeur « null ».|
|`passEnvVars`|boolean| Spécifie s’il faut inclure des variables d’environnement supplémentaires dans le contexte de la tâche. Ces variables sont différentes de celles définies à l’aide de la propriété `envVars`. La valeur par défaut est « true ».|

## <a name="launch-properties"></a>Propriétés de lancement

Lorsque le type de tâche est `launch`, ces propriétés sont disponibles :

||||
|-|-|-|
|**Property**|**Type**|**Description**|
|`command`|string| Spécifie le chemin d’accès complet du processus ou du script à lancer.|
|`args`|Tableau .| Spécifie une liste séparée par des virgules des arguments passés à la commande.|
|`launchOption`|string| Valeurs autorisées : « None », « ContinueOnError », « IgnoreError ». Spécifie comment continuer avec la commande lorsqu’il y a des erreurs.|
|`workingDirectory`|string| Spécifie le répertoire dans lequel la commande sera exécutée. La valeur par défaut est le répertoire de travail actuel du projet.|
|`customLaunchCommand`|string| Spécifie une personnalisation de portée globale à appliquer avant d’exécuter la commande. Utile pour définir des variables d’environnement telles que% PATH%.|
|`customLaunchCommandArgs`|string| Spécifie des arguments pour customLaunchCommand. (Requiert `customLaunchCommand`.)|
 `env`| Spécifie une liste de valeurs clés de variables d’environnement personnalisées. Par exemple, "myEnv" : "myVal"|
|`commands`|Tableau .| Spécifie une liste de commandes à appeler dans l’ordre.|

### <a name="example"></a>Exemple

Les tâches suivantes appellent *Make. exe* lorsqu’un Makefile est fourni dans le dossier et que l’environnement de `Mingw64` a été défini dans *CppProperties. JSON*, comme indiqué dans la [référence de schéma CppProperties. JSON](cppproperties-schema-reference.md#user_defined_environments):

```json
 {
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "gcc make",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make"
    },
    {
      "taskLabel": "gcc clean",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make",
      "args": ["clean"]
    }
  ]
}
```

Ces tâches peuvent être appelées à partir du menu contextuel quand vous cliquez avec le bouton droit sur un fichier *. cpp* dans **Explorateur de solutions**.

## <a name="remote-properties"></a>Propriétés distantes

Les tâches à distance sont activées lorsque vous installez le C++ développement Linux avec une charge de travail et ajoutez une connexion à un ordinateur distant à l’aide du gestionnaire de connexions Visual Studio. Une tâche à distance exécute des commandes sur un système distant et peut également y copier des fichiers.

Lorsque le type de tâche est `remote`, ces propriétés sont disponibles :

||||
|-|-|-|
|**Property**|**Type**|**Description**|
|`remoteMachineName`|string|Nom de la machine distante. Doit correspondre à un nom d’ordinateur dans le **Gestionnaire de connexions**.|
|`command`|string|Commande à envoyer à l’ordinateur distant. Par défaut, les commandes sont exécutées dans le répertoire $HOME sur le système distant.|
|`remoteWorkingDirectory`|string|Répertoire de travail actuel sur l’ordinateur distant.|
|`localCopyDirectory`|string|Répertoire local à copier sur la machine distante. La valeur par défaut est le répertoire de travail actuel.|
|`remoteCopyDirectory`|string|Répertoire sur l’ordinateur distant dans lequel `localCopyDirectory` est copié.|
|`remoteCopyMethod`|string| Méthode à utiliser pour la copie. Valeurs autorisées : « None », « SFTP », « rsync ». la synchronisation d’annuaire est recommandée pour les grands projets.|
|`remoteCopySourcesOutputVerbosity`|string| Valeurs autorisées : « normal », « Verbose », « diagnostic ».|
|`rsyncCommandArgs`|string|La valeur par défaut est « -t--delete ».|
|`remoteCopyExclusionList`|Tableau .|Liste de fichiers séparés par des virgules dans `localCopyDirectory` à exclure des opérations de copie.|

### <a name="example"></a>Exemple

La tâche suivante s’affiche dans le menu contextuel lorsque vous cliquez avec le bouton droit sur *main. cpp* dans **Explorateur de solutions**. Il dépend d’un ordinateur distant appelé `ubuntu` dans le **Gestionnaire de connexions**. La tâche copie le dossier actuellement ouvert dans Visual Studio dans le répertoire `sample` sur l’ordinateur distant, puis appelle g + + pour générer le programme.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Build",
      "appliesTo": "main.cpp",
      "type": "remote",
      "contextType": "build",
      "command": "g++ main.cpp",
      "remoteMachineName": "ubuntu",
      "remoteCopyDirectory": "~/sample",
      "remoteCopyMethod": "sftp",
      "remoteWorkingDirectory": "~/sample/hello",
      "remoteCopySourcesOutputVerbosity": "Verbose"
    }
  ]
}
```

## <a name="msbuild-properties"></a>MSBuild (propriétés)

Lorsque le type de tâche est `msbuild`, ces propriétés sont disponibles :

||||
|-|-|-|
|**Property**|**Type**|**Description**|
|`verbosity`|string| Spécifie les valeurs verbosityAllowed de sortie de génération du projet MSBuild : « quiet », « minimal », « normal », « detailed », « diagnostic ».|
|`toolsVersion`|string| Spécifie la version de l’ensemble d’outils pour générer le projet, par exemple "2,0", "3,5", "4,0", "Current". La valeur par défaut est « Current ».|
|`globalProperties`|Objet|Spécifie une liste de valeurs clés des propriétés globales à transmettre au projet, par exemple, « configuration » : « version finale »|
|`properties`|Objet| Spécifie une liste de valeurs de clé de propriétés de projet supplémentaires uniquement.|
|`targets`|Tableau .| Spécifie la liste des cibles à appeler, dans l’ordre, sur le projet. La cible par défaut du projet est utilisée si aucun n’est spécifié.|
