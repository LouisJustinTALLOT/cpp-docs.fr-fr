---
title: Traitement des Messages de Notification dans un contrôle Rebar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a06df0bdfe8d1b81b4285fc86378f3da99882698
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348414"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Traitement des messages de notification dans un contrôle rebar
Dans la classe parente du contrôle rebar, créez un `OnChildNotify` fonction de gestionnaire avec une instruction switch pour n’importe quel contrôle rebar (`CReBarCtrl`) vous souhaitez gérer les messages de notification. Notifications sont envoyées à la fenêtre parente lorsque l’utilisateur fait glisser des objets sur le contrôle rebar, modifications de la disposition des bandes, supprime des bandes du contrôle rebar et ainsi de suite.  
  
 Les messages de notification suivants peuvent être envoyés par l’objet de contrôle rebar :  
  
-   **RBN_AUTOSIZE** envoyé par un contrôle rebar (créé avec le **RBS_AUTOSIZE** style) lorsque le rebar se redimensionne automatiquement.  
  
-   **RBN_BEGINDRAG** envoyé par un contrôle rebar lorsque l’utilisateur commence à faire glisser une bande.  
  
-   **RBN_CHILDSIZE** envoyé par un contrôle rebar lorsque la fenêtre enfant d’une bande est redimensionnée.  
  
-   **RBN_DELETEDBAND** envoyé par un contrôle rebar après qu’une bande a été supprimée.  
  
-   **RBN_DELETINGBAND** envoyé par un contrôle rebar lorsqu’une bande est sur le point d’être supprimé.  
  
-   **RBN_ENDDRAG** envoyé par un contrôle rebar lorsque l’utilisateur arrête de faire glisser une bande.  
  
-   **RBN_GETOBJECT** envoyé par un contrôle rebar (créé avec le **RBS_REGISTERDROP** style) lorsqu’un objet est déplacé sur une bande dans le contrôle.  
  
-   **RBN_HEIGHTCHANGE** envoyé par un contrôle rebar lorsque sa hauteur a changé.  
  
-   **RBN_LAYOUTCHANGED** envoyé par un contrôle rebar lorsque l’utilisateur modifie la disposition des bandes du contrôle.  
  
 Pour plus d’informations sur ces notifications, consultez [référence de contrôle Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774375) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

