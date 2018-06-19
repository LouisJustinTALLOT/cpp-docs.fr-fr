---
title: Définition d’une clé à chaud | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3987ddee98ae35e02a181e38cd71f181801aeb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379643"
---
# <a name="setting-a-hot-key"></a>Définition d'une touche d'accès rapide
Votre application peut utiliser les informations fournies par une touche d’accès rapide ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) contrôle de deux manières :  
  
-   Définir une touche d’accès rapide pour activer une fenêtre non-enfant en envoyant un [message WM_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) message dans la fenêtre d’être activées.  
  
-   Définissez une touche d’accès rapide spécifiques aux threads en appelant la fonction Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

