---
title: Notifications d'un contrôle RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: 206fc02088f6531338bf2aa4cf272a1da096bae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622225"
---
# <a name="notifications-from-a-rich-edit-control"></a>Notifications d'un contrôle RichEdit

Les messages de notification signalent des événements affectant un contrôle Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)). Ils peuvent être traités par la fenêtre parente ou, à l’aide de la réflexion de message, par le contrôle Rich Edit lui-même. Les contrôles RichEdit prennent en charge tous les messages de notification utilisés avec les contrôles d’édition, ainsi que plusieurs autres. Vous pouvez déterminer les messages de notification qu’un contrôle RichEdit envoie à sa fenêtre parente en définissant son « masque d’événement ».

Pour définir le masque d’événement pour un contrôle RichEdit, utilisez la fonction membre [SetEventMask](reference/cricheditctrl-class.md#seteventmask) . Vous pouvez récupérer le masque d’événement actuel d’un contrôle RichEdit à l’aide de la fonction membre [GetEventMask](reference/cricheditctrl-class.md#geteventmask) .

Les paragraphes suivants répertorient plusieurs notifications spécifiques et leurs utilisations :

- EN_MSGFILTER la gestion de la notification EN_MSGFILTER permet à une classe, soit le contrôle Rich Edit, soit sa fenêtre parente, de filtrer toutes les entrées de clavier et de souris sur le contrôle. Le gestionnaire peut empêcher le traitement du message clavier ou de la souris ou peut le modifier en modifiant la structure [msgfilter](/windows/win32/api/richedit/ns-richedit-msgfilter) spécifiée.

- EN_PROTECTED gérer le message de notification EN_PROTECTED pour détecter quand l’utilisateur tente de modifier du texte protégé. Pour marquer une plage de texte comme protégée, vous pouvez définir l’effet de caractère protégé. Pour plus d’informations, consultez [mise en forme des caractères dans les contrôles RichEdit](character-formatting-in-rich-edit-controls.md).

- EN_DROPFILES vous pouvez autoriser l’utilisateur à déposer des fichiers dans un contrôle RichEdit en traitant le message de notification EN_DROPFILES. La structure [ENDROPFILES](/windows/win32/api/richedit/ns-richedit-endropfiles) spécifiée contient des informations sur les fichiers en cours de suppression.

- EN_SELCHANGE une application peut détecter à quel moment la sélection actuelle change en traitant le message de notification EN_SELCHANGE. Le message de notification spécifie une structure [selChange](/windows/win32/api/richedit/ns-richedit-selchange) contenant des informations sur la nouvelle sélection.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Commandes](controls-mfc.md)
