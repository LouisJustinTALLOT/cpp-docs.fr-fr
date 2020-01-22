---
title: Connexion à votre système Linux cible dans Visual Studio
description: Comment se connecter à une machine Linux distante ou à un sous-système Windows pour Linux C++ à partir d’un projet Visual Studio.
ms.date: 01/17/2020
ms.openlocfilehash: d0065b63d7a81d3ae3d68b26184c88aca77f601c
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518216"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Connexion à votre système Linux cible dans Visual Studio

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range="vs-2017"

Vous pouvez configurer un projet Linux pour cibler une machine virtuelle ou le sous-système Windows pour Linux (WSL). Pour les ordinateurs distants et pour WSL, vous devez configurer une connexion à distance dans Visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Vous pouvez configurer un projet Linux pour cibler une machine virtuelle ou le sous-système Windows pour Linux (WSL). Pour un ordinateur distant, vous devez configurer une connexion à distance dans Visual Studio. Pour vous connecter à WSL, passez directement à la section [se connecter à WSL](#connect-to-wsl) .

::: moniker-end

::: moniker range=">=vs-2017"

Lors de l’utilisation d’une connexion à distance C++ , Visual Studio génère des projets Linux sur l’ordinateur distant. Peu importe s’il s’agit d’un ordinateur physique, d’une machine virtuelle dans le Cloud ou de WSL.
Pour générer le projet, Visual Studio copie le code source sur votre ordinateur Linux distant. Ensuite, le code est compilé en fonction des paramètres de Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 version 16,5 et versions ultérieures prennent également en charge les connexions de chiffrement sécurisées, normes FIPS (Federal Information Processing Standard) (FIPS) 140-2 aux systèmes Linux pour le développement à distance. Pour utiliser une connexion conforme aux normes FIPS, suivez les étapes décrites dans [configurer le développement Linux à distance sécurisé compatible FIPS](set-up-fips-compliant-secure-remote-linux-development.md) à la place.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>Configuration du serveur SSH sur le système distant

Si ssh n’est pas déjà configuré et en cours d’exécution sur votre système Linux, procédez comme suit pour l’installer. Les exemples de cet article utilisent Ubuntu 18,04 LTS avec OpenSSH Server version 7,6. Toutefois, les instructions doivent être les mêmes pour tout distribution utilisant une version modérément récente d’OpenSSH.

1. Sur le système Linux, installez et démarrez le serveur OpenSSH :

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Si vous souhaitez que le serveur SSH démarre automatiquement lorsque le système démarre, activez-le à l’aide de systemctl :

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>Configurer la connexion à distance

1. Dans Visual Studio, choisissez **outils > options** dans la barre de menus pour ouvrir la boîte de dialogue **options** . Ensuite, sélectionnez **multiplateforme > gestionnaire de connexions** pour ouvrir la boîte de dialogue Gestionnaire de connexions.

   Si vous n’avez pas encore configuré de connexion dans Visual Studio, quand vous générez votre projet pour la première fois, Visual Studio ouvre la boîte de dialogue Gestionnaire de connexions pour vous.

1. Dans la boîte de dialogue Gestionnaire de connexions, cliquez sur le bouton **Ajouter** pour ajouter une nouvelle connexion.

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

   Vous pouvez utiliser un mot de passe ou un fichier de clé et une phrase secrète pour l’authentification. Pour de nombreux scénarios de développement, l’authentification par mot de passe est suffisante, mais les fichiers clés sont plus sécurisés. Si vous disposez déjà d’une paire de clés, il est possible de la réutiliser. Actuellement, Visual Studio ne prend en charge que les clés RSA et DSA pour les connexions à distance.

1. Choisissez le bouton **se connecter** pour tenter une connexion à l’ordinateur distant.

   Si la connexion est établie, Visual Studio configure IntelliSense pour utiliser les en-têtes distants. Pour plus d’informations, consultez [IntelliSense pour les en-têtes sur les systèmes distants](configure-a-linux-project.md#remote_intellisense).

   Si la connexion échoue, les zones des entrées qui doivent être modifiées seront surlignées en rouge.

   ![Erreur du Gestionnaire de connexion](media/settings_connectionmanagererror.png)

   Si vous utilisez des fichiers de clé pour l’authentification, assurez-vous que le serveur SSH de l’ordinateur cible est en cours d’exécution et qu’il est configuré correctement.

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>Journalisation des connexions à distance

   Vous pouvez activer la journalisation pour aider à résoudre les problèmes de connexion. Dans la barre de menus, sélectionnez **outils > options**. Dans la boîte de dialogue **options** , sélectionnez **multiplateforme > la journalisation**:

   ![Journalisation à distance](media/remote-logging-vs2019.png)

   Les journaux incluent les connexions, toutes les commandes envoyées à la machine distante (leur texte, le code de sortie et la durée d’exécution) et toutes les sorties de Visual Studio à dans l’interpréteur de commandes. La journalisation fonctionne pour n’importe quel projet CMake multiplateforme ou projet Linux basé sur MSBuild dans Visual Studio.

   Vous pouvez configurer la sortie pour accéder à un fichier ou au volet de **journalisation multiplateforme** dans la fenêtre sortie. Pour les projets Linux basés sur MSBuild, les commandes MSBuild envoyées à l’ordinateur distant ne sont pas acheminées vers le **fenêtre Sortie** , car elles sont émises hors processus. Au lieu de cela, ils sont enregistrés dans un fichier, avec le préfixe « msbuild_ ».

## <a name="command-line-utility-for-the-connection-manager"></a>Utilitaire de ligne de commande pour le gestionnaire de connexions  

**Visual studio 2019 version 16,5 ou ultérieure**: ConnectionManager. exe est un utilitaire de ligne de commande permettant de gérer les connexions de développement à distance en dehors de Visual Studio. Elle est utile pour des tâches telles que la configuration d’un nouvel ordinateur de développement. Ou vous pouvez l’utiliser pour configurer Visual Studio pour une intégration continue. Pour obtenir des exemples et une référence complète à la commande ConnectionManager, consultez [référence ConnectionManager](connectionmanager-reference.md).  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>Réacheminement de port TCP

Le support Linux de Visual Studio dépend de la réacheminement de port TCP. La **synchronisation** et les **gdbserver** sont affectés si le transfert de port TCP est désactivé sur votre système distant. Si vous êtes concerné par cette dépendance, vous pouvez voter ce ticket de [suggestion](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) sur la communauté des développeurs.

la synchronisation est utilisée par les projets Linux basés sur MSBuild et les projets CMake pour [copier les en-têtes de votre système distant vers Windows en vue d’une utilisation par IntelliSense](configure-a-linux-project.md#remote_intellisense). Lorsque vous ne pouvez pas activer le transfert de port TCP, désactivez le téléchargement automatique des en-têtes distants. Pour le désactiver, utilisez **outils > Options > multiplateforme > gestionnaire de connexions > en-têtes distants gestionnaire IntelliSense**. Si le réacheminement de port TCP n’est pas activé sur le système distant, vous voyez cette erreur lorsque le téléchargement des en-têtes distants pour IntelliSense commence :

![Erreur en-têtes](media/port-forwarding-headers-error.png)

la synchronisation de la synchronisation est également utilisée par la prise en charge CMake de Visual Studio pour copier les fichiers sources sur le système distant. Si vous ne pouvez pas activer le réacheminement de port TCP, vous pouvez utiliser SFTP comme méthode de copie distante de sources. sftp est souvent plus lent que la synchronisation d’annuaire, mais ne dépend pas du transfert de port TCP. Vous pouvez gérer votre méthode de copie distante de sources à l’aide de la propriété **remoteCopySourcesMethod** dans l' [éditeur de paramètres cmake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Si le transfert de port TCP est désactivé sur votre système distant, une erreur s’affiche dans la fenêtre de sortie de CMake la première fois qu’elle appelle la synchronisation.

![Erreur de synchronisation](media/port-forwarding-copy-error.png)

gdbserver peut être utilisé pour le débogage sur des appareils intégrés. Si vous ne pouvez pas activer le réacheminement de port TCP, vous devez utiliser gdb pour tous les scénarios de débogage distant. gdb est utilisé par défaut lors du débogage de projets sur un système distant.

## <a name="connect-to-wsl"></a>Se connecter à WSL

::: moniker-end

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
