---
title: Séquence de destruction de fenêtres
ms.date: 11/04/2016
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
ms.openlocfilehash: d4592e6ac0077d6bc335b50f2d67b140402b4fe2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287659"
---
# <a name="window-destruction-sequence"></a>Séquence de destruction de fenêtres

Dans l’infrastructure MFC, lorsque l’utilisateur ferme la fenêtre frame, la valeur par défaut de la fenêtre [OnClose](../mfc/reference/cwnd-class.md#onclose) appels du gestionnaire [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). Est la dernière fonction membre appelée lorsque la fenêtre Windows est détruite [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), qui effectue un nettoyage, appelle le [par défaut](../mfc/reference/cwnd-class.md#default) membre de fonction pour effectuer un nettoyage de Windows et enfin appelle la fonction membre virtuelle [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). Le [CFrameWnd](../mfc/reference/cframewnd-class.md) implémentation de `PostNcDestroy` supprime l’objet fenêtre C++.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Allocation et libération de mémoire Windows](../mfc/allocating-and-deallocating-window-memory.md)

- [Détachement d’un objet CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Voir aussi

[Destruction d’objets fenêtres](../mfc/destroying-window-objects.md)
