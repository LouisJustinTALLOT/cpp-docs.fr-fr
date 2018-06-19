---
title: Gestionnaires pour les plages de la table des messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be596ea38a8d0a3919ed43d9c5478bb0127032d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351720"
---
# <a name="handlers-for-message-map-ranges"></a>Gestionnaires pour les plages de table des messages
Cet article explique comment mapper une plage de messages à une fonction de gestionnaire de message unique (au lieu d’associer un message à une seule fonction).  
  
 Il est parfois que vous deviez traiter plus d’une notification de message ou un contrôle dans la même façon. À tout moment, vous souhaitez peut-être mapper tous les messages à une seule fonction gestionnaire. Plages des tables des messages vous autorise à effectuer cette opération pour une plage contiguë de messages :  
  
-   Vous pouvez mapper les plages d’ID de commande pour :  
  
    -   Une fonction de gestionnaire de commandes.  
  
    -   Une fonction de gestionnaire de mise à jour de commande.  
  
-   Vous pouvez mapper les messages de notification de contrôle pour une plage d’ID de contrôle à une fonction de gestionnaire de messages.  
  
 Les rubriques abordées dans cet article sont les suivantes :  
  
-   [Écriture de l’entrée de table des messages](#_core_writing_the_message.2d.map_entry)  
  
-   [Déclaration de la fonction de gestionnaire](#_core_declaring_the_handler_function)  
  
-   [Exemple d’une plage d’ID de commande](#_core_example_for_a_range_of_command_ids)  
  
-   [Exemple d’une plage d’ID de contrôle](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> Écriture de l’entrée de table des messages  
 Dans le. CPP, ajoutez votre entrée de table des messages, comme indiqué dans l’exemple suivant :  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]  
  
 L’entrée de table des messages se compose des éléments suivants :  
  
-   La macro plage de la table des messages :  
  
    -   [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)  
  
    -   [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)  
  
    -   [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)  
  
-   Paramètres de la macro :  
  
     Les deux premières macros prennent trois paramètres :  
  
    -   L’ID de commande qui commence la plage  
  
    -   L’ID de commande qui termine la plage  
  
    -   Le nom de la fonction de gestionnaire de messages  
  
     La plage d’ID de commande doit être contiguë.  
  
     La troisième macro `ON_CONTROL_RANGE`, prend un paramètre supplémentaire de première : une notification de contrôle d’un message, tel que **EN_CHANGE**.  
  
##  <a name="_core_declaring_the_handler_function"></a> Déclaration de la fonction de gestionnaire  
 Ajoutez votre déclaration de fonction de gestionnaire dans le. Fichier de H. Le code suivant montre comment cela peut se présenter comme suit :  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]  
  
 Normalement, les fonctions de gestionnaire de commandes simples acceptent aucun paramètre. À l’exception des fonctions de gestionnaire de mise à jour, les fonctions de gestionnaires pour les plages de la table des messages exigent un paramètre supplémentaire, `nID`, de type **UINT**. Ce paramètre est le premier paramètre. Le paramètre supplémentaire contient l’ID de commande supplémentaires nécessaire pour spécifier la commande que l’utilisateur a choisi réellement.  
  
 Pour plus d’informations sur la configuration des paramètres de fonctions de gestionnaire de mise à jour, consultez [exemple pour une plage d’ID de commande](#_core_example_for_a_range_of_command_ids).  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> Exemple d’une plage d’ID de commandes  
 Lorsque vous utiliserez plages, par exemple, lors du traitement des commandes telles que la commande Zoom dans l’exemple MFC [HIERSVR](../visual-cpp-samples.md). Cette commande effectue un zoom de la vue mise à l’échelle d’il entre 25 et 300 % de sa taille normale. Classe de vue HIERSVR utilise une plage pour gérer les commandes de Zoom avec une entrée de table des messages qui ressemble à ceci :  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]  
  
 Lorsque vous écrivez l’entrée de table des messages, vous spécifiez :  
  
-   Deux ID de commande, début et de fin d’une plage contiguë.  
  
     Voici `ID_VIEW_ZOOM25` et `ID_VIEW_ZOOM300`.  
  
-   Le nom de la fonction de gestionnaire pour les commandes.  
  
     Elle a ici `OnZoom`.  
  
 La déclaration de fonction se présente comme suit :  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]  
  
 Le cas des fonctions de gestionnaire de mise à jour est susceptible d’être plus largement utiles et similaires. Il est assez courant d’écrire `ON_UPDATE_COMMAND_UI` gestionnaires pour un nombre de commandes et trouvez l’écriture ou de la copie, le même code plusieurs fois. La solution consiste à mapper une plage d’ID à une mise à jour la fonction de gestionnaire à l’aide des commandes du `ON_UPDATE_COMMAND_UI_RANGE` (macro). Les ID de commande doivent former une plage contiguë. Pour obtenir un exemple, consultez la **OnUpdateZoom** gestionnaire et ses `ON_UPDATE_COMMAND_UI_RANGE` entrée de table des messages dans la classe d’affichage de l’exemple HIERSVR.  
  
 Mettre à jour des fonctions de gestionnaire de commandes uniques normalement un seul paramètre, `pCmdUI`, de type **CCmdUI\***. Contrairement aux fonctions gestionnaires, les fonctions de gestionnaire de mise à jour pour les plages de la table des messages ne nécessitent pas un paramètre supplémentaire, `nID`, de type **UINT**. L’ID de commande, qui est nécessaire pour spécifier la commande que l’utilisateur a choisi en fait, se trouve dans le `CCmdUI` objet.  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> Exemple d’un ID de contrôle de plage  
 Un autre cas intéressant consiste à mapper les messages de notification de contrôle pour une plage d’ID de contrôle à un seul gestionnaire. Supposons que l’utilisateur peut cliquer sur un des boutons de 10. Pour mapper toutes les 10 boutons à un seul gestionnaire, votre entrée de table des messages ressemble à ceci :  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]  
  
 Lorsque vous écrivez le `ON_CONTROL_RANGE` la macro dans votre table des messages, vous spécifiez :  
  
-   Un message de notification de contrôle particulier.  
  
     Elle a ici **BN_CLICKED**.  
  
-   Les valeurs d’ID de contrôle associés à la plage contiguë de contrôles.  
  
     Ceux-ci sont `IDC_BUTTON1` et `IDC_BUTTON10`.  
  
-   Le nom de la fonction de gestionnaire de messages.  
  
     Elle a ici `OnButtonClicked`.  
  
 Lorsque vous écrivez la fonction gestionnaire, spécifiez le fichier extra **UINT** paramètre, comme indiqué dans les éléments suivants :  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]  
  
 Le `OnButtonClicked` gestionnaire pour un seul **BN_CLICKED** message ne prend aucun paramètre. Le même gestionnaire pour une plage de boutons prend un **UINT**. Le paramètre supplémentaire permet d’identifier le contrôle spécifique chargé de générer la **BN_CLICKED** message.  
  
 Le code indiqué dans l’exemple est typique : conversion de la valeur passée à une `int` au sein de la plage de messages et confirme que c’est le cas. Ensuite, vous pouvez effectuer une action différente selon le bouton a été utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)
