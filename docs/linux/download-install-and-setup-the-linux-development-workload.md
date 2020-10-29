---
title: Installer la charge de travail Linux C++ dans Visual Studio
description: Comment télécharger, installer et configurer la charge de travail Linux pour C++ dans Visual Studio.
ms.date: 05/03/2020
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 9d0c832ec383286b5f89b8ed1474e69d72b5cb98
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921605"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Télécharger, installer et configurer la charge de travail Linux

::: moniker range="msvc-140"

Les projets Linux sont pris en charge dans Visual Studio 2017 et ultérieur. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end

::: moniker range=">=msvc-150"

Vous pouvez utiliser l’IDE de Visual Studio sur Windows pour créer, modifier et déboguer des projets C++ qui s’exécutent sur un système Linux distant, une machine virtuelle ou le [sous-système Windows pour Linux](/windows/wsl/about).

Vous pouvez travailler sur votre base de code existante qui utilise CMake sans avoir à la convertir en projet Visual Studio. Si votre base de code est multiplateforme, vous pouvez cibler Windows et Linux à partir de Visual Studio. Par exemple, vous pouvez modifier, générer et déboguer votre code sur Windows à l’aide de Visual Studio. Ensuite, reciblez rapidement le projet pour Linux pour la génération et le débogage dans un environnement Linux. Les fichiers d’en-tête Linux sont automatiquement copiés sur votre ordinateur local. Visual Studio les utilise pour fournir une prise en charge complète d’IntelliSense (saisie semi-automatique des instructions, atteindre la définition, etc.).

Tous ces scénarios nécessitent la charge de travail de **développement Linux en C++** .

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="visual-studio-setup"></a>Installation Visual Studio

1. Tapez « Visual Studio Installer » dans la zone de recherche Windows :

   ![Zone de recherche Windows](media/visual-studio-installer-search.png)

1. Recherchez le programme d’installation dans les résultats situés sous **Applications** , puis double-cliquez dessus. Quand le programme d’installation s’ouvre, choisissez **modifier** , puis cliquez sur l’onglet **charges de travail** . Faites défiler jusqu’à d' **autres ensembles d’outils** et sélectionnez la charge **de travail développement Linux en C++** .

   ![Charge de travail Visual C++ pour le développement sous Linux](media/linuxworkload.png)

1. Si vous ciblez des plateformes IoT ou Embedded, accédez au volet des détails de l' **installation** à droite. Sous **développement Linux avec C++** , développez **composants facultatifs** , puis choisissez les composants dont vous avez besoin. La prise en charge de CMake pour Linux est sélectionnée par défaut.

1. Cliquez sur **Modifier** pour continuer l’installation.

## <a name="options-for-creating-a-linux-environment"></a>Options pour la création d’un environnement Linux

Si vous n’avez pas encore de machine Linux, vous pouvez créer une Machine virtuelle Linux sur Azure. Pour plus d’informations, consultez [Guide de démarrage rapide : Créer une machine virtuelle Linux sur le Portail Azure](/azure/virtual-machines/linux/quick-create-portal).

Sur Windows 10, vous pouvez installer et cibler votre distribution Linux favorite sur le sous-système Windows pour Linux (WSL). Pour plus d’informations, consultez [Guide d’installation du sous-système Windows pour Linux pour Windows 10](/windows/wsl/install-win10). Si vous ne parvenez pas à accéder au Windows Store, vous pouvez [Télécharger manuellement les packages WSL distribution](/windows/wsl/install-manual). WSL est un environnement de console pratique, mais il n’est pas recommandé pour les applications graphiques.

::: moniker-end

::: moniker range="msvc-160"

Dans Visual Studio, les projets Linux requièrent l’installation des dépendances suivantes sur votre système Linux distant ou WSL :

