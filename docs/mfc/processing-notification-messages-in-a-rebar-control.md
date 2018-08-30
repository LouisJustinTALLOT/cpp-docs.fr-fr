---
title: Traitement des Messages de Notification dans un contrôle Rebar | Microsoft Docs
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
ms.openlocfilehash: dce09e84e9a2b5262d05847746f819a122ec36c5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208973"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Traitement des messages de notification dans un contrôle rebar
Dans la classe parente du contrôle rebar, créez un `OnChildNotify` fonction gestionnaire avec une instruction switch pour n’importe quel contrôle rebar (`CReBarCtrl`) des messages de notification que vous souhaitez gérer. Notifications sont envoyées vers la fenêtre parente lorsque l’utilisateur fait glisser des objets sur le contrôle rebar, modifications de bandes, supprime la disposition des bandes à partir du contrôle rebar et ainsi de suite.  
  
 Les messages de notification suivants peuvent être envoyés par l’objet de contrôle rebar :  
  
-   RBN_AUTOSIZE envoyé par un contrôle rebar (créé avec le style RBS_AUTOSIZE) lorsque le rebar se redimensionne automatiquement.  
  
-   RBN_BEGINDRAG envoyé par un contrôle rebar lorsque l’utilisateur commence à faire glisser une bande.  
  
-   RBN_CHILDSIZE envoyé par un contrôle rebar lorsque la fenêtre enfant d’une bande est redimensionnée.  
  
-   RBN_DELETEDBAND envoyé par un contrôle rebar après la suppression d’une bande.  
  
-   RBN_DELETINGBAND envoyé par un contrôle rebar lorsqu’une bande est sur le point d’être supprimé.  
  
-   RBN_ENDDRAG envoyé par un contrôle rebar lorsque l’utilisateur arrête de faire glisser une bande.  
  
-   RBN_GETOBJECT envoyé par un contrôle rebar (créé avec le style RBS_REGISTERDROP) lorsqu’un objet est glissé sur une bande dans le contrôle.  
  
-   RBN_HEIGHTCHANGE envoyé par un contrôle rebar lorsque sa hauteur a été modifiée.  
  
-   RBN_LAYOUTCHANGED envoyé par un contrôle rebar lorsque l’utilisateur modifie la disposition des bandes du contrôle.  
  
 Pour plus d’informations sur ces notifications, consultez [référence de contrôle Rebar](https://msdn.microsoft.com/library/windows/desktop/bb774375) dans le SDK Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

