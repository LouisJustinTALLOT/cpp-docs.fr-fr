---
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
ms.openlocfilehash: fc33df6957beab6e4e8de3093dfc00cf2651780e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370505"
---
# <a name="handlers-for-message-map-ranges"></a>Gestionnaires pour les plages de table des messages

Cet article explique comment cartographier une gamme de messages à une seule fonction de gestionnaire de message (au lieu de cartographier un message à une seule fonction).

Il y a des moments où vous devez traiter plus d’un message ou contrôler la notification exactement de la même manière. Dans ces moments, vous pouvez cartographier tous les messages à une seule fonction de gestionnaire. Les plages de carte de message vous permettent de le faire pour une gamme contigu de messages :

- Vous pouvez cartographier les plages d’informations d’ID de commande pour :

  - Une fonction de gestionnaire de commande.

  - Une fonction de gestionnaire de mise à jour de commande.

- Vous pouvez cartographier les messages de notification de contrôle pour une gamme d’informations de contrôle à une fonction de gestionnaire de message.

Les sujets abordés dans cet article sont les suivants :

- [Rédaction de l’entrée de la carte des messages](#_core_writing_the_message.2d.map_entry)

- [Déclarer la fonction de gestionnaire](#_core_declaring_the_handler_function)

- [Exemple pour une gamme d’ID de commande](#_core_example_for_a_range_of_command_ids)

- [Exemple pour une gamme d’ID de contrôle](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>Rédaction de l’entrée Message-Map

Dans le . Fichier du RPC, ajoutez votre entrée de carte de message, comme indiqué dans l’exemple suivant :

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

L’entrée de la carte des messages se compose des éléments suivants :

- La gamme de carte de message macro:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Paramètres à la macro:

  Les deux premières macros prennent trois paramètres :

  - L’ID de commande qui démarre la plage

  - L’ID de commande qui termine la plage

  - Le nom de la fonction de gestionnaire de message

  La portée des 90 personnes doit être contigu.

  La troisième `ON_CONTROL_RANGE`macro, , prend un premier paramètre supplémentaire: un message de contrôle-notification, comme **EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>Déclarer la fonction Handler

Ajoutez votre déclaration de fonction de gestionnaire dans le . Fichier H. Le code suivant montre à quoi cela pourrait ressembler, comme indiqué ci-dessous:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Les fonctions de gestionnaire pour les commandes simples ne prennent normalement aucun paramètre. À l’exception des fonctions de gestionnaire de mise à jour, les fonctions de gestionnaire pour les plages de carte de message exigent un paramètre supplémentaire, *nID*, de type **UINT**. Ce paramètre est le premier paramètre. Le paramètre supplémentaire s’adapte à l’ID de commande supplémentaire nécessaire pour spécifier la commande que l’utilisateur a réellement choisie.

Pour plus d’informations sur les paramètres requis pour la mise à jour des fonctions des gestionnaires, voir [Exemple pour une gamme d’articles de commande](#_core_example_for_a_range_of_command_ids).

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>Exemple pour une gamme d’ID de commande

Quand pouvez-vous utiliser des plages Un exemple est dans la manipulation des commandes comme la commande Zoom dans l’échantillon MFC [HIERSVR](../overview/visual-cpp-samples.md). Cette commande zoome la vue, la évoluant entre 25% et 300% de sa taille normale. La classe de vue d’HIERSVR utilise une plage pour gérer les commandes Zoom avec une entrée de carte de message ressemblant à ceci :

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Lorsque vous écrivez l’entrée de la carte de message, vous spécifiez :

- Deux articles de commande, commençant et mettant fin à une plage contigu.

   Ici, ils sont **ID_VIEW_ZOOM25** et **ID_VIEW_ZOOM300**.

- Le nom de la fonction de gestionnaire pour les commandes.

   Ici, c’est `OnZoom`.

La déclaration de fonction ressemblerait à ceci :

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

Le cas des fonctions de gestionnaire de mise à jour est similaire, et susceptible d’être plus largement utile. Il est assez courant `ON_UPDATE_COMMAND_UI` d’écrire des gestionnaires pour un certain nombre de commandes et de vous retrouver à écrire, ou copier, le même code encore et encore. La solution consiste à cartographier une gamme d’informations `ON_UPDATE_COMMAND_UI_RANGE` de commande à une fonction de gestionnaire de mise à jour à l’aide de la macro. Les UDI de commande doivent former une portée contigu. Par exemple, voir `OnUpdateZoom` le `ON_UPDATE_COMMAND_UI_RANGE` gestionnaire et son entrée de carte de message dans la classe de vue de l’échantillon HIERSVR.

Mettre à jour les fonctions de gestionnaire pour les commandes simples `CCmdUI*`normalement prendre un seul paramètre, *pCmdUI*, de type . Contrairement aux fonctions de gestionnaire, mettre à jour les fonctions de gestionnaire pour les plages de carte de message ne nécessitent pas un paramètre supplémentaire, *nID*, de type **UINT**. L’ID de commande, qui est nécessaire pour spécifier quelle commande l’utilisateur a réellement choisi, se trouve dans l’objet. `CCmdUI`

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>Exemple pour une gamme d’ID de contrôle

Un autre cas intéressant est la cartographie des messages de contrôle-notification pour une gamme d’ID de contrôle à un seul gestionnaire. Supposons que l’utilisateur peut cliquer sur l’un des 10 boutons. Pour cartographier les 10 boutons d’un seul gestionnaire, votre entrée de carte de message ressemblerait à ceci :

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Lorsque vous `ON_CONTROL_RANGE` écrivez la macro dans votre carte de message, vous spécifiez :

- Un message de contrôle-notification particulier.

   Ici, c’est **BN_CLICKED**.

- Les valeurs d’identification de contrôle associées à la gamme contigus de contrôles.

   Voici **IDC_BUTTON1** et **IDC_BUTTON10**.

- Le nom de la fonction de gestionnaire de message.

   Ici, c’est `OnButtonClicked`.

Lorsque vous écrivez la fonction de gestionnaire, spécifiez le paramètre **UINT** supplémentaire, tel qu’indiqué dans ce qui suit :

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

Le `OnButtonClicked` gestionnaire d’un seul **message BN_CLICKED** ne prend aucun paramètre. Le même gestionnaire pour une gamme de boutons prend un **UINT**. Le paramètre supplémentaire permet d’identifier le contrôle particulier responsable de la génération du **message BN_CLICKED.**

Le code indiqué dans l’exemple est typique `int` : convertir la valeur transmise dans la plage de messages et affirmer que c’est le cas. Ensuite, vous pouvez prendre des mesures différentes en fonction du bouton a été cliqué.

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)
