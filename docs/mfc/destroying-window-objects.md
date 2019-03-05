---
title: Destruction d'objets fenêtres
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: f50d198f9868a70d25370f6c1399b66efaa5490b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289843"
---
# <a name="destroying-window-objects"></a>Destruction d'objets fenêtres

Être vigilant avec vos propres fenêtres enfants pour détruire l’objet fenêtre C++ lorsque l’utilisateur a terminé avec la fenêtre. Si ces objets ne sont pas détruits, votre application ne récupérera pas leur mémoire. Heureusement, le framework gère la destruction de fenêtres, ainsi que la création de fenêtres frame, les vues et les boîtes de dialogue. Si vous créez des fenêtres supplémentaires, vous êtes responsable de leur destruction.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Séquence de destruction de fenêtres](../mfc/window-destruction-sequence.md)

- [Allocation et libération de mémoire Windows](../mfc/allocating-and-deallocating-window-memory.md)

- [Détachement d’un objet CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Séquence de création d’une fenêtre générale](../mfc/general-window-creation-sequence.md)

- [Destruction des fenêtres frame](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)
