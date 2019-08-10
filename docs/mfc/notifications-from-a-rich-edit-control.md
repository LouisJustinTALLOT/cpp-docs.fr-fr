---
title: Notifications d'un contrôle RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: bc4c027ff26df89539b22c6d04f1d1dc95fc459a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916400"
---
# <a name="notifications-from-a-rich-edit-control"></a>Notifications d'un contrôle RichEdit

Les messages de notification signalent des événements affectant un contrôle Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Ils peuvent être traités par la fenêtre parente ou, à l’aide de la réflexion de message, par le contrôle Rich Edit lui-même. Les contrôles RichEdit prennent en charge tous les messages de notification utilisés avec les contrôles d’édition, ainsi que plusieurs autres. Vous pouvez déterminer les messages de notification qu’un contrôle RichEdit envoie à sa fenêtre parente en définissant son «masque d’événement».

Pour définir le masque d’événement pour un contrôle RichEdit, utilisez la fonction membre [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) . Vous pouvez récupérer le masque d’événement actuel d’un contrôle RichEdit à l’aide de la fonction membre [GetEventMask](../mfc/reference/cricheditctrl-class.md#geteventmask) .

Les paragraphes suivants répertorient plusieurs notifications spécifiques et leurs utilisations:

- EN_MSGFILTER la gestion de la notification EN_MSGFILTER permet à une classe, soit le contrôle Rich Edit, soit sa fenêtre parente, de filtrer toutes les entrées du clavier et de la souris sur le contrôle. Le gestionnaire peut empêcher le traitement du message clavier ou de la souris ou peut le modifier en modifiant la structure [msgfilter](/windows/desktop/api/richedit/ns-richedit-msgfilter) spécifiée.

- EN_PROTECTED gère le message de notification EN_PROTECTED pour détecter quand l’utilisateur tente de modifier du texte protégé. Pour marquer une plage de texte comme protégée, vous pouvez définir l’effet de caractère protégé. Pour plus d’informations, consultez [mise en forme des caractères dans les contrôles RichEdit](../mfc/character-formatting-in-rich-edit-controls.md).

- EN_DROPFILES vous pouvez autoriser l’utilisateur à déposer des fichiers dans un contrôle RichEdit en traitant le message de notification EN_DROPFILES. La structure [ENDROPFILES](/windows/desktop/api/richedit/ns-richedit-endropfiles) spécifiée contient des informations sur les fichiers en cours de suppression.

- EN_SELCHANGE une application peut détecter lorsque la sélection actuelle change en traitant le message de notification EN_SELCHANGE. Le message de notification spécifie une structure [selChange](/windows/desktop/api/richedit/ns-richedit-selchange) contenant des informations sur la nouvelle sélection.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
