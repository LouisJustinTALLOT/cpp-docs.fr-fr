---
description: 'En savoir plus sur : styles de contrôle Slider'
title: Styles de contrôle Slider
ms.date: 11/04/2016
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
ms.openlocfilehash: cec057683862212a4d999ec7d0488c5f2a0837cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216910"
---
# <a name="slider-control-styles"></a>Styles de contrôle Slider

Les contrôles Slider ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) peuvent avoir une orientation verticale ou horizontale. Ils peuvent contenir des graduations de chaque côté, des deux côtés, ou d'aucun côté. Ils peuvent également être utilisés pour spécifier une plage de valeurs consécutives. Ces propriétés sont contrôlées en utilisant les styles de commande de réglage, que vous spécifiez lors de la création du curseur.

Les styles TBS_HORZ et TBS_VERT déterminent l’orientation du contrôle Slider. Si vous ne spécifiez aucune orientation, le curseur est orienté horizontalement.

Le style de TBS_AUTOTICKS crée un contrôle Slider qui a une graduation pour chaque incrément dans sa plage de valeurs. Ces graduations sont ajoutées automatiquement quand vous appelez la fonction membre [SetRange](../mfc/reference/csliderctrl-class.md#setrange) . Si vous ne spécifiez pas TBS_AUTOTICKS, vous pouvez utiliser des fonctions membres, telles que [SetTic](../mfc/reference/csliderctrl-class.md#settic) et [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), pour spécifier les positions des graduations. Pour créer un contrôle Slider qui n’affiche pas de graduations, vous pouvez utiliser le style TBS_NOTICKS.

Vous pouvez afficher les graduations d'un côté ou de l'autre, ou des deux côtés de la commande de réglage. Pour les contrôles de curseur horizontaux, vous pouvez spécifier le style de TBS_BOTTOM ou de TBS_TOP. Pour les contrôles Slider verticaux, vous pouvez spécifier le style de TBS_RIGHT ou de TBS_LEFT. (TBS_BOTTOM et TBS_RIGHT sont les paramètres par défaut.) Pour les graduations des deux côtés du contrôle Slider dans n’importe quelle orientation, spécifiez le style de TBS_BOTH.

Un contrôle Slider ne peut afficher une plage de sélection que si vous spécifiez le style de TBS_ENABLESELRANGE lors de sa création. Avec ce style, les graduations aux positions de début et de fin d'une plage de sélection sont affichées sous la forme de triangles (au lieu des tirets verticaux) et la plage de sélection est mise en surbrillance. Par exemple, les plages de sélection peuvent être utiles pour une application de planification. L'utilisateur peut sélectionner une plage de graduations qui correspondent aux heures d'une journée pour identifier une heure de réunion planifiée.

Par défaut, la longueur du curseur dans un contrôle Slider varie en fonction des modifications apportées à la plage de sélection. Si le curseur a le style TBS_FIXEDLENGTH, la longueur du curseur reste la même même si la plage de sélection change. Un curseur qui a le style TBS_NOTHUMB n'inclut pas de curseur.

## <a name="see-also"></a>Voir aussi

[Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
