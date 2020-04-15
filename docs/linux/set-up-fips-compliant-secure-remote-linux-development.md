---
title: Configurer le développement Linux à distance sécurisé compatible FIPS
description: Comment configurer une connexion cryptographique conforme à la FIPS entre Visual Studio et une machine Linux pour le développement à distance.
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "76520892"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>Configurer le développement Linux à distance sécurisé compatible FIPS

::: moniker range="<=vs-2017"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur. Le développement Linux sécurisé conforme à FIPS est disponible dans la version 16.5 de Visual Studio 2019 et plus tard.

::: moniker-end

::: moniker range="vs-2019"

Federal Information Processing Standard (FIPS) Publication 140-2 est une norme du gouvernement américain pour les modules cryptographiques. Les implémentations de la norme sont validées par NIST. Windows a [validé la prise en charge des modules cryptographiques conformes au FIPS](/windows/security/threat-protection/fips-140-validation). Dans visual Studio 2019 version 16.5 et plus tard, vous pouvez utiliser une connexion cryptographique sécurisée conforme à la FIPS à votre système Linux pour le développement à distance.

Voici comment configurer une connexion sécurisée conforme aux FIPS entre Visual Studio et votre système Linux distant. Ce guide s’applique lorsque vous construisez des projets CMake ou MSBuild Linux dans Visual Studio. Cet article est la version conforme aux FIPS des instructions de connexion dans [Connect to your remote Linux computer](connect-to-your-remote-linux-computer.md).

## <a name="prepare-a-fips-compliant-connection"></a>Préparer une connexion conforme au FIPS

Une certaine préparation est nécessaire pour utiliser une connexion ssh conforme à la FIPS et cryptographiquement sécurisée entre Visual Studio et votre système Linux distant. Pour la conformité FIPS-140-2, Visual Studio ne prend en charge que les clés RSA.

Les exemples de cet article utilisent Ubuntu 18.04 LTS avec la version serveur OpenSSH 7.6. Cependant, les instructions devraient être les mêmes pour toute distro en utilisant une version modérément récente de OpenSSH.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>Configurer le serveur SSH sur le système distant

1. Sur le système Linux, installez et démarrez le serveur OpenSSH :

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Si vous souhaitez que le serveur ssh démarre automatiquement lorsque le système démarre, activez-le à l’aide de systemctl :

   ```bash
   sudo systemctl enable ssh
   ```

