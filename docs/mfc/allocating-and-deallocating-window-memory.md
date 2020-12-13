---
description: 'En savoir plus sur : l’allocation et la libération de la mémoire Windows'
title: Allocation et libération de la mémoire Windows
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: 7648914289babffdfb5195f1ec53cd736e26892c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343716"
---
# <a name="allocating-and-deallocating-window-memory"></a>Allocation et libération de la mémoire Windows

N’utilisez pas l' **`delete`** opérateur C++ pour détruire une fenêtre frame ou une vue. Au lieu de cela, appelez la `CWnd` fonction membre `DestroyWindow` . Les fenêtres Frame, par conséquent, doivent être allouées sur le tas avec l’opérateur **`new`** . Soyez prudent lorsque vous allouez des fenêtres Frame sur le frame de pile ou globalement. Dans la mesure du possible, d’autres fenêtres doivent être allouées sur le frame de pile.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres](creating-windows.md)

- [Séquence de destruction de fenêtres](window-destruction-sequence.md)

- [Détachement d'un objet CWnd de son HWND](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Voir aussi

[Destruction d’objets fenêtres](destroying-window-objects.md)
