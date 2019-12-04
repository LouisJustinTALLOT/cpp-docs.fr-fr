---
title: Connexion à votre système Linux cible dans Visual Studio
description: Comment se connecter à une machine Linux distante ou à un sous-système Windows pour Linux C++ à partir d’un projet Visual Studio.
ms.date: 11/09/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 4069979100c3b71a32e90ad72fb334d21a226e64
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755276"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Connexion à votre système Linux cible dans Visual Studio

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

Vous pouvez configurer un projet Linux pour cibler une machine virtuelle ou le sous-système Windows pour Linux (WSL). Pour les machines distantes et WSL sur Visual Studio 2017, vous devez configurer une connexion à distance.

## <a name="connect-to-a-remote-linux-computer"></a>Se connecter à un ordinateur Linux distant

Lors de la C++ création d’un projet Linux pour un système Linux distant (machine virtuelle ou ordinateur physique), le code source Linux est copié sur votre ordinateur Linux distant. Elle est ensuite compilée en fonction des paramètres de Visual Studio.

Pour configurer cette connexion distante :

1. Générez le projet pour la première fois. Ou vous pouvez créer une nouvelle entrée manuellement. Sélectionnez **outils > options**, ouvrez le nœud **Cross Platform > Connection Manager** , puis cliquez sur le bouton **Ajouter** .

   ![Gestionnaire de connexion](media/settings_connectionmanager.png)

   Dans les deux cas de figure, la fenêtre **se connecter à un système distant** s’affiche.

   ![Connect to Remote System (Se connecter au système distant)](media/connect.png)

