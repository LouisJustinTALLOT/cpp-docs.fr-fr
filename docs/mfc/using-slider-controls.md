---
title: Utilisation de contrôles Slider
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
ms.openlocfilehash: 7bb5bda4a7b85ea8bb852649b20f10f0c4693188
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533560"
---
# <a name="using-slider-controls"></a>Utilisation de contrôles Slider

L’utilisation normale d’un contrôle slider suit le modèle suivant :

- Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue, la création est automatique lors de la création de la boîte de dialogue. (Vous devez avoir un [CSliderCtrl](../mfc/reference/csliderctrl-class.md) membre dans votre classe de boîte de dialogue qui correspond au contrôle de curseur.) Vous pouvez également utiliser le [créer](../mfc/reference/csliderctrl-class.md#create) fonction membre pour créer le contrôle en tant que fenêtre enfant de n’importe quelle fenêtre.

- Appelez les diverses fonctions de membre ensemble pour définir les valeurs pour le contrôle. Les modifications que vous pouvez effectuer incluent définissant les positions minimales et maximales pour le curseur, le dessin des graduations, la définition d’une plage de sélection et le repositionnement du curseur. Pour les contrôles dans une boîte de dialogue, un bon moment pour ce faire est dans la boîte de dialogue [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (fonction).

- Lorsque l’utilisateur interagit avec le contrôle, il envoie différents messages de notification. Vous pouvez extraire la valeur de curseur à partir du contrôle en appelant le [GetPos](../mfc/reference/csliderctrl-class.md#getpos) fonction membre.

- Lorsque vous avez terminé avec le contrôle, vous devez vous assurer qu’il est correctement détruit. Si le contrôle de curseur se trouve dans une boîte de dialogue, elle et la `CSliderCtrl` objet sera détruit automatiquement. Si pas, vous devez vous assurer que les deux le contrôle et le `CSliderCtrl` objet sont détruits correctement.

## <a name="see-also"></a>Voir aussi

[Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

