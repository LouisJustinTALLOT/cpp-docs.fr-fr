---
title: Notifications d'un contrôle RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: 87168b6e58264b4257b7adfb32207ec1dd40729e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529205"
---
# <a name="notifications-from-a-rich-edit-control"></a>Notifications d'un contrôle RichEdit

Messages de notification d’événements qui affectent une riche contrôle d’édition de rapport ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Ils peuvent être traités par la fenêtre parente ou, à l’aide de la réflexion de message, par la riche contrôle d’édition lui-même. Les contrôles RichEdit prennent en charge tous les messages de notification utilisés avec les contrôles d’édition, ainsi que quelques autres. Vous pouvez déterminer quels messages de notification un contrôle RichEdit envoie sa fenêtre parente en définissant son « masque d’événement ».

Pour définir le masque d’événement pour un contrôle rich edit, utilisez la [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) fonction membre. Vous pouvez récupérer le masque d’événement en cours pour un contrôle rich edit à l’aide de la [GetEventMask](../mfc/reference/cricheditctrl-class.md#geteventmask) fonction membre.

Les paragraphes suivants répertorient plusieurs notifications spécifiques et leurs utilisations :

- EN_MSGFILTER la gestion de la notification EN_MSGFILTER permet à une classe, soit le contrôle rich edit ou sa fenêtre parente, filtrer toutes les entrée clavier et souris pour le contrôle. Le gestionnaire peut empêcher le traitement de message de clavier ou la souris, ou peut modifier le message en modifiant le texte spécifié [MSGFILTER](/windows/desktop/api/richedit/ns-richedit-_msgfilter) structure.

- EN_PROTECTED gérez le message de notification EN_PROTECTED pour détecter lorsque l’utilisateur tente de modifier du texte protégé. Pour marquer une plage de texte comme protégé, vous pouvez définir l’effet de caractère protégé. Pour plus d’informations, consultez [mise en forme des caractères dans les contrôles RichEdit](../mfc/character-formatting-in-rich-edit-controls.md).

- EN_DROPFILES vous pouvez autoriser l’utilisateur à déposer des fichiers dans un contrôle RichEdit en traitant le message de notification EN_DROPFILES. Spécifié [ENDROPFILES](/windows/desktop/api/richedit/ns-richedit-_endropfiles) structure contient des informations sur les fichiers en cours de suppression.

- EN_SELCHANGE une application peut détecter lorsque la sélection actuelle change en traitant le message de notification EN_SELCHANGE. Le message de notification spécifie un [SELCHANGE](/windows/desktop/api/richedit/ns-richedit-_selchange) structure contenant des informations sur la nouvelle sélection.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

