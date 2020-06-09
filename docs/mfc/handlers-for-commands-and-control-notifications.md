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
ms.openlocfilehash: cc89cbfde0a1eba5dc736b40c178d4a4fde37a4d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625768"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Gestionnaires pour les commandes et les notifications de contrôle

Il n’existe aucun gestionnaire par défaut pour les commandes ou les messages de notification de contrôle. Par conséquent, vous êtes lié uniquement par Convention pour nommer vos gestionnaires pour ces catégories de messages. Lorsque vous mappez la commande ou la notification de contrôle à un gestionnaire, l' [Assistant classe](reference/mfc-class-wizard.md) propose un nom basé sur l’ID de commande ou le code de notification de contrôle. Vous pouvez accepter le nom proposé, le modifier ou le remplacer.

La Convention suggère que vous nommez des gestionnaires dans les deux catégories pour l’objet interface utilisateur qu’ils représentent. Par conséquent, un gestionnaire de la commande couper du menu Edition peut être nommé

[!code-cpp[NVC_MFCMessageHandling#4](codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Étant donné que la commande Cut est si souvent implémentée dans les applications, l’infrastructure prédéfinit l’ID de commande pour la commande Cut comme **ID_EDIT_CUT**. Pour obtenir la liste de tous les ID de commande prédéfinis, consultez le fichier AFXRES. Manutention. Pour plus d’informations, consultez [commandes standard](standard-commands.md).

En outre, la Convention suggère un gestionnaire pour le message de notification **BN_CLICKED** à partir d’un bouton intitulé « mon bouton » peut être nommé

[!code-cpp[NVC_MFCMessageHandling#5](codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

Vous pouvez affecter à cette commande un ID de **IDC_MY_BUTTON** , car elle équivaut à un objet d’interface utilisateur spécifique à l’application.

Les deux catégories de messages ne prennent pas d’arguments et ne retournent aucune valeur.

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](declaring-message-handler-functions.md)
