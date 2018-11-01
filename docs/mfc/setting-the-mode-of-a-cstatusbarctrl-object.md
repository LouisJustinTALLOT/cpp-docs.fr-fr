---
title: Définition du mode d'un objet CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: 0009f73f11b1a3c57f5001269f34834c22b045c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655251"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Définition du mode d'un objet CStatusBarCtrl

Il existe deux modes pour un `CStatusBarCtrl` objet : simple et non simple. Dans la plupart des cas, votre contrôle de barre d’état aura une ou plusieurs parties, ainsi que le texte et éventuellement une icône ou d’icônes. Il s’agit du mode non simple. Pour plus d’informations sur ce mode, consultez [initialisation des parties d’un objet CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Toutefois, il existe des cas où vous devez uniquement afficher une seule ligne de texte. Dans ce cas, le mode simple est suffisant pour vos besoins. Pour modifier le mode de la `CStatusBarCtrl` objet simple, effectuez un appel à la [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) fonction membre. Une fois que le contrôle de barre d’état est en mode simple, définissez le texte en appelant le `SetText` fonction membre, en passant 255 comme valeur pour le *nPane* paramètre.

Vous pouvez utiliser la [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) fonction permettant de déterminer quel mode le `CStatusBarCtrl` objet se trouve dans.

> [!NOTE]
>  Si l’objet de barre d’état est en cours de modification à partir de non simple simple, ou vice versa, la fenêtre est immédiatement redessinée et, le cas échéant, toutes les parties définies sont automatiquement restaurés.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

