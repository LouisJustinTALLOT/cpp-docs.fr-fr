---
title: Interaction souris pendant l’inactivité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: faf1ea1958d6a6381bbe1c6e7d3db26f5f5b7c17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349673"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Prise en charge de l'interaction souris pendant l'inactivité
Si votre contrôle n’est pas activé immédiatement, vous souhaiterez à traiter `WM_SETCURSOR` et `WM_MOUSEMOVE` des messages, même si le contrôle n’a pas de fenêtre. Cela peut être accompli en activant `COleControl`d’implémentation de la `IPointerInactive` interface, qui est désactivée par défaut. (Consultez la *ActiveX SDK* pour obtenir une description de cette interface.) Pour l’activer, vous devez inclure le `pointerInactive` indicateur dans le jeu d’indicateurs retourné par [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 Le code permettant d’inclure cet indicateur est automatiquement généré si vous sélectionnez le **souris pointeur Notifications lors de l’inactivité** option sur le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page lors de la création de votre contrôle avec la **Assistant contrôle ActiveX MFC**.  
  
 Lorsque le `IPointerInactive` interface est activée, les délégués de conteneur `WM_SETCURSOR` et `WM_MOUSEMOVE` messages. `COleControl`de la mise en œuvre de `IPointerInactive` distribue les messages via une table des messages de votre contrôle après ajustement de la souris en coordonnées en conséquence. Vous pouvez traiter les messages comme des messages de fenêtre ordinaires en ajoutant les entrées correspondantes à la table des messages. Dans les gestionnaires de ces messages, évitez d’utiliser le `m_hWnd` variable membre (ou une fonction membre qui l’utilise) sans vérifier au préalable que sa valeur n’est pas **NULL**.  
  
 Vous pouvez également un contrôle inactif à être la cible d’une opération de glisser-déplacer OLE. Cela nécessite l’activation du contrôle au moment où que l’utilisateur fait glisser un objet, afin que la fenêtre du contrôle peut être enregistrée comme une cible de dépôt. Pour que l’activation se produisent pendant une opération de glissement, substituez [COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)et retourner le **POINTERINACTIVE_ACTIVATEONDRAG** indicateur :  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 L’activation de la `IPointerInactive` interface signifie généralement que vous souhaitez le contrôle doit être capable de traiter des messages de la souris en permanence. Pour obtenir ce comportement dans un conteneur qui ne prend en charge la `IPointerInactive` interface, vous devez avoir toujours activé quand il est visible, ce qui signifie que le contrôle doit inclure le **OLEMISC_ACTIVATEWHENVISIBLE** indicateur entre ses indicateurs divers. Toutefois, pour empêcher cet indicateur de prise d’effet dans un conteneur qui prend en charge `IPointerInactive`, vous pouvez également spécifier le **OLEMISC_IGNOREACTIVATEWHENVISIBLE** indicateur :  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC : optimisation](../mfc/mfc-activex-controls-optimization.md)

