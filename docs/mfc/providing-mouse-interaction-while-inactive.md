---
title: Prise en charge de l'interaction souris pendant l'inactivité
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
ms.openlocfilehash: d37deeec06551ae8bf340c99a9759327ce2ec2b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287841"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Prise en charge de l'interaction souris pendant l'inactivité

Si votre contrôle n’est pas activé immédiatement, vous souhaiterez peut-être toujours vers le processus WM_SETCURSOR et messages WM_MOUSEMOVE, même si le contrôle n’a pas de fenêtre. Cela est possible en activant `COleControl`d’implémentation de la `IPointerInactive` interface, qui est désactivé par défaut. (Consultez le *ActiveX SDK* pour obtenir une description de cette interface.) Pour l’activer, incorporez l’indicateur pointerInactive dans le jeu d’indicateurs retournés par [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

Le code pour inclure cet indicateur est automatiquement généré si vous sélectionnez le **souris pointeur Notifications lors de l’inactivité** option sur le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page lors de la création de votre contrôle avec la **Assistant contrôle ActiveX MFC**.

Lorsque le `IPointerInactive` interface est activée, le conteneur délègue WM_SETCURSOR et WM_MOUSEMOVE des messages. `COleControl`d’implémentation de `IPointerInactive` distribue les messages via la table des messages de votre contrôle après le réglage de la souris en coordonnées en conséquence. Vous pouvez traiter les messages comme messages de fenêtre ordinaire en ajoutant les entrées correspondantes à la table des messages. Dans les gestionnaires de ces messages, évitez d’utiliser le *m_hWnd* variable membre (ou n’importe quelle fonction membre qui l’utilise) sans vérifier au préalable que sa valeur n’est pas **NULL**.

Vous pouvez également un contrôle inactif à être la cible d’une opération de glisser-déplacer OLE. Cela nécessite l’activation du contrôle au moment où que l’utilisateur fait glisser un objet positionnée sur celle-ci, afin que la fenêtre du contrôle peut être enregistrée comme une cible de dépôt. Pour que l’activation se produisent pendant une opération de glissement, substituez [COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)et retourne l’indicateur POINTERINACTIVE_ACTIVATEONDRAG :

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

L’activation de la `IPointerInactive` interface signifie généralement que vous souhaitez le contrôle doit être capable de traiter les messages de la souris en permanence. Pour obtenir ce comportement dans un conteneur qui ne prend en charge la `IPointerInactive` interface, vous devez avoir toujours activé lorsqu’elle est visible, ce qui signifie que le contrôle doit inclure l’indicateur OLEMISC_ACTIVATEWHENVISIBLE parmi ses indicateurs divers. Toutefois, pour empêcher cet indicateur de prendre effet dans un conteneur qui prend en charge `IPointerInactive`, vous pouvez également spécifier l’indicateur OLEMISC_IGNOREACTIVATEWHENVISIBLE :

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : Optimisation](../mfc/mfc-activex-controls-optimization.md)
