---
title: Connexion à votre système Linux cible dans Visual Studio
description: Comment se connecter à un ordinateur Linux distant ou WSL à partir d’un projet C++ Visual Studio.
ms.date: 06/19/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 00d7facca2857efb0b8b43b5aaf38edce348a511
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861150"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Connexion à votre système Linux cible dans Visual Studio

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

Vous pouvez configurer un projet Linux pour cibler une machine virtuelle ou un sous-système Windows pour Linux (WSL). Pour les machines distantes et WSL sur Visual Studio 2017, vous devez configurer une connexion. 

## <a name="connect-to-a-remote-linux-computer"></a>Se connecter à un ordinateur Linux distant

Lors de la génération d’un projet Linux C++ pour un système Linux distant (machine virtuelle ou machine physique), le code Linux est copié sur votre ordinateur Linux distant, puis compilé selon les paramètres Visual Studio.

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

   ::: moniker-end

## <a name="connect-to-wsl"></a>Se connecter à WSL

::: moniker range="vs-2017"

Dans Visual Studio 2017, vous vous connectez à WSL en utilisant les mêmes étapes que pour la connexion à une machine Linux distante, comme décrit précédemment dans cet article. Utilisez **localhost** pour le **Nom d’hôte**.

::: moniker-end

::: moniker range="vs-2019"

Dans Visual Studio 2019 version 16.1, lorsque vous ciblez WSL, il n’est plus nécessaire d’ajouter une connexion à distance ou de configurer SSH. Seuls gcc, gdb, make, rsync et zip sont nécessaires sur le système Linux. Visual Studio nécessite rsync et zip seulement pour extraire les fichiers d’en-tête lors de la première utilisation de votre instance WSL sur le système de fichiers Windows à utiliser pour IntelliSense. Dans Visual Studio 2019 version 16.1, la prise en charge de WSL est basée sur Windows version 1809. Vous pouvez exécuter une version ultérieure de Windows, mais Visual Studio ne tire pas encore parti des nouvelles fonctionnalités de WSL.

Si votre distribution prend en charge apt, vous pouvez installer les packages requis avec cette commande :

```bash
sudo apt install g++ gdb make rsync zip
```

Pour configurer votre projet pour WSL, consultez [Configurer un projet Linux](configure-a-linux-project.md) ou [Configurer un projet Linux CMake](cmake-linux-project.md) selon le type de projet que vous avez.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Configurer un projet Linux](configure-a-linux-project.md)<br />
[Configurer un projet CMake Linux](cmake-linux-project.md)<br />
[Déployer, exécuter et déboguer un projet Linux](deploy-run-and-debug-your-linux-project.md)<br />




