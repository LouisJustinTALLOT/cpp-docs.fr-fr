---
description: 'En savoir plus sur : utilisation des contrôles Slider'
title: Utilisation de contrôles Slider
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
ms.openlocfilehash: b9134d76261bf5c15bfef90260394ee6a4c760e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322658"
---
# <a name="using-slider-controls"></a>Utilisation de contrôles Slider

L’utilisation classique d’un contrôle Slider suit le modèle ci-dessous :

- Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue, la création est automatique lors de la création de la boîte de dialogue. (Vous devez avoir un membre [CSliderCtrl](../mfc/reference/csliderctrl-class.md) dans votre classe de boîte de dialogue qui correspond au contrôle Slider.) Vous pouvez également utiliser la fonction membre [Create](../mfc/reference/csliderctrl-class.md#create) pour créer le contrôle en tant que fenêtre enfant de n’importe quelle fenêtre.

- Appelez les différentes fonctions membres Set pour définir les valeurs du contrôle. Les modifications que vous pouvez apporter incluent la définition des positions minimale et maximale pour le curseur, le dessin des graduations, la définition d’une plage de sélection et le repositionnement du curseur. Pour les contrôles d’une boîte de dialogue, il est judicieux de le faire dans la fonction [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) de la boîte de dialogue.

- À mesure que l’utilisateur interagit avec le contrôle, il envoie différents messages de notification. Vous pouvez extraire la valeur de curseur du contrôle en appelant la fonction membre [GetPos](../mfc/reference/csliderctrl-class.md#getpos) .

- Lorsque vous avez terminé avec le contrôle, vous devez vous assurer qu’il est correctement détruit. Si le contrôle Slider se trouve dans une boîte de dialogue, il `CSliderCtrl` sera détruit automatiquement. Si ce n’est pas le cas, vous devez vous assurer que le contrôle et l' `CSliderCtrl` objet sont correctement détruits.

## <a name="see-also"></a>Voir aussi

[Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
