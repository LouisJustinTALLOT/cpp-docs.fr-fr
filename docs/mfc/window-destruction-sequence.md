---
description: 'En savoir plus sur : séquence de destruction de fenêtre'
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
ms.openlocfilehash: 2ba60f1dcd3668a754bbe4384a6c8cf6b4d541d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207681"
---
# <a name="window-destruction-sequence"></a>Séquence de destruction de fenêtres

Dans l’infrastructure MFC, lorsque l’utilisateur ferme la fenêtre frame, le gestionnaire [OnClose](../mfc/reference/cwnd-class.md#onclose) par défaut de la fenêtre appelle [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La dernière fonction membre appelée lorsque la fenêtre Windows est détruite est [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), qui effectue un nettoyage, appelle la fonction membre [par défaut](../mfc/reference/cwnd-class.md#default) pour effectuer le nettoyage de Windows et enfin appelle la fonction membre virtuelle [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). L’implémentation [CFrameWnd](../mfc/reference/cframewnd-class.md) de `PostNcDestroy` supprime l’objet fenêtre C++.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Allocation et libération de la mémoire de fenêtre](../mfc/allocating-and-deallocating-window-memory.md)

- [Détachement d'un objet CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Voir aussi

[Destruction d’objets fenêtres](../mfc/destroying-window-objects.md)
