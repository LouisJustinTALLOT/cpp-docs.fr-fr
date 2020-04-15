---
title: Informations de référence sur ConnectionManager
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 1c6236cedba88714e9918dd2c096b5e78d2f08ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "77258031"
---
# <a name="connectionmanager-reference"></a>Informations de référence sur ConnectionManager

::: moniker range="<=vs-2017"

ConnectionManager.exe est disponible dans Visual Studio 2019 version 16.5 et plus tard.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager.exe est un utilitaire de ligne de commande pour gérer les connexions de développement à distance en dehors de Visual Studio. Il est utile pour des tâches telles que l’approvisionnement d’une nouvelle machine de développement. Ou, utilisez-le pour configurer Visual Studio pour une intégration continue.Vous pouvez l’utiliser dans une fenêtre De commande de développeur Prompt. Pour plus d’informations sur l’invite de commande de développeur, voir [Utilisez l’outil Microsoft CMD de la ligne de commande](../build/building-on-the-command-line.md).

ConnectionManager.exe est disponible dans Visual Studio 2019 version 16.5 et plus tard. Il fait partie du développement Linux avec la charge de travail **de CMD** dans l’installateur visual Studio. Il est également installé automatiquement lorsque vous choisissez le composant **Connection Manager** dans l’installateur. Il est installé en *%VCIDEInstallDir%\\Linux\\bin\\\\ConnectionManagerExe ConnectionManager.exe*.

La fonctionnalité de ConnectionManager.exe est également disponible dans Visual Studio. Pour gérer les connexions de développement à distance dans l’IDE, sur la barre de menu, choisissez des options **d’outils** > **Options** pour ouvrir le dialogue Options. Dans le dialogue Options, sélectionnez **Cross Platform** > **Connection Manager**.

## <a name="syntax"></a>Syntaxe

> **ConnectionManager.exe** *arguments* \[ *de commande* \[] *options*]

### <a name="commands-and-arguments"></a>Commandes et arguments

- **ajouter** *\@l’hôte* \[de \[ **l’utilisateur - port** *port*] **-mot de passe mot de passe** *password*] \[ **--privatekey** *privatekey_file*]

  Authentifie et ajoute une nouvelle connexion. Par défaut, il utilise l’authentification du port 22 et du mot de passe. (Vous serez invité à entrer un mot de passe.) Utilisez à la fois **--mot de passe** et **--privatekey** pour spécifier un mot de passe pour une clé privée.

- **supprimer** \[ *\@connection_id’hôte* *connection_id* \| \[utilisateur **--port** *port*]]

  Supprime une connexion. Si aucun argument n’est spécifié, vous êtes invité à spécifier quelle connexion supprimer.

- **supprimer tous**

  Supprime toutes les connexions stockées.

- **list**

  Affiche les informations et les informations d’information de toutes les connexions stockées.

- **Aide**

  Affiche un écran d’aide.

- **version**

  Affiche les informations de version.

### <a name="options"></a>Options

- **-q**, **--calme**

  Empêche la `stdout` sortie `stderr`à ou .

- **--pas-prompt**

  Échec au lieu d’être rapide, le cas échéant.

- **--no-verify**

  Ajouter ou modifier une connexion sans authentification.

- **--fichier** *nom de fichier*

  Lisez les informations de connexion à partir du *nom de fichier*fourni .

- **--no-télémétrie**

  Désactiver l’envoi de données d’utilisation à Microsoft. Les données d’utilisation sont collectées et renvoyées à Microsoft à moins que le drapeau **--no-telemetry** soit passé.  

- **-n**, **--dry-run**

  Est-ce qu’une course à sec de la commande.

- **-p**

  Même que **--mot de passe**.

- **-i**

  Comme **--privatekey**.

## <a name="examples"></a>Exemples

Cette commande ajoute une connexion pour un utilisateur nommé "utilisateur" sur localhost. La connexion utilise un fichier clé pour l’authentification, trouvé dans *%USERPROFILE%\.ssh-id_rsa*.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

Cette commande supprime la connexion qui a ID 1975957870 de la liste des connexions.

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>Voir aussi

[Connexion à votre système Linux cible dans Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end
