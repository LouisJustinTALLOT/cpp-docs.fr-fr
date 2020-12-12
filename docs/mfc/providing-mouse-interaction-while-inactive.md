---
description: 'En savoir plus sur : fournir une interaction avec la souris en cours d’inactivité'
title: Prise en charge de l'interaction souris pendant l'inactivité
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
ms.openlocfilehash: bd3c069b052b58059de5f311e4ead795400d32fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248734"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Prise en charge de l'interaction souris pendant l'inactivité

Si votre contrôle n’est pas immédiatement activé, vous souhaiterez peut-être tout de même traiter WM_SETCURSOR et WM_MOUSEMOVE messages, même si le contrôle n’a pas de fenêtre propre. Pour ce faire, vous pouvez activer `COleControl` l’implémentation de l' `IPointerInactive` interface, qui est désactivée par défaut. (Pour obtenir une description de cette interface, consultez le *Kit de développement logiciel (SDK) ActiveX* .) Pour l’activer, incluez l’indicateur pointerInactive dans le jeu d’indicateurs retourné par [COleControl :: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

Le code permettant d’inclure cet indicateur est généré automatiquement si vous sélectionnez l’option **notifications du pointeur de la souris en cas d’inactivité** dans la page [paramètres du contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) lors de la création de votre contrôle à l’aide de l' **Assistant contrôle ActiveX MFC**.

Lorsque l' `IPointerInactive` interface est activée, le conteneur délègue WM_SETCURSOR et WM_MOUSEMOVE messages à celle-ci. `COleControl`l’implémentation de `IPointerInactive` distribue les messages via la table des messages de votre contrôle après avoir ajusté les coordonnées de la souris de manière appropriée. Vous pouvez traiter les messages comme des messages de fenêtre ordinaires en ajoutant les entrées correspondantes à la table des messages. Dans vos gestionnaires pour ces messages, évitez d’utiliser la variable membre *m_hWnd* (ou toute autre fonction membre qui l’utilise) sans vérifier d’abord que sa valeur n’est pas **null**.

Vous pouvez également souhaiter qu’un contrôle inactif soit la cible d’une opération glisser-déplacer OLE. Cela nécessite l’activation du contrôle au moment où l’utilisateur fait glisser un objet sur lui, afin que la fenêtre du contrôle puisse être enregistrée en tant que cible de déplacement. Pour faire en sorte que l’activation se produise pendant un déplacement, remplacez [COleControl :: GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)et retournez l’indicateur POINTERINACTIVE_ACTIVATEONDRAG :

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

L’activation de l' `IPointerInactive` interface signifie généralement que vous souhaitez que le contrôle soit capable de traiter des messages de souris à tout moment. Pour obtenir ce comportement dans un conteneur qui ne prend pas en charge l' `IPointerInactive` interface, vous devez faire en sorte que votre contrôle soit toujours activé quand il est visible, ce qui signifie que le contrôle doit inclure l’indicateur OLEMISC_ACTIVATEWHENVISIBLE parmi ses différents indicateurs. Toutefois, pour éviter que cet indicateur prenne effet dans un conteneur qui prend en charge `IPointerInactive` , vous pouvez également spécifier l’indicateur OLEMISC_IGNOREACTIVATEWHENVISIBLE :

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : optimisation](../mfc/mfc-activex-controls-optimization.md)
