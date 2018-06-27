---
title: Touches d’accès rapide spécifiques aux threads | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14da7f0e5b0adbe72b6705700c1e9298751bc345
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953607"
---
# <a name="thread-specific-hot-keys"></a>Touches d'accès rapide spécifiques aux threads
Une application définit une touche d’accès rapide spécifiques aux threads ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) à l’aide de Windows `RegisterHotKey` (fonction). Lorsque l’utilisateur appuie sur une touche d’accès rapide spécifiques aux threads, Windows publie une [WM_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) message au début de la file d’attente des messages d’un thread particulier. Le message WM_HOTKEY contient le code de touche virtuelle, état du décalage et défini par l’utilisateur ID de la touche d’accès rapide spécifique qui a été enfoncée. Pour obtenir la liste de codes de touches virtuelles, consultez Winuser.h. Pour plus d’informations sur cette méthode, consultez [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
 Notez que les indicateurs de l’état du décalage utilisé dans l’appel à `RegisterHotKey` ne sont pas les mêmes que ceux retournés par la [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) fonction membre ; vous devez traduire ces indicateurs avant d’appeler `RegisterHotKey`.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

