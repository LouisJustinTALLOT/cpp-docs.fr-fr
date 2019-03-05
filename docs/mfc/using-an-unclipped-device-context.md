---
title: Utilisation d'un contexte de périphérique non découpé
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
ms.openlocfilehash: 0f129c0bfa5bd76df4ba34b117e7ed8aa08c2ecb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270668"
---
# <a name="using-an-unclipped-device-context"></a>Utilisation d'un contexte de périphérique non découpé

Si vous êtes absolument certain que votre contrôle ne dessinera pas en dehors de son rectangle client, vous pouvez réaliser un gain de vitesse modeste mais palpable en désactivant l’appel à `IntersectClipRect` qui est effectuée par `COleControl`. Pour ce faire, supprimez le *clipPaintDC* indicateur dans le jeu d’indicateurs retournés par [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Exemple :

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

Le code pour supprimer cet indicateur est automatiquement généré si vous sélectionnez le **contexte de périphérique non découpé** option sur le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page, lors de la création de votre contrôle avec l’Assistant de contrôle ActiveX MFC.

Si vous utilisez l’activation sans fenêtre, cette optimisation n’a aucun effet.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : Optimisation](../mfc/mfc-activex-controls-optimization.md)
