---
title: Touches d'accès rapide spécifiques aux threads
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 49bac6ac357924c26f131bbd8e1092cd74514167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511140"
---
# <a name="thread-specific-hot-keys"></a>Touches d'accès rapide spécifiques aux threads

Une application définit une touche d’accès rapide spécifique à un thread ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) à `RegisterHotKey` l’aide de la fonction Windows. Quand l’utilisateur appuie sur une touche d’accès rapide spécifique à un thread, Windows publie un message [WM_HOTKEY](/windows/win32/inputdev/wm-hotkey) au début de la file d’attente de messages d’un thread particulier. Le message WM_HOTKEY contient le code de la touche virtuelle, l’état de décalage et l’ID défini par l’utilisateur de la touche d’accès rapide spécifique qui a été enfoncée. Pour obtenir la liste des codes de touches virtuelles standard, consultez Winuser. h. Pour plus d’informations sur cette méthode, consultez [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

Notez que les indicateurs d’état de décalage utilisés dans l' `RegisterHotKey` appel à ne sont pas les mêmes que ceux retournés par la fonction membre [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) ; vous devrez traduire ces `RegisterHotKey`indicateurs avant d’appeler.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
