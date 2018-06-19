---
title: Utilisation d’une barre de boîte de dialogue avec un contrôle Rebar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WM_EX_TRANSPARENT
dev_langs:
- C++
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47894c14e3b3d694847f94e7f981c9397383e598
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382904"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Utilisation d'une barre de boîte de dialogue avec un contrôle rebar
Comme mentionné dans [contrôles Rebar et bandes](../mfc/rebar-controls-and-bands.md), chaque bande peut contenir qu’une seule fenêtre enfant (ou contrôle). Cela peut être une limitation si vous souhaitez avoir plus d’une fenêtre enfant par bande. Une solution pratique consiste à créer une ressource de barre de boîte de dialogue avec plusieurs contrôles et d’ajouter une bande (contenant la barre de boîte de dialogue) au contrôle rebar.  
  
 Normalement, si vous voulez que la bande de barre de boîte de dialogue transparente, vous devez définir le **WS_EX_TRANSPARENT** extended style de l’objet de barre de boîte de dialogue. Toutefois, étant donné que **WS_EX_TRANSPARENT** a des problèmes liés à peindre correctement l’arrière-plan d’une barre de boîte de dialogue, vous devez effectuer un travail supplémentaire pour obtenir l’effet souhaité.  
  
 La procédure suivante détaille les étapes nécessaires pour obtenir la transparence sans utiliser le **WS_EX_TRANSPARENT** style étendu.  
  
### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Pour implémenter une barre de boîte de dialogue transparent dans une bande rebar  
  
1.  À l’aide de la [boîte de dialogue Ajouter une classe](../mfc/reference/adding-an-mfc-class.md), ajoutez une nouvelle classe (par exemple, `CMyDlgBar`) qui implémente votre objet de barre de boîte de dialogue.  
  
2.  Ajoutez un gestionnaire pour le `WM_ERASEBKGND` message.  
  
3.  Dans le nouveau gestionnaire, modifiez le code existant pour correspondre à l’exemple suivant :  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  Ajoutez un gestionnaire pour le `WM_MOVE` message.  
  
5.  Dans le nouveau gestionnaire, modifiez le code existant pour correspondre à l’exemple suivant :  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 Les nouveaux gestionnaires simulent la transparence de la barre de boîte de dialogue par le transfert du `WM_ERASEBKGND` le message à la fenêtre parente et forcer la mise à jour chaque fois que l’objet de barre de boîte de dialogue est déplacé.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

