---
title: Touches d’accès rapide globales | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2ef1e2135ebd780938fb0ed194a93058fd010f6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209152"
---
# <a name="global-hot-keys"></a>Touches globales d'accès rapide
Une touche d’accès rapide est associée à une fenêtre non-enfant particulière. Il permet à l’utilisateur Activer la fenêtre à partir de n’importe quelle partie du système. Une application définit une touche d’accès rapide pour une fenêtre particulière en envoyant le [message WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) message à cette fenêtre. Par exemple, si `m_HotKeyCtrl` est la [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) objet et `pMainWnd` est un pointeur vers la fenêtre à activer lorsque vous appuyez sur la touche d’accès rapide, vous pouvez utiliser le code suivant pour associer la touche d’accès rapide spécifiée dans le contrôle avec la fenêtre vers laquelle pointe `pMainWnd`.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]  
  
 Chaque fois que l’utilisateur appuie sur une touche d’accès rapide, la fenêtre spécifiée reçoit un [WM_SYSCOMMAND](/windows/desktop/menurc/wm-syscommand) message spécifie **SC_HOTKEY** en tant que le type de la commande. Ce message Active également la fenêtre qui le reçoit. Étant donné que ce message n’inclut pas toutes les informations sur la clé exacte qui a été enfoncée, à l’aide de cette méthode ne permet de pas faire la distinction entre différentes touches d’accès rapide qui peuvent être attachées à la même fenêtre. La touche d’accès rapide reste valide jusqu'à ce que l’application qui a envoyé **message WM_SETHOTKEY** se termine.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