1. Entrez les informations suivantes :

   | Entrée | Description
   | ----- | ---
   | **Nom de l’hôte**           | Nom ou adresse IP de votre appareil cible
   | **Port**                | Port sur lequel le service SSH est exécuté, en général 22
   | **Nom d’utilisateur**           | Utilisateur sous le nom duquel s’authentifier
   | **Type d’authentification** | Le mot de passe et la clé privée sont pris en charge
   | **Mot de passe**            | Mot de passe du nom d’utilisateur entré
   | **Fichier de clé privée**    | Fichier de clé privée créé pour la connexion ssh
   | **Phrase secrète**          | Phrase secrète utilisée avec la clé privée sélectionnée ci-dessus

   Vous pouvez utiliser un mot de passe ou un fichier de clé et une phrase secrète pour l’authentification. Pour de nombreux scénarios de développement, l’authentification par mot de passe est suffisante. Si vous préférez utiliser un fichier de clé publique/privée, vous pouvez en créer un nouveau ou [en réutiliser un](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). Actuellement, seules les clés RSA et DSA sont prises en charge.

   Vous pouvez créer un fichier de clé privée RSA en suivant ces étapes :

   1. Sur la machine Windows, créez la paire de clés ssh avec `ssh-keygen -t rsa`. La commande crée une clé publique et une clé privée. Par défaut, il place les clés sous `C:\Users\%USERNAME%\.ssh`, à l’aide des noms `id_rsa.pub` et `id_rsa`.

   1. À partir de Windows, copiez la clé publique sur la machine Linux : `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

   1. Sur le système Linux, ajoutez la clé à la liste de clés autorisées (et vérifiez que le fichier dispose des autorisations appropriées) : `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Choisissez le bouton **se connecter** pour tenter une connexion à l’ordinateur distant.

   Si la connexion réussit, Visual Studio commence à configurer IntelliSense pour utiliser les en-têtes distants. Pour plus d’informations, consultez [IntelliSense pour les en-têtes sur les systèmes distants](configure-a-linux-project.md#remote_intellisense).

   Si la connexion échoue, les zones des entrées qui doivent être modifiées seront surlignées en rouge.

   ![Erreur du Gestionnaire de connexion](media/settings_connectionmanagererror.png)

   Si vous utilisez des fichiers de clé pour l’authentification, assurez-vous que le serveur SSH de l’ordinateur cible est en cours d’exécution et qu’il est configuré correctement.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Accédez à **Outils > Options > Multiplateforme > Journalisation** pour activer la journalisation afin de résoudre les problèmes de connexion :

   ![Journalisation à distance](media/remote-logging-vs2019.png)

   Les journaux incluent les connexions, toutes les commandes envoyées à la machine distante (leur texte, le code de sortie et la durée d’exécution) et toutes les sorties de Visual Studio à dans l’interpréteur de commandes. La journalisation fonctionne pour n’importe quel projet CMake multiplateforme ou projet Linux basé sur MSBuild dans Visual Studio.

   Vous pouvez configurer la sortie pour qu’elle soit écrite dans un fichier ou dans le volet de **Journalisation multiplateforme** dans la fenêtre Sortie. Pour les projets Linux basés sur MSBuild, les commandes MSBuild envoyées à l’ordinateur distant ne sont pas acheminées vers le **fenêtre Sortie** , car elles sont émises hors processus. Au lieu de cela, ils sont enregistrés dans un fichier, avec le préfixe « msbuild_ ».

## <a name="tcp-port-forwarding"></a>Réacheminement de port TCP

Le support Linux de Visual Studio dépend de la réacheminement de port TCP. La **synchronisation** et la **gdbserver** sont affectées si le transfert de port TCP est désactivé sur votre système distant. Si vous êtes concerné par cette dépendance, vous pouvez voter ce ticket de [suggestion](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) sur la communauté des développeurs.

la synchronisation est utilisée par les projets Linux basés sur MSBuild et les projets CMake pour [copier les en-têtes de votre système distant vers Windows en vue d’une utilisation par IntelliSense](configure-a-linux-project.md#remote_intellisense). Lorsque vous ne pouvez pas activer le transfert de port TCP, désactivez le téléchargement automatique des en-têtes distants. Pour le désactiver, utilisez **outils > Options > multiplateforme > gestionnaire de connexions > en-têtes distants gestionnaire IntelliSense**. Si le réacheminement de port TCP n’est pas activé sur le système distant, vous voyez cette erreur lorsque le téléchargement des en-têtes distants pour IntelliSense commence :

![Erreur en-têtes](media/port-forwarding-headers-error.png)

La synchronisation de la synchronisation est également utilisée par la prise en charge CMake de Visual Studio pour copier les fichiers sources sur le système distant. Si vous ne pouvez pas activer le réacheminement de port TCP, vous pouvez utiliser SFTP comme méthode de copie distante de sources. sftp est souvent plus lent que la synchronisation d’annuaire, mais ne dépend pas du transfert de port TCP. Vous pouvez gérer votre méthode de copie distante de sources à l’aide de la propriété **remoteCopySourcesMethod** dans l' [éditeur de paramètres cmake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Si le transfert de port TCP est désactivé sur votre système distant, une erreur s’affiche dans la fenêtre de sortie de CMake la première fois qu’elle appelle la synchronisation.

![Erreur de synchronisation](media/port-forwarding-copy-error.png)

Gdbserver peut être utilisé pour le débogage sur des appareils intégrés. Si vous ne pouvez pas activer le réacheminement de port TCP, vous devez utiliser gdb pour tous les scénarios de débogage distant. Gdb est utilisé par défaut lors du débogage de projets sur un système distant.

::: moniker-end

## <a name="connect-to-wsl"></a>Se connecter à WSL

::: moniker range="vs-2017"

Dans Visual Studio 2017, vous utilisez la même procédure pour vous connecter à WSL que pour une machine Linux distante. Utilisez **localhost** pour le **Nom d’hôte**.

::: moniker-end

::: moniker range="vs-2019"

Ajout de la prise en charge native de Visual Studio 2019 version 16.1 pour utiliser C++ avec le [sous-système Windows pour Linux (WSL)](/windows/wsl/about). Cela signifie que vous pouvez créer et déboguer directement sur votre installation WSL locale. Vous n’avez plus besoin d’ajouter une connexion à distance ni de configurer SSH. Vous trouverez des détails sur l’[installation de WSL](/windows/wsl/install-win10) ici.

Pour configurer votre installation WSL de sorte qu’elle fonctionne avec Visual Studio, vous devez avoir installé les outils suivants : GCC ou Clang, gdb, Make, rsync et zip. Vous pouvez les installer sur distributions qui utilisent apt à l’aide de cette commande, qui installe également le compilateur g + + :

```bash
sudo apt install g++ gdb make rsync zip
```

Pour plus d’informations, consultez [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Pour configurer un projet MSBuild pour WSL, consultez [configurer un projet Linux](configure-a-linux-project.md). Pour configurer un projet CMake pour WSL, consultez [configurer un projet cmake Linux](cmake-linux-project.md). Pour suivre les instructions pas à pas permettant de créer une application console simple avec WSL, consultez ce billet de blog d’introduction sur [C++ avec Visual Studio 2019 et le sous-système Windows pour Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Configurer un projet Linux](configure-a-linux-project.md)\
[Configurer un projet cmake Linux](cmake-linux-project.md)\
[Déployez, exécutez et déboguez votre projet Linux](deploy-run-and-debug-your-linux-project.md)\
[Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md)
