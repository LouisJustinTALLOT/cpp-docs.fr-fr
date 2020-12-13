---
description: 'En savoir plus sur : installer et configurer les outils de génération à l’aide d’iOS'
title: Installer et configurer des outils de génération en utilisant iOS
ms.date: 10/17/2019
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
ms.openlocfilehash: e6d91dc679d86085c1886cab0d330a4fafb3c617
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339460"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Installer et configurer des outils de génération en utilisant iOS

Vous pouvez utiliser Visual Studio avec le **développement mobile multiplateforme avec** les outils C++ pour modifier, déboguer et déployer du code iOS sur le simulateur iOS ou sur un appareil iOS. Toutefois, en raison des restrictions de licences, le code doit être généré et exécuté à distance sur un Mac. Pour générer et exécuter des applications iOS à l’aide de Visual Studio, vous devez installer et configurer l’agent distant, [vcremote](https://www.npmjs.com/package/vcremote), sur votre Mac. L’agent distant gère les demandes de génération de Visual Studio et exécute l’application sur un appareil iOS connecté au Mac ou dans le simulateur iOS sur le Mac.

> [!NOTE]
> Pour plus d’informations sur l’utilisation des services Mac hébergés dans le cloud plutôt que sur un Mac, consultez [Configurer Visual Studio pour vous connecter à votre Mac hébergé dans le cloud](/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017&preserve-view=true#configure-visual-studio-to-connect-to-your-cloud-hosted-mac). Les instructions portent sur la génération à l’aide de Visual Studio Tools pour Apache Cordova. Pour utiliser les instructions de génération à l’aide de C++, remplacez `vcremote` par `remotebuild` .

Une fois que vous avez installé les outils de génération à l’aide d’iOS, reportez-vous à cet article pour savoir comment configurer et mettre à jour rapidement l’agent distant pour le développement iOS dans Visual Studio et sur votre Mac.

## <a name="prerequisites"></a>Prérequis

Pour installer et utiliser l’agent distant en vue de développer du code pour iOS, vous devez tout d’abord disposer des éléments suivants :

- Un ordinateur Mac exécutant macOS Mojave version 10.14 ou ultérieure

- Un [ID Apple](https://appleid.apple.com/)

- Un compte [Programme développeur Apple](https://developer.apple.com/programs/) actif

   Vous pouvez obtenir un compte gratuit qui permet le chargement indépendant (sideloading) d’applications sur un appareil iOS uniquement pour le test, mais pas pour la distribution.

- [Xcode](https://developer.apple.com/xcode/downloads/) version 10.2.1 ou ultérieure

   Xcode peut être téléchargé depuis l’App Store.

- Outils en ligne de commande Xcode

   Pour installer les outils en ligne de commande Xcode, ouvrez l’application Terminal sur votre Mac et entrez la commande suivante :

   `xcode-select --install`

- Un compte ID Apple configuré dans Xcode comme identité de signature pour signer des applications

   Pour afficher ou définir votre identité de signature dans Xcode, ouvrez le menu **Xcode** et choisissez **Preferences**. Sélectionnez **Accounts** , choisissez votre ID Apple, puis cliquez sur le bouton **View Details** . Consultez [Ajouter votre compte ID Apple](https://help.apple.com/xcode/mac/current/#/devaf282080a) pour obtenir des instructions détaillées.

   Pour plus d’informations sur les exigences de signature, consultez [What is app signing](https://help.apple.com/xcode/mac/current/#/dev3a05256b8).

- Si vous utilisez un appareil iOS pour le développement, un profil de provisionnement configuré dans Xcode pour votre appareil

   Xcode fournit la signature automatique là où il crée les certificats de signature pour vous, selon les besoins. Pour plus d’informations sur la signature automatique Xcode, consultez [Automatic signing](https://help.apple.com/xcode/mac/current/#/dev80cc24546).

   Si vous souhaitez effectuer la signature manuellement, vous devez créer un profil de provisionnement pour votre application. Pour plus d’informations sur la création de profils de provisionnement, consultez [Create a development provisioning profile](https://help.apple.com/developer-account/#/devf2eb157f8).

- [Node.js](https://nodejs.org/) version 12.14.1 et NPM version 6.13.4

   Installez la version 12.14.1 de Node.js sur votre Mac. Si vous installez le package Node.js, il doit être fourni avec NPM version 6.13.4. D’autres versions de Node.js et NPM peuvent ne pas prendre en charge certains modules utilisés dans l’agent distant `vcremote` , ce qui peut entraîner `vcremote` l’échec de l’installation. Nous vous recommandons d’installer Node.js à l’aide d’un gestionnaire de package tel que [node version Manager](https://nodejs.org/en/download/package-manager/#nvm). Évitez d’utiliser la commande `sudo` pour installer Node.js, car l’installation de certains modules peut échouer lors de l’utilisation de `sudo` .

## <a name="install-the-remote-agent-for-ios"></a><a name="Install"></a> Installer l’agent distant pour iOS

Lorsque vous installez le développement mobile avec la charge de travail C++, Visual Studio peut communiquer avec [vcremote](https://www.npmjs.com/package/vcremote), un agent distant en cours d’exécution sur votre Mac pour transférer des fichiers, générer et exécuter votre application iOS et envoyer des commandes de débogage.

Avant d’installer l’agent distant, assurez-vous que vous avez respecté les [conditions préalables](#prerequisites) et effectué les étapes d’installation décrites dans [installer le développement mobile multiplateforme en C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools).

### <a name="to-download-and-install-the-remote-agent"></a><a name="DownloadInstall"></a> Pour télécharger et installer l’agent distant

- À partir de l’application Terminal sur votre Mac, vérifiez que la version de Node.js en cours d’utilisation est la version requise 12.14.1. Pour vérifier la version, exécutez la commande :

  `node -v`
  
  S’il ne s’agit pas de la bonne version, vous devrez peut-être suivre les instructions d’installation de Node.js dans les conditions préalables. Ensuite, redémarrez Node.js.

- Après avoir vérifié que le Node.js requis est en cours d’utilisation, exécutez la commande suivante pour installer vcremote sous cette version de Node.js :

   `npm install -g --unsafe-perm vcremote`

   Le commutateur d’installation globale (**-g**) est recommandé, mais pas obligatoire. Si vous n’utilisez pas le commutateur d’installation global, vcremote est installé sous le chemin d’accès actif actuel dans l’application Terminal.

   Pendant l’installation de, `vcremote` est installé et le mode développeur est activé sur votre Mac. [Homebrew](https://brew.sh/) et deux packages NPM, `vcremote-lib` et `vcremote-utils` , sont également installés. Une fois l’installation terminée, ne tenez pas compte des avertissements relatifs aux dépendances facultatives ignorées.

   > [!NOTE]
   > Pour installer Homebrew, vous devez disposer d’un accès sudo (administrateur). Si vous devez installer `vcremote` sans sudo, vous pouvez installer Homebrew manuellement dans un emplacement usr/local et ajouter son dossier bin à votre chemin d’accès. Pour plus d’informations, consultez la [documentation Homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Pour activer manuellement le mode développeur, entrez cette commande dans l’application Terminal : `DevToolsSecurity -enable`

Si vous avez mis à jour Visual Studio vers une nouvelle version, vous devez aussi mettre à jour l’agent distant vers la version actuelle. Pour mettre à jour l’agent distant, répétez la procédure de téléchargement et d’installation de l’agent à distance.

## <a name="start-the-remote-agent"></a><a name="Start"></a> Démarrer l’agent distant

L’agent distant doit s’exécuter pour permettre à Visual Studio de générer et exécuter votre code iOS. Pour pouvoir communiquer, Visual Studio doit être couplé à l’agent distant. Par défaut, l’agent distant s’exécute en mode de connexion sécurisée, ce qui nécessite qu’un code confidentiel soit couplé à Visual Studio.

### <a name="to-start-the-remote-agent"></a><a name="RemoteAgentStartServer"></a> Pour démarrer l’agent distant

- Dans l’application Terminal de votre Mac, entrez :

   `vcremote`

   Cette commande démarre l’agent distant avec un répertoire de build par défaut de `~/vcremote` . Des options de configuration supplémentaires sont décrites dans la section [Configure the remote agent on the Mac](#ConfigureMac).

La première fois que vous démarrez l’agent et chaque fois que vous créez un certificat client, les informations nécessaires à la configuration de l’agent dans Visual Studio vous sont fournies, notamment le nom d’hôte, le port et le code confidentiel.

![Utiliser Vcremote pour générer un code PIN sécurisé](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "Utiliser Vcremote pour générer un code PIN sécurisé")

Si vous envisagez de configurer l’agent distant dans Visual Studio en utilisant le nom d’hôte, envoyez une requête ping au Mac à partir de Windows en utilisant le nom d’hôte pour vérifier qu’il est accessible. Dans le cas contraire, vous serez peut-être amené à utiliser l’adresse IP à la place.

Le code confidentiel généré est à usage unique et n’est valable que pour une durée limitée. Si vous ne couplez pas Visual Studio à l’agent distant avant l’expiration du délai, vous devrez générer un nouveau code confidentiel. Pour plus d'informations, consultez [Generate a new security PIN](#GeneratePIN).

Vous pouvez utiliser l’agent distant en mode non sécurisé. En mode non sécurisé, l’agent distant peut être couplé à Visual Studio sans code confidentiel.

#### <a name="to-disable-secured-connection-mode"></a>Pour désactiver le mode de connexion sécurisée

- Pour désactiver le mode de connexion sécurisée dans `vcremote` , entrez cette commande dans l’application Terminal sur votre Mac :

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>Pour activer le mode de connexion sécurisée

- Pour activer le mode de connexion sécurisée, entrez cette commande :

   `vcremote --secure true`

Une fois l’agent distant démarré, vous pouvez l’utiliser dans Visual Studio jusqu’à ce que vous l’arrêtiez.

#### <a name="to-stop-the-remote-agent"></a>Pour arrêter l’agent distant

- Dans la fenêtre du terminal `vcremote` s’exécutant dans, entrez **le contrôle** + **C**.

## <a name="configure-the-remote-agent-in-visual-studio"></a><a name="ConfigureVS"></a> Configurer l’agent distant dans Visual Studio

Pour vous connecter à l’agent distant dans Visual Studio, vous devez spécifier la configuration à distance dans les options Visual Studio.

### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Pour configurer l’agent distant dans Visual Studio

1. Si l’agent n’est pas déjà en cours d’exécution sur votre Mac, suivez les étapes décrites dans [Démarrer l’agent distant](#Start). Votre Mac doit être en cours `vcremote` d’exécution pour permettre à Visual Studio de coupler, de connecter et de générer votre projet avec succès.

1. Sur votre Mac, obtenez le nom d’hôte ou l’adresse IP de votre Mac.

   Vous pouvez obtenir l’adresse IP en utilisant la commande **ifconfig** dans une fenêtre Terminal. Utilisez l’adresse inet répertoriée sous l’interface réseau active.

1. Dans la barre de menus Visual Studio, choisissez **Outils**, **Options**.

1. Dans la boîte de dialogue **Options** , développez **Multiplateforme**, **C++**, **iOS**.

1. Dans les champs **Nom d’hôte** et **Port** , entrez les valeurs spécifiées par l’agent distant au moment où vous l’avez démarré. Le nom d’hôte peut être le nom DNS ou l’adresse IP de votre Mac. Le numéro de port par défaut est 3030.

   > [!NOTE]
   > Si vous ne pouvez pas envoyer une requête ping au Mac en utilisant le nom d’hôte, vous devrez peut-être utiliser l’adresse IP.

1. Si vous utilisez l’agent distant en mode de connexion sécurisée par défaut, cochez la case **Sécuriser** , puis entrez la valeur de code confidentiel spécifiée par l’agent distant dans le champ **Code confidentiel** . Si vous utilisez l’agent distant en mode de connexion non sécurisée, décochez la case **Sécuriser** et laisser le champ **Code confidentiel** vide.

1. Choisissez **Coupler** pour activer le couplage.

   ![Configurer la connexion vcremote pour les builds iOS](../cross-platform/media/cppmdd-options-ios.png "Configurer la connexion vcremote pour les builds iOS")

   Le couplage persiste tant que vous ne changez pas de nom d’hôte ou de port. Si vous changez de nom d’hôte ou de port dans la boîte de dialogue **Options** , pour annuler la modification, choisissez le bouton **Rétablir** pour revenir au couplage précédent.

   Si le couplage n’aboutit pas, vérifiez que l’agent distant s’exécute en suivant les étapes décrites dans [Start the remote agent](#Start). Si trop de temps s’est écoulé après la génération du code confidentiel de l’agent, suivez les étapes décrites dans [Generate a new security PIN](#GeneratePIN) sur le Mac, puis réessayez. Si vous utilisez le nom d’hôte de votre Mac, essayez plutôt d’utiliser l’adresse IP qui figure dans le champ **Nom d’hôte** .

1. Mettez à jour le nom de dossier dans le champ **Racine distante** pour spécifier le dossier utilisé par l’agent distant dans le répertoire de base (*~*) du Mac. Par défaut, l’agent distant utilise `/Users/<username>/vcremote` comme racine distante.

1. Choisissez **OK** pour enregistrer les paramètres de connexion de couplage à distance.

Visual Studio utilise les mêmes informations pour se connecter à l’agent distant sur votre Mac chaque fois que vous l’utilisez. Vous n’avez pas besoin de coupler à nouveau Visual Studio à l’agent distant, sauf si vous générez un nouveau certificat de sécurité sur votre Mac ou que son nom d’hôte ou son adresse IP est modifié.

## <a name="generate-a-new-security-pin"></a><a name="GeneratePIN"></a> Generate a new security PIN

Quand vous démarrez l’agent distant pour la première fois, le code confidentiel généré est valide pendant une période limitée (par défaut, 10 minutes). Si vous ne couplez pas Visual Studio à l’agent distant avant l’expiration de ce délai, vous devez générer un nouveau code confidentiel.

### <a name="to-generate-a-new-pin"></a>Pour générer un nouveau code confidentiel

1. Arrêtez l’agent ou ouvrez une deuxième fenêtre d’application Terminal sur votre Mac et utilisez-la pour entrer la commande.

1. Entrez cette commande dans l’application Terminal :

   `vcremote generateClientCert`

   L’agent distant génère un nouveau code confidentiel temporaire. Pour coupler Visual Studio à l’aide du nouveau code confidentiel, répétez les étapes décrites dans [Configurer l’agent distant dans Visual Studio](#ConfigureVS).

## <a name="generate-a-new-server-certificate"></a><a name="GenerateCert"></a> Générer un nouveau certificat de serveur

Pour des raisons de sécurité, les certificats de serveur qui couplent Visual Studio à l’agent distant sont liés à l’adresse IP ou au nom d’hôte de votre Mac. Si ces valeurs changent, vous devez générer un nouveau certificat de serveur et reconfigurer Visual Studio avec les nouvelles valeurs.

### <a name="to-generate-a-new-server-certificate"></a>Pour générer un nouveau certificat de serveur

1. Arrêtez l' `vcremote` agent.

1. Entrez cette commande dans l’application Terminal :

   `vcremote resetServerCert`

1. Quand vous êtes invité à confirmer l’opération, entrez `Y`

1. Entrez cette commande dans l’application Terminal :

   `vcremote generateClientCert`

   Cette commande génère un nouveau code confidentiel temporaire.

1. Pour coupler Visual Studio à l’aide du nouveau code confidentiel, répétez les étapes décrites dans [Configurer l’agent distant dans Visual Studio](#ConfigureVS).

## <a name="configure-the-remote-agent-on-the-mac"></a><a name="ConfigureMac"></a> Configure the remote agent on the Mac

Vous pouvez configurer l’agent distant à l’aide de différentes options de ligne de commande. Par exemple, vous pouvez spécifier le port à écouter pour les demandes de génération et spécifier le nombre maximal de builds à conserver sur le système de fichiers. Par défaut, cette limite est de 10 builds. Au moment de l’arrêt, l’agent supprime les builds qui dépassent ce nombre maximal.

### <a name="to-configure-the-remote-agent"></a>Pour configurer l’agent distant

- Pour afficher la liste complète des commandes de l’agent distant, dans l’application Terminal, entrez :

   `vcremote --help`

- Pour désactiver le mode sécurisé et activer les connexions HTTP simples, entrez :

   `vcremote --secure false`

   Quand vous utilisez cette option, décochez la case **Sécuriser** et laissez le champ **Code PIN** vide pendant la configuration de l’agent dans Visual Studio.

- Pour spécifier l’emplacement des fichiers de l’agent distant, entrez :

   `vcremote --serverDir directory_path`

   où *chemin_répertoire* est l’emplacement sur votre Mac où seront placés les fichiers journaux, les builds et les certificats de serveur. Par défaut, cet emplacement est `/Users/<username>/vcremote` . Les builds sont organisées par numéro de build à cet emplacement.

- Pour utiliser un processus en arrière-plan pour capturer `stdout` et `stderr` dans un fichier nommé serveur.log, entrez :

   `vcremote > server.log 2>&1 &`

   Le fichier serveur.log peut aider à la résolution des problèmes de génération.

- Pour exécuter l’agent en utilisant un fichier de configuration au lieu de paramètres de ligne de commande, entrez :

   `vcremote --config config_file_path`

   où *chemin_fichier_config* est le chemin d’accès à un fichier de configuration au format JSON. Les options de démarrage et leurs valeurs ne doivent pas inclure de tirets.

## <a name="troubleshoot-the-remote-agent"></a>Résoudre les problèmes de l’agent distant

### <a name="debugging-on-an-ios-device"></a>Débogage sur un appareil iOS

Si le débogage sur un appareil iOS ne fonctionne pas, il peut y avoir des problèmes avec l’outil [ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller), qui est utilisé pour communiquer avec un appareil iOS. Cet outil est généralement installé à partir de homebrew pendant l’installation de `vcremote` . Pour une solution de contournement, suivez les étapes ci-dessous.

Ouvrez l’application Terminal et mettez à jour `ideviceinstaller` et ses dépendances en exécutant les commandes suivantes dans l’ordre :

1. Vérifiez que Homebrew est mis à jour

   `brew update`

1. Désinstaller `libimobiledevice` et `usbmuxd`

   `brew uninstall --ignore-dependencies libimobiledevice`

   `brew uninstall --ignore-dependencies usbmuxd`

1. Installer la dernière version de `libimobiledevice` et `usbmuxd`

   `brew install --HEAD usbmuxd`

   `brew unlink usbmuxd`

   `brew link usbmuxd`

   `brew install --HEAD libimobiledevice`

1. Désinstaller et réinstaller `ideviceinstaller`

   `brew uninstall ideviceinstaller`

   `brew install ideviceinstaller`

Vérifiez que `ideviceinstaller` peut communiquer avec l’appareil en essayant de répertorier les applications installées sur l’appareil :

`ideviceinstaller -l`

Si des `ideviceinstaller` Erreurs ne peuvent pas accéder au dossier `/var/db/lockdown` , modifiez le privilège sur le dossier avec :

`sudo chmod 777 /var/db/lockdown`

Ensuite, vérifiez à nouveau si `ideviceinstaller` peut communiquer avec l’appareil.

## <a name="see-also"></a>Voir aussi

- [Installer le développement mobile multiplateforme avec C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
