---
title: Touches globales d'accès rapide
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 59918648ea24fd1e2a86ca786de3081cd6cca2df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508565"
---
# <a name="global-hot-keys"></a>Touches globales d'accès rapide

Une touche d’accès rapide globale est associée à une fenêtre non enfant particulière. Elle permet à l’utilisateur d’activer la fenêtre à partir de n’importe quelle partie du système. Une application définit une touche d’accès rapide globale pour une fenêtre particulière en envoyant le message [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) à cette fenêtre. Par exemple, si `m_HotKeyCtrl` est l’objet [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) et `pMainWnd` est un pointeur vers la fenêtre à activer quand la touche d’accès rapide est enfoncée, vous pouvez utiliser le code suivant pour associer la touche d’accès rapide spécifiée dans le contrôle à la fenêtre vers laquelle pointe `pMainWnd`.

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

Chaque fois que l’utilisateur appuie sur une touche d’accès rapide globale, la fenêtre spécifiée reçoit un message [WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand) qui spécifie **SC_HOTKEY** comme type de la commande. Ce message active également la fenêtre qui le reçoit. Étant donné que ce message n’inclut aucune information sur la touche exacte qui a été enfoncée, l’utilisation de cette méthode n’autorise pas la distinction entre les différentes touches d’accès rapide qui peuvent être attachées à la même fenêtre. La touche d’accès rapide reste valide jusqu’à ce que l’application qui a envoyé **WM_SETHOTKEY** se termine.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
