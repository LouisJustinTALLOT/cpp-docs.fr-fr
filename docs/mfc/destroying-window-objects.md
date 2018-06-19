---
title: Destruction d’objets fenêtres | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3aacb01d945429bc36543f78e3635c39ef58223d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343374"
---
# <a name="destroying-window-objects"></a>Destruction d’objets fenêtres
Être vigilant avec vos propres fenêtres enfants pour détruire l’objet fenêtre C++ quand l’utilisateur a terminé avec la fenêtre. Si ces objets ne sont pas détruits, votre application ne récupère pas leur mémoire. Heureusement, le framework gère la destruction des fenêtres, ainsi que la création de boîtes de dialogue, des vues et fenêtres frame. Si vous créez des fenêtres supplémentaires, vous êtes responsable de leur destruction.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Séquence de destruction de fenêtres](../mfc/window-destruction-sequence.md)  
  
-   [Allocation et libération de mémoire (fenêtre)](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Détachement d’un objet CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Séquence de création d’une fenêtre générale](../mfc/general-window-creation-sequence.md)  
  
-   [Détruire des fenêtres frame](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objets fenêtre](../mfc/window-objects.md)

