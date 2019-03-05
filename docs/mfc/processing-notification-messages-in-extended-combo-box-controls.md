---
title: Traitement des messages de notification dans les contrôles de zone de liste déroulante étendue
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 1890267f26ef43fd1dbf8fdea28f02e3d882d475
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280743"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Traitement des messages de notification dans les contrôles de zone de liste déroulante étendue

Quand les utilisateurs interagissent avec la zone de liste déroulante étendue, le contrôle (`CComboBoxEx`) envoie des messages de notification à sa fenêtre parente, généralement un objet d’affichage ou de boîte de dialogue. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur Active la liste déroulante ou clique dans la zone d’édition du contrôle, la notification CBEN_BEGINEDIT est envoyée.

Utilisez la fenêtre Propriétés pour ajouter des gestionnaires de notification à la classe parente pour les messages que vous voulez implémenter.

La liste suivante décrit les différentes notifications envoyées par le contrôle de zone de liste déroulante étendue.

- CBEN_BEGINEDIT Envoyé lorsque l’utilisateur Active la liste déroulante ou clique dans la zone d’édition du contrôle.

- CBEN_DELETEITEM envoyé lorsqu’un élément a été supprimé.

- CBEN_DRAGBEGIN Envoyé lorsque l’utilisateur commence à faire glisser l’image de l’élément affiché dans la zone d’édition du contrôle.

- CBEN_ENDEDIT envoyé lorsque l’utilisateur a terminé une opération dans la zone d’édition ou qu’il a sélectionné un élément de la liste du contrôle liste déroulante.

- CBEN_GETDISPINFO envoyée pour récupérer les informations d’affichage d’un élément de rappel.

- CBEN_INSERTITEM envoyé lorsqu’un nouvel élément a été inséré dans le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
