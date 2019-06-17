---
title: Déployer, exécuter et déboguer votre projet Linux C++ dans Visual Studio
description: Décrit comment compiler, exécuter et déboguer du code sur la cible distante au sein d’un projet Linux C++ dans Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 707915a502aafefee47af7e84b534e06ba678b3d
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821615"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Déployer, exécuter et déboguer un projet Linux

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

Une fois que vous avez créé un projet Linux C++ dans Visual Studio et que vous vous y êtes connecté par le biais du [Gestionnaire de connexions Linux](connect-to-your-remote-linux-computer.md), vous pouvez l’exécuter et le déboguer. Vous compilez, exécutez et déboguez le code sur la cible distante.

::: moniker range="vs-2019"

**Visual Studio 2019 version 16.1** vous pouvez cibler différents systèmes Linux pour le débogage et la génération. Spécifiez la machine de build dans la page de propriétés **Général** et la machine de débogage dans la page de propriétés **Débogage**.

::: moniker-end

Il existe plusieurs façons de manipuler et déboguer votre projet Linux.

- Vous pouvez utiliser les fonctionnalités de débogage standard de Visual Studio, comme les points d’arrêt, les fenêtres Espion et le pointage sur une variable. Ces méthodes vous permettent de déboguer votre projet comme vous le faites habituellement pour d’autres types de projets.

- Affichez la sortie de l’ordinateur cible dans la fenêtre de console Linux. Vous pouvez également utiliser la console pour envoyer les entrées à l’ordinateur cible.

## <a name="debug-your-linux-project"></a>Déboguer votre projet Linux

1. Sélectionnez le mode de débogage dans la page de propriétés **Débogage**.

   
   
   ::: moniker range="vs-2019"

   GDB est utilisé pour déboguer les applications exécutées sur Linux. Lors du débogage sur un système distant (pas WSL), GDB peut s’exécuter dans deux modes différents, que vous pouvez sélectionner à partir de l’option **Mode de débogage** dans la page de propriétés **Débogage** du projet :

   ![Options GDB](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB est utilisé pour déboguer les applications exécutées sur Linux. GDB peut s’exécuter dans deux modes différents, que vous pouvez sélectionner à partir de l’option **Mode de débogage** dans la page de propriétés **Débogage** du projet :

   ![Options GDB](media/vs2017-debugger-settings.png)

   ::: moniker-end


   - En mode **gdbserver**, GDB s’exécute localement et se connecte à gdbserver sur le système distant.  Notez qu’il s’agit du seul mode que la fenêtre de console Linux prend en charge.

   - En mode **gdb**, le débogueur Visual Studio exécute GDB sur le système distant. C’est la meilleure option si la version locale de GDB n’est pas compatible avec la version installée sur la machine cible. |

   > [!NOTE]
   > Si vous ne pouvez pas atteindre les points d’arrêt en mode de débogage gdbserver, essayez le mode gdb. Vous devez d’abord [installer](download-install-and-setup-the-linux-development-workload.md) gdb sur la cible distante.

1. Sélectionnez la cible distante dans la barre d’outils **Déboguer** standard de Visual Studio.

   Quand la cible distante est disponible, elle s’affiche par son nom ou son adresse IP.

   ![Cible distante](media/remote_target.png)

   Si vous n’êtes pas encore connecté à la cible distante, vous voyez une instruction qui vous demande d’utiliser le [Gestionnaire de connexions Linux](connect-to-your-remote-linux-computer.md) pour vous connecter à la cible distante.

   ![Architecture distante](media/architecture.png)

1. Définissez un point d’arrêt en cliquant dans la marge gauche d’une section de code qui s’exécute correctement.

   Un point rouge s’affiche sur la ligne de code où vous avez défini le point d’arrêt.

1. Appuyez sur **F5** (ou **Déboguer > Démarrer le débogage**) pour démarrer le débogage.

   Quand vous démarrez le débogage, l’application est compilée sur la cible distante avant de démarrer. Les erreurs de compilation éventuelles s’affichent dans la fenêtre **Liste d’erreurs**.

   S’il n’y a aucune erreur, l’application démarre et le débogueur s’interrompt au point d’arrêt.

   ![Atteindre un point d’arrêt](media/hit_breakpoint.png)

   Maintenant, vous pouvez interagir avec l’application dans son état actuel, afficher les variables et exécuter le code pas à pas en appuyant sur des touches de commande (par exemple, **F10** ou **F11**).

1. Si vous souhaitez utiliser la console Linux pour interagir avec votre application, sélectionnez **Déboguer > Console Linux**.

   ![Menu de console Linux](media/consolemenu.png)

   Cette console affiche toutes les sorties de console de l’ordinateur cible et prend les entrées pour les envoyer à l’ordinateur cible.

   ![Fenêtre de console Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>Configurer d’autres options de débogage

- Vous pouvez passer les arguments de ligne de commande à l’exécutable en utilisant l’élément **Arguments de programme** dans la page de propriétés **Débogage** du projet.

   ![Arguments de programme](media/settings_programarguments.png)

- Vous pouvez passer des options de débogueur spécifiques à GDB à l’aide de l’entrée **Commandes de débogueur supplémentaires**.  Par exemple, il est conseillé d’ignorer les signaux d’instruction non conforme (SIGILL).  Vous pouvez utiliser la commande **handle** pour y parvenir  en ajoutant le code suivant à l’entrée **Commandes de débogueur supplémentaires** comme indiqué ci-dessus :

   `handle SIGILL nostop noprint`

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

**AttachOptionsForConnection** contient une grande partie des attributs dont vous pouvez avoir besoin. L’exemple ci-dessus montre comment spécifier un emplacement pour rechercher des bibliothèques .so supplémentaires. L’élément enfant **ServerOptions** permet d’effectuer un attachement au processus distant avec gdbserver à la place. Pour ce faire, vous devez spécifier un client gdb local (celui fourni dans Visual Studio 2017 est indiqué ci-dessus) et une copie locale du binaire contenant les symboles. L’élément **SetupCommands** permet de transmettre des commandes directement à gdb. Vous pouvez trouver toutes les options disponibles dans le [schéma LaunchOptions.xsd](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) sur GitHub.

## <a name="next-steps"></a>Étapes suivantes

- Pour déboguer des appareils ARM sur Linux, consultez ce billet de blog : [Debugging an embedded ARM device in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Voir aussi

[Débogage C++, propriétés (Linux C++)](prop-pages/debugging-linux.md)
