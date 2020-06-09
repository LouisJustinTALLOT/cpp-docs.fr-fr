---
title: Allocation et libération de la mémoire Windows
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: 02546559183d0e14973bc2e5ccb26a4570a39b1e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623267"
---
# <a name="allocating-and-deallocating-window-memory"></a>Allocation et libération de la mémoire Windows

N’utilisez pas l’opérateur C++ **Delete** pour détruire une fenêtre frame ou une vue. Au lieu de cela, appelez la `CWnd` fonction membre `DestroyWindow` . Les fenêtres Frame, par conséquent, doivent être allouées sur le tas avec l’opérateur **New**. Soyez prudent lorsque vous allouez des fenêtres Frame sur le frame de pile ou globalement. Dans la mesure du possible, d’autres fenêtres doivent être allouées sur le frame de pile.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres](creating-windows.md)

- [Séquence de destruction de fenêtres](window-destruction-sequence.md)

- [Détachement d’un CWnd de son HWND](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Voir aussi

[Destruction d'objets fenêtres](destroying-window-objects.md)
