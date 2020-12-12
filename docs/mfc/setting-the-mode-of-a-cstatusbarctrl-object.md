---
description: 'En savoir plus sur : définition du mode d’un objet CStatusBarCtrl'
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
ms.openlocfilehash: 46a87c17c68059e1d12476f4963f159cd2915824
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217105"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Définition du mode d'un objet CStatusBarCtrl

Il existe deux modes pour un `CStatusBarCtrl` objet : simple et simple. Dans la plupart des cas, votre contrôle de barre d’État comportera une ou plusieurs parties, ainsi que du texte et peut-être une icône ou des icônes. C’est ce que l’on appelle le mode non simple. Pour plus d’informations sur ce mode, consultez [initialisation des parties d’un objet CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Toutefois, dans certains cas, vous ne devez afficher qu’une seule ligne de texte. Dans ce cas, le mode simple est suffisant pour répondre à vos besoins. Pour modifier le mode de l' `CStatusBarCtrl` objet pour qu’il soit simple, appelez la fonction membre [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) . Une fois que le contrôle de barre d’État est en mode simple, définissez le texte en appelant la `SetText` fonction membre, en passant 255 comme valeur pour le paramètre *nPane* .

Vous pouvez utiliser la fonction [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) pour déterminer le mode `CStatusBarCtrl` dans lequel se trouve l’objet.

> [!NOTE]
> Si l’objet de barre d’état passe de non simple à simple, ou vice versa, la fenêtre est immédiatement redessinée et, le cas échéant, toutes les parties définies sont restaurées automatiquement.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
