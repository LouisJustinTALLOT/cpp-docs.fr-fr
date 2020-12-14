---
description: En savoir plus sur les touches d’accès rapide Thread-Specific
title: Touches d'accès rapide spécifiques aux threads
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 352d39b801d7e6dcecfbf27d841d6977d3666138
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216117"
---
# <a name="thread-specific-hot-keys"></a>Touches d'accès rapide spécifiques aux threads

Une application définit une touche d’accès rapide spécifique à un thread ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) à l’aide de la `RegisterHotKey` fonction Windows. Quand l’utilisateur appuie sur une touche d’accès rapide spécifique à un thread, Windows publie un [WM_HOTKEY](/windows/win32/inputdev/wm-hotkey) message au début de la file d’attente de messages d’un thread particulier. Le message WM_HOTKEY contient le code de la touche virtuelle, l’état de décalage et l’ID défini par l’utilisateur de la touche d’accès rapide spécifique qui a été enfoncée. Pour obtenir la liste des codes de touches virtuelles standard, consultez Winuser. h. Pour plus d’informations sur cette méthode, consultez [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

Notez que les indicateurs d’état de décalage utilisés dans l’appel à `RegisterHotKey` ne sont pas les mêmes que ceux retournés par la fonction membre [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) ; vous devrez traduire ces indicateurs avant d’appeler `RegisterHotKey` .

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
