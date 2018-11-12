---
title: Touches d'accès rapide spécifiques aux threads
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 4b393fe1af060a4b235162ce8cdfd94a1a391085
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594153"
---
# <a name="thread-specific-hot-keys"></a>Touches d'accès rapide spécifiques aux threads

Une application définit une touche d’accès rapide spécifiques aux threads ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) à l’aide de la Windows `RegisterHotKey` (fonction). Lorsque l’utilisateur appuie sur une touche d’accès rapide spécifiques aux threads, Windows publie une [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) message au début de la file d’attente des messages d’un thread particulier. Le message WM_HOTKEY contient le code de touche virtuelle, état du décalage et défini par l’utilisateur ID de la touche d’accès rapide spécifique qui a été enfoncée. Pour obtenir la liste de codes de touches virtuelles, consultez Winuser.h. Pour plus d’informations sur cette méthode, consultez [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).

Notez que l’état du décalage d’indicateurs utilisé dans l’appel à `RegisterHotKey` ne sont pas les mêmes que ceux retournés par la [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) fonction membre ; vous devrez traduire ces indicateurs avant d’appeler `RegisterHotKey`.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

