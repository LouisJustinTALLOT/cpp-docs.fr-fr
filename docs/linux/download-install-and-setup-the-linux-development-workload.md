---
title: Installer la charge de travail Linux C++ dans Visual Studio
description: Décrit comment télécharger, installer et configurer la charge de travail Linux pour C++ dans Visual Studio.
ms.date: 10/12/2018
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 2fa4036ece6dd161c73a5176740870c5593f4669
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441923"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Télécharger, installer et configurer la charge de travail Linux

Vous pouvez utiliser l’IDE Visual Studio dans Windows pour créer, modifier et déboguer des projets C++ qui s’exécutent sur une machine virtuelle, un ordinateur physique Linux ou le [sous-système Windows pour Linux](/windows/wsl/about). Pour chacun de ces scénarios, installez d’abord la charge de travail **Développement Linux en C++**.

## <a name="visual-studio-setup"></a>Installation Visual Studio

1. Tapez « Visual Studio Installer » dans la zone de recherche Windows : ![zone de recherche Windows](media/visual-studio-installer-search.png)
2. Recherchez le programme d’installation dans les résultats situés sous **Applications**, puis double-cliquez dessus. Quand le programme d’installation s’ouvre, choisissez **Modifier**, puis cliquez sur l’onglet **Charges de travail**. Faites défiler vers le bas jusqu’à **Autres ensembles d’outils** et sélectionnez la charge de travail **Développement Linux en C++**.

   ![Charge de travail Visual C++ pour le développement sous Linux](media/linuxworkload.png)

1. Si vous utilisez CMake ou que vous ciblez des plateformes incorporées ou IoT, accédez au volet **Détails de l’installation** à droite, sous **Développement Linux en C++**, développez **Composants facultatifs** et choisissez les composants dont vous avez besoin.

1. Cliquez sur **Modifier** pour continuer l’installation.

## <a name="options-for-creating-a-linux-environment"></a>Options pour la création d’un environnement Linux

Si vous n’avez pas encore de machine Linux, vous pouvez créer une Machine virtuelle Linux sur Azure. Pour plus d’informations, consultez [Guide de démarrage rapide : Créer une machine virtuelle Linux sur le Portail Azure](/azure/virtual-machines/linux/quick-create-portal).

Une autre option, sur Windows 10, consiste à activer le sous-système Windows pour Linux. Pour plus d’informations, consultez le [Guide d’installation de Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup-ubuntu"></a>Installation Linux : Ubuntu

**openssh-server**, **g++**, **gdb** et **gdbserver** doivent être installés sur l’ordinateur Linux cible et le démon ssh doit être en cours d’exécution. **zip** est obligatoire pour la synchronisation automatique des en-têtes distants avec votre ordinateur local pour la prise en charge d’Intellisense. Si ces applications ne sont pas déjà présentes, vous pouvez les installer comme suit :

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Vous pouvez être invité à indiquer votre mot de passe racine en raison de la commande sudo.  Dans ce cas, entrez-la et continuez. Quand vous avez terminé, les outils et services obligatoires sont installés.

1. Vérifiez que le service ssh est en cours d’exécution sur votre ordinateur Linux en exécutant :

   `sudo service ssh start`

   Vous démarrez ainsi le service qui s’exécute en arrière-plan, prêt à accepter des connexions.

## <a name="linux-setup-fedora"></a>Installation Linux : Fedora

L’ordinateur cible exécutant Fedora utilise le programme d’installation de package **fnd**. Pour télécharger **openssh-server**, **g++**, **gdb**, **gdbserver** et **zip**, et redémarrer le démon ssh, suivez ces instructions :

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   `sudo dnf install openssh-server g++ gdb gdbserver zip`

   Vous pouvez être invité à indiquer votre mot de passe racine en raison de la commande sudo.  Dans ce cas, entrez-la et continuez. Quand vous avez terminé, les outils et services obligatoires sont installés.

1. Vérifiez que le service ssh est en cours d’exécution sur votre ordinateur Linux en exécutant :

   `sudo systemctl start sshd`

   Vous démarrez ainsi le service qui s’exécute en arrière-plan, prêt à accepter des connexions.

