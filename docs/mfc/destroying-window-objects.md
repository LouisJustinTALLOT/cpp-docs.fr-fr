---
title: Destruction d’objets fenêtres | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 704122f028cd744f0ce064f0153825830144d5b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401639"
---
# <a name="destroying-window-objects"></a>Destruction d’objets fenêtres

Être vigilant avec vos propres fenêtres enfants pour détruire l’objet fenêtre C++ lorsque l’utilisateur a terminé avec la fenêtre. Si ces objets ne sont pas détruits, votre application ne récupérera pas leur mémoire. Heureusement, le framework gère la destruction de fenêtres, ainsi que la création de fenêtres frame, les vues et les boîtes de dialogue. Si vous créez des fenêtres supplémentaires, vous êtes responsable de leur destruction.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Séquence de destruction de fenêtres](../mfc/window-destruction-sequence.md)

- [Allocation et libération de mémoire Windows](../mfc/allocating-and-deallocating-window-memory.md)

- [Détachement d’un objet CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Séquence de création d’une fenêtre générale](../mfc/general-window-creation-sequence.md)

- [Destruction des fenêtres frame](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)

