---
description: 'En savoir plus sur : fonctions membres de bouton toupie'
title: Bouton toupie, fonctions membres
ms.date: 11/04/2016
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
ms.openlocfilehash: 6a03ab33d29634ed85d807eb5b51edfdef310d65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216832"
---
# <a name="spin-button-member-functions"></a>Bouton toupie, fonctions membres

Plusieurs fonctions membres sont disponibles pour le contrôle spin ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Utilisez ces fonctions pour modifier les attributs suivants du bouton toupie.

- **Accélération** Vous pouvez ajuster la fréquence à laquelle la position change lorsque l’utilisateur appuie sur le bouton fléché. Pour utiliser l’accélération, utilisez les fonctions membres [SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) et [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) .

- De **base** Vous pouvez modifier la base (10 ou 16) utilisée pour afficher la position dans la légende de la fenêtre associée. Pour utiliser la base, utilisez les fonctions membres [getBase (](../mfc/reference/cspinbuttonctrl-class.md#getbase) et [setbase](../mfc/reference/cspinbuttonctrl-class.md#setbase) .

- **Fenêtre associée** Vous pouvez définir dynamiquement la fenêtre associée. Pour interroger ou modifier le contrôle qui est la fenêtre associée, utilisez les fonctions membres [GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) et [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) .

- **Position** Vous pouvez interroger et modifier la position. Pour travailler directement avec la position, utilisez les fonctions membres [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) et [SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) . Étant donné que la légende du contrôle associé peut avoir changé (par exemple, dans le cas où l’ami est un contrôle d’édition), `GetPos` récupère la légende actuelle et ajuste la position en conséquence.

- **Plage** Vous pouvez modifier les positions maximale et minimale pour le bouton toupie. Par défaut, la valeur maximale est définie sur 0, et la valeur minimale est définie sur 100. Étant donné que la valeur maximale par défaut est inférieure à la valeur minimale par défaut, les actions des boutons de direction sont exintuitifs. En règle générale, vous allez définir la plage à l’aide de la fonction membre [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) . Pour interroger la plage, utilisez [GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange).

## <a name="see-also"></a>Voir aussi

[Utilisation de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
