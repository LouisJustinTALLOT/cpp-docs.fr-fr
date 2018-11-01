---
title: Détachement d'un objet CWnd de son HWND
ms.date: 11/04/2016
f1_keywords:
- CWnd
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: fe4d9efa6adcec51d5944755e4a8abb1cc0784e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653971"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Détachement d'un objet CWnd de son HWND

Si vous avez besoin de contourner l’objet -`HWND` relation, MFC fournit une autre `CWnd` fonction membre, [détachement](../mfc/reference/cwnd-class.md#detach), qui déconnecte l’objet fenêtre C++ à partir de la fenêtre de Windows. Cela empêche le destructeur de détruire la fenêtre Windows quand l’objet est détruit.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Création de fenêtres](../mfc/creating-windows.md)

- [Séquence de destruction de fenêtres](../mfc/window-destruction-sequence.md)

- [Allocation et libération de mémoire Windows](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)

