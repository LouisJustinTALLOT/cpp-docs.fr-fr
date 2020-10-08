---
title: Informations de référence sur ConnectionManager
description: Comment gérer vos connexions SSH distantes à partir d’un outil de ligne de commande.
ms.date: 10/7/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 2f38fec21e7526fa214db811b00fc545504f0610
ms.sourcegitcommit: 611e903f222ec794ef14195796b332851ab98904
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91847136"
---
# <a name="connectionmanager-reference"></a>Informations de référence sur ConnectionManager

::: moniker range="<=vs-2017"

ConnectionManager.exe est disponible dans Visual Studio 2019 version 16,5 et versions ultérieures.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager.exe est un utilitaire de ligne de commande permettant de gérer les connexions de développement à distance en dehors de Visual Studio. Elle est utile pour des tâches telles que la configuration d’un nouvel ordinateur de développement. Ou utilisez-le pour configurer Visual Studio pour une intégration continue.Vous pouvez l’utiliser dans une fenêtre de Invite de commandes développeur. Pour plus d’informations sur la Invite de commandes développeur, consultez [utiliser l’ensemble d’outils Microsoft C++ à partir de la ligne de commande](../build/building-on-the-command-line.md).

ConnectionManager.exe est disponible dans Visual Studio 2019 version 16,5 et versions ultérieures. Il fait partie de la charge de travail **développement Linux avec C++** dans le Visual Studio installer. Il est également installé automatiquement lorsque vous choisissez le composant **Gestionnaire de connexions** dans le programme d’installation. Il est installé dans *% VCIDEInstallDir% \\ Linux \\ bin \\ ConnectionManagerExe \\ConnectionManager.exe*.

Les fonctionnalités de ConnectionManager.exe sont également disponibles dans Visual Studio. Pour gérer les connexions de développement à distance dans l’IDE, dans la barre de menus, choisissez **Outils**  >  **options** pour ouvrir la boîte de dialogue Options. Dans la boîte de dialogue Options **Cross Platform**, sélectionnez  >  **Gestionnaire de connexions**multiplateforme.

## <a name="syntax"></a>Syntaxe

> **`ConnectionManager.exe`***commande* \[ *arguments*] \[ *options*]

### <a name="commands-and-arguments"></a>Commandes et arguments

- **`add`*** \@ hôte* \[ d’utilisateur **`--port`** *port*] \[ **`--password`** *mot de passe*] \[ **`--privatekey`** *privatekey_file*]

  Authentifie et ajoute une nouvelle connexion. Par défaut, il utilise le port 22 et l’authentification par mot de passe. (Vous serez invité à entrer un mot de passe.) Utilisez **-`-password`** et **`--privatekey`** pour spécifier un mot de passe pour une clé privée.

- **`remove`**\[ *connection_id* le port d' \| * \@ hôte* de l’utilisateur \[ **`--port`** *port*]]

  Supprime une connexion. Si aucun argument n’est spécifié, vous êtes invité à spécifier la connexion à supprimer.
  
- **`modify`** valeur \[ *par défaut* \| *connection_id* \| *port \@ hôte utilisateur* \[ **`--port`** *port*]] \[ **`--property`** *clé = valeur*]

  Définit ou modifie une propriété sur une connexion. \
  Si la *valeur* est vide, la *clé* de la propriété est supprimée. \
  Si l’authentification échoue, aucune modification n’est apportée.
  Si aucune connexion n’est spécifiée (ce qui est prévu par *défaut*), la connexion à distance par défaut de l’utilisateur est utilisée.

- **`remove-all`**

  Supprime toutes les connexions stockées.
  
- **`clean`**

  Supprime le cache d’en-tête pour les connexions qui n’existent plus. 

- **`list`** \[**`--properties`**]

  Affiche des informations, des ID et des propriétés de toutes les connexions stockées. 

- **`help`**

  Affiche un écran d’aide.

- **`version`**

  Affiche des informations sur la version.

### <a name="options"></a>Options

- **`-q`**, **`--quiet`**

  Empêche la sortie vers `stdout` ou `stderr` .

- **`--no-prompt`**

  Échoue au lieu de prompt, le cas échéant.

- **`--no-verify`**

  Ajoutez ou modifiez une connexion sans authentification.

- **`--file`***nom du fichier*

  Lire les informations de connexion à partir du *nom de fichier*fourni.

- **`--no-telemetry`**

  Désactivez l’envoi des données d’utilisation à Microsoft. Les données d’utilisation sont collectées et renvoyées à Microsoft à moins que l' **`--no-telemetry`** indicateur ne soit passé.  

- **`-n`**, **`--dry-run`**

  Effectue une exécution à sec de la commande.
 
- **`--p`**

  Identique à **`--password`** .

- **`-i`**

  Identique à **`--privatekey`** .

## <a name="examples"></a>Exemples

Cette commande ajoute une connexion pour un utilisateur nommé « User » sur localhost. La connexion utilise un fichier de clé pour l’authentification, situé dans *% UserProfile% \. ssh \ id_rsa*.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

Cette commande supprime la connexion ayant l’ID 1975957870 dans la liste des connexions.

```cmd
ConnectionManager.exe remove 1975957870
```

Cette commande remplace le choix de l’interpréteur de commandes pour la connexion avec l’ID de connexion 21212121. Les shells pris en charge sont les suivants : **`sh, csh, bash, tcsh, ksh, zsh, dash`** . Si l’interpréteur de commandes trouvé sur le système Linux n’est pas pris en charge, nous revenons à l’utilisation explicite **`sh`** pour toutes les commandes.

```cmd
ConnectionManager.exe modify 21212121 --property shell=csh
```

## <a name="see-also"></a>Voir aussi

[Connexion à votre système Linux cible dans Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end