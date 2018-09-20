---
title: Utilisation de CSliderCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CSliderCtrl
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls [MFC], using
ms.assetid: 242c7bcd-126e-4b9b-8f76-8082ad06fe73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8dec5e0500d7857c8b6781cfd0f78fb18cf93349
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380314"
---
# <a name="using-csliderctrl"></a>Utilisation de CSliderCtrl

Le [CSliderCtrl](../mfc/reference/csliderctrl-class.md) classe représente un contrôle slider, également appelé barre de suivi. Un « contrôle de curseur » est une fenêtre qui contient un curseur et des graduations facultatives marques. Lorsque l’utilisateur déplace le curseur, à l’aide de la souris ou les touches de direction, le contrôle slider envoie des messages de notification pour indiquer la modification.

Contrôles Slider sont utiles lorsque vous souhaitez que l’utilisateur de sélectionner une valeur discrète ou un ensemble de valeurs consécutives dans une plage. Par exemple, vous pouvez utiliser un contrôle slider pour autoriser l’utilisateur à définir la fréquence de répétition du clavier en déplaçant le curseur jusqu'à une graduation donnée.

Le curseur dans un contrôle de curseur se déplace en incréments que vous spécifiez lors de sa création. Par exemple, si vous spécifiez que le contrôle slider doit avoir une plage de cinq, le curseur ne peut occuper six positions : une position sur le côté gauche du contrôle slider et une position pour chaque incrément dans la plage. En règle générale, chacune de ces positions est identifiée par une graduation.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Utilisation de contrôles Slider](../mfc/using-slider-controls.md)

- [Styles de contrôle Slider](../mfc/slider-control-styles.md)

- [Fonctions membres de contrôle Slider](../mfc/slider-control-member-functions.md)

- [Messages de notification du Slider](../mfc/slider-notification-messages.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)

