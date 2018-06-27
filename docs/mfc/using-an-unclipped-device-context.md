---
title: Utilisation d’un contexte de périphérique non découpé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4fcfbe8e8e7eb174f85ced03bec822b4968bde
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954333"
---
# <a name="using-an-unclipped-device-context"></a>Utilisation d'un contexte de périphérique non découpé
Si vous êtes absolument certain que votre contrôle ne dessinera pas en dehors de sa zone client, vous pouvez réaliser un gain de vitesse modeste mais palpable en désactivant l’appel à `IntersectClipRect` effectué par `COleControl`. Pour ce faire, supprimez le *clipPaintDC* indicateur dans le jeu d’indicateurs retourné par [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Exemple :  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]  
  
 Le code pour supprimer cet indicateur est automatiquement généré si vous sélectionnez le **contexte de périphérique non découpé** option sur le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page, lors de la création de votre contrôle avec l’Assistant contrôle ActiveX MFC.  
  
 Si vous utilisez l’activation sans fenêtre, cette optimisation n’a aucun effet.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC : optimisation](../mfc/mfc-activex-controls-optimization.md)

