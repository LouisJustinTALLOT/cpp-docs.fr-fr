---
title: Touches d'accès rapide spécifiques aux threads
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 68c50ec5f29dab271f9af9abc50eb72ec15157e7
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893325"
---
# <a name="thread-specific-hot-keys"></a>Touches d'accès rapide spécifiques aux threads

Une application définit une touche d’accès rapide spécifiques aux threads ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) à l’aide de la Windows `RegisterHotKey` (fonction). Lorsque l’utilisateur appuie sur une touche d’accès rapide spécifiques aux threads, Windows publie une [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) message au début de la file d’attente des messages d’un thread particulier. Le message WM_HOTKEY contient le code de touche virtuelle, état du décalage et défini par l’utilisateur ID de la touche d’accès rapide spécifique qui a été enfoncée. Pour obtenir la liste de codes de touches virtuelles, consultez Winuser.h. Pour plus d’informations sur cette méthode, consultez [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

Notez que l’état du décalage d’indicateurs utilisé dans l’appel à `RegisterHotKey` ne sont pas les mêmes que ceux retournés par la [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) fonction membre ; vous devrez traduire ces indicateurs avant d’appeler `RegisterHotKey`.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

