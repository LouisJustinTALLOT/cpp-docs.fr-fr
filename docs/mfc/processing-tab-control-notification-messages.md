---
description: 'En savoir plus sur : traitement des messages de notification du contrôle onglet'
title: Traitement des messages de notification du contrôle Tab
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
ms.openlocfilehash: f5d81437b566143e2fc7cb1e0f275c0f9e9993de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154719"
---
# <a name="processing-tab-control-notification-messages"></a>Traitement des messages de notification du contrôle Tab

Quand les utilisateurs cliquent sur des onglets ou des boutons, le contrôle onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) envoie des messages de notification à sa fenêtre parente. Vous devez gérer ces messages si vous voulez faire quelque chose en réponse. Par exemple, quand l’utilisateur clique sur un onglet, vous souhaiterez peut-être prédéfinir les données du contrôle sur la page avant de l’afficher.

Traitez les messages WM_NOTIFY à partir du contrôle onglet dans votre classe d’affichage ou de boîte de dialogue. Utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour créer une fonction gestionnaire [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) avec une instruction switch basée sur le message de notification géré. Pour obtenir la liste des notifications qu’un contrôle onglet peut envoyer à sa fenêtre parente, consultez la section **notifications** de la [référence de contrôle onglet](/windows/win32/controls/tab-control-reference) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
