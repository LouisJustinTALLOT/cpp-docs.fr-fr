---
title: Le traitement des Messages de Notification de contrôle Tab | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 462d9177b1f6300eb356d052cbdfff3b85db86a1
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928060"
---
# <a name="processing-tab-control-notification-messages"></a>Traitement des messages de notification du contrôle Tab
Comme les utilisateurs cliquent sur des onglets ou des boutons, le contrôle d’onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) envoie des messages de notification à sa fenêtre parente. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, lorsque l’utilisateur clique sur un onglet, vous voudrez prédéfini les données de contrôle sur la page avant de les afficher.  
  
 Traitez les messages WM_NOTIFY à partir du contrôle onglet dans votre classe d’affichage ou de la boîte de dialogue. Utilisez la fenêtre Propriétés pour créer un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) fonction de gestionnaire avec une instruction switch basée sur le message de notification est traité. Pour obtenir la liste des notifications d’un contrôle tab peut envoyer à sa fenêtre parente, consultez le **Notifications** section de [référence de contrôle onglet](http://msdn.microsoft.com/library/windows/desktop/bb760548) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

