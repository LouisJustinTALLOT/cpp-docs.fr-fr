---
title: Se connecter à un ordinateur Linux distant dans Visual Studio
description: Comment se connecter à un ordinateur Linux distant à partir d’un projet C++ Visual Studio.
ms.date: 06/07/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 6348681ecc8e6f7863b2119810db24879526a1c6
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821614"
---
# <a name="connect-to-your-remote-linux-computer"></a>Se connecter à un ordinateur Linux distant

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range="vs-2019"

Quand vous ciblez le sous-système Windows pour Linux (WSL), Visual Studio interagit avec votre distribution Linux directement par le biais du système de fichiers ; aucune connexion à distance n’est nécessaire.

::: moniker-end

Lors de la génération d’un projet Linux C++ pour un système Linux distant (machine virtuelle ou machine physique), le code Linux est copié sur votre ordinateur Linux distant, puis compilé selon les paramètres Visual Studio. Pour configurer cette connexion distante :

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

1. Cliquez sur le bouton **Connect** (Se connecter) pour tenter une connexion à l’ordinateur distant.  Si la connexion échoue, les zones des entrées qui doivent être modifiées seront surlignées en rouge.

   ![Erreur du Gestionnaire de connexion](media/settings_connectionmanagererror.png)