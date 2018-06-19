---
title: Allocation et libération de mémoire (fenêtre) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1364b4d29e2ccd2c9563359716eba6880df5436
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341457"
---
# <a name="allocating-and-deallocating-window-memory"></a>Allocation et libération de la mémoire Windows
N’utilisez pas le C++ **supprimer** opérateur pour détruire une fenêtre frame ou une vue. Au lieu de cela, appelez le `CWnd` fonction membre `DestroyWindow`. Par conséquent, les fenêtres frame, doivent être allouées sur le tas avec l’opérateur **nouveau**. Soyez prudent lors de l’allocation de fenêtres frames sur le frame de pile ou globalement. Autres fenêtres doivent être alloués sur le frame de pile chaque fois que possible.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Création de fenêtres](../mfc/creating-windows.md)  
  
-   [Séquence de destruction de fenêtres](../mfc/window-destruction-sequence.md)  
  
-   [Détachement d’un objet CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Destruction d’objets fenêtres](../mfc/destroying-window-objects.md)

