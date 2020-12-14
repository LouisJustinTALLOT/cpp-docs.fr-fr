---
description: 'En savoir plus sur : utilisation de CStatusBarCtrl pour créer un objet CStatusBarCtrl'
title: Utilisation de CStatusBarCtrl pour créer un objet CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 0b76065ce4e90600bdec7e4f4a89ee2c5bb14085
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202377"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Utilisation de CStatusBarCtrl pour créer un objet CStatusBarCtrl

Voici un exemple d’utilisation classique de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>Pour utiliser un contrôle de barre d’État avec des parties

1. Construisez l' `CStatusBarCtrl` objet.

1. Appelez [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) si vous souhaitez définir la hauteur minimale de la zone de dessin du contrôle de barre d’État.

1. Appelez [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) pour définir la couleur d’arrière-plan du contrôle de barre d’État.

1. Appelez [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) pour définir le nombre de parties dans un contrôle de barre d’État et la coordonnée du bord droit de chaque partie.

1. Appelez [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) pour définir le texte dans une partie donnée du contrôle de barre d’État. Le message invalide la partie du contrôle qui a changé, provoquant l’affichage du nouveau texte lorsque le contrôle reçoit ensuite le message de WM_PAINT.

Dans certains cas, la barre d’État ne doit afficher qu’une ligne de texte. Dans ce cas, effectuez un appel à [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). Cela place le contrôle de barre d’État en mode « simple », qui affiche une seule ligne de texte.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
