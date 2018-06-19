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
ms.openlocfilehash: c678af3444ef408a0a9c50e972942d67e2d3cf1b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353851"
---
# <a name="notifications-from-a-rich-edit-control"></a>Notifications d'un contrôle RichEdit
Messages de notification d’événements affectant une riche contrôle d’édition de rapport ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Ils peuvent être traités par la fenêtre parente ou, à l’aide de la réflexion de message, par la riche contrôle d’édition lui-même. Les contrôles RichEdit prennent en charge tous les messages de notification utilisés avec les contrôles d’édition, ainsi que quelques autres. Vous pouvez déterminer quels messages de notification un contrôle RichEdit envoie sa fenêtre parente en définissant son « masque d’événement ».  
  
 Pour définir le masque d’événement pour un contrôle RichEdit, utilisez la [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) fonction membre. Vous pouvez récupérer le masque d’événement actuel pour un contrôle rich edit à l’aide de la [GetEventMask](../mfc/reference/cricheditctrl-class.md#geteventmask) fonction membre.  
  
 Les paragraphes suivants répertorient plusieurs notifications spécifiques et leurs utilisations :  
  
-   **EN_MSGFILTER** gère la **EN_MSGFILTER** notification permet à une classe, soit la riche contrôle modifier ou sa fenêtre parente, filtre toutes les clavier et les entrées pour le contrôle de la souris. Le gestionnaire peut empêcher le traitement de message du clavier ou la souris, ou peut modifier le message en modifiant le texte spécifié [MSGFILTER](http://msdn.microsoft.com/library/windows/desktop/bb787936) structure.  
  
-   **EN_PROTECTED** gérer le **EN_PROTECTED** message de notification pour détecter lorsque l’utilisateur tente de modifier du texte protégé. Pour marquer une plage de texte comme protégé, vous pouvez définir l’effet de caractère protégé. Pour plus d’informations, consultez [mise en forme des caractères dans les contrôles RichEdit](../mfc/character-formatting-in-rich-edit-controls.md).  
  
-   **EN_DROPFILES** vous pouvez activer l’utilisateur à supprimer des fichiers dans un contrôle RichEdit en traitant le **EN_DROPFILES** message de notification. Spécifié [ENDROPFILES](http://msdn.microsoft.com/library/windows/desktop/bb787895) structure contient des informations sur les fichiers en cours de suppression.  
  
-   **EN_SELCHANGE** une application peut détecter lorsque la sélection actuelle change en traitant le **EN_SELCHANGE** message de notification. Le message de notification spécifie une [SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb787952) structure contenant des informations sur la nouvelle sélection.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

