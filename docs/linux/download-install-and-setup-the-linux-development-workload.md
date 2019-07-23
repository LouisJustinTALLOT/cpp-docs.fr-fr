---
title: Installer la charge de travail Linux C++ dans Visual Studio
description: Décrit comment télécharger, installer et configurer la charge de travail Linux pour C++ dans Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 5df7b323d202f398059e92abaeeeedbf73439fa4
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299795"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Télécharger, installer et configurer la charge de travail Linux

::: moniker range="vs-2015"

Les projets Linux sont pris en charge dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

Vous pouvez utiliser l’IDE Visual Studio dans Windows pour créer, modifier et déboguer des projets C++ qui s’exécutent sur une machine virtuelle, un ordinateur physique Linux ou le [sous-système Windows pour Linux](/windows/wsl/about). 

Vous pouvez reprendre votre base de code existante qui utilise CMake ou tout autre système de build sans avoir à la convertir en projet Visual Studio. Si votre base de code est multiplateforme, vous pouvez cibler Windows et Linux à partir de Visual Studio. Par exemple, vous pouvez modifier, déboguer et profiler votre code sur Windows à l’aide de Visual Studio, puis recibler rapidement le projet pour Linux afin d’effectuer des tests supplémentaires. Les fichiers d’en-tête Linux sont automatiquement copiés sur votre machine locale où Visual Studio les utilise pour fournir des fonctionnalités IntelliSense complètes (Saisie semi-automatique des instructions, Atteindre la définition, etc.). 
 
Tous ces scénarios nécessitent la charge de travail de **développement Linux en C++** . 

::: moniker-end

::: moniker range="vs-2019"

Dans Visual Studio 2019, vous pouvez spécifier des cibles distinctes pour la génération et le débogage. Quand vous ciblez WSL, il n’est plus nécessaire d’ajouter une connexion à distance ou de configurer SSH.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Installation Visual Studio

1. Tapez « Visual Studio Installer » dans la zone de recherche Windows :

   ![Zone de recherche Windows](media/visual-studio-installer-search.png)

2. Recherchez le programme d’installation dans les résultats situés sous **Applications**, puis double-cliquez dessus. Quand le programme d’installation s’ouvre, choisissez **Modifier**, puis cliquez sur l’onglet **Charges de travail**. Faites défiler vers le bas jusqu’à **Autres ensembles d’outils** et sélectionnez la charge de travail **Développement Linux en C++** .

   ![Charge de travail Visual C++ pour le développement sous Linux](media/linuxworkload.png)

1. Si vous ciblez des plateformes incorporées ou IoT, accédez au volet **Détails de l’installation** à droite, sous **Développement Linux en C++** , développez **Composants facultatifs** et choisissez les composants dont vous avez besoin. La prise en charge de CMake pour Linux est sélectionnée par défaut.

1. Cliquez sur **Modifier** pour continuer l’installation.

## <a name="options-for-creating-a-linux-environment"></a>Options pour la création d’un environnement Linux

Si vous n’avez pas encore de machine Linux, vous pouvez créer une Machine virtuelle Linux sur Azure. Pour plus d’informations, consultez [Démarrage rapide : Créer une machine virtuelle Linux dans le portail Azure](/azure/virtual-machines/linux/quick-create-portal).

Sur Windows 10, vous pouvez installer et cibler votre distribution Linux favorite sur le sous-système Windows pour Linux (WSL). Pour plus d’informations, consultez [Guide d’installation du sous-système Windows pour Linux pour Windows 10](/windows/wsl/install-win10). WSL est un environnement de console pratique mais n’est pas recommandé pour les applications graphiques. 

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Installation Linux : Ubuntu sur WSL

Lorsque vous ciblez WSL, il n’est pas nécessaire d’ajouter une connexion à distance ou de configurer SSH pour compiler et déboguer. **zip** et **rsync** sont nécessaires pour la synchronisation automatique des en-têtes Linux avec Visual Studio en vue de la prise en charge d’Intellisense. Si les applications requises ne sont pas déjà présentes, vous pouvez les installer comme suit :

```bash
sudo apt-get install g++ gdb make rsync zip
```
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu sur les systèmes Linux distants

**openssh-server**, **g++** , **gdb** et **gdbserver** doivent être installés sur le système Linux cible et le démon ssh doit être en cours d’exécution. **zip** est obligatoire pour la synchronisation automatique des en-têtes distants avec votre ordinateur local pour la prise en charge d’Intellisense. Si ces applications ne sont pas déjà présentes, vous pouvez les installer comme suit :

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   ```bash
   sudo apt-get install openssh-server g++ gdb gdbserver zip
   ```

   Vous pouvez être invité à indiquer votre mot de passe racine en raison de la commande sudo.  Dans ce cas, entrez-la et continuez. Quand vous avez terminé, les outils et services obligatoires sont installés.

1. Vérifiez que le service ssh est en cours d’exécution sur votre ordinateur Linux en exécutant :

   ```bash
   sudo service ssh start
   ```
   Vous démarrez ainsi le service qui s’exécute en arrière-plan, prêt à accepter des connexions.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora sur WSL

Fedora utilise le programme d’installation du package **dnf**. Pour télécharger **g++** , **gdb**, **rsync** et **zip**, exécutez :

   ```bash
   sudo dnf install gcc-g++ gdb rsync zip
   ```

**zip** et **rsync** sont nécessaires pour la synchronisation automatique des en-têtes Linux avec Visual Studio en vue de la prise en charge d’Intellisense.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora sur les systèmes Linux distants

L’ordinateur cible exécutant Fedora utilise le programme d’installation de package **fnd**. Pour télécharger **openssh-server**, **g++** , **gdb**, **gdbserver** et **zip**, et redémarrer le démon ssh, suivez ces instructions :

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip
   ```
   Vous pouvez être invité à indiquer votre mot de passe racine en raison de la commande sudo.  Dans ce cas, entrez-la et continuez. Quand vous avez terminé, les outils et services obligatoires sont installés.

1. Vérifiez que le service ssh est en cours d’exécution sur votre ordinateur Linux en exécutant :

   ```bash
   sudo systemctl start sshd
   ```

   Vous démarrez ainsi le service qui s’exécute en arrière-plan, prêt à accepter des connexions.

::: moniker-end

::: moniker range="vs-2015"

La prise en charge du développement C++ Linux est disponible dans Visual Studio versions 2017 et ultérieures.

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Vous êtes maintenant prêt à créer ou ouvrir un projet Linux et à le configurer pour qu’il s’exécute sur le système cible. Pour plus d'informations, voir :

- [Créer un projet Linux](create-a-new-linux-project.md)
- [Configurer un projet CMake Linux](cmake-linux-project.md)
