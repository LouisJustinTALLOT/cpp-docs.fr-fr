---
title: Projets CMake dans Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 04/28/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0e7852ad3fbd88b815aea8266bafc2879494d8a
ms.sourcegitcommit: f923f667065cd6c4203d10ca9520600ee40e5f84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900665"
---
# <a name="cmake-projects-in-visual-c"></a>Projets CMake dans Visual C++

Cet article suppose que vous êtes familiarisé avec CMake, un outil open source multiplateforme qui permet de définir les processus de génération qui s’exécutent sur plusieurs plateformes.

Dans Visual Studio 2015, les utilisateurs de Visual Studio peuvent utiliser un [générateur CMake](https://cmake.org/cmake/help/v3.9/manual/cmake-generators.7.html) pour générer des fichiers projet MSBuild, consommés ensuite par l’IDE pour IntelliSense, la navigation et la compilation. 

À compter de Visual Studio 2017, le composant **Visual C++ Tools pour CMake** utilise la fonctionnalité **Ouvrir le dossier** pour activer l’IDE afin de consommer des fichiers projet CMake (comme CMakeLists.txt) directement pour IntelliSense et la navigation. Si vous utilisez un générateur Visual Studio, un fichier projet temporaire est généré et transmis à msbuild.exe, mais il n’est jamais chargé pour IntelliSense ou la navigation. 

**Visual Studio 2017 version 15.3** : La prise en charge est fournie pour les deux générateurs Ninja et Visual Studio.

**Visual Studio 2017 version 15.4** : La prise en charge est ajoutée pour CMake sur Linux. Pour plus d’informations, consultez [Configurer un projet CMake Linux](../linux/cmake-linux-project.md).

**Visual Studio 2017 version 15.5** : La prise en charge est ajoutée pour l’importation d’un cache CMake existant. Visual Studio extrait automatiquement des variables personnalisées et crée un fichier CMakeSettings.json prérempli.

**Visual Studio 2017 version 15.7** : La prise en charge est ajoutée pour la désactivation de la génération automatique du cache, l’affichage des cibles dans **l’Explorateur de solutions**et la compilation de fichier unique.

## <a name="installation"></a>Installation

**Visual C++ Tools pour CMake** est installé par défaut dans le cadre de la charge de travail **Développement Desktop en C++**.

![Composant CMake dans la charge de travail Desktop C++](media/cmake-install.png)
 
## <a name="ide-integration"></a>Intégration à l’IDE

Quand vous choisissez **Fichier | Ouvrir | Dossier** pour ouvrir un dossier contenant un fichier CMakeLists.txt, les événements suivants se produisent :

- Visual Studio ajoute un élément de menu **CMake** au menu principal, avec des commandes pour voir et modifier les scripts CMake.
- **L’Explorateur de solutions** affiche la structure de dossiers et les fichiers.
- Visual Studio exécute CMake.exe et génère le cache CMake pour la *configuration* par défaut, qui est x86 Debug. La ligne de commande CMake s’affiche dans la **fenêtre Sortie**, ainsi que la sortie supplémentaire de CMake.  **Visual Studio 2017 versions 15.7 et ultérieures** : La génération automatique du cache peut être désactivée dans la boîte de dialogue **Outils | Options | CMake | Général**.
- En arrière-plan, Visual Studio démarre pour indexer les fichiers sources afin d’activer IntelliSense, les informations de navigation, la refactorisation et ainsi de suite. Pendant que vous travaillez, Visual Studio surveille les changements dans l’éditeur et sur le disque pour synchroniser son index avec les sources.
 
Vous pouvez ouvrir des dossiers avec un nombre quelconque de projets CMake. Visual Studio détecte et configure tous les fichiers CMakeLists.txt « racines » dans votre espace de travail. Les opérations CMake (configurer, générer, déboguer) ainsi que les opérations C++ IntelliSense et de navigation sont disponibles pour tous les projets CMake dans votre espace de travail.

![Projet CMake avec plusieurs racines](media/cmake-multiple-roots.png)  

**Visual Studio 2017 versions 15.7 et ultérieures** : Vous pouvez également voir vos projets organisés logiquement par cibles. Choisissez **Targets view** (Affichage des cibles) dans la liste déroulante dans la barre d’outils de **l’Explorateur de solutions** :

![Bouton Affichage des cibles de CMake](media/cmake-targets-view.png)

## <a name="import-an-existing-cache"></a>Importer un cache existant

Quand vous importez un fichier CMakeCache.txt existant, Visual Studio extrait automatiquement des variables personnalisées à partir desquelles il crée un fichier CMakeSettings.json prérempli. Le cache d’origine n’est modifié en aucune façon et peut encore être utilisé à partir de la ligne de commande ou avec n’importe quel outil ou IDE qui a été utilisé pour sa génération. Le nouveau fichier CMakeSettings.json est placé à côté du fichier CMakeLists.txt racine du projet. Visual Studio génère un nouveau cache en fonction du fichier de paramètres.  


**Visual Studio 2017 versions 15.7 et ultérieures** : Vous pouvez substituer la génération automatique du cache dans la boîte de dialogue **Outils | Options | CMake | Général**.

Le contenu du cache n’est pas importé en totalité.  Des propriétés comme le générateur et l’emplacement des compilateurs sont remplacées par les valeurs par défaut qui fonctionnent avec l’IDE.

### <a name="to-import-an-existing-cache"></a>Pour importer un cache existant

1. Dans le menu principal, choisissez **Fichier | Ouvrir | CMake** :

   ![Ouvrir CMake](media/cmake-file-open.png "Fichier, Ouvrir, CMake") 

   Cette opération lance l’Assistant **Importer CMake à partir du cache**. 
   
2. Accédez au fichier CMakeCache.txt à importer, puis cliquez sur **OK**. L’Assistant **Importer un projet CMake à partir du cache** apparaît :

   ![Importer un cache CMake](media/cmake-import-wizard.png "Ouvrir l’Assistant Importer un cache CMake") 

   Une fois l’Assistant terminé, vous pouvez voir le nouveau fichier CMakeCache.txt dans **l’Explorateur de solutions** à côté du fichier CMakeLists.txt racine dans votre projet.


## <a name="building-cmake-projects"></a>Génération de projets CMake

Pour générer un projet CMake, vous avez ces possibilités :

1. Sélectionnez la cible dans la liste déroulante **Déboguer** et appuyez sur **F5**, ou cliquez sur le bouton **Exécuter** (triangle vert). Le projet est d’abord généré automatiquement, comme une solution Visual Studio.
1. Cliquez avec le bouton droit sur CMakeLists.txt et sélectionnez **Générer** dans le menu contextuel. Si vous avez plusieurs cibles dans votre structure de dossiers, vous pouvez choisir de générer toutes les cibles ou une seule cible spécifique, ou
1. Dans le menu principal, sélectionnez **Générer | Générer la solution** (**F7** ou **Ctrl + Maj + B**). Vérifiez qu’une cible CMake est déjà sélectionnée dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**.

![Commande de menu de génération CMake](media/cmake-build-menu.png "Commande de menu de génération CMake") 

Si un générateur Visual Studio est sélectionné pour la configuration active, MSBuild.exe est appelé avec les arguments `-m -v:minimal`. Pour personnaliser la génération, dans le fichier CMakeSettings.json, vous pouvez spécifier des arguments de ligne de commande supplémentaires à passer au système de génération via la propriété `buildCommandArgs` :

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```

Comme attendu, les résultats de génération sont affichés dans la **fenêtre sortie** et la **Liste des erreurs**.
 
![Erreurs de génération CMake](media/cmake-build-errors.png "Erreurs de génération CMake")

Dans un dossier avec plusieurs cibles de génération, vous pouvez choisir l’élément **Générer** dans le menu **CMake** ou le menu contextuel de **CMakeLists.txt** pour spécifier la cible CMake à générer. Quand vous appuyez sur **Ctrl + Maj + B** dans un projet CMake, le document actif est généré.

## <a name="debug-the-project"></a>Déboguer le projet

Pour déboguer un projet CMake, choisissez la configuration souhaitée et appuyez sur **F5**, ou appuyez sur le bouton **Exécuter** dans la barre d’outils. Si le bouton **Exécuter** indique « Sélectionner un élément de démarrage », sélectionnez la flèche déroulante et choisissez la cible à exécuter. (Dans un projet CMake, l’option « Document actif » est uniquement valide pour les fichiers .cpp.) 

![Bouton d’exécution de CMake](media/cmake-run-button.png "Bouton d’exécution de CMake")

Les commandes **Exécuter** ou **F5** génèrent d’abord le projet si des modifications ont été apportées depuis la dernière génération.

## <a name="configure-cmake-debugging-sessions"></a>Configurer des sessions de débogage CMake

Toutes les cibles CMake exécutables figurent dans la liste déroulante **Élément de démarrage** dans la barre d’outils **Général**. Pour démarrer une session de débogage, sélectionnez-en une et lancez le débogueur.

![Liste déroulante d’éléments de démarrage CMake](media/cmake-startup-item-dropdown.png "Liste déroulante d’éléments de démarrage CMake")


Vous pouvez également démarrer une session de débogage à partir des menus de CMake.

Pour personnaliser les paramètres du débogueur pour toutes les cibles CMake exécutables dans votre projet, cliquez avec le bouton droit sur le fichier CMakeLists.txt et sélectionnez **Paramètres de débogage et de lancement**. Quand vous sélectionnez une cible CMake dans le sous-menu, un fichier appelé launch.vs.json est créé. Ce fichier est prérempli avec les informations de la cible CMake que vous avez sélectionnée et vous permet de spécifier des paramètres supplémentaires comme les arguments de programme ou le type de débogueur. Pour référencer une clé dans un fichier CMakeSettings.json, préfixez-la avec « CMake. » dans launch.vs.json. L’exemple suivant montre un fichier launch.vs.json simple qui tire (pull) la valeur de la clé « remoteCopySources » dans le fichier CMakeSettings.json pour la configuration actuellement sélectionnée :

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

Dès que vous enregistrez le fichier launch.vs.json, une entrée est créée dans la liste déroulante **Élément de démarrage** avec le nouveau nom. En modifiant le fichier launch.vs.json, vous pouvez créer autant de configurations de débogage que vous voulez pour n’importe quel nombre de cibles CMake.

**Visual Studio 2017 version 15.4** : Le fichier launch.vs.json prend en charge les variables qui sont déclarées dans CMakeSettings.json (voir ci-dessous) et qui s’appliquent à la configuration actuellement sélectionnée. Il a également une clé nommée « currentDir », qui définit le répertoire actuel de l’application de lancement :


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

## <a name="editing-cmakeliststxt-files"></a>Modification des fichiers CMakeLists.txt

Pour modifier un fichier CMakeLists.txt, cliquez avec le bouton droit sur le fichier dans **l’Explorateur de solutions** et choisissez **Ouvrir**. Si vous modifiez le fichier, une barre d’état jaune s’affiche pour vous informer qu’IntelliSense va effectuer la mise à jour et vous donne la possibilité d’annuler l’opération de mise à jour. Pour plus d’informations sur CMakeLists.txt, consultez la [documentation de CMake](https://cmake.org/documentation/).

   ![Modification du fichier CMakeLists.txt](media/cmake-cmakelists.png "Modification du fichier CMakeLists.txt")


Dès que vous enregistrez le fichier, l’étape de configuration s’exécute à nouveau automatiquement et affiche les informations dans la fenêtre **Sortie**. Les erreurs et les avertissements sont affichés dans la **Liste des erreurs** ou la fenêtre **Sortie**. Double-cliquez sur une erreur dans la **Liste des erreurs** pour accéder à la ligne concernée dans CMakeLists.txt.

   ![Erreurs du fichier CMakeLists.txt](media/cmake-cmakelists-error.png "Erreurs du fichier CMakeLists.txt")

## <a name="cmake_settings"></a> Paramètres de CMake et configurations personnalisées

Par défaut, Visual Studio fournit six configurations CMake (« x86-Debug », « x86-Release », « x64-Debug », « x64-Release », « Linux-Debug » et « Linux-Release »). Ces configurations définissent la façon dont CMake.exe est appelé afin de créer le cache CMake pour un projet donné. Pour modifier ces configurations ou créer une configuration personnalisée, choisissez **CMake | Changer les paramètres CMake**, puis choisissez le fichier CMakeLists.txt auxquels s’appliquent les paramètres. La commande **Changer les paramètres CMake** est également disponible dans le menu contextuel du fichier dans **l’Explorateur de solutions**. Cette commande crée un fichier CMakeSettings.json dans le dossier du projet. Ce fichier est utilisé pour recréer le fichier de cache CMake, par exemple, après une opération **Clean**. 

   ![Commande de menu principal CMake pour changer les paramètres](media/cmake-change-settings.png)

JSON IntelliSense vous permet de modifier le fichier CMakeSettings.json :

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

L’exemple suivant montre un exemple de configuration, que vous pouvez utiliser comme point de départ pour créer la vôtre dans CMakeSettings.json :

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

1. **name** : nom qui apparaît dans la liste déroulante des configurations C++. Cette valeur de propriété peut également être utilisée comme une macro, `${name}`, pour spécifier d’autres valeurs de propriété. Pour obtenir un exemple, consultez la définition de **buildRoot** dans CMakeSettings.json.
1. **generator** : correspond au commutateur **-G** et spécifie le générateur à utiliser. Cette propriété peut également être utilisée comme une macro, `${generator}`, pour spécifier d’autres valeurs de propriété. Visual Studio prend actuellement en charge les générateurs CMake suivants :

    - « Ninja »
    - « Visual Studio 14 2015 »
    - « Visual Studio 14 2015 ARM »
    - « Visual Studio 14 2015 Win64 »
    - « Visual Studio 15 2017 »
    - « Visual Studio 15 2017 ARM »
    - « Visual Studio 15 2017 Win64 »

Comme Ninja est conçu pour des vitesses de génération rapides plutôt que pour la flexibilité et la fonctionnalité, il est défini par défaut. Toutefois, certains projets CMake peuvent ne pas pouvoir être générés correctement avec Ninja. Si cela se produit, vous pouvez demander à CMake de générer un projet Visual Studio à la place.

Pour spécifier un générateur Visual Studio, ouvrez CMakeSettings.json à partir du menu principal en choisissant **CMake | Changer les paramètres CMake**. Supprimez « Ninja » et tapez « V ». Cela active IntelliSense, qui vous permet de choisir le générateur souhaité.

1. **buildRoot** : correspond au commutateur **-DCMAKE_BINARY_DIR** et spécifie où est créé le cache CMake. Si le dossier n’existe pas, il est créé.
1. **variables** : contient une paire nom-valeur de variables CMake qui sont passées sous la forme **-D**_name_**=**_value_ à CMake. Si vos instructions de génération de projet CMake spécifient l’ajout des variables directement dans le fichier de cache CMake, nous vous recommandons de les ajouter ici à la place.
1. **cmakeCommandArgs** : Spécifie tous les commutateurs supplémentaires que vous voulez passer à CMake.exe.
1. **configurationType** : Définit le type de configuration de génération du générateur sélectionné. Les valeurs actuellement prises en charge sont « Debug », « MinSizeRel », « Release » et « RelWithDebInfo ».
1. **ctestCommandArgs** : spécifie les commutateurs supplémentaires à passer à CTest durant l’exécution des tests.
1. **buildCommandArgs** : spécifie les commutateurs supplémentaires à passer au système de build sous-jacent. Par exemple, si vous passez -v quand vous utilisez le générateur Ninja, cela oblige Ninja à sortir des lignes de commande.

### <a name="environment-variables"></a>Variables d’environnement

CMakeSettings.json prend également en charge la consommation de variables d’environnement dans n’importe quelle propriété mentionnée ci-dessus. La syntaxe à utiliser est `${env.FOO}` pour développer la variable d’environnement %FOO%.
Vous avez également accès aux macros intégrées dans ce fichier :

- `${workspaceRoot}` : Fournit le chemin complet du dossier de l’espace de travail
- `${workspaceHash}` : Hachage de l’emplacement de l’espace de travail. Utile pour créer un identificateur unique pour l’espace de travail actuel (par exemple, à utiliser dans les chemins de dossier)
- `${projectFile}` : Chemin complet du fichier racine CMakeLists.txt
- `${projectDir}` : Chemin complet du dossier du fichier racine CMakeLists.txt
- `${thisFile}` : Chemin complet du fichier CMakeSettings.json
- `${name}` : Nom de la configuration
- `${generator}` : Nom du générateur CMake utilisé dans cette configuration

### <a name="ninja-command-line-arguments"></a>Arguments de ligne de commande Ninja

Si les cibles ne sont pas spécifiées, génère la cible « par défaut » (voir le manuel).

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Option|Description|
|--------------|------------|
| --version  | imprime la version de Ninja (« 1.7.1 »)|
|   -C DIR   | passe à DIR avant toute autre opération|
|   -f FILE  | spécifie le fichier d’entrée de génération (valeur par défaut = build.ninja)|
|   -j N     | exécute des travaux N en parallèle (valeur par défaut = 14, dérivée des processeurs disponibles)|
|   -k N     | continue jusqu’à ce que N travaux échouent (valeur par défaut = 1)|
|   -l N     | ne démarre pas de nouveaux travaux si la charge moyenne est supérieure à N|
|   -n      | test (n’exécute pas de commandes mais agit comme elles avaient réussi)|
|   -v       | affiche toutes les lignes de commande pendant la génération|
|   -d MODE  | active le débogage (utilisez -d list pour obtenir la liste des modes)|
|   -t TOOL  | exécute un sous-outil (utilisez -t list pour obtenir la liste des sous-outils). met fin aux options de niveau supérieur. Les autres indicateurs sont transmis à l’outil| 
|   -w FLAG  | ajuste les avertissements (utiliser -w list pour obtenir la liste des avertissements)|

### <a name="inherited-environments-visual-studio-2017-version-155"></a>Environnements hérités (Visual Studio 2017 version 15.5)
CMakeSettings.json prend désormais en charge les environnements hérités. Cette fonctionnalité vous permet (1) d’hériter les environnements par défaut et (2) de créer des variables d’environnement personnalisées qui sont passées à CMake.exe quand il s’exécute.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

L’exemple ci-dessus revient à exécuter **l’invite de commandes développeur pour VS 2017** avec les arguments **-arch=amd64 -host_arch=amd64**.

Le tableau suivant montre les valeurs par défaut et leurs équivalents de ligne de commande :

|Nom du contexte|Description|
|-----------|-----------------|
|vsdev|Environnement Visual Studio par défaut|
|msvc_x86|Compiler pour x86 à l’aide d’outils x86|
|msvc_arm| Compiler pour ARM à l’aide d’outils x86|
|msvc_arm64|Compiler pour ARM64 à l’aide d’outils x86|
|msvc_x86_x64|Compiler pour AMD64 à l’aide d’outils x86|
|msvc_x64_x64|Compiler pour AMD64 à l’aide d’outils 64 bits|
|msvc_arm_x64|Compiler pour ARM à l’aide d’outils 64 bits|
|msvc_arm64_x64|Compiler pour ARM64 à l’aide d’outils 64 bits|

### <a name="custom-environment-variables"></a>Variables d’environnement personnalisées
Dans CMakeSettings.json, vous pouvez définir des variables d’environnement personnalisées globalement ou par configuration dans la propriété **environments**. L’exemple suivant définit une variable globale, **BuildDir**, qui est héritée dans les configurations x86-Debug et de x64-Debug. Chaque configuration utilise la variable pour spécifier la valeur de la propriété **buildRoot** pour cette configuration. Notez également la façon dont chaque configuration utilise la propriété **inheritEnvironments** pour spécifier une variable qui s’applique uniquement à cette configuration.

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

Dans l’exemple suivant, la configuration x86-Debug définit sa propre valeur pour la propriété **BuildDir** et cette valeur remplace la valeur définie par la propriété globale **BuildDir** afin que **BuildRoot** prenne la valeur `D:\custom-builddir\x86-Debug`.

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir",
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ], 
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="cmake-configure-step"></a>Étape de configuration CMake

Quand des changements importants sont apportés aux fichiers CMakeSettings.json ou CMakeLists.txt, Visual Studio réexécute automatiquement l’étape de configuration CMake. Si l’étape de configuration se termine sans erreur, les informations collectées sont disponibles dans C++ IntelliSense et les services de langage, et également dans les opérations de génération et de débogage.

Quand plusieurs projets CMake utilisent le même nom de configuration CMake (par exemple, x86-Debug), ils sont tous configurés et générés (dans son propre dossier racine de build) quand cette configuration est sélectionnée. Vous pouvez déboguer les cibles de tous les projets CMake qui participent à cette configuration CMake.

   ![Élément de menu CMake Générer uniquement](media/cmake-build-only.png "Élément de menu CMake Générer uniquement")

Pour limiter les générations et les sessions de débogage à un sous-ensemble des projets dans l’espace de travail, créez une configuration avec un nom unique dans le fichier CMakeSettings.json et appliquez-le à ces projets uniquement. Quand cette configuration est sélectionnée, les commandes de génération et de débogage IntelliSense sont activées uniquement pour les projets spécifiés.

## <a name="troubleshooting-cmake-cache-errors"></a>Résolution des erreurs de cache CMake

Si vous avez besoin de plus d’informations sur l’état du cache CMake pour diagnostiquer un problème, ouvrez le menu principal de **CMake** ou le menu contextuel de **CMakeLists.txt** dans **l’Explorateur de solutions** pour exécuter l’une des commandes suivantes :

- **Afficher le cache** ouvre le fichier CMakeCache.txt à partir du dossier racine de build dans l’éditeur. (Toutes les modifications que vous apportez ici à CMakeCache.txt sont effacées si vous nettoyez le cache. Pour apporter des modifications qui persistent une fois le cache nettoyé, consultez [Paramètres CMake et configurations personnalisées](#cmake_settings) plus haut dans cet article.)
- **Ouvrir le dossier de cache** ouvre une fenêtre de l’Explorateur dans le dossier racine de build.  
- **Nettoyer le cache** supprime le dossier racine de build pour que la prochaine étape de configuration CMake démarre à partir d’un cache propre.
- **Générer le cache** force l’exécution de l’étape de génération même si Visual Studio considère l’environnement comme étant à jour.
 
**Visual Studio 2017 versions 15.7 et ultérieures** : La génération automatique du cache peut être désactivée dans la boîte de dialogue **Outils | Options | CMake | Général**.

## <a name="single-file-compilation"></a>Compilation de fichier unique

**Visual Studio 2017 versions 15.7 et ultérieures** : Pour générer un fichier unique dans un projet CMake, cliquez avec le bouton droit sur le fichier dans **l’Explorateur de solutions** et choisissez **Compiler**. Vous pouvez également générer le fichier qui est actuellement ouvert dans l’éditeur à l’aide du menu CMake principal :

![Compilation de fichier unique CMake](media/cmake-single-file-compile.png)