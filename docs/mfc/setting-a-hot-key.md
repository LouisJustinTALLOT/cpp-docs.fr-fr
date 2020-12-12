---
description: 'En savoir plus sur : définition d’une touche d’accès rapide'
title: Définition d'une touche d'accès rapide
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: fa713be2d478eb18b11dca27558656e5e6993076
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217183"
---
# <a name="setting-a-hot-key"></a>Définition d'une touche d'accès rapide

Votre application peut utiliser les informations fournies par un contrôle de touche[](../mfc/reference/chotkeyctrl-class.md)d’accès rapide de l’une des deux manières suivantes :

- Configurez une touche d’accès rapide globale pour activer une fenêtre qui n’est pas enfant en envoyant un message [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) à la fenêtre à activer.

- Configurez une touche d’accès rapide spécifique au thread en appelant la fonction Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