1. Ouvrez */etc/ssh/sshd_config* comme racine. Modifier (ou ajouter, s’ils n’existent pas) les lignes suivantes :

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa est le seul algorithme clé d’hôte conforme à la FIPS VS prend en charge. Les algorithmes aes-ctr\*sont également conformes FIPS, mais la mise en œuvre dans Visual Studio n’est pas approuvé. Les algorithmes\* d’échange ecdh-clés sont conformes à LA FIPS, mais Visual Studio ne les prend pas en charge.

   Vous ne vous limitez pas à ces options. Vous pouvez configurer ssh pour utiliser des chiffrements supplémentaires, héberger des algorithmes clés, et ainsi de suite. D’autres options de sécurité pertinentes `PermitRootLogin` `PasswordAuthentication`que `PermitEmptyPasswords`vous voudrez peut-être envisager sont , , et . Pour plus d’informations, consultez la page homme pour sshd_config ou l’article [SSH Server Configuration](https://www.ssh.com/ssh/sshd_config).

1. Après l’enregistrement et la fermeture sshd_config, redémarrez le serveur ssh pour appliquer la nouvelle configuration :

   ```bash
   sudo service ssh restart
   ```

Ensuite, vous allez créer une paire de clés RSA sur votre ordinateur Windows. Ensuite, vous copierez la clé publique du système Linux à distance pour une utilisation par ssh.

### <a name="to-create-and-use-an-rsa-key-file"></a>Créer et utiliser un fichier clé RSA

1. Sur la machine Windows, générer une paire de clés RSA public/privé en utilisant cette commande :

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   La commande crée une clé publique et une clé privée. Par défaut, les clés sont *enregistrées\\à %USERPROFILE% .ssh\\id_rsa* et *%USERPROFILE%\\.ssh\\id_rsa.pub*. (Dans Powershell, `$env:USERPROFILE` utilisez au lieu `%USERPROFILE%`de la macro cmd ) Si vous modifiez le nom clé, utilisez le nom changé dans les étapes qui suivent.  Nous vous recommandons d’utiliser un passphrase pour une sécurité accrue.

1. De Windows, copiez la clé publique de la machine Linux :

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. Sur le système Linux, ajoutez la clé à la liste des clés autorisées et assurez-vous que le fichier dispose des autorisations correctes :

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. Maintenant, vous pouvez tester pour voir si la nouvelle clé fonctionne en ssh. Utilisez-le pour vous connecter à partir de Windows:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

Vous avez réussi à configurer ssh, créé et déployé des clés de chiffrement, et testé votre connexion. Maintenant, vous êtes prêt à configurer la connexion Visual Studio.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Connectez-vous au système distant de Visual Studio

1. Dans Visual Studio, choisissez **Tools > Options** sur la barre de menu pour ouvrir le dialogue **Options.** Sélectionnez ensuite **Cross Platform > Connection Manager** pour ouvrir le dialogue Connection Manager.

   Si vous n’avez pas déjà établi de connexion dans Visual Studio, lorsque vous construisez votre projet pour la première fois, Visual Studio vous ouvre le dialogue Connection Manager.

1. Dans le dialogue Connection Manager, choisissez le bouton **Ajouter** pour ajouter une nouvelle connexion.

   ![Gestionnaire de connexions](media/settings_connectionmanager.png)

   La fenêtre **Connect to Remote System** s’affiche.

   ![Connect to Remote System (Se connecter au système distant)](media/connect.png)

1. Dans le dialogue **Connect to Remote System,** entrez les détails de connexion de votre machine à distance.

   | Entrée | Description
   | ----- | ---
   | **Nom de l’hôte**           | Nom ou adresse IP de votre appareil cible
   | **Port**                | Port sur lequel le service SSH est exécuté, en général 22
   | **Nom d'utilisateur**           | Utilisateur sous le nom duquel s’authentifier
   | **Type d’authentification** | Choisissez la clé privée pour une connexion conforme au FIPS
   | **Fichier de clé privée**    | Fichier de clé privée créé pour la connexion ssh
   | **Phrase**          | Phrase secrète utilisée avec la clé privée sélectionnée ci-dessus

   Modifier le type d’authentification en **clé privée**. Entrez le chemin de votre clé privée dans le domaine **du fichier clé privé.** Vous pouvez utiliser le bouton **Parcourir** pour naviguer vers votre fichier clé privé à la place. Ensuite, entrez la passphrase utilisée pour chiffrer votre fichier clé privé dans le champ **Passphrase.**

1. Choisissez le bouton **Connect** pour tenter une connexion à l’ordinateur distant.

   Si la connexion réussit, Visual Studio configure IntelliSense pour utiliser les en-têtes distants. Pour plus d’informations, consultez [IntelliSense pour les en-têtes sur les systèmes distants](configure-a-linux-project.md#remote_intellisense).

   Si la connexion échoue, les zones des entrées qui doivent être modifiées seront surlignées en rouge.

   ![Erreur du Gestionnaire de connexion](media/settings_connectionmanagererror.png)

   Pour plus d’informations sur le dépannage de votre connexion, consultez [Connectez-vous à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

## <a name="command-line-utility-for-the-connection-manager"></a>Service public de la ligne de commandement pour le gestionnaire de connexion  

**Visual Studio 2019 version 16.5 ou plus tard**: ConnectionManager.exe est un utilitaire de commande pour gérer les connexions de développement à distance en dehors de Visual Studio. Il est utile pour des tâches telles que l’approvisionnement d’une nouvelle machine de développement. Ou, vous pouvez l’utiliser pour configurer Visual Studio pour une intégration continue. Pour des exemples et une référence complète à la commande ConnectionManager, voir [ConnectionManager référence](connectionmanager-reference.md).  

## <a name="optional-enable-or-disable-fips-mode"></a>Facultatif : Activez ou désactiver le mode FIPS

Il est possible d’activer le mode FIPS dans le monde entier dans Windows.

1. Pour activer le mode FIPS, appuyez sur **Windows-R** pour ouvrir le dialogue Run, puis exécutez gpedit.msc.

1. Élargir **la politique informatique locale > la configuration informatique > les paramètres Windows > paramètres de sécurité > les politiques locales** et sélectionner les **options de sécurité**.

1. En vertu **de la politique**, sélectionnez la **cryptographie du système : utilisez des algorithmes conformes au FIPS pour le chiffrement, le hachage et la signature,** puis appuyez sur **Enter** pour ouvrir sa boîte de dialogue.

1. Dans l’onglet **Local Security Setting,** sélectionnez **Activé** ou **Désactivé,** puis choisissez **OK** pour enregistrer vos modifications.

> [!WARNING]
> L’activation du mode FIPS peut entraîner la rupture ou le comportement inattendu de certaines applications. Pour plus d’informations, voir le blog [Pourquoi nous ne recommandons pas "mode FIPS" Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037).

## <a name="additional-resources"></a>Ressources supplémentaires

[Documentation Microsoft sur la validation FIPS 140](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2: Exigences de sécurité pour les modules cryptographiques](https://csrc.nist.gov/publications/detail/fips/140/2/final) (de NIST)

[Programme de validation des algorithmes cryptographiques : Notes](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) de validation (de NIST)

Microsoft blog post sur [Pourquoi nous ne recommandons pas "mode FIPS" Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

[Configuration du serveur SSH](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>Voir aussi

[Configurer un projet Linux](configure-a-linux-project.md)\
[Configurer un projet Linux CMake](cmake-linux-project.md)\
[Connectez-vous à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md)\
[Déployez, exécutez et débassez votre projet Linux](deploy-run-and-debug-your-linux-project.md)\
[Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
