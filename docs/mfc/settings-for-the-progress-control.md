---
title: Paramètres du contrôle Progress
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 444dc45c816e0dfc2fd45bad999ad90c2acacc01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481777"
---
# <a name="settings-for-the-progress-control"></a>Paramètres du contrôle Progress

Les paramètres de base du contrôle progress ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) sont la plage et la position actuelle. La plage représente l’ensemble de la durée de l’opération. La position actuelle représente la progression de votre application a effectué l’opération. Toute modification de la plage ou la position provoque le contrôle de progression se redessiner.

Par défaut, la plage est définie sur 0 - 100 et la position initiale est définie sur 0. Pour récupérer les paramètres actuels de la plage du contrôle progress, utilisez la [GetRange](../mfc/reference/cprogressctrl-class.md#getrange) fonction membre. Pour modifier la plage, utilisez la [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) fonction membre.

Pour définir la position, utilisez [fonction membre SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Pour récupérer la position actuelle sans spécifier une nouvelle valeur, utilisez [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Par exemple, vous souhaiterez peut-être simplement interroger l’état de l’opération en cours.

Pour l’étape de la position actuelle du contrôle de progression, utilisez [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Pour définir la quantité de chaque étape, utilisez [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>Voir aussi

[Utilisation de CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

