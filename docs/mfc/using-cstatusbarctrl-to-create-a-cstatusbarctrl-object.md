---
title: Utilisation de CStatusBarCtrl pour créer un objet CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 05baf212f53956095af89377c0877db79b6e25ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552761"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Utilisation de CStatusBarCtrl pour créer un objet CStatusBarCtrl

Voici un exemple d’utilisation classique de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>Pour utiliser un contrôle de barre d’état avec des parties

1. Construire la `CStatusBarCtrl` objet.

1. Appelez [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) si vous souhaitez définir la hauteur minimale du contrôle de barre d’état de zone de dessin.

1. Appelez [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) pour définir la couleur d’arrière-plan du contrôle de barre d’état.

1. Appelez [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) pour définir le nombre de parties dans un barre d’état contrôle et les coordonnées du bord droit de chaque partie.

1. Appelez [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) pour définir le texte dans une partie donnée du contrôle de barre d’état. Le message invalide la partie du contrôle qui a changé, provoquant l’affichage du nouveau texte lorsque le contrôle reçoit ensuite le message WM_PAINT.

Dans certains cas, la barre d’état doit afficher une ligne de texte. Dans ce cas, effectuer un appel à [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). Cela place le contrôle de barre d’état en mode « simple », qui affiche une seule ligne de texte.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

