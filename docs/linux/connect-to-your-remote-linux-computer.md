---
title: Connexion à votre système Linux cible dans Visual Studio
description: Comment se connecter à une machine Linux à distance ou sous-système Windows pour Linux à partir de l’intérieur d’un projet Visual Studio C .
ms.date: 01/17/2020
ms.openlocfilehash: 624dce6bb05e4f4a961628e0c6f455e11c14dff8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364361"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Connexion à votre système Linux cible dans Visual Studio

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range="vs-2017"

Vous pouvez configurer un projet Linux pour cibler une machine virtuelle ou le sous-système Windows pour Linux (WSL). Pour les machines à distance et pour WSL, vous devez configurer une connexion à distance dans Visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Vous pouvez configurer un projet Linux pour cibler une machine virtuelle ou le sous-système Windows pour Linux (WSL). Pour une machine à distance, vous devez configurer une connexion à distance dans Visual Studio. Pour vous connecter à WSL, passez à l’avance à la section [Connect to WSL.](#connect-to-wsl)

::: moniker-end

::: moniker range=">=vs-2017"

Lors de l’utilisation d’une connexion à distance, Visual Studio construit des projets Linux sur la machine à distance. Peu importe s’il s’agit d’une machine physique, d’un VM dans le cloud ou d’un WSL.
Pour construire le projet, Visual Studio copie le code source à votre ordinateur Linux distant. Ensuite, le code est compilé en fonction des paramètres Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 version 16.5 et plus tard prend également en charge sécurisé, Federal Information Processing Standard (FIPS) 140-2 connexions cryptographiques conformes aux systèmes Linux pour le développement à distance. Pour utiliser une connexion conforme à la FIPS, suivez plutôt les étapes du [développement Linux sécurisé conforme à la FIPS.](set-up-fips-compliant-secure-remote-linux-development.md)

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>Configurez le serveur SSH sur le système distant

Si ssh n’est pas déjà configuré et en cours d’exécution sur votre système Linux, suivez ces étapes pour l’installer. Les exemples de cet article utilisent Ubuntu 18.04 LTS avec la version serveur OpenSSH 7.6. Cependant, les instructions devraient être les mêmes pour toute distro en utilisant une version modérément récente de OpenSSH.

1. Sur le système Linux, installez et démarrez le serveur OpenSSH :

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Si vous souhaitez que le serveur ssh démarre automatiquement lorsque le système démarre, activez-le à l’aide de systemctl :

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>Configurer la connexion à distance

1. Dans Visual Studio, choisissez **Tools > Options** sur la barre de menu pour ouvrir le dialogue **Options.** Sélectionnez ensuite **Cross Platform > Connection Manager** pour ouvrir le dialogue Connection Manager.

   Si vous n’avez pas déjà établi de connexion dans Visual Studio, lorsque vous construisez votre projet pour la première fois, Visual Studio vous ouvre le dialogue Connection Manager.

1. Dans le dialogue Connection Manager, choisissez le bouton **Ajouter** pour ajouter une nouvelle connexion.

   ![Gestionnaire de connexions](media/settings_connectionmanager.png)

   Dans l’un ou l’autre des scénarios, la fenêtre **Connect to Remote System** s’affiche.

   ![Connect to Remote System (Se connecter au système distant)](media/connect.png)

1. Entrez les informations suivantes :

   | Entrée | Description
   | ----- | ---
   | **Nom de l’hôte**           | Nom ou adresse IP de votre appareil cible
   | **Port**                | Port sur lequel le service SSH est exécuté, en général 22
   | **Nom d'utilisateur**           | Utilisateur sous le nom duquel s’authentifier
   | **Type d’authentification** | Mot de passe et clé privée sont tous deux pris en charge
   | **Mot de passe**            | Mot de passe du nom d’utilisateur entré
   | **Fichier de clé privée**    | Fichier de clé privée créé pour la connexion ssh
   | **Phrase**          | Phrase secrète utilisée avec la clé privée sélectionnée ci-dessus

   Vous pouvez utiliser un mot de passe ou un fichier clé et passer la parole pour l’authentification. Pour de nombreux scénarios de développement, l’authentification par mot de passe est suffisante, mais les fichiers clés sont plus sécurisés. Si vous avez déjà une paire clé, il est possible de la réutiliser. Actuellement Visual Studio ne prend en charge que les clés RSA et DSA pour les connexions à distance.

1. Choisissez le bouton **Connect** pour tenter une connexion à l’ordinateur distant.

   Si la connexion réussit, Visual Studio configure IntelliSense pour utiliser les en-têtes distants. Pour plus d’informations, consultez [IntelliSense pour les en-têtes sur les systèmes distants](configure-a-linux-project.md#remote_intellisense).

   Si la connexion échoue, les zones des entrées qui doivent être modifiées seront surlignées en rouge.

   ![Erreur du Gestionnaire de connexion](media/settings_connectionmanagererror.png)

   Si vous utilisez des fichiers clés pour l’authentification, assurez-vous que le serveur SSH de la machine cible est en marche et configuré correctement.

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>Enregistrement pour les connexions à distance

   Vous pouvez activer l’enregistrement pour aider à résoudre les problèmes de connexion. Sur la barre de menu, sélectionnez **Outils > Options**. Dans le dialogue **Options,** sélectionnez **Cross Platform > Logging**:

   ![Journalisation à distance](media/remote-logging-vs2019.png)

   Les journaux incluent les connexions, toutes les commandes envoyées à la machine distante (leur texte, le code de sortie et la durée d’exécution) et toutes les sorties de Visual Studio à dans l’interpréteur de commandes. La journalisation fonctionne pour n’importe quel projet CMake multiplateforme ou projet Linux basé sur MSBuild dans Visual Studio.

   Vous pouvez configurer la sortie pour aller à un fichier ou à la **plate-forme cross panoramique d’enregistrement** dans la fenêtre de sortie. Pour les projets Linux basés sur MSBuild, les commandes MSBuild envoyées à la machine distante ne sont pas acheminées vers la **fenêtre de sortie** parce qu’elles sont émises hors-processus. Au lieu de cela, ils sont connectés à un fichier, avec un préfixe de "msbuild_".

## <a name="command-line-utility-for-the-connection-manager"></a>Service public de la ligne de commandement pour le gestionnaire de connexion  

**Visual Studio 2019 version 16.5 ou plus tard**: ConnectionManager.exe est un utilitaire de commande pour gérer les connexions de développement à distance en dehors de Visual Studio. Il est utile pour des tâches telles que l’approvisionnement d’une nouvelle machine de développement. Ou, vous pouvez l’utiliser pour configurer Visual Studio pour une intégration continue. Pour des exemples et une référence complète à la commande ConnectionManager, voir [ConnectionManager référence](connectionmanager-reference.md).  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>TCP Port Forwarding

Le support Linux de Visual Studio dépend de l’endage du port TCP. **Rsync** et **gdbserver** sont affectés si l’endage portuaire TCP est désactivé sur votre système distant. Si vous êtes touché par cette dépendance, vous pouvez upvote ce [billet suggestion](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) sur Developer Community.

rsync est utilisé à la fois par les projets Linux basés sur MSBuild et les projets CMake pour [copier les en-têtes de votre système distant à Windows pour une utilisation par IntelliSense](configure-a-linux-project.md#remote_intellisense). Lorsque vous ne pouvez pas activer l’endage du port TCP, désactiver le téléchargement automatique d’en-têtes à distance. Pour le désactiver, utilisez **Tools > Options > Cross Platform > Connection Manager > Remote Headers IntelliSense Manager**. Si le système distant n’a pas activé l’endage du port TCP, vous verrez cette erreur lorsque le téléchargement d’en-têtes à distance pour IntelliSense commence :

![Erreur d’en-têtes](media/port-forwarding-headers-error.png)

rsync est également utilisé par le support CMake de Visual Studio pour copier des fichiers sources au système distant. Si vous ne pouvez pas activer l’endage du port TCP, vous pouvez utiliser sftp comme méthode de source de copie à distance. sftp est souvent plus lent que rsync, mais n’a pas une dépendance à l’avance du port TCP. Vous pouvez gérer votre méthode de sources de copie à distance avec la propriété **remoteCopySourcesMethod** dans [l’éditeur de paramètres CMake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Si l’endage du port TCP est désactivé sur votre système distant, vous verrez une erreur dans la fenêtre de sortie CMake la première fois qu’elle invoque rsync.

![Erreur de Rsync](media/port-forwarding-copy-error.png)

gdbserver peut être utilisé pour débogage sur les appareils embarqués. Si vous ne pouvez pas activer l’endélisation du port TCP, alors vous devez utiliser gdb pour tous les scénarios de débogage à distance. gdb est utilisé par défaut lors de la débogage des projets sur un système distant.

## <a name="connect-to-wsl"></a>Se connecter à WSL

::: moniker-end

::: moniker range="vs-2017"

Dans Visual Studio 2017, vous utilisez les mêmes étapes pour vous connecter à WSL que vous l’utilisez pour une machine Linux distante. Utilisez **localhost** pour le **Nom d’hôte**.

::: moniker-end

::: moniker range="vs-2019"

Ajout de la prise en charge native de Visual Studio 2019 version 16.1 pour utiliser C++ avec le [sous-système Windows pour Linux (WSL)](/windows/wsl/about). Cela signifie que vous pouvez construire et déboiffer directement sur votre installation WSL locale. Vous n’avez plus besoin d’ajouter une connexion à distance ou de configurer SSH. Vous trouverez des détails sur l’[installation de WSL](/windows/wsl/install-win10) ici.

Pour configurer votre installation WSL pour travailler avec Visual Studio, vous avez besoin des outils suivants installés : gcc ou clang, gdb, make, ninja-build (seulement requis pour les projets CMake utilisant Visual Studio 2019 version 16.6 ou plus tard), rsync, et zip. Vous pouvez les installer sur les distros qui utilisent le bon en utilisant cette commande, qui installe également le compilateur gMD:

```bash
sudo apt install g++ gdb make ninja-build rsync zip
```

Pour plus d’informations, voir [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Pour configurer un projet MSBuild pour WSL, voir [Configurer un projet Linux](configure-a-linux-project.md). Pour configurer un projet CMake pour WSL, voir [Configurer un projet Linux CMake](cmake-linux-project.md). Pour suivre les instructions pas à pas permettant de créer une application console simple avec WSL, consultez ce billet de blog d’introduction sur [C++ avec Visual Studio 2019 et le sous-système Windows pour Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Configurer un projet Linux](configure-a-linux-project.md)\
[Configurer un projet Linux CMake](cmake-linux-project.md)\
[Déployez, exécutez et débassez votre projet Linux](deploy-run-and-debug-your-linux-project.md)\
[Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md)
