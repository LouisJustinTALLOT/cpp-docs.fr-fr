---
title: Gestionnaires pour les commandes et les notifications de contrôle
ms.date: 11/04/2016
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
ms.openlocfilehash: 28bed2937409cd1df5ee8d295e466609232e0e91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622051"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Gestionnaires pour les commandes et les notifications de contrôle

Il n’existe aucun gestionnaire par défaut pour les commandes ou les messages de notification de contrôle. Par conséquent, vous êtes lié uniquement par convention de dénomination vos gestionnaires pour ces catégories de messages. Lorsque vous mappez la notification de commande ou le contrôle à un gestionnaire, les fenêtres de propriétés propose un nom basé sur le code d’ID ou de notification de contrôle de commande. Vous pouvez accepter le nom proposé, modifier ou remplacer.

Convention, vous devez nommer les gestionnaires dans les deux catégories de l’objet d’interface utilisateur qu’ils représentent. Par conséquent, un gestionnaire pour la commande Couper dans le menu Edition peut être nommé

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Étant donné que la commande Couper est couramment implémentée dans les applications, le framework prédéfinit l’ID de commande pour la commande Couper en tant que **ID_EDIT_CUT**. Pour obtenir la liste de tous les ID de commandes prédéfinies, consultez le fichier AFXRES. H. Pour plus d’informations, consultez [commandes Standard](../mfc/standard-commands.md).

En outre, la convention suggère qu’un gestionnaire pour le **BN_CLICKED** message de notification à partir d’un bouton intitulé « Mon bouton » peut être nommé.

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

Vous pouvez affecter à cette commande ID **IDC_MY_BUTTON** , car il est équivalent à un objet d’interface utilisateur spécifique à l’application.

Les deux catégories de messages prennent aucun argument et ne retournent aucune valeur.

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)