- **Un compilateur** -Visual Studio 2019 prend entièrement en charge GCC et [Clang](../build/clang-support-cmake.md).
- **gdb** : Visual Studio lance automatiquement gdb sur le système Linux et utilise le composant frontal du débogueur Visual Studio pour offrir une expérience de débogage complète sur Linux.
- **synchronisation** et **zip** : l’inclusion de la synchronisation et du zip permet à Visual Studio d’extraire des fichiers d’en-tête de votre système Linux vers le système de fichiers Windows pour une utilisation par IntelliSense.
- **make**
- **OpenSSH-serveur** (systèmes Linux distants uniquement)-Visual Studio se connecte aux systèmes Linux distants via une connexion SSH sécurisée.
- **Cmake** (projets cmake uniquement)-vous pouvez installer [les binaires cmake liés de manière statique de Microsoft pour Linux](https://github.com/microsoft/CMake/releases).
- **Ninja-Build** (projets cmake uniquement)- [Ninja](https://ninja-build.org/) est le générateur par défaut pour les configurations Linux et WSL dans Visual Studio 2019 version 16,6 ou ultérieure.

Les commandes suivantes supposent que vous utilisez g + + à la place de Clang.

::: moniker-end

::: moniker range="msvc-150"

Dans Visual Studio, les projets Linux requièrent l’installation des dépendances suivantes sur votre système Linux distant ou WSL :

- **GCC** -Visual Studio 2017 offre une prise en charge complète de GCC.
- **gdb** : Visual Studio lance automatiquement gdb sur le système Linux et utilise le composant frontal du débogueur Visual Studio pour offrir une expérience de débogage complète sur Linux.
- **synchronisation** et **zip** : l’inclusion de la synchronisation et du zip permet à Visual Studio d’extraire des fichiers d’en-tête de votre système Linux vers le système de fichiers Windows à utiliser pour IntelliSense.
- **make**
- **OpenSSH-Server** -Visual Studio se connecte aux systèmes Linux distants via une connexion SSH sécurisée.
- **Cmake** (projets cmake uniquement)-vous pouvez installer [les binaires cmake liés de manière statique de Microsoft pour Linux](https://github.com/microsoft/CMake/releases).

::: moniker-end

::: moniker range="msvc-160"

## <a name="linux-setup-ubuntu-on-wsl"></a>Configuration de Linux : Ubuntu sur WSL

Lorsque vous ciblez WSL, il n’est pas nécessaire d’ajouter une connexion à distance ou de configurer SSH pour la génération et le débogage. **zip** et **rsync** sont nécessaires pour la synchronisation automatique des en-têtes Linux avec Visual Studio en vue de la prise en charge d’Intellisense. **Ninja-Build** est requis uniquement pour les projets cmake. Si les applications requises ne sont pas déjà présentes, vous pouvez les installer à l’aide de la commande suivante :

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu sur les systèmes Linux distants

Le système Linux cible doit avoir **OpenSSH-Server** , **g + +** , **gdb** et **être** installé. **Ninja-Build** est requis pour les projets cmake uniquement. Le démon **SSH** doit être en cours d’exécution. **zip** et **rsync** sont requis pour la synchronisation automatique des en-têtes distants avec votre ordinateur local pour la prise en charge d’IntelliSense. Si ces applications ne sont pas déjà présentes, vous pouvez les installer comme suit :

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
   ```

   Vous pouvez être invité à entrer votre mot de passe racine pour exécuter la commande sudo. Dans ce cas, entrez-la et continuez. Quand vous avez terminé, les outils et services obligatoires sont installés.

1. Vérifiez que le service ssh est en cours d’exécution sur votre ordinateur Linux en exécutant :

   ```bash
   sudo service ssh start
   ```

   Cette commande démarre le service et l’exécute en arrière-plan, prêt à accepter les connexions.

::: moniker-end

::: moniker range="msvc-160"

## <a name="fedora-on-wsl"></a>Fedora sur WSL

Fedora utilise le programme d’installation du package **dnf** . Pour télécharger **g + +** , **gdb** , **Make** , **rsync** , **Ninja-Build** et **zip** , exécutez :

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

**zip** et **rsync** sont nécessaires pour la synchronisation automatique des en-têtes Linux avec Visual Studio en vue de la prise en charge d’Intellisense. **Ninja-Build** est requis uniquement pour les projets cmake.

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="fedora-on-remote-linux-systems"></a>Fedora sur les systèmes Linux distants

L’ordinateur cible exécutant Fedora utilise le programme d’installation de package **fnd** . Pour télécharger **OpenSSH-Server** , **g + +** , **gdb** , **Make** , **Ninja-Build** , **rsync** et **zip** , puis redémarrez le démon SSH, suivez ces instructions. **Ninja-Build** est requis uniquement pour les projets cmake.

1. À l’invite de commandes du shell sur votre ordinateur Linux, exécutez :

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
   ```

   Vous pouvez être invité à entrer votre mot de passe racine pour exécuter la commande sudo. Dans ce cas, entrez-la et continuez. Quand vous avez terminé, les outils et services obligatoires sont installés.

1. Vérifiez que le service ssh est en cours d’exécution sur votre ordinateur Linux en exécutant :

   ```bash
   sudo systemctl start sshd
   ```

   Cette commande démarre le service et l’exécute en arrière-plan, prêt à accepter les connexions.

## <a name="next-steps"></a>Étapes suivantes

Vous êtes maintenant prêt à créer ou ouvrir un projet Linux et à le configurer pour qu’il s’exécute sur le système cible. Pour plus d'informations, consultez les pages suivantes :

- [Créer un projet C++ MSBuild Linux](create-a-new-linux-project.md)
- [Configurer un projet CMake Linux](cmake-linux-project.md)

::: moniker-end
