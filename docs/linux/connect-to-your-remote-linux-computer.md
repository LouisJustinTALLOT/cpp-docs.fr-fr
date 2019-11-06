---
title: Connexion à votre système Linux cible dans Visual Studio
description: Comment se connecter à un ordinateur Linux distant ou WSL à partir d’un projet C++ Visual Studio.
ms.date: 09/04/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 3d91faa7aa83c86e8c2f3544ee61c16f75f8c346
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626776"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Connexion à votre système Linux cible dans Visual Studio

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

Vous pouvez configurer un projet Linux pour cibler une machine virtuelle ou le sous-système Windows pour Linux (WSL). Pour les machines distantes et WSL sur Visual Studio 2017, vous devez configurer une connexion à distance. 

## <a name="connect-to-a-remote-linux-computer"></a>Se connecter à un ordinateur Linux distant

Lors de la génération d’un projet Linux C++ pour un système Linux distant (machine virtuelle ou machine physique), le code source Linux est copié sur votre ordinateur Linux distant, puis compilé selon les paramètres Visual Studio.

Pour configurer cette connexion distante :

1. Générez le projet pour la première fois ou créez manuellement une entrée en sélectionnant **Outils > Options**, puis ouvrez le nœud **Multiplateforme > Gestionnaire de connexion** et cliquez sur le bouton **Ajouter**.

   ![Gestionnaire de connexion](media/settings_connectionmanager.png)

   Dans les deux cas, la fenêtre **Connect to Remote System** (Se connecter au système distant) s’affiche.

   ![Connect to Remote System (Se connecter au système distant)](media/connect.png)

