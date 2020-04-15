---
title: Doubles interfaces et événements
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 4ce5048c25bd55feb0f1eb20fc04ec6bfeead746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319606"
---
# <a name="dual-interfaces-and-events"></a>Doubles interfaces et événements

Bien qu’il soit possible de concevoir une interface d’événement comme un double, il ya un certain nombre de bonnes raisons de conception de ne pas le faire. La raison fondamentale est que la source de l’événement ne `Invoke`sera le feu de l’événement via le vtable ou via , pas les deux. Si la source de l’événement déclenche l’événement comme un appel de méthode vtable directe, les `IDispatch` méthodes ne seront jamais utilisées et il est clair que l’interface aurait dû être une interface vtable pure. Si la source de l’événement `Invoke`déclenche l’événement comme un appel à , les méthodes vtable ne sera jamais utilisé et il est clair que l’interface aurait dû être un dispinterface. Si vous définissez vos interfaces d’événement comme des duels, vous devrez implémenter des clients une partie d’une interface qui ne sera jamais utilisée.

> [!NOTE]
> Cet argument ne s’applique pas aux interfaces doubles, en général. Du point de vue de la mise en œuvre, les duels sont une façon rapide, pratique et bien soutenue de mettre en œuvre des interfaces accessibles à un large éventail de clients.

Il y a d’autres raisons d’éviter les interfaces à double événement; ni Visual Basic ni Internet Explorer ne les soutiennent.

## <a name="see-also"></a>Voir aussi

[Double interfaces et ATL](../atl/dual-interfaces-and-atl.md)
