---
title: Configurer le développement Linux à distance sécurisé conforme aux normes FIPS
description: Comment configurer une connexion de chiffrement compatible FIPS entre Visual Studio et une machine Linux pour le développement à distance.
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520892"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>Configurer le développement Linux à distance sécurisé conforme aux normes FIPS

::: moniker range="<=vs-2017"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur. Le développement Linux à distance sécurisé conforme aux normes FIPS est disponible dans Visual Studio 2019 version 16,5 et versions ultérieures.

::: moniker-end

::: moniker range="vs-2019"

La publication normes FIPS (Federal Information Processing Standard) (FIPS) 140-2 est une norme gouvernementale américaine pour les modules cryptographiques. Les implémentations de la norme sont validées par NIST. Windows a [validé la prise en charge des modules de chiffrement conformes aux normes FIPS](/windows/security/threat-protection/fips-140-validation). Dans Visual Studio 2019 version 16,5 et versions ultérieures, vous pouvez utiliser une connexion de chiffrement sécurisée et compatible FIPS à votre système Linux pour le développement à distance.

Voici comment configurer une connexion sécurisée et compatible FIPS entre Visual Studio et votre système Linux distant. Ce guide s’applique quand vous générez des projets CMake ou MSBuild Linux dans Visual Studio. Cet article est la version conforme aux normes FIPS des instructions de connexion de la rubrique [se connecter à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

## <a name="prepare-a-fips-compliant-connection"></a>Préparer une connexion conforme aux normes FIPS

Une certaine préparation est nécessaire pour utiliser une connexion SSH sécurisée par chiffrement sécurisée avec FIPS entre Visual Studio et votre système Linux distant. Pour la conformité FIPS-140-2, Visual Studio ne prend en charge que les clés RSA.

Les exemples de cet article utilisent Ubuntu 18,04 LTS avec OpenSSH Server version 7,6. Toutefois, les instructions doivent être les mêmes pour tout distribution utilisant une version modérément récente d’OpenSSH.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>Pour configurer le serveur SSH sur le système distant

1. Sur le système Linux, installez et démarrez le serveur OpenSSH :

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Si vous souhaitez que le serveur SSH démarre automatiquement lorsque le système démarre, activez-le à l’aide de systemctl :

   ```bash
   sudo systemctl enable ssh
   ```

1. Ouvrez */etc/ssh/sshd_config* en tant que root. Modifiez (ou ajoutez, s’ils n’existent pas) les lignes suivantes :

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-RSA est le seul algorithme de clé d’hôte compatible FIPS et prend en charge. Les algorithmes AES\*-CTR sont également compatibles FIPS, mais l’implémentation dans Visual Studio n’est pas approuvée. Les algorithmes d’échange de clés ECDH-\* sont compatibles FIPS, mais Visual Studio ne les prend pas en charge.

   Vous n’êtes pas limité à ces options. Vous pouvez configurer ssh pour utiliser des chiffrements supplémentaires, des algorithmes de clé d’hôte, et ainsi de suite. D’autres options de sécurité pertinentes que vous pouvez envisager sont `PermitRootLogin`, `PasswordAuthentication`et `PermitEmptyPasswords`. Pour plus d’informations, consultez la page man de sshd_config ou l’article [configuration du serveur SSH](https://www.ssh.com/ssh/sshd_config).

1. Après avoir enregistré et fermé sshd_config, redémarrez le serveur SSH pour appliquer la nouvelle configuration :

   ```bash
   sudo service ssh restart
   ```

Ensuite, vous allez créer une paire de clés RSA sur votre ordinateur Windows. Vous copierez ensuite la clé publique sur le système Linux distant pour une utilisation par SSH.

### <a name="to-create-and-use-an-rsa-key-file"></a>Pour créer et utiliser un fichier de clé RSA

1. Sur l’ordinateur Windows, générez une paire de clés RSA publique/privée à l’aide de cette commande :

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   La commande crée une clé publique et une clé privée. Par défaut, les clés sont enregistrées dans *% UserProfile%\\. ssh\\id_rsa* et *% UserProfile%\\. ssh\\id_rsa. pub*. (Dans PowerShell, utilisez `$env:USERPROFILE` au lieu de la macro cmd `%USERPROFILE%`) Si vous modifiez le nom de la clé, utilisez le nom modifié dans les étapes qui suivent.  Nous vous recommandons d’utiliser une phrase secrète pour une sécurité accrue.

1. À partir de Windows, copiez la clé publique sur la machine Linux :

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. Sur le système Linux, ajoutez la clé à la liste des clés autorisées et assurez-vous que le fichier dispose des autorisations appropriées :

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. À présent, vous pouvez tester pour voir si la nouvelle clé fonctionne dans SSH. Utilisez-le pour vous connecter à partir de Windows :

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

Vous avez correctement configuré SSH, créé et déployé des clés de chiffrement et testé votre connexion. Vous êtes maintenant prêt à configurer la connexion Visual Studio.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Se connecter au système distant dans Visual Studio

1. Dans Visual Studio, choisissez **outils > options** dans la barre de menus pour ouvrir la boîte de dialogue **options** . Ensuite, sélectionnez **multiplateforme > gestionnaire de connexions** pour ouvrir la boîte de dialogue Gestionnaire de connexions.

   Si vous n’avez pas encore configuré de connexion dans Visual Studio, quand vous générez votre projet pour la première fois, Visual Studio ouvre la boîte de dialogue Gestionnaire de connexions pour vous.

1. Dans la boîte de dialogue Gestionnaire de connexions, cliquez sur le bouton **Ajouter** pour ajouter une nouvelle connexion.

   ![Gestionnaire de connexion](media/settings_connectionmanager.png)

   La fenêtre **se connecter à un système distant** s’affiche.

   ![Connect to Remote System (Se connecter au système distant)](media/connect.png)

1. Dans la boîte de dialogue **se connecter au système distant** , entrez les détails de connexion de votre machine distante.

   | Entrée | Description
   | ----- | ---
   | **Nom de l’hôte**           | Nom ou adresse IP de votre appareil cible
   | **Port**                | Port sur lequel le service SSH est exécuté, en général 22
   | **Nom d’utilisateur**           | Utilisateur sous le nom duquel s’authentifier
   | **Type d’authentification** | Choisir une clé privée pour une connexion conforme aux normes FIPS
   | **Fichier de clé privée**    | Fichier de clé privée créé pour la connexion ssh
   | **Phrase secrète**          | Phrase secrète utilisée avec la clé privée sélectionnée ci-dessus

   Remplacez le type d’authentification par **clé privée**. Entrez le chemin d’accès à votre clé privée dans le champ **fichier de clé privée** . Vous pouvez utiliser le bouton **Parcourir** pour accéder à votre fichier de clé privée à la place. Ensuite, entrez la phrase secrète utilisée pour chiffrer votre fichier de clé privée dans le champ **phrase secrète** .

1. Choisissez le bouton **se connecter** pour tenter une connexion à l’ordinateur distant.

   Si la connexion est établie, Visual Studio configure IntelliSense pour utiliser les en-têtes distants. Pour plus d’informations, consultez [IntelliSense pour les en-têtes sur les systèmes distants](configure-a-linux-project.md#remote_intellisense).

   Si la connexion échoue, les zones des entrées qui doivent être modifiées seront surlignées en rouge.

   ![Erreur du Gestionnaire de connexion](media/settings_connectionmanagererror.png)

   Pour plus d’informations sur le dépannage de votre connexion, consultez [se connecter à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

## <a name="command-line-utility-for-the-connection-manager"></a>Utilitaire de ligne de commande pour le gestionnaire de connexions  

**Visual studio 2019 version 16,5 ou ultérieure**: ConnectionManager. exe est un utilitaire de ligne de commande permettant de gérer les connexions de développement à distance en dehors de Visual Studio. Elle est utile pour des tâches telles que la configuration d’un nouvel ordinateur de développement. Ou vous pouvez l’utiliser pour configurer Visual Studio pour une intégration continue. Pour obtenir des exemples et une référence complète à la commande ConnectionManager, consultez [référence ConnectionManager](connectionmanager-reference.md).  

## <a name="optional-enable-or-disable-fips-mode"></a>Facultatif : activer ou désactiver le mode FIPS

Il est possible d’activer le mode FIPS dans le monde entier dans Windows.

1. Pour activer le mode FIPS, appuyez sur **Windows + R** pour ouvrir la boîte de dialogue Exécuter, puis exécutez gpedit. msc.

1. Développez stratégie de l' **ordinateur Local > configuration de l’ordinateur > paramètres Windows > paramètres de sécurité > stratégies locales** et sélectionnez **options de sécurité**.

1. Sous **stratégie**, sélectionnez **chiffrement du système : utilisez des algorithmes compatibles FIPS pour le chiffrement, le hachage et la signature**, puis appuyez sur **entrée** pour ouvrir la boîte de dialogue correspondante.

1. Dans l’onglet **paramètre de sécurité locale** , sélectionnez **activé** ou **désactivé**, puis choisissez **OK** pour enregistrer vos modifications.

> [!WARNING]
> L’activation du mode FIPS peut entraîner l’interruption ou le comportement inattendu de certaines applications. Pour plus d’informations, consultez le billet de blog [pourquoi nous ne recommandons plus le « mode FIPS »](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037).

## <a name="additional-resources"></a>Ressources supplémentaires

[Documentation Microsoft sur la validation FIPS 140](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2 : exigences de sécurité pour les modules de chiffrement](https://csrc.nist.gov/publications/detail/fips/140/2/final) (à partir de NIST)

[Programme de validation de l’algorithme de chiffrement : notes de validation](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) (à partir de NIST)

Billet de blog Microsoft [expliquant pourquoi nous ne recommandons plus le « mode FIPS »](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

[Configuration du serveur SSH](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>Voir aussi

[Configurer un projet Linux](configure-a-linux-project.md)\
[Configurer un projet cmake Linux](cmake-linux-project.md)\
[Connectez-vous à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md)\
[Déployez, exécutez et déboguez votre projet Linux](deploy-run-and-debug-your-linux-project.md)\
[Configurer des sessions de débogage CMake](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
