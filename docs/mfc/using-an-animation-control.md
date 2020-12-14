---
description: 'En savoir plus sur : utilisation d’un contrôle d’animation'
title: Utilisation d'un contrôle Animation
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
ms.openlocfilehash: 7ef4a7b5eb005569ac2a3e3cb66cc0ed785e9299
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202715"
---
# <a name="using-an-animation-control"></a>Utilisation d'un contrôle Animation

L’utilisation classique d’un contrôle d’animation suit le modèle ci-dessous :

- Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue, la création est automatique lors de la création de la boîte de dialogue. (Vous devez avoir un membre [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) dans votre classe de boîte de dialogue qui correspond au contrôle d’animation.) Vous pouvez également utiliser la fonction membre [Create](../mfc/reference/canimatectrl-class.md#create) pour créer le contrôle en tant que fenêtre enfant de n’importe quelle fenêtre.

- Chargez un clip AVI dans le contrôle d’animation en appelant la fonction membre [Open](../mfc/reference/canimatectrl-class.md#open) . Si votre contrôle d’animation se trouve dans une boîte de dialogue, il est préférable de le faire dans la fonction [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) de la classe dialog.

- Lisez le clip en appelant la fonction membre [Play](../mfc/reference/canimatectrl-class.md#play) . Si votre contrôle d’animation se trouve dans une boîte de dialogue, il est préférable de le faire dans la fonction de la classe Dialog `OnInitDialog` . L’appel de `Play` n’est pas nécessaire si le style de ACS_AUTOPLAY est défini pour le contrôle d’animation.

- Si vous souhaitez afficher des portions du clip ou le lire frame par cadre, utilisez la `Seek` fonction membre. Pour arrêter un clip en train de s’exécuter, utilisez la `Stop` fonction membre.

- Si vous ne souhaitez pas détruire le contrôle immédiatement, retirez le clip de la mémoire en appelant la `Close` fonction membre.

- Si le contrôle d’animation se trouve dans une boîte de dialogue, il `CAnimateCtrl` sera détruit automatiquement. Si ce n’est pas le cas, vous devez vous assurer que le contrôle et l' `CAnimateCtrl` objet sont correctement détruits. La destruction du contrôle ferme automatiquement le clip AVI.

## <a name="see-also"></a>Voir aussi

[Utilisation de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
