---
title: "Gestionnaires pour les commandes et les Notifications de contrôle | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 748bdd1a2ce6b94a2c935df94de68767ee36875e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="handlers-for-commands-and-control-notifications"></a>Gestionnaires pour les commandes et les notifications de contrôle
Il n’existe aucun gestionnaire par défaut pour les commandes ou les messages de notification de contrôle. Par conséquent, vous êtes lié uniquement par la convention d’affectation de noms vos gestionnaires pour ces catégories de messages. Lorsque vous mappez la notification de commande ou un contrôle à un gestionnaire, la fenêtre Propriétés propose un nom basé sur le code d’ID ou de notification de contrôle de commande. Vous pouvez accepter le nom proposé, modifier ou remplacer.  
  
 Convention, vous devez nommer les gestionnaires dans les deux catégories de l’objet d’interface utilisateur qu’ils représentent. Par conséquent, un gestionnaire pour la commande Couper dans le menu Edition peut être nommé  
  
 [!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]  
  
 Étant donné que la commande Couper est couramment implémentée dans les applications, la structure prédéfinit l’ID de commande de la commande Couper en tant que **ID_EDIT_CUT**. Pour obtenir la liste de tous les ID de commandes prédéfinies, consultez le fichier AFXRES. H. Pour plus d’informations, consultez [commandes Standard](../mfc/standard-commands.md).  
  
 En outre, la convention suggère qu’un gestionnaire pour le **BN_CLICKED** message de notification à partir d’un bouton étiqueté « Mon bouton » peut être nommé.  
  
 [!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]  
  
 Vous pouvez affecter à cette commande ID `IDC_MY_BUTTON` , car elle est équivalente à un objet d’interface utilisateur spécifiques à l’application.  
  
 Les deux catégories de messages prennent pas d’arguments et ne retournent aucune valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)
