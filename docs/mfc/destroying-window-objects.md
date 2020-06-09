---
title: Destruction d'objets fenêtres
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 22b483c1005931b229453ae229935c0e716ab726
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621864"
---
# <a name="destroying-window-objects"></a>Destruction d'objets fenêtres

Vous devez veiller à ce que vos propres fenêtres enfants détruisent l’objet fenêtre C++ lorsque l’utilisateur a terminé la fenêtre. Si ces objets ne sont pas détruits, votre application ne récupérera pas leur mémoire. Heureusement, l’infrastructure gère la destruction de la fenêtre, ainsi que la création de fenêtres Frame, de vues et de boîtes de dialogue. Si vous créez des fenêtres supplémentaires, vous êtes chargé de les détruire.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Séquence de destruction de fenêtres](window-destruction-sequence.md)

- [Allocation et libération de la mémoire Windows](allocating-and-deallocating-window-memory.md)

- [Détachement d’un CWnd de son HWND](detaching-a-cwnd-from-its-hwnd.md)

- [Séquence de création de fenêtre générale](general-window-creation-sequence.md)

- [Destruction des fenêtres d’image](destroying-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Objets fenêtres](window-objects.md)
