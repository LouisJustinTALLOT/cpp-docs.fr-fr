---
title: Traitement des messages de notification dans les contrôles de zone de liste déroulante étendue
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 044cef644f746f7cb70944805882bd8e2f2806b4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908110"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Traitement des messages de notification dans les contrôles de zone de liste déroulante étendue

Quand les utilisateurs interagissent avec la zone de liste déroulante étendue, le contrôle (`CComboBoxEx`) envoie des messages de notification à sa fenêtre parente, généralement un objet d’affichage ou de boîte de dialogue. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, quand l’utilisateur active la liste déroulante ou clique dans la zone d’édition du contrôle, la notification CBEN_BEGINEDIT est envoyée.

Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour ajouter des gestionnaires de notification à la classe parente pour les messages que vous souhaitez implémenter.

La liste suivante décrit les différentes notifications envoyées par le contrôle de zone de liste déroulante étendue.

- CBEN_BEGINEDIT envoyé lorsque l’utilisateur active la liste déroulante ou clique dans la zone d’édition du contrôle.

- CBEN_DELETEITEM Envoyé lorsqu’un élément a été supprimé.

- CBEN_DRAGBEGIN envoyé lorsque l’utilisateur commence à faire glisser l’image de l’élément affiché dans la partie modifiable du contrôle.

- CBEN_ENDEDIT envoyé lorsque l’utilisateur a terminé une opération dans la zone d’édition ou qu’il a sélectionné un élément dans la liste déroulante du contrôle.

- CBEN_GETDISPINFO envoyé pour récupérer des informations d’affichage sur un élément de rappel.

- CBEN_INSERTITEM envoyé lorsqu’un nouvel élément a été inséré dans le contrôle.

## <a name="see-also"></a>Voir aussi

[Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
