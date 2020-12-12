---
description: 'En savoir plus sur : paramètres du contrôle Progress'
title: Paramètres du contrôle Progress
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 0cf3caa5e7b87062b1714f8e5e350840157ff7ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217066"
---
# <a name="settings-for-the-progress-control"></a>Paramètres du contrôle Progress

Les paramètres de base du contrôle Progress ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) correspondent à la plage et à la position actuelle. La plage représente la durée totale de l’opération. La position actuelle représente la progression de votre application vers la fin de l’opération. Toute modification apportée à la plage ou à la position entraîne le redessin du contrôle Progress.

Par défaut, la plage est définie sur 0-100 et la position initiale est définie sur 0. Pour récupérer les paramètres de plage actuels pour le contrôle Progress, utilisez la fonction membre [GetRange](../mfc/reference/cprogressctrl-class.md#getrange) . Pour modifier la plage, utilisez la fonction membre [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) .

Pour définir la position, utilisez [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Pour récupérer la position actuelle sans spécifier de nouvelle valeur, utilisez [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Par exemple, vous souhaiterez peut-être simplement interroger l’état de l’opération en cours.

Pour exécuter pas à pas la position actuelle du contrôle de progression, utilisez [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Pour définir la quantité de chaque étape, utilisez [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>Voir aussi

[Utilisation de CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
