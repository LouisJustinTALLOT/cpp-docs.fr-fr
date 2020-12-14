---
description: 'En savoir plus sur : les gestionnaires pour les plages Message-Map'
title: Gestionnaires pour les plages de table des messages
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
ms.openlocfilehash: 1b0f829a4c75aa8ee6148bdf3e96f6886ab07aba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248916"
---
# <a name="handlers-for-message-map-ranges"></a>Gestionnaires pour les plages de table des messages

Cet article explique comment mapper une plage de messages à une seule fonction du gestionnaire de messages (au lieu de mapper un message à une seule fonction).

Il peut arriver que vous deviez traiter plusieurs messages ou notifications de contrôle exactement de la même façon. À ce moment-là, vous souhaiterez peut-être mapper tous les messages à une seule fonction de gestionnaire. Les plages de la table des messages vous permettent d’effectuer cette opération pour une plage contiguë de messages :

- Vous pouvez mapper des plages d’ID de commande à :

  - Fonction de gestionnaire de commandes.

  - Fonction de gestionnaire de mise à jour de commande.

- Vous pouvez mapper des messages de notification de contrôle pour une plage d’ID de contrôle à une fonction de gestionnaire de messages.

Les sujets abordés dans cet article sont les suivants :

- [Écriture de l’entrée de la table des messages](#_core_writing_the_message.2d.map_entry)

- [Déclaration de la fonction de gestionnaire](#_core_declaring_the_handler_function)

- [Exemple pour une plage d’ID de commande](#_core_example_for_a_range_of_command_ids)

- [Exemple pour une plage d’ID de contrôle](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a> Écriture de l’entrée Message-Map

Dans le. CPP, ajoutez votre entrée de table des messages, comme indiqué dans l’exemple suivant :

[!code-cpp[NVC_MFCMessageHandling#6](codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

L’entrée de la table des messages est composée des éléments suivants :

- La macro de la plage de la table des messages :

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Paramètres de la macro :

  Les deux premières macros acceptent trois paramètres :

  - ID de commande qui démarre la plage

  - ID de commande qui termine la plage

  - Nom de la fonction de gestionnaire de messages

  La plage d’ID de commandes doit être contiguë.

  La troisième macro, `ON_CONTROL_RANGE` , prend un premier paramètre supplémentaire : un message de notification de contrôle, tel que **EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a> Déclaration de la fonction de gestionnaire

Ajoutez la déclaration de la fonction gestionnaire dans le. Fichier H. Le code suivant montre comment cela peut se présenter, comme indiqué ci-dessous :

[!code-cpp[NVC_MFCMessageHandling#7](codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Les fonctions de gestionnaire pour les commandes uniques ne prennent normalement aucun paramètre. À l’exception des fonctions de gestionnaire de mise à jour, les fonctions de gestionnaire pour les plages de table de messages requièrent un paramètre supplémentaire, *nid*, de type **uint**. Ce paramètre est le premier paramètre. Le paramètre extra prend en compte l’ID de commande supplémentaire nécessaire pour spécifier la commande que l’utilisateur a réellement choisie.

Pour plus d’informations sur les paramètres requis pour la mise à jour des fonctions de gestionnaire, consultez l' [exemple d’une plage d’ID de commandes](#_core_example_for_a_range_of_command_ids).

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a> Exemple pour une plage d’ID de commande

Quand vous pouvez utiliser des plages, un exemple consiste à gérer des commandes telles que la commande zoom dans l’exemple MFC [HIERSVR](../overview/visual-cpp-samples.md). Cette commande effectue un zoom sur la vue, en la mettant à l’échelle entre 25% et 300% de sa taille normale. La classe d’affichage de HIERSVR utilise une plage pour gérer les commandes de zoom avec une entrée de table des messages ressemblant à ceci :

[!code-cpp[NVC_MFCMessageHandling#8](codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Lorsque vous écrivez l’entrée de la table des messages, vous spécifiez :

- Deux ID de commande, de début et de fin d’une plage contiguë.

   Ici, elles sont **ID_VIEW_ZOOM25** et **ID_VIEW_ZOOM300**.

- Nom de la fonction gestionnaire pour les commandes.

   Ici, il s’agit de `OnZoom` .

La déclaration de fonction doit ressembler à ceci :

[!code-cpp[NVC_MFCMessageHandling#9](codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

Le cas des fonctions de gestionnaire de mise à jour est similaire et est susceptible d’être plus largement utile. Il est assez courant d’écrire `ON_UPDATE_COMMAND_UI` des gestionnaires pour un certain nombre de commandes et d’écrire ou de copier le même code. La solution consiste à mapper une plage d’ID de commandes à une fonction de gestionnaire de mise à jour à l’aide de la `ON_UPDATE_COMMAND_UI_RANGE` macro. Les ID de commande doivent former une plage contiguë. Pour obtenir un exemple, consultez le `OnUpdateZoom` Gestionnaire et son `ON_UPDATE_COMMAND_UI_RANGE` entrée de table des messages dans la classe d’affichage de l’exemple HIERSVR.

Les fonctions de gestionnaire de mise à jour pour les commandes uniques acceptent normalement un seul paramètre, *pCmdUI*, de type `CCmdUI*` . Contrairement aux fonctions de gestionnaire, les fonctions de gestionnaire de mise à jour pour les plages de table de messages ne nécessitent pas de paramètre supplémentaire, *nid*, de type **uint**. L’ID de commande, qui est nécessaire pour spécifier la commande que l’utilisateur a réellement choisie, se trouve dans l' `CCmdUI` objet.

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a> Exemple pour une plage d’ID de contrôle

Un autre cas intéressant est le mappage des messages de notification de contrôle pour une plage d’ID de contrôle à un gestionnaire unique. Supposons que l’utilisateur puisse cliquer sur l’un des 10 boutons. Pour mapper les 10 boutons à un seul gestionnaire, votre entrée de table des messages ressemble à ceci :

[!code-cpp[NVC_MFCMessageHandling#10](codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Lorsque vous écrivez la `ON_CONTROL_RANGE` macro dans votre table des messages, vous spécifiez :

- Message de notification de contrôle particulier.

   C’est **BN_CLICKED**.

- Valeurs d’ID de contrôle associées à la plage contiguë de contrôles.

   Voici **IDC_BUTTON1** et **IDC_BUTTON10**.

- Nom de la fonction de gestionnaire de messages.

   Ici, il s’agit de `OnButtonClicked` .

Lorsque vous écrivez la fonction gestionnaire, spécifiez le paramètre **uint** supplémentaire, comme indiqué dans l’exemple suivant :

[!code-cpp[NVC_MFCMessageHandling#11](codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

Le `OnButtonClicked` Gestionnaire d’un seul message de **BN_CLICKED** ne prend pas de paramètres. Le même gestionnaire pour une plage de boutons prend un **uint**. Le paramètre supplémentaire permet d’identifier le contrôle particulier chargé de générer le **BN_CLICKED** message.

Le code présenté dans l’exemple est standard : la conversion de la valeur passée à un **`int`** dans la plage de messages et la déclaration que c’est le cas. Vous pouvez effectuer une action différente selon le bouton sur lequel l’utilisateur a cliqué.

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](declaring-message-handler-functions.md)
