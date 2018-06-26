---
title: Contrôle d’édition de notifications à partir d’une riche | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 928728093ff6e2150578c4ba48f2d8081620a48d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931142"
---
# <a name="notifications-from-a-rich-edit-control"></a>Notifications d'un contrôle RichEdit
Messages de notification d’événements affectant une riche contrôle d’édition de rapport ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Ils peuvent être traités par la fenêtre parente ou, à l’aide de la réflexion de message, par la riche contrôle d’édition lui-même. Les contrôles RichEdit prennent en charge tous les messages de notification utilisés avec les contrôles d’édition, ainsi que quelques autres. Vous pouvez déterminer quels messages de notification un contrôle RichEdit envoie sa fenêtre parente en définissant son « masque d’événement ».  
  
 Pour définir le masque d’événement pour un contrôle RichEdit, utilisez la [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) fonction membre. Vous pouvez récupérer le masque d’événement actuel pour un contrôle rich edit à l’aide de la [GetEventMask](../mfc/reference/cricheditctrl-class.md#geteventmask) fonction membre.  
  
 Les paragraphes suivants répertorient plusieurs notifications spécifiques et leurs utilisations :  
  
-   EN_MSGFILTER la gestion de la notification EN_MSGFILTER permet à une classe, soit le contrôle rich edit ou sa fenêtre parente, filtrer toutes les entrée clavier et souris pour le contrôle. Le gestionnaire peut empêcher le traitement de message du clavier ou la souris, ou peut modifier le message en modifiant le texte spécifié [MSGFILTER](http://msdn.microsoft.com/library/windows/desktop/bb787936) structure.  
  
-   EN_PROTECTED gérez le message de notification EN_PROTECTED pour détecter lorsque l’utilisateur tente de modifier du texte protégé. Pour marquer une plage de texte comme protégé, vous pouvez définir l’effet de caractère protégé. Pour plus d’informations, consultez [mise en forme des caractères dans les contrôles RichEdit](../mfc/character-formatting-in-rich-edit-controls.md).  
  
-   EN_DROPFILES vous pouvez activer l’utilisateur à supprimer des fichiers dans un contrôle RichEdit en traitant le message de notification EN_DROPFILES. Spécifié [ENDROPFILES](http://msdn.microsoft.com/library/windows/desktop/bb787895) structure contient des informations sur les fichiers en cours de suppression.  
  
-   La sélection actuelle change en traitant le message de notification EN_SELCHANGE EN_SELCHANGE une application peut détecter. Le message de notification spécifie une [SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb787952) structure contenant des informations sur la nouvelle sélection.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

