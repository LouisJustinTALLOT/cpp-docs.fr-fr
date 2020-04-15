---
title: Installer la charge de travail Linux C++ dans Visual Studio
description: Décrit comment télécharger, installer et configurer la charge de travail Linux pour C++ dans Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 8e10521ab35f3d85ced8bffd771b4e101d4d4fe6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364342"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Télécharger, installer et configurer la charge de travail Linux

::: moniker range="vs-2015"

Les projets Linux sont pris en charge dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

Vous pouvez utiliser le Visual Studio IDE sur Windows pour créer, modifier et débouger des projets CMD qui s’exécutent sur un système Linux à distance, une machine virtuelle ou le [sous-système Windows pour Linux](/windows/wsl/about).

Vous pouvez travailler sur votre base de code existante qui utilise CMake sans avoir à la convertir en un projet Visual Studio. Si votre base de code est multiplateforme, vous pouvez cibler Windows et Linux à partir de Visual Studio. Par exemple, vous pouvez modifier, construire et déboiffer votre code sur Windows à l’aide de Visual Studio, puis rapidement réétiqueter le projet pour Linux de construire et de déboiffer dans un environnement Linux. Les fichiers d’en-tête Linux sont automatiquement copiés sur votre machine locale, où Visual Studio les utilise pour fournir un support IntelliSense complet (Déclaration Completion, Go to Definition, et ainsi de suite).

Tous ces scénarios nécessitent la charge de travail de **développement Linux en C++**.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Installation Visual Studio

1. Tapez « Visual Studio Installer » dans la zone de recherche Windows :

   ![Zone de recherche Windows](media/visual-studio-installer-search.png)

1. Recherchez le programme d’installation dans les résultats situés sous **Applications**, puis double-cliquez dessus. Lorsque l’installateur s’ouvre, choisissez **Modifier,** puis cliquez sur l’onglet **Charges de travail.** Faites défiler vers le bas vers les **autres ensembles d’outils** et sélectionnez le développement Linux avec la charge de travail **C.**

   ![Charge de travail Visual C++ pour le développement sous Linux](media/linuxworkload.png)

1. Si vous ciblez des plates-formes IoT ou intégrées, rendez-vous sur le volet **détails d’installation** sur la droite. Dans **le cadre du développement Linux avec CMD,** élargissez les composants **facultatifs**et choisissez les composants dont vous avez besoin. La prise en charge de CMake pour Linux est sélectionnée par défaut.

1. Cliquez sur **Modifier** pour continuer l’installation.

## <a name="options-for-creating-a-linux-environment"></a>Options pour la création d’un environnement Linux

Si vous n’avez pas encore de machine Linux, vous pouvez créer une Machine virtuelle Linux sur Azure. Pour plus d’informations, consultez [Guide de démarrage rapide : Créer une machine virtuelle Linux sur le Portail Azure](/azure/virtual-machines/linux/quick-create-portal).

Sur Windows 10, vous pouvez installer et cibler votre distribution Linux favorite sur le sous-système Windows pour Linux (WSL). Pour plus d’informations, consultez [Guide d’installation du sous-système Windows pour Linux pour Windows 10](/windows/wsl/install-win10). Si vous n’êtes pas en mesure d’accéder au Windows Store, vous pouvez [télécharger manuellement les paquets de distro WSL](/windows/wsl/install-manual). WSL est un environnement de console pratique, mais n’est pas recommandé pour les applications graphiques.

::: moniker-end

::: moniker range="vs-2019"

Les projets Linux de Visual Studio exigent que les dépendances suivantes soient installées sur votre système Linux à distance ou WSL :

