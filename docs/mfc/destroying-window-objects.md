---
description: 'En savoir plus sur : destruction d’objets fenêtres'
title: Destruction d'objets fenêtres
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: c2837ba6b9f568d7f6ab0175ae3ad99c31ccdc7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327818"
---
# <a name="destroying-window-objects"></a>Destruction d'objets fenêtres

Vous devez veiller à ce que vos propres fenêtres enfants détruisent l’objet fenêtre C++ lorsque l’utilisateur a terminé la fenêtre. Si ces objets ne sont pas détruits, votre application ne récupérera pas leur mémoire. Heureusement, l’infrastructure gère la destruction de la fenêtre, ainsi que la création de fenêtres Frame, de vues et de boîtes de dialogue. Si vous créez des fenêtres supplémentaires, vous êtes chargé de les détruire.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Séquence de destruction de fenêtres](window-destruction-sequence.md)

- [Allocation et libération de la mémoire de fenêtre](allocating-and-deallocating-window-memory.md)

- [Détachement d'un objet CWnd de son HWND](detaching-a-cwnd-from-its-hwnd.md)

- [Séquence de création de fenêtre générale](general-window-creation-sequence.md)

- [Destruction des fenêtres d’image](destroying-frame-windows.md)

## <a name="see-also"></a>Voir aussi

[Objets de fenêtre](window-objects.md)
