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
ms.openlocfilehash: 2e0484698654cd14f22a92be76a80f71c0f9adf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621844"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Détachement d'un objet CWnd de son HWND

Si vous avez besoin de contourner la `HWND` relation objet, MFC fournit une autre `CWnd` fonction membre, [Detach](reference/cwnd-class.md#detach), qui déconnecte l’objet fenêtre C++ de la fenêtre Windows. Cela empêche le destructeur de détruire la fenêtre Windows lorsque l’objet est détruit.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres](creating-windows.md)

- [Séquence de destruction de fenêtres](window-destruction-sequence.md)

- [Allocation et libération de la mémoire Windows](allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Voir aussi

[Objets fenêtres](window-objects.md)