- **Un compilateur** - Visual Studio 2019 a un support out-of-the-box pour le CCG et [Clang](/cpp/build/clang-support-cmake?view=vs-2019).
- **gdb** - Visual Studio lance automatiquement gdb sur le système Linux, et utilise l’avant-extrémité du debugger Visual Studio pour fournir une expérience de débogage pleine fidélité sur Linux.
- **rsync** et **zip** - l’inclusion de rsync et zip permet Visual Studio d’extraire des fichiers en-tête de votre système Linux au système de fichiers Windows pour une utilisation par IntelliSense.
- **Faire**
- **ouvre le serveur** (systèmes Linux à distance uniquement) - Visual Studio se connecte aux systèmes Linux distants sur une connexion SSH sécurisée.
- **CMake** (projets CMake seulement) - Vous pouvez installer [les binaires CMake statiquement liés de](https://github.com/microsoft/CMake/releases)Microsoft pour Linux .
- **ninja-build** (projets CMake seulement)- [Ninja](https://ninja-build.org/) est le générateur par défaut pour les configurations Linux et WSL dans Visual Studio 2019 version 16.6 ou plus tard.

Les commandes suivantes supposent que vous utilisez gmd au lieu de clang.

::: moniker-end

::: moniker range="vs-2017"

Les projets Linux de Visual Studio exigent que les dépendances suivantes soient installées sur votre système Linux à distance ou WSL :

- **gcc** - Visual Studio 2017 a un support hors de la boîte pour le CCG.
- **gdb** - Visual Studio lance automatiquement gdb sur le système Linux et utilise l’avant du debugger Visual Studio pour fournir une expérience de débogage pleine fidélité sur Linux.
- **rsync** et **zip** - l’inclusion de rsync et zip permet Visual Studio d’extraire des fichiers en-tête de votre système Linux au système de fichiers Windows à utiliser pour IntelliSense.
- **Faire**
- **ouvre le serveur** - Visual Studio se connecte aux systèmes Linux distants sur une connexion SSH sécurisée.
- **CMake** (projets CMake seulement) - Vous pouvez installer [les binaires CMake statiquement liés de](https://github.com/microsoft/CMake/releases)Microsoft pour Linux .

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Configuration Linux: Ubuntu sur WSL

Lorsque vous ciblez WSL, il n’est pas nécessaire d’ajouter une connexion à distance ou de configurer SSH pour compiler et déboguer. **zip** et **rsync** sont nécessaires pour la synchronisation automatique des en-têtes Linux avec Visual Studio en vue de la prise en charge d’Intellisense. Si les applications requises ne sont pas déjà présentes, vous pouvez les installer comme suit. **ninja-build** n’est nécessaire que pour les projets CMake.

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu sur les systèmes Linux distants

Le système Linux cible doit avoir **ouvreh-serveur**, **g ,** **gdb**, **ninja-build** (projets CMake seulement), et **faire** installé, et le daemon ssh doit être en cours d’exécution. **zip** et **rsync** sont nécessaires pour la synchronisation automatique des en-têtes à distance avec votre machine locale pour le soutien Intellisense. Si ces applications ne sont pas déjà présentes, vous pouvez les installer comme suit :

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
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

Fedora utilise le programme d’installation du package **dnf**. Pour télécharger **g ,** **gdb**, **faire**, **rsync**, **ninja-build**, et **zip**, exécuter:

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

**zip** et **rsync** sont nécessaires pour la synchronisation automatique des en-têtes Linux avec Visual Studio en vue de la prise en charge d’Intellisense. **ninja-build** n’est nécessaire que pour les projets CMake.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora sur les systèmes Linux distants

L’ordinateur cible exécutant Fedora utilise le programme d’installation de package **fnd**. Pour télécharger **opensh-server**, **g ,** **gdb**, **faire**, **ninja-build**, **rsync**, et **zip**, et redémarrer le daemon ssh, suivez ces instructions. **ninja-build** n’est nécessaire que pour les projets CMake.

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
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

Vous êtes maintenant prêt à créer ou ouvrir un projet Linux et à le configurer pour qu’il s’exécute sur le système cible. Pour plus d'informations, consultez les pages suivantes :

- [Créer un projet Linux](create-a-new-linux-project.md)
- [Configurer un projet CMake Linux](cmake-linux-project.md)
