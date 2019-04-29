---
title: Mise à disposition de l'activation sans scintillement
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: fad24d6201260e87ff32436752a9fbf035e822ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297045"
---
# <a name="providing-flicker-free-activation"></a>Mise à disposition de l'activation sans scintillement

Si votre contrôle se dessine lui-même de façon identique dans des états actifs et inactifs (et n’utilise pas l’activation sans fenêtre), vous pouvez éliminer les opérations de dessin et le scintillement accompagne normalement se produire lors d’une transition entre l’inactif États et actif. Pour cela, incluez le **noFlickerActivate** indicateur dans le jeu d’indicateurs retournés par [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Exemple :

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

Le code pour inclure cet indicateur est automatiquement généré si vous sélectionnez le **l’activation sans scintillement** option sur le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page lors de la création de votre contrôle avec l’Assistant de contrôle ActiveX MFC.

Si vous utilisez l’activation sans fenêtre, cette optimisation n’a aucun effet.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : Optimisation](../mfc/mfc-activex-controls-optimization.md)
