---
title: Définition d'une touche d'accès rapide
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a77aad4881acd04c6dabb6dce90acc01be2cfbc8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281276"
---
# <a name="setting-a-hot-key"></a>Définition d'une touche d'accès rapide

Votre application peut utiliser les informations fournies par une touche d’accès rapide ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) contrôle de deux manières :

- Configurer une touche d’accès rapide pour activer une fenêtre non-enfant en envoyant un [message WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) message dans la fenêtre à activer.

- Définissez une touche d’accès rapide spécifiques aux threads en appelant la fonction Windows [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
