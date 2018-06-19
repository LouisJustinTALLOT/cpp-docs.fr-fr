---
title: Bouton toupie, membre fonctions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 524863b816c62903cb610b57a6e3275bcdf6a3d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381249"
---
# <a name="spin-button-member-functions"></a>Bouton toupie, fonctions membres
Plusieurs fonctions membres sont disponibles pour le contrôle de sélection numérique ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Utilisez ces fonctions pour modifier les attributs suivants de la toupie.  
  
-   **Accélération** vous pouvez ajuster la vitesse à laquelle la position change lorsque l’utilisateur appuie sur le bouton de flèche. Pour utiliser l’accélération, utilisez le [fonctions membres SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) et [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) fonctions membres.  
  
-   **Base** vous pouvez modifier la base (10 ou 16) utilisée pour afficher la position de la légende de la fenêtre associée. Pour travailler avec la base, utilisez le [GetBase](../mfc/reference/cspinbuttonctrl-class.md#getbase) et [SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase) fonctions membres.  
  
-   **Amis fenêtre** vous pouvez définir de façon dynamique la fenêtre associée. Pour interroger ou modifier le contrôle qui est la fenêtre associée, utilisez le [fonctions membres GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) et [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) fonctions membres.  
  
-   **Position** vous pouvez interroger et modifier la position. Pour travailler directement avec la position, utilisez la [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) et [fonction membre SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) fonctions membres. Étant donné que la légende du contrôle associé peut avoir changé (par exemple, dans le cas agit d’un contrôle d’édition), `GetPos` récupère la légende en cours et ajuste la position en conséquence.  
  
-   **Plage** vous pouvez modifier les positions minimales et maximales pour le bouton de sélection numérique. Par défaut, la valeur maximale est définie sur 0, et la valeur minimale est définie à 100. Étant donné que la valeur maximale par défaut est inférieure à la valeur minimale par défaut, les actions des boutons fléchés sont inversées. En règle générale, vous allez définir la plage à l’aide de la [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) fonction membre. Pour interroger la plage, utilisez [GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

