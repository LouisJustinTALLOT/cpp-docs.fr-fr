---
title: Définition du mode d'un objet CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: e09a7bd274c44df2da48bbc007a95802fadd8cf0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365415"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Définition du mode d'un objet CStatusBarCtrl

Il existe deux `CStatusBarCtrl` modes pour un objet : simple et nonimple. Dans la majorité des cas, votre contrôle de barre d’état aura une ou plusieurs parties, avec le texte et peut-être une icône ou des icônes. C’est ce qu’on appelle le mode nonimple. Pour plus d’informations sur ce mode, voir [Initializing the Parts of a CStatusBarCtrl Object](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Cependant, il ya des cas où vous avez seulement besoin d’afficher une seule ligne de texte. Dans ce cas, le mode simple est suffisant pour vos besoins. Pour changer le `CStatusBarCtrl` mode de l’objet en simple, faites un appel à la fonction [membre SetSimple.](../mfc/reference/cstatusbarctrl-class.md#setsimple) Une fois que le contrôle de barre d’état est en mode simple, définissez le texte en appelant la `SetText` fonction de membre, en passant 255 comme valeur pour le paramètre *nPane.*

Vous pouvez utiliser la fonction [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) pour déterminer dans quel mode l’objet `CStatusBarCtrl` se trouve.

> [!NOTE]
> Si l’objet de barre d’état est changé de non-implantation à simple, ou vice versa, la fenêtre est immédiatement redessinée et, le cas échéant, toutes les pièces définies sont automatiquement restaurées.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
