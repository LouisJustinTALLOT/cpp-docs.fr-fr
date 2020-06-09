---
title: Manipulation du contrôle Progress
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: 3e3521a82854a85062f9b06bc33eb268d4b9c7a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622431"
---
# <a name="manipulating-the-progress-control"></a>Manipulation du contrôle Progress

Il existe trois façons de modifier la position actuelle d’un contrôle Progress ([CProgressCtrl](reference/cprogressctrl-class.md)).

- La position peut être modifiée par une valeur d’incrément de présélection.

- La position peut être modifiée par une quantité arbitraire.

- La position peut être remplacée par une valeur spécifique.

### <a name="to-change-the-position-by-a-preset-amount"></a>Pour modifier la position d’une valeur prédéfinie

1. Utilisez la fonction membre [SetStep](reference/cprogressctrl-class.md#setstep) pour définir la quantité d’incrémentation. Par défaut, cette valeur est 10. Cette valeur est généralement définie comme l’un des paramètres initiaux du contrôle. La valeur de l’étape peut être négative.

1. Utilisez la fonction membre [StepIt](reference/cprogressctrl-class.md#stepit) pour incrémenter la position. Le contrôle se redessine alors lui-même.

    > [!NOTE]
    >  `StepIt`provoque l’encapsulation de la position. Par exemple, étant donné une plage de 1 -100, une étape de 20 et une position de 90, `StepIt` la position est définie sur 10.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Pour modifier la position d’une quantité arbitraire

1. Utilisez la fonction membre [OffsetPos](reference/cprogressctrl-class.md#offsetpos) pour modifier la position. `OffsetPos`accepte les valeurs négatives.

    > [!NOTE]
    >  `OffsetPos`, contrairement à `StepIt` , n’encapsule pas la position. La nouvelle position est ajustée pour rester dans la plage.

### <a name="to-change-the-position-to-a-specific-value"></a>Pour changer la position en une valeur spécifique

1. Utilisez la fonction membre [SetPos](reference/cprogressctrl-class.md#setpos) pour définir la position sur une valeur spécifique. Si nécessaire, la nouvelle position est ajustée pour être comprise dans la plage.

En règle générale, le contrôle de progression est utilisé uniquement pour la sortie. Pour obtenir la position actuelle sans spécifier de nouvelle valeur, utilisez [GetPos](reference/cprogressctrl-class.md#getpos).

## <a name="see-also"></a>Voir aussi

[Utilisation de CProgressCtrl](using-cprogressctrl.md)<br/>
[Commandes](controls-mfc.md)
