---
title: Installer la charge de travail Linux C++ dans Visual Studio
description: Décrit comment télécharger, installer et configurer la charge de travail Linux pour C++ dans Visual Studio.
ms.date: 03/05/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 74155724abb3a0e02cc27dd8a8d144f142ee4b6f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747720"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Télécharger, installer et configurer la charge de travail Linux

Vous pouvez utiliser l’IDE Visual Studio 2017 dans Windows pour créer, modifier et déboguer des projets C++ qui s’exécutent sur un ordinateur physique ou une machine virtuelle Linux, ou sur le [sous-système Windows pour Linux](/windows/wsl/about). 

Vous pouvez reprendre votre base de code existante qui utilise CMake ou tout autre système de build sans avoir à la convertir en projet Visual Studio. Si votre base de code est multiplateforme, vous pouvez cibler Windows et Linux à partir de Visual Studio. Par exemple, vous pouvez modifier, déboguer et profiler votre code sur Windows à l’aide de Visual Studio, puis recibler rapidement le projet pour Linux afin d’effectuer des tests supplémentaires. Les fichiers d’en-tête Linux sont automatiquement copiés sur votre machine locale où Visual Studio les utilise pour fournir des fonctionnalités IntelliSense complètes (Saisie semi-automatique des instructions, Atteindre la définition, etc.).
 
Tous ces scénarios nécessitent la charge de travail de **développement Linux en C++**. 

## <a name="visual-studio-setup"></a>Installation Visual Studio

1. Tapez « Visual Studio Installer » dans la zone de recherche Windows : ![Zone de recherche Windows](media/visual-studio-installer-search.png)
2. Recherchez le programme d’installation dans les résultats situés sous **Applications**, puis double-cliquez dessus. Quand le programme d’installation s’ouvre, choisissez **Modifier**, puis cliquez sur l’onglet **Charges de travail**. Faites défiler vers le bas jusqu’à **Autres ensembles d’outils** et sélectionnez la charge de travail **Développement Linux en C++**.

   ![Charge de travail Visual C++ pour le développement sous Linux](media/linuxworkload.png)

1. Si vous utilisez CMake ou que vous ciblez des plateformes incorporées ou IoT, accédez au volet **Détails de l’installation** à droite, sous **Développement Linux en C++**, développez **Composants facultatifs** et choisissez les composants dont vous avez besoin.

    **Visual Studio 2017 15.4 et versions ultérieures**<br/>: Quand vous installez la charge de travail Linux C++ pour Visual Studio, la prise en charge de CMake pour Linux est sélectionnée par défaut.

1. Cliquez sur **Modifier** pour continuer l’installation.

## <a name="options-for-creating-a-linux-environment"></a>Options pour la création d’un environnement Linux

Si vous n’avez pas encore de machine Linux, vous pouvez créer une Machine virtuelle Linux sur Azure. Pour plus d’informations, consultez [Démarrage rapide : Créer une machine virtuelle Linux dans le portail Azure](/azure/virtual-machines/linux/quick-create-portal).

Une autre option, sur Windows 10, consiste à activer le sous-système Windows pour Linux. Pour plus d’informations, consultez le [Guide d’installation de Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup-ubuntu"></a>Installation Linux : Ubuntu

**openssh-server**, **g++**, **gdb** et **gdbserver** doivent être installés sur l’ordinateur Linux cible et le démon ssh doit être en cours d’exécution. **zip** est obligatoire pour la synchronisation automatique des en-têtes distants avec votre ordinateur local pour la prise en charge d’Intellisense. Si ces applications ne sont pas déjà présentes, vous pouvez les installer comme suit :

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Vous pouvez être invité à indiquer votre mot de passe racine en raison de la commande sudo.  Dans ce cas, entrez-la et continuez. Quand vous avez terminé, les outils et services obligatoires sont installés.

1. Vérifiez que le service ssh est en cours d’exécution sur votre ordinateur Linux en exécutant :

   `sudo service ssh start`

   Vous démarrez ainsi le service qui s’exécute en arrière-plan, prêt à accepter des connexions.

## <a name="linux-setup-fedora"></a>Installation Linux : Fedora

L’ordinateur cible exécutant Fedora utilise le programme d’installation de package **fnd**. Pour télécharger **openssh-server**, **g++**, **gdb**, **gdbserver** et **zip**, et redémarrer le démon ssh, suivez ces instructions :

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   `sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip`

   Vous pouvez être invité à indiquer votre mot de passe racine en raison de la commande sudo.  Dans ce cas, entrez-la et continuez. Quand vous avez terminé, les outils et services obligatoires sont installés.

1. Vérifiez que le service ssh est en cours d’exécution sur votre ordinateur Linux en exécutant :

   `sudo systemctl start sshd`

   Vous démarrez ainsi le service qui s’exécute en arrière-plan, prêt à accepter des connexions.

## <a name="ensure-you-have-cmake-38-on-the-remote-linux-machine"></a>Assurez-vous d’avoir installé CMake 3.8 sur la machine Linux distante

Votre distribution Linux peut avoir une version antérieure de CMake. La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur qui a été introduit dans CMake 3.8. Pour une variante de CMake fournie par Microsoft, téléchargez les fichiers binaires prédéfinis les plus récents sur votre machine Linux à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).
