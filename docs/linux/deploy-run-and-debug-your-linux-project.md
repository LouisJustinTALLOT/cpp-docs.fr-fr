---
title: Déployer, exécuter et déboguer votre projet C++ MSBuild Linux dans Visual Studio
description: Décrit comment compiler, exécuter et déboguer du code sur la cible distante à partir d’un projet Linux C++ dans Visual Studio.
ms.date: 08/08/2020
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 7c038e1903fe029e04e8e9e9e41c11c7bff61ee2
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334193"
---
# <a name="deploy-run-and-debug-your-linux-msbuild-project"></a>Déployer, exécuter et déboguer votre projet Linux MSBuild

::: moniker range="msvc-140"
La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur. Pour consulter la documentation de ces versions, définissez la liste déroulante **version** située au-dessus de la table des matières dans **Visual Studio 2017** ou **Visual Studio 2019**.
::: moniker-end

Une fois que vous avez créé un projet Linux C++ dans Visual Studio et que vous vous êtes connecté au projet à l’aide du [Gestionnaire de connexions Linux](connect-to-your-remote-linux-computer.md), vous pouvez exécuter et déboguer le projet. Vous compilez, exécutez et déboguez le code sur la cible distante.

::: moniker range="msvc-160"

**Visual Studio 2019 version 16.1** vous pouvez cibler différents systèmes Linux pour le débogage et la génération. Par exemple, vous pouvez utiliser la compilation croisée sur x64 et déployer sur un appareil ARM lors du ciblage de scénarios IoT. Pour plus d’informations, consultez [Spécifier des machines différentes pour effectuer le build et déboguer](#separate_build_debug) plus loin dans cet article.

::: moniker-end

Il existe plusieurs façons de manipuler et déboguer votre projet Linux.

- Vous pouvez utiliser les fonctionnalités de débogage standard de Visual Studio, comme les points d’arrêt, les fenêtres Espion et le pointage sur une variable. Ces méthodes vous permettent de déboguer votre projet comme vous le faites habituellement pour d’autres types de projets.

- Affichez la sortie de l’ordinateur cible dans la fenêtre de console Linux. Vous pouvez également utiliser la console pour envoyer les entrées à l’ordinateur cible.

## <a name="debug-your-linux-project"></a>Déboguer votre projet Linux

1. Sélectionnez le mode de débogage dans la page de propriétés **Débogage**.

   ::: moniker range="msvc-160"

   GDB est utilisé pour déboguer les applications exécutées sur Linux. Lors du débogage sur un système distant (pas WSL), GDB peut s’exécuter dans deux modes différents, que vous pouvez sélectionner à partir de l’option **Mode de débogage** dans la page de propriétés **Débogage** du projet :

   ![Capture d’écran de la boîte de dialogue pages de propriétés de l’application console Linux de Visual Studio 2019 avec les propriétés de configuration > le débogage sélectionné et le mode de débogage mis en surbrillance avec G B D sélectionné et mis en surbrillance dans la liste déroulante.](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="msvc-150"

   GDB est utilisé pour déboguer les applications exécutées sur Linux. GDB peut s’exécuter dans deux modes différents, que vous pouvez sélectionner à partir de l’option **Mode de débogage** dans la page de propriétés **Débogage** du projet :

   ![Capture d’écran de la boîte de dialogue pages de propriétés de l’application console Linux de Visual Studio 2017 avec les propriétés de configuration > le débogage sélectionné et le mode de débogage mis en surbrillance avec G B D sélectionné et mis en surbrillance dans la liste déroulante.](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - En mode **gdbserver** , GDB s’exécute localement et se connecte à gdbserver sur le système distant.

   - En mode **gdb** , le débogueur Visual Studio exécute GDB sur le système distant. Il s’agit d’une meilleure option si la version locale de GDB n’est pas compatible avec la version installée sur l’ordinateur cible. Il s’agit du seul mode pris en charge par la fenêtre de console Linux.

   > [!NOTE]
   > Si vous ne pouvez pas atteindre les points d’arrêt en mode de débogage gdbserver, essayez le mode gdb. Vous devez d’abord [installer](download-install-and-setup-the-linux-development-workload.md) gdb sur la cible distante.

1. Sélectionnez la cible distante dans la barre d’outils **Déboguer** standard de Visual Studio.

   Lorsque la cible distante est disponible, vous voyez qu’elle est indiquée par un nom ou une adresse IP.

   ![Cible distante](media/remote_target.png)

   Si vous ne vous êtes pas encore connecté à la cible distante, vous verrez une instruction permettant d’utiliser le [Gestionnaire de connexions Linux](connect-to-your-remote-linux-computer.md) pour vous connecter à la cible distante.

   ![Architecture distante](media/architecture.png)

1. Définissez un point d’arrêt en cliquant dans la marge gauche d’une section de code qui s’exécute correctement.

   Un point rouge s’affiche sur la ligne de code où vous avez défini le point d’arrêt.

1. Appuyez sur **F5** (ou **Déboguer > Démarrer le débogage** ) pour démarrer le débogage.

   Quand vous démarrez le débogage, l’application est compilée sur la cible distante avant de démarrer. Les erreurs de compilation éventuelles s’affichent dans la fenêtre **Liste d’erreurs**.

   S’il n’y a aucune erreur, l’application démarre et le débogueur s’interrompt au point d’arrêt.

   ![Atteindre un point d’arrêt](media/hit_breakpoint.png)

   Maintenant, vous pouvez interagir avec l’application dans son état actuel, afficher les variables et exécuter le code pas à pas en appuyant sur des touches de commande (par exemple, **F10** ou **F11** ).

1. Si vous souhaitez utiliser la console Linux pour interagir avec votre application, sélectionnez **Déboguer > Console Linux**.

   ![Menu de console Linux](media/consolemenu.png)

   Cette console affiche toutes les sorties de console de l’ordinateur cible et les envoie à l’ordinateur cible.

   ![Fenêtre de console Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-projects"></a>Configurer d’autres options de débogage (projets MSBuild)

- Vous pouvez passer les arguments de ligne de commande à l’exécutable en utilisant l’élément **Arguments de programme** dans la page de propriétés **Débogage** du projet.
- Vous pouvez exporter la `DISPLAY` variable d’environnement à l’aide de la **commande de prélancement** dans les pages de propriétés de **débogage** du projet. Par exemple : `export DISPLAY=:0.0`

   ![Arguments de programme](media/settings_programarguments.png)

- Vous pouvez passer des options de débogueur spécifiques à GDB à l’aide de l’entrée **Commandes de débogueur supplémentaires**.  Par exemple, il est conseillé d’ignorer les signaux d’instruction non conforme (SIGILL).  Vous pouvez utiliser la commande **handle** pour le faire en ajoutant ce qui suit à l’entrée **Commandes de débogueur supplémentaires** comme indiqué ci-dessus :

   `handle SIGILL nostop noprint`
   
- Vous pouvez spécifier le chemin d’accès au GDB utilisé par Visual Studio à l’aide de l’élément de **chemin d’accès gdb** dans la page de propriétés de **débogage** du projet. Cette propriété est disponible dans Visual Studio 2019 version 16,9 et versions ultérieures.

## <a name="debug-with-attach-to-process"></a>Déboguer avec Attacher au processus

La page de propriétés [Débogage](prop-pages/debugging-linux.md) pour les projets Visual Studio et les paramètres **Launch.vs.json** pour les projets CMake ont des paramètres qui vous permettent d’effectuer un attachement à un processus en cours d’exécution. Si vous avez besoin d’un contrôle supplémentaire au-delà de celui fourni dans ces paramètres, vous pouvez placer un fichier nommé `Microsoft.MIEngine.Options.xml` à la racine de votre solution ou espace de travail. Voici un exemple simple :

```xml
<?xml version="1.0" encoding="utf-8"?>
<SupplementalLaunchOptions>
    <AttachOptions>
      <AttachOptionsForConnection AdditionalSOLibSearchPath="/home/user/solibs">
        <ServerOptions MIDebuggerPath="C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\Common7\IDE\VC\Linux\bin\gdb\7.9\x86_64-linux-gnu-gdb.exe"
ExePath="C:\temp\ConsoleApplication17\ConsoleApplication17\bin\x64\Debug\ConsoleApplication17.out"/>
        <SetupCommands>
          <Command IgnoreFailures="true">-enable-pretty-printing</Command>
        </SetupCommands>
      </AttachOptionsForConnection>
    </AttachOptions>
</SupplementalLaunchOptions>
```

**AttachOptionsForConnection** contient une grande partie des attributs dont vous pouvez avoir besoin. L’exemple ci-dessus montre comment spécifier un emplacement pour rechercher des bibliothèques .so supplémentaires. L’élément enfant **ServerOptions** permet d’effectuer un attachement au processus distant avec gdbserver à la place. Pour ce faire, vous devez spécifier un client gdb local (celui fourni dans Visual Studio 2017 est illustré ci-dessus) et une copie locale du fichier binaire avec des symboles. L’élément **SetupCommands** permet de transmettre des commandes directement à gdb. Vous pouvez trouver toutes les options disponibles dans le [schéma LaunchOptions.xsd](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) sur GitHub.

::: moniker range="msvc-160"

## <a name="specify-different-machines-for-building-and-debugging-in-msbuild-based-linux-projects"></a><a name="separate_build_debug"></a> Spécifier des ordinateurs différents pour la génération et le débogage dans des projets Linux basés sur MSBuild

Dans Visual Studio 2019 version 16,1, vous pouvez séparer votre ordinateur de build distant de votre ordinateur de débogage distant pour les projets Linux basés sur MSBuild et les projets CMake qui ciblent un ordinateur Linux distant. Par exemple, vous pouvez maintenant utiliser la compilation croisée sur x64 et déployer sur un appareil ARM lors du ciblage de scénarios IoT.

Par défaut, l’ordinateur de débogage distant est le même que l’ordinateur de build distant ( **Propriétés de configuration**  >  **général**  >  **machine de build distante** ). Pour spécifier une nouvelle machine de débogage à distance, cliquez sur le projet dans **l’Explorateur de solutions** et accédez à **Propriétés de configuration** > **Débogage** > **Machine de débogage distante**.  

![Machine de débogage Linux distante](media/linux-remote-debug-machine.png)

Le menu déroulant pour **Machine de débogage distante** est renseigné avec toutes les connexions à distance établies. Pour ajouter une nouvelle connexion à distance, accédez à **Outils**  >  **options**  >  **Cross Platform**  >  **Gestionnaire de connexions** multiplateforme ou recherchez « gestionnaire de connexions » dans **lancement rapide**. Vous pouvez également spécifier un nouveau répertoire de déploiement distant dans les pages de propriétés du projet ( **Propriétés de configuration**  >  **général**  >  **Répertoire de déploiement distant** général).

Par défaut, seuls les fichiers nécessaires pour le processus à déboguer sont déployés sur la machine de débogage distante. Vous pouvez utiliser **l’Explorateur de solutions** pour configurer les fichiers source qui seront déployés sur la machine de débogage distante. Lorsque vous cliquez sur un fichier source, vous voyez s’afficher un aperçu de ses propriétés de fichier directement sous le Explorateur de solutions.

![Fichiers à déployer Linux](media/linux-deployable-content.png)

La propriété **Contenu** spécifie si le fichier doit être déployé sur la machine de débogage distante. Vous pouvez désactiver entièrement le déploiement en accédant à **pages de propriétés**  >  **Configuration Manager** et en désactivant **déployer** pour la configuration souhaitée.

Dans certains cas, vous pouvez avoir besoin de davantage de contrôle sur le déploiement de votre projet. Par exemple, certains fichiers que vous souhaitez déployer peuvent être en dehors de votre solution ou vous souhaitez personnaliser votre répertoire de déploiement distant par fichier ou par répertoire. Dans ce cas, ajoutez le ou les blocs de code suivants à votre fichier .vcxproj et remplacez « example.cpp » par les noms des fichiers que vous souhaitez utiliser :

```xml

<ItemGroup>
   <RemoteDeploy Include="__example.cpp">
<!-- This is the source Linux machine, can be empty if DeploymentType is LocalRemote -->
      <SourceMachine>$(RemoteTarget)</SourceMachine>
      <TargetMachine>$(RemoteDebuggingTarget)</TargetMachine>
      <SourcePath>~/example.cpp</SourcePath>
      <TargetPath>~/example.cpp</TargetPath>
<!-- DeploymentType can be LocalRemote, in which case SourceMachine will be empty and SourcePath is a local file on Windows -->
      <DeploymentType>RemoteRemote</DeploymentType>
<!-- Indicates whether the deployment contains executables -->
      <Executable>true</Executable>
   </RemoteDeploy>
</ItemGroup>
```

### <a name="cmake-projects"></a>Projets CMake

Pour les projets CMake qui ciblent une machine Linux distante, vous pouvez spécifier une nouvelle machine de débogage distante dans launch.vs.json. Par défaut, la valeur de « remoteMachineName » est synchronisée avec la propriété « remoteMachineName » dans CMakeSettings.json, qui correspond à votre machine de build distante. Ces propriétés n’ont plus besoin de correspondre, et la valeur de « remoteMachineName » dans launch.vs.json détermine la machine distante utilisée pour le déploiement et le débogage.

![Machine de débogage CMake distante](media/cmake-remote-debug-machine.png)

IntelliSense propose une liste de toutes les connexions à distance établies. Vous pouvez ajouter une nouvelle connexion à distance en accédant à **Outils**  >  **options**  >  **Cross Platform**  >  **Gestionnaire de connexions** multiplateforme ou en recherchant « gestionnaire de connexions » dans **lancement rapide**.

Si vous souhaitez avoir le contrôle total sur votre déploiement, vous pouvez ajouter le ou les blocs de code suivants au fichier launch.vs.json. N’oubliez pas de remplacer les valeurs d’espace réservé par de vraies valeurs :

```json
"disableDeploy": false,
"deployDirectory": "~\foo",
"deploy" : [
   {
      "sourceMachine": "127.0.0.1 (username=example1, port=22, authentication=Password)",
      "targetMachine": "192.0.0.1 (username=example2, port=22, authentication=Password)",
      "sourcePath": "~/example.cpp",
      "targetPath": "~/example.cpp",
      "executable": "false"
   }
]
```

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

- Pour déboguer les appareils ARM sur Linux, consultez ce billet de blog : [Debugging an embedded ARM device in Visual Studio](https://devblogs.microsoft.com/cppblog/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Voir aussi

[Débogage C++, propriétés (Linux C++)](prop-pages/debugging-linux.md)
