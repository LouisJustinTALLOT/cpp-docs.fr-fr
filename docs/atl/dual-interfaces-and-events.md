---
title: Interfaces doubles et événements
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 01233edb63145d69d335349bb9dff91e6a4aca5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198263"
---
# <a name="dual-interfaces-and-events"></a>Interfaces doubles et événements

Bien qu’il soit possible de concevoir une interface d’événement comme un double, il existe de nombreuses raisons d’une bonne conception ne pas à le faire. La raison fondamentale est que la source de l’événement se déclenche uniquement l’événement via la vtable ou via `Invoke`, pas les deux. Si la source d’événement déclenche l’événement comme un appel de méthode vtable direct, le `IDispatch` méthodes ne seront jamais utilisées et il est clair que l’interface doit être une interface vtable pures. Si la source d’événement déclenche l’événement comme un appel à `Invoke`, les méthodes vtable ne seront jamais utilisés et il est clair que l’interface doit être une dispinterface. Si vous définissez vos interfaces d’événement comme duals, vous allez exiger que les clients implémentent une partie d’une interface qui ne sera jamais utilisée.

> [!NOTE]
>  Cet argument ne s’applique pas aux interfaces doubles, en général. Du point de vue de l’implémentation, les interfaces doubles sont un moyen rapide, facile et bien prise en charge de l’implémentation des interfaces qui sont accessibles à un large éventail de clients.

Il existe d’autres raisons pour éviter les interfaces d’événement doubles ; Visual Basic ni Internet Explorer ne les prennent en charge.

## <a name="see-also"></a>Voir aussi

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)
