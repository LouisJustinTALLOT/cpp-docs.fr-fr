---
title: Détachement d'un objet CWnd de son HWND
ms.date: 11/04/2016
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: f7a6f97ba9f1dd3a928a5450c1a899ce09a4ac5f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446958"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Détachement d'un objet CWnd de son HWND

Si vous avez besoin de contourner la relation objet-`HWND`, MFC fournit une autre `CWnd` fonction membre, [Detach](../mfc/reference/cwnd-class.md#detach), qui déconnecte l' C++ objet Window de la fenêtre Windows. Cela empêche le destructeur de détruire la fenêtre Windows lorsque l’objet est détruit.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres](../mfc/creating-windows.md)

- [Séquence de destruction de fenêtre](../mfc/window-destruction-sequence.md)

- [Allocation et libération de la mémoire Windows](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)
