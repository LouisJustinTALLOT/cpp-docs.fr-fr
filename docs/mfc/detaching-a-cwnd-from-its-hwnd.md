---
description: 'En savoir plus sur : détachement d’un CWnd de son HWND'
title: Détachement d'un objet CWnd de son HWND
ms.date: 11/04/2016
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: a3bb1c50b769724ff9ea0f7cdcd2d1fa92cb3a84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327801"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Détachement d'un objet CWnd de son HWND

Si vous avez besoin de contourner la `HWND` relation objet, MFC fournit une autre `CWnd` fonction membre, [Detach](reference/cwnd-class.md#detach), qui déconnecte l’objet fenêtre C++ de la fenêtre Windows. Cela empêche le destructeur de détruire la fenêtre Windows lorsque l’objet est détruit.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres](creating-windows.md)

- [Séquence de destruction de fenêtres](window-destruction-sequence.md)

- [Allocation et libération de la mémoire de fenêtre](allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Voir aussi

[Objets de fenêtre](window-objects.md)
