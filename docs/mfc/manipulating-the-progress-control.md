---
title: Manipulation du contrôle Progress | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 415061306c5e743b9ed95ee5c7105133d2e4d340
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347401"
---
# <a name="manipulating-the-progress-control"></a>Manipulation du contrôle Progress
Il existe trois façons de modifier la position actuelle d’un contrôle de progression ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).  
  
-   La position peut être modifiée par un incrément prédéfini.  
  
-   La position peut être modifiée par une quantité arbitraire.  
  
-   La position peut être modifiée sur une valeur spécifique.  
  
### <a name="to-change-the-position-by-a-preset-amount"></a>Pour modifier la position d’un incrément prédéfini  
  
1.  Utilisez le [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) fonction membre pour définir la quantité d’incrémentation. Par défaut, cette valeur est 10. Cette valeur est généralement définie comme l’un des paramètres initiaux pour le contrôle. La valeur de l’étape peut être négative.  
  
2.  Utilisez le [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) fonction membre pour incrémenter la position. Cela entraîne le contrôle à redessiner.  
  
    > [!NOTE]
    >  `StepIt` provoque la position à encapsuler. Par exemple, prenons une plage de 1 -100, une étape de 20 et une position de 90, `StepIt` définira la position à 10.  
  
### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Pour modifier la position d’une quantité arbitraire  
  
1.  Utilisez le [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) fonction membre pour modifier la position. `OffsetPos` accepte les valeurs négatives.  
  
    > [!NOTE]
    >  `OffsetPos`, contrairement à `StepIt`, pas encapsule la position. La nouvelle position est ajustée pour rester dans la plage.  
  
### <a name="to-change-the-position-to-a-specific-value"></a>Pour modifier la position sur une valeur spécifique  
  
1.  Utilisez le [fonction membre SetPos](../mfc/reference/cprogressctrl-class.md#setpos) fonction membre pour définir la position sur une valeur spécifique. Si nécessaire, la nouvelle position est ajustée pour être dans la plage.  
  
 En règle générale, le contrôle de progression est utilisé uniquement pour la sortie. Pour obtenir la position actuelle sans spécifier une nouvelle valeur, utilisez [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

