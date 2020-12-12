---
description: 'En savoir plus sur : utilisation d’une barre de boîte de dialogue avec un contrôle rebar'
title: Utilisation d'une barre de boîte de dialogue avec un contrôle rebar
ms.date: 11/04/2016
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: 97fb8ca5c356d91fa4b4ba44753fbdc9bf298435
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263528"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Utilisation d'une barre de boîte de dialogue avec un contrôle rebar

Comme mentionné dans les [contrôles et les bandes rebar](../mfc/rebar-controls-and-bands.md), chaque bande ne peut contenir qu’une seule fenêtre enfant (ou contrôle). Cela peut être une limitation si vous souhaitez avoir plusieurs fenêtres enfants par bande. Une solution de contournement pratique consiste à créer une ressource de barre de boîte de dialogue avec plusieurs contrôles, puis à ajouter une bande rebar (contenant la barre de boîte de dialogue) au contrôle rebar.

Normalement, si vous souhaitez que la bande de la barre de boîte de dialogue apparaisse transparente, vous devez définir le WS_EX_TRANSPARENT style étendu pour l’objet de barre de boîte de dialogue. Toutefois, étant donné que WS_EX_TRANSPARENT rencontre des problèmes avec la peinture correcte de l’arrière-plan d’une barre de boîte de dialogue, vous devrez effectuer un peu de travail supplémentaire pour obtenir l’effet souhaité.

La procédure suivante détaille les étapes nécessaires pour obtenir la transparence sans utiliser le style étendu WS_EX_TRANSPARENT.

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Pour implémenter une barre de boîte de dialogue transparente dans une bande rebar

1. À l’aide de la [boîte de dialogue Ajouter une classe](../mfc/reference/adding-an-mfc-class.md), ajoutez une nouvelle classe (par exemple, `CMyDlgBar` ) qui implémente l’objet de barre de boîte de dialogue.

1. Ajoutez un gestionnaire pour le message de WM_ERASEBKGND.

1. Dans le nouveau gestionnaire, modifiez le code existant pour qu’il corresponde à l’exemple suivant :

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. Ajoutez un gestionnaire pour le message de WM_MOVE.

1. Dans le nouveau gestionnaire, modifiez le code existant pour qu’il corresponde à l’exemple suivant :

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

Les nouveaux gestionnaires simulent la transparence de la barre de boîte de dialogue en transférant le WM_ERASEBKGND message à la fenêtre parente et en forçant un redessin à chaque déplacement de l’objet de barre de boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
