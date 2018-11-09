---
title: Vous connecter à votre ordinateur Linux distant dans Visual Studio
description: Comment se connecter à un ordinateur Linux distant à partir d’un projet C++ Visual Studio.
ms.date: 07/20/2018
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: ce6a3c02846586dbc46b0c9bc0db0d579878c814
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575238"
---
# <a name="connect-to-your-remote-linux-computer"></a>Se connecter à votre ordinateur Linux distant

Lors de la génération d’un projet Linux C++ dans Visual Studio, le code Linux est copié sur votre ordinateur Linux distant, puis compilé selon les paramètres Visual Studio. Pour configurer cette connexion distante :

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