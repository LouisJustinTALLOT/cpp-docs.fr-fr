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
ms.openlocfilehash: 60f99c01c7a311c31602269b49efaf434d16827a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267795"
---
# <a name="allocating-and-deallocating-window-memory"></a>Allocation et libération de la mémoire Windows

N’utilisez pas le C++ **supprimer** opérateur pour détruire une fenêtre frame ou une vue. Au lieu de cela, appelez le `CWnd` fonction membre `DestroyWindow`. Fenêtres frame, par conséquent, doivent être alloués sur le tas avec l’opérateur **nouveau**. Soyez prudent lors de l’allocation de fenêtres frame sur le frame de pile ou dans le monde entier. Autres fenêtres doivent être alloués sur le frame de pile chaque fois que possible.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Création de fenêtres](../mfc/creating-windows.md)

- [Séquence de destruction de fenêtres](../mfc/window-destruction-sequence.md)

- [Détachement d’un objet CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Voir aussi

[Destruction d’objets fenêtres](../mfc/destroying-window-objects.md)
