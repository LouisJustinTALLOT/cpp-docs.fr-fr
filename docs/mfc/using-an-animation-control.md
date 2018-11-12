---
title: Utilisation d'un contrôle Animation
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
ms.openlocfilehash: fa5ce6cc30d4bc31dbe52c0e559ce97e40acacba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630995"
---
# <a name="using-an-animation-control"></a>Utilisation d'un contrôle Animation

L’utilisation normale d’un contrôle animation suit le modèle suivant :

- Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue, la création est automatique lors de la création de la boîte de dialogue. (Vous devez avoir un [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) membre dans votre classe de boîte de dialogue qui correspond au contrôle de l’animation.) Vous pouvez également utiliser le [créer](../mfc/reference/canimatectrl-class.md#create) fonction membre pour créer le contrôle en tant que fenêtre enfant de n’importe quelle fenêtre.

- Charger un clip AVI dans le contrôle de l’animation en appelant le [Open](../mfc/reference/canimatectrl-class.md#open) fonction membre. Si votre contrôle animation se trouve dans une boîte de dialogue, un bon emplacement pour ce faire est de la classe de boîte de dialogue [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (fonction).

- Lire le clip en appelant le [lire](../mfc/reference/canimatectrl-class.md#play) fonction membre. Si votre contrôle animation se trouve dans une boîte de dialogue, un bon emplacement pour ce faire est de la classe de boîte de dialogue `OnInitDialog` (fonction). Appel `Play` n’est pas nécessaire si le style ACS_AUTOPLAY est définie par le contrôle d’animation.

- Si vous souhaitez afficher des parties de l’élément ou le lire frame par frame, utilisez le `Seek` fonction membre. Pour arrêter un clip en cours de lecture, utilisez le `Stop` fonction membre.

- Si vous ne souhaitez pas détruire le contrôle immédiatement, supprimer l’élément de la mémoire en appelant le `Close` fonction membre.

- Si le contrôle de l’animation se trouve dans une boîte de dialogue, elle et la `CAnimateCtrl` objet sera détruit automatiquement. Si pas, vous devez vous assurer que les deux le contrôle et le `CAnimateCtrl` objet sont détruits correctement. Destruction du contrôle automatiquement ferme le clip AVI.

## <a name="see-also"></a>Voir aussi

[Utilisation de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

