---
description: 'En savoir plus sur : fournir une activation Flicker-Free'
title: Mise à disposition de l'activation sans scintillement
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: c0af1ccdd4795f55296ff38e0e74bc6492f79eb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248825"
---
# <a name="providing-flicker-free-activation"></a>Mise à disposition de l'activation sans scintillement

Si votre contrôle se dessine de la même façon dans les États inactifs et actifs (et n’utilise pas l’activation sans fenêtre), vous pouvez éliminer les opérations de dessin et le scintillateur visuel qui l’accompagne qui se produisent normalement lors de la transition entre les États inactif et actif. Pour ce faire, incluez l’indicateur **noFlickerActivate** dans le jeu d’indicateurs retourné par [COleControl :: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Par exemple :

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

Le code permettant d’inclure cet indicateur est généré automatiquement si vous sélectionnez l’option **activation sans scintillement** dans la page [paramètres du contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) lors de la création de votre contrôle à l’aide de l’Assistant contrôle ActiveX MFC.

Si vous utilisez l’activation sans fenêtre, cette optimisation n’a aucun effet.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : optimisation](../mfc/mfc-activex-controls-optimization.md)
