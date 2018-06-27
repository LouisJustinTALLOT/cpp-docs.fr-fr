---
title: Styles de contrôle Slider | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f76fbe9f85d978a5c2865b48720588b620508a07
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951050"
---
# <a name="slider-control-styles"></a>Styles de contrôle Slider
Contrôles Slider ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) peut avoir une orientation verticale ou horizontale. Ils peuvent contenir des graduations de chaque côté, des deux côtés, ou d'aucun côté. Ils peuvent également être utilisés pour spécifier une plage de valeurs consécutives. Ces propriétés sont contrôlées en utilisant les styles de commande de réglage, que vous spécifiez lors de la création du curseur.  
  
 Les styles TBS_HORZ et TBS_VERT déterminent l’orientation du contrôle slider. Si vous ne spécifiez aucune orientation, le curseur est orienté horizontalement.  
  
 Le style TBS_AUTOTICKS crée un contrôle de curseur qui a une graduation pour chaque incrément dans sa plage de valeurs. Ces graduations sont ajoutées automatiquement lorsque vous appelez le [SetRange](../mfc/reference/csliderctrl-class.md#setrange) fonction membre. Si vous ne spécifiez pas TBS_AUTOTICKS, vous pouvez utiliser les fonctions membres, tels que [SetTic](../mfc/reference/csliderctrl-class.md#settic) et [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), pour spécifier les positions des graduations. Pour créer un contrôle de curseur qui n’affiche pas les graduations, vous pouvez utiliser le style TBS_NOTICKS.  
  
 Vous pouvez afficher les graduations d'un côté ou de l'autre, ou des deux côtés de la commande de réglage. Pour les contrôles slider horizontal, vous pouvez spécifier le style de style TBS_BOTTOM ou TBS_TOP. Pour les contrôles slider vertical, vous pouvez spécifier le style TBS_RIGHT ou TBS_LEFT. (TBS_BOTTOM et TBS_RIGHT sont les paramètres par défaut). Pour les graduations des deux côtés du contrôle slider dans n’importe quelle orientation, spécifiez le style TBS_BOTH.  
  
 Un contrôle de curseur peut afficher une plage de sélection uniquement si vous spécifiez le style TBS_ENABLESELRANGE lors de sa création. Avec ce style, les graduations aux positions de début et de fin d'une plage de sélection sont affichées sous la forme de triangles (au lieu des tirets verticaux) et la plage de sélection est mise en surbrillance. Par exemple, les plages de sélection peuvent être utiles pour une application de planification. L'utilisateur peut sélectionner une plage de graduations qui correspondent aux heures d'une journée pour identifier une heure de réunion planifiée.  
  
 Par défaut, la longueur du curseur dans un contrôle Slider varie en fonction des modifications apportées à la plage de sélection. Si le contrôle slider possède le style TBS_FIXEDLENGTH, la longueur du curseur reste le même, même si la plage de sélection est modifiée. Un contrôle de curseur qui a le style TBS_NOTHUMB n’inclut pas d’un curseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

