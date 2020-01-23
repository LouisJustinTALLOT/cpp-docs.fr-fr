---
title: Référence ConnectionManager
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 2b01bfbcd81984e7ddf32cd5ab0485fff17b3d2b
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520899"
---
# <a name="connectionmanager-reference"></a>Référence ConnectionManager

::: moniker range="<=vs-2017"

ConnectionManager. exe est disponible dans Visual Studio 2019 version 16,5 et versions ultérieures.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager. exe est un utilitaire de ligne de commande permettant de gérer les connexions de développement à distance en dehors de Visual Studio. Elle est utile pour des tâches telles que la configuration d’un nouvel ordinateur de développement. Ou utilisez-le pour configurer Visual Studio pour une intégration continue. Vous pouvez l’utiliser dans une fenêtre de Invite de commandes développeur. Pour plus d’informations sur la Invite de commandes développeur, consultez [utiliser l' C++ ensemble d’outils Microsoft à partir de la ligne de commande](..\build\building-on-the-command-line.md).

ConnectionManager. exe est disponible dans Visual Studio 2019 version 16,5 et versions ultérieures. Elle fait partie du **développement Linux avec C++**  une charge de travail dans le Visual Studio installer. Il est également installé automatiquement lorsque vous choisissez le composant **Gestionnaire de connexions** dans le programme d’installation. Il est installé dans *% VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager. exe*.

Les fonctionnalités de ConnectionManager. exe sont également disponibles dans Visual Studio. Pour gérer les connexions de développement à distance dans l’IDE, dans la barre de menus, choisissez **outils** > **options** pour ouvrir la boîte de dialogue Options. Dans la boîte de dialogue Options, sélectionnez **Cross Platform** > **Connection Manager**.

## <a name="syntax"></a>Syntaxe

> **ConnectionManager. exe** *Command* \[*arguments*] \[*options*]

### <a name="commands-and-arguments"></a>Commandes et arguments

- **Add** *user\@Host* \[ **--** *port port]* \[ **--** password *Password*] \[ **--PrivateKey** *privatekey_file*]

  Authentifie et ajoute une nouvelle connexion. Par défaut, il utilise le port 22 et l’authentification par mot de passe. (Vous serez invité à entrer un mot de passe.) Utilisez à la fois **--Password** et **--PrivateKey** pour spécifier un mot de passe pour une clé privée.

- **supprimer** \[*connection_id* \| *utilisateur\@l’ordinateur \[hôte* **--** *port port]]*

  Supprime une connexion. Si aucun argument n’est spécifié, vous êtes invité à spécifier la connexion à supprimer.

- **supprimer tout**

  Supprime toutes les connexions stockées.

- **liste**

  Affiche des informations et des ID de toutes les connexions stockées.

- **help**

  Affiche un écran d’aide.

- **version**

  Affiche des informations sur la version.

### <a name="options"></a>Options

- **-q**, **--Quiet**

  Empêche la sortie vers `stdout` ou `stderr`.

- **--No-prompt**

  Échoue au lieu de prompt, le cas échéant.

- **--No-Verify**

  Ajoutez ou modifiez une connexion sans authentification.

- **--fichier** *nom_fichier*

  Lire les informations de connexion à partir du *nom de fichier*fourni.

- **--non-télémétrie**

  Désactivez l’envoi des données d’utilisation à Microsoft. Les données d’utilisation sont collectées et renvoyées à Microsoft à moins que l’indicateur **--no-telemétrie** soit passé.  

- **-n**, **--sèche-exécution**

  Effectue une exécution à sec de la commande.

- **-p**

  Identique **à--Password**.

- **-i**

  Identique **à--PrivateKey**.

## <a name="examples"></a>Exemples

Cette commande ajoute une connexion pour un utilisateur nommé « User » sur localhost. La connexion utilise un fichier de clé pour l’authentification, situé dans *% UserProfile%\.SSH \ id_rsa*.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

Cette commande supprime la connexion ayant l’ID 1975957870 dans la liste des connexions.

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>Voir aussi

[Se connecter à votre système Linux cible dans Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end
