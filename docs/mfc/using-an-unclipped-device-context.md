---
description: 'En savoir plus sur : utilisation d’un contexte de périphérique non découpé'
title: Utilisation d'un contexte de périphérique non découpé
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
ms.openlocfilehash: 76131d35b108b04caf0b07be8c46e250120f9f62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202637"
---
# <a name="using-an-unclipped-device-context"></a>Utilisation d'un contexte de périphérique non découpé

Si vous êtes absolument sûr que votre contrôle n’est pas peint à l’extérieur de son rectangle client, vous pouvez réaliser un gain de vitesse faible mais détectable en désactivant l’appel à `IntersectClipRect` qui est effectué par `COleControl` . Pour ce faire, supprimez l’indicateur *clipPaintDC* du jeu d’indicateurs retourné par [COleControl :: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Par exemple :

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

Le code permettant de supprimer cet indicateur est généré automatiquement si vous sélectionnez l’option de **contexte de périphérique non découpé** sur la page [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) , lors de la création de votre contrôle à l’aide de l’Assistant contrôle ActiveX MFC.

Si vous utilisez l’activation sans fenêtre, cette optimisation n’a aucun effet.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : optimisation](../mfc/mfc-activex-controls-optimization.md)
