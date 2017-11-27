---
title: "Déployer, exécuter et déboguer un projet Linux | Microsoft Docs"
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 237b6f3dbca8d529362a545f67ee0db4f9770d8d
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Déployer, exécuter et déboguer un projet Linux

Une fois que vous avez créé un projet Linux et que vous vous êtes connecté au projet par le biais du [Gestionnaire de connexions Linux](../linux/connect-to-your-remote-linux-computer.md), vous pouvez exécuter et déboguer le projet. Vous compilez, exécutez et déboguez le code sur la cible distante.

Il existe plusieurs façons de manipuler et déboguer votre projet Linux.

* Vous pouvez utiliser les fonctionnalités de débogage standard de Visual Studio, comme les points d’arrêt, les fenêtres Espion et le pointage sur une variable. Ces méthodes vous permettent de déboguer votre projet comme vous le faites habituellement pour d’autres types de projets.
* Affichez la sortie de l’ordinateur cible dans une fenêtre de console Linux spécifique. Vous pouvez également utiliser la console pour envoyer les entrées à l’ordinateur cible.

## <a name="debug-your-linux-project"></a>Déboguer votre projet Linux

1. Sélectionnez le mode de débogage dans la page de propriétés **Débogage**.

    GDB est utilisé pour déboguer les applications exécutées sur Linux.  Toutefois, il existe deux modes d’exécution différents qui peuvent être sélectionnés à partir de l’option **Mode de débogage** dans la page de propriétés **Débogage** du projet :

    ![Options GDB](media/settings_debugger.png)

    - En mode **gdbserver**, GDB s’exécute localement et se connecte à gdbserver, qui s’exécute sur le système distant.  Notez qu’il s’agit du seul mode que la fenêtre de console Linux prend en charge.

    - En mode **gdb**, le débogueur Visual Studio exécute GDB sur le système distant, ce qui est plus compatible si la version locale de GDB n’est pas compatible avec la version installée sur l’ordinateur cible. |

    > [!NOTE] 
    > Si vous ne pouvez pas atteindre les points d’arrêt en mode de débogage gdbserver, essayez le mode gdb. Vous devez d’abord [installer](../linux/download-install-and-setup-the-linux-development-workload.md) gdb sur la cible distante.

2. Sélectionnez la cible distante dans la barre d’outils **Déboguer** standard de Visual Studio.

    Quand la cible distante est disponible, elle s’affiche par son nom ou son adresse IP.

    ![Cible distante](media/remote_target.png)

    Si vous n’êtes pas encore connecté à la cible distante, vous voyez une instruction qui vous demande d’utiliser le [Gestionnaire de connexions Linux](../linux/connect-to-your-remote-linux-computer.md) pour vous connecter à la cible distante.

    ![Architecture distante](media/architecture.png)

3. Définissez un point d’arrêt en cliquant dans la marge gauche d’une section de code qui s’exécute correctement.

    Un point rouge s’affiche sur la ligne de code où vous avez défini le point d’arrêt.

4. Appuyez sur **F5** (ou **Déboguer > Démarrer le débogage**) pour démarrer le débogage.

    Quand vous démarrez le débogage, l’application est compilée sur la cible distante avant de démarrer. Les erreurs de compilation éventuelles s’affichent dans la fenêtre **Liste d’erreurs**.

    S’il n’y a aucune erreur, l’application démarre et le débogueur s’interrompt au point d’arrêt.

    ![Atteindre un point d’arrêt](media/hit_breakpoint.png)  

    Maintenant, vous pouvez interagir avec l’application dans son état actuel, afficher les variables et exécuter le code pas à pas en appuyant sur des touches de commande (par exemple, **F10** ou **F11**).

4. Si vous souhaitez utiliser la console Linux pour interagir avec votre application, sélectionnez **Déboguer > Console Linux**.

  ![Menu de console Linux](media/consolemenu.png)

  Cette console affiche toutes les sorties de console de l’ordinateur cible et prend les entrées pour les envoyer à l’ordinateur cible.

  ![Fenêtre de console Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>Configurer d’autres options de débogage

* Vous pouvez passer les arguments de ligne de commande à l’exécutable en utilisant l’élément **Arguments de programme** dans la page de propriétés **Débogage** du projet.
  
  ![Arguments de programme](media/settings_programarguments.png)

* Vous pouvez passer des options de débogueur spécifiques à GDB à l’aide de l’entrée **Commandes de débogueur supplémentaires**.  Par exemple, il est conseillé d’ignorer les signaux d’instruction non conforme (SIGILL).  Vous pouvez utiliser la commande **handle** pour y parvenir  en ajoutant le code suivant à l’entrée **Commandes de débogueur supplémentaires** comme indiqué ci-dessus :

  ```handle SIGILL nostop noprint```

## <a name="see-also"></a>Voir aussi
[Débogage C++, propriétés (Linux C++)](../linux/prop-pages/debugging-linux.md).
