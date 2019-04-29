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
ms.openlocfilehash: c9da6f8048adf1c7da184570ff7f94deee7441e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279188"
---
# <a name="manipulating-the-progress-control"></a>Manipulation du contrôle Progress

Il existe trois façons pour modifier la position actuelle d’un contrôle de progression ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).

- La position peut être modifiée par un incrément prédéfini.

- La position peut être modifiée par une quantité arbitraire.

- La position peut être modifiée sur une valeur spécifique.

### <a name="to-change-the-position-by-a-preset-amount"></a>Pour modifier la position d’un incrément prédéfini

1. Utilisez le [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) fonction membre pour définir la quantité d’incrémentation. Par défaut, cette valeur est 10. Cette valeur est généralement définie comme l’un des paramètres initiaux pour le contrôle. La valeur de l’étape peut être négative.

1. Utilisez le [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) fonction membre pour incrémenter la position. Cela entraîne le contrôle à redessiner.

    > [!NOTE]
    >  `StepIt` entraîne la position à encapsuler. Par exemple, étant donné une plage de 1 -100, une étape de 20 et une position de 90 `StepIt` définira la position à 10.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Pour modifier la position d’une valeur arbitraire

1. Utilisez le [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) fonction membre pour modifier la position. `OffsetPos` accepte les valeurs négatives.

    > [!NOTE]
    >  `OffsetPos`, contrairement à `StepIt`, ne sera pas encapsuler la position. La nouvelle position est ajustée pour rester dans la plage.

### <a name="to-change-the-position-to-a-specific-value"></a>Pour modifier la position sur une valeur spécifique

1. Utilisez le [fonction membre SetPos](../mfc/reference/cprogressctrl-class.md#setpos) fonction membre pour définir la position sur une valeur spécifique. Si nécessaire, la nouvelle position est ajustée pour être dans la plage.

En règle générale, le contrôle de progression est utilisé uniquement pour la sortie. Pour obtenir la position actuelle sans spécifier une nouvelle valeur, utilisez [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).

## <a name="see-also"></a>Voir aussi

[Utilisation de CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
