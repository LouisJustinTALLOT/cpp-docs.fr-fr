---
title: Bouton toupie, fonctions membres
ms.date: 11/04/2016
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
ms.openlocfilehash: 5ad6f529762e77e1cf1c00f41eea0add5d196fbb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307261"
---
# <a name="spin-button-member-functions"></a>Bouton toupie, fonctions membres

Plusieurs fonctions membres sont disponibles pour le contrôle de sélection numérique ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Utilisez ces fonctions pour modifier les attributs suivants du bouton toupie (spin).

- **Accélération** vous pouvez ajuster la fréquence à laquelle la position change lorsque l’utilisateur appuie sur le bouton fléché vers le bas. Pour utiliser l’accélération, utilisez le [fonctions membres SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) et [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) fonctions membres.

- **Base** vous pouvez modifier la base (10 ou 16) utilisée pour afficher la position dans la légende de la fenêtre associée. Pour travailler avec la base, utilisez le [GetBase](../mfc/reference/cspinbuttonctrl-class.md#getbase) et [SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase) fonctions membres.

- **Copain fenêtre** vous pouvez définir dynamiquement la fenêtre associée. Pour interroger ou modifier le contrôle qui est la fenêtre associée, utilisez le [fonctions membres GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) et [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) fonctions membres.

- **Position** vous pouvez interroger et modifier la position. Pour travailler directement avec la position, utilisez la [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) et [fonction membre SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) fonctions membres. Dans la mesure où la légende du contrôle associé a pu changer (par exemple, dans le cas que l’ami est un contrôle d’édition), `GetPos` récupère la légende en cours et ajuste la position en conséquence.

- **Plage** vous pouvez modifier les positions minimales et maximales pour le bouton de sélection numérique. Par défaut, la valeur maximale est définie sur 0, et la valeur minimale est définie à 100. Dans la mesure où la valeur maximale par défaut est inférieure à la valeur minimale par défaut, les actions des boutons fléchés sont inversées. En règle générale, vous allez définir la plage à l’aide de la [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) fonction membre. Pour interroger l’utilisation de la plage [GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange).

## <a name="see-also"></a>Voir aussi

[Utilisation de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