1. Entrez les informations suivantes :

   | Entrée | Description
   | ----- | ---
   | **Nom de l’hôte**           | Nom ou adresse IP de votre appareil cible
   | **Port**                | Port sur lequel le service SSH est exécuté, en général 22
   | **Nom d’utilisateur**           | Utilisateur sous le nom duquel s’authentifier
   | **Type d’authentification** | Un mot de passe ou une clé privée sont tous deux pris en charge
   | **Mot de passe**            | Mot de passe du nom d’utilisateur entré
   | **Fichier de clé privée**    | Fichier de clé privée créé pour la connexion ssh
   | **Phrase secrète**          | Phrase secrète utilisée avec la clé privée sélectionnée ci-dessus

   Vous pouvez utiliser un mot de passe ou un fichier de clé avec une phrase secrète pour l’authentification. Pour de nombreux scénarios de développement, l’authentification par mot de passe est suffisante. Si vous préférez utiliser un fichier de clé publique/privée, vous pouvez en créer un nouveau ou [en réutiliser un](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). Actuellement, seules les clés RSA et DSA sont prises en charge. 
   
   Vous pouvez créer un fichier de clé privée RSA en suivant ces étapes :

    1. Sur la machine Windows, créez la paire de clés ssh avec `ssh-keygen -t rsa`. Cela crée une clé publique et une clé privée. Par défaut, les clés sont placées sous `C:\Users\%USERNAME%\.ssh` avec les noms `id_rsa.pub` et `id_rsa`.

    1. À partir de Windows, copiez la clé publique sur la machine Linux : `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

    1. Sur le système Linux, ajoutez la clé à la liste de clés autorisées (et vérifiez que le fichier dispose des autorisations appropriées) : `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Cliquez sur le bouton **Connect** (Se connecter) pour tenter une connexion à l’ordinateur distant. 

   Si la connexion réussit, Visual Studio commence à configurer IntelliSense pour utiliser les en-têtes distants. Pour plus d’informations, consultez [IntelliSense pour les en-têtes sur les systèmes distants](configure-a-linux-project.md#remote_intellisense).

   Si la connexion échoue, les zones des entrées qui doivent être modifiées seront surlignées en rouge.

   ![Erreur du Gestionnaire de connexion](media/settings_connectionmanagererror.png)

   Si vous utilisez des fichiers de clé pour l’authentification, vérifiez que le serveur SSH de la machine cible est en cours d’exécution et configuré correctement.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Accédez à **Outils > Options > Multiplateforme > Journalisation** pour activer la journalisation afin de résoudre les problèmes de connexion :

   ![Journalisation à distance](media/remote-logging-vs2019.png)

   Les journaux incluent les connexions, toutes les commandes envoyées à la machine distante (leur texte, le code de sortie et la durée d’exécution) et toutes les sorties de Visual Studio à dans l’interpréteur de commandes. La journalisation fonctionne pour n’importe quel projet CMake multiplateforme ou projet Linux basé sur MSBuild dans Visual Studio.

   Vous pouvez configurer la sortie pour qu’elle soit écrite dans un fichier ou dans le volet de **Journalisation multiplateforme** dans la fenêtre Sortie. Pour les projets Linux basés sur MSBuild, les commandes émises par MSBuild sur la machine distante ne sont pas acheminées vers la **fenêtre Sortie**, car elles sont émises en dehors du processus. Au lieu de cela, elles sont enregistrées dans un fichier avec le préfixe « msbuild_ ».
   
## <a name="tcp-port-forwarding"></a>Réacheminement de port TCP

Le support Linux de Visual Studio dépend de la réacheminement de port TCP. La **synchronisation** et la **gdbserver** sont affectées si le transfert de port TCP est désactivé sur votre système distant. 

La synchronisation est utilisée par les projets Linux basés sur MSBuild et les projets CMake pour [copier les en-têtes de votre système distant vers Windows à utiliser pour IntelliSense](configure-a-linux-project.md#remote_intellisense). Si vous n’êtes pas en mesure d’activer le transfert de port TCP, vous pouvez désactiver le téléchargement automatique des en-têtes distants via Outils > Options > inter-plateforme > Gestionnaire de connexions > Gestionnaire d’en-têtes distants IntelliSense. Si le réacheminement de port TCP n’est pas activé sur le système distant auquel vous essayez de vous connecter, l’erreur suivante s’affiche lorsque le téléchargement des en-têtes distants pour IntelliSense démarre.

![Erreur en-têtes](media/port-forwarding-headers-error.png)

La synchronisation de la synchronisation est également utilisée par la prise en charge CMake de Visual Studio pour copier les fichiers sources sur le système distant. Si vous n’êtes pas en mesure d’activer le transfert de port TCP, vous pouvez utiliser SFTP comme méthode de copie distante de sources. Sftp est généralement plus lent que la synchronisation d’annuaire, mais ne dépend pas du transfert de port TCP. Vous pouvez gérer votre méthode de copie distante de sources à l’aide de la propriété remoteCopySourcesMethod dans l' [éditeur de paramètres cmake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Si le transfert de port TCP est désactivé sur votre système distant, vous verrez une erreur dans la fenêtre de sortie CMake lors de la première exécution de la synchronisation.

![Erreur de synchronisation](media/port-forwarding-copy-error.png)

Gdbserver peut être utilisé pour le débogage sur des appareils intégrés. Si vous n’êtes pas en mesure d’activer le transfert de port TCP, vous devez utiliser gdb pour tous les scénarios de débogage distant. Gdb est utilisé par défaut lors du débogage de projets sur un système distant. 

   ::: moniker-end

## <a name="connect-to-wsl"></a>Se connecter à WSL

::: moniker range="vs-2017"

Dans Visual Studio 2017, vous vous connectez à WSL en utilisant les mêmes étapes que pour la connexion à une machine Linux distante, comme décrit précédemment dans cet article. Utilisez **localhost** pour le **Nom d’hôte**.

::: moniker-end

::: moniker range="vs-2019"

Ajout de la prise en charge native de Visual Studio 2019 version 16.1 pour utiliser C++ avec le [sous-système Windows pour Linux (WSL)](https://docs.microsoft.com/windows/wsl/about).  Cela signifie que vous n’avez plus besoin d’ajouter une connexion à distance ou de configurer SSH pour générer et déboguer sur votre installation WSL locale. Vous trouverez des détails sur l’[installation de WSL](https://docs.microsoft.com/windows/wsl/install-win10) ici.

Pour configurer votre installation WSL de façon à ce qu’elle fonctionne avec Visual Studio, vous devez avoir installé les outils suivants : GCC ou Clang, gdb, Make, rsync et zip. Vous pouvez les installer sur distributions qui utilisent apt à l’aide de cette commande, qui installe également le compilateur g + + : 

```bash
sudo apt install g++ gdb make rsync zip
```
Pour plus d’informations, consultez [Télécharger, installer et configurer la charge de travail Linux](download-install-and-setup-the-linux-development-workload.md).

Pour configurer votre projet pour WSL, consultez [Configurer un projet Linux](configure-a-linux-project.md) ou [Configurer un projet Linux CMake](cmake-linux-project.md) selon le type de projet que vous avez. Pour suivre les instructions pas à pas permettant de créer une application console simple avec WSL, consultez ce billet de blog d’introduction sur [C++ avec Visual Studio 2019 et le sous-système Windows pour Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Configurer un projet Linux](configure-a-linux-project.md)<br />
[Configurer un projet CMake Linux](cmake-linux-project.md)<br />
[Déployer, exécuter et déboguer un projet Linux](deploy-run-and-debug-your-linux-project.md)<br />
[Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md)
