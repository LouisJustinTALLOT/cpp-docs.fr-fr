---
title: Allocation et libération de mémoire Windows | Microsoft Docs
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
ms.openlocfilehash: 149a8e860913515551fc85be9b49675856d7e129
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415189"
---
# <a name="allocating-and-deallocating-window-memory"></a>Allocation et libération de la mémoire Windows

N’utilisez pas le C++ **supprimer** opérateur pour détruire une fenêtre frame ou une vue. Au lieu de cela, appelez le `CWnd` fonction membre `DestroyWindow`. Fenêtres frame, par conséquent, doivent être alloués sur le tas avec l’opérateur **nouveau**. Soyez prudent lors de l’allocation de fenêtres frame sur le frame de pile ou dans le monde entier. Autres fenêtres doivent être alloués sur le frame de pile chaque fois que possible.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Création de fenêtres](../mfc/creating-windows.md)

- [Séquence de destruction de fenêtres](../mfc/window-destruction-sequence.md)

- [Détachement d’un objet CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Voir aussi

[Destruction d’objets fenêtres](../mfc/destroying-window-objects.md)

