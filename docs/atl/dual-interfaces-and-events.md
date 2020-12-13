---
description: 'En savoir plus sur : interfaces doubles et événements'
title: Interfaces doubles et événements
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 231df7a0dfc8376acd6a9a0f9d85d0ed68fdd0b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153025"
---
# <a name="dual-interfaces-and-events"></a>Interfaces doubles et événements

Bien qu’il soit possible de concevoir une interface d’événement en tant que double, il existe un certain nombre de bonnes raisons de conception. La raison fondamentale est que la source de l’événement déclenchera uniquement l’événement via la vtable ou via `Invoke` , et non les deux. Si la source d’événement déclenche l’événement en tant qu’appel de méthode vtable directe, les `IDispatch` méthodes ne seront jamais utilisées et il est clair que l’interface aurait dû être une interface vtable pure. Si la source de l’événement déclenche l’événement en tant qu’appel à `Invoke` , les méthodes vtable ne seront jamais utilisées et il est clair que l’interface aurait dû être une dispinterface. Si vous définissez vos interfaces d’événements comme étant doubles, vous devrez demander aux clients d’implémenter une partie d’une interface qui ne sera jamais utilisée.

> [!NOTE]
> Cet argument ne s’applique pas aux interfaces doubles, en général. Du point de vue de la mise en œuvre, les doubles sont un moyen rapide, pratique et bien pris en charge d’implémenter des interfaces qui sont accessibles à un large éventail de clients.

Il existe d’autres raisons d’éviter les interfaces d’événements doubles ; ni Visual Basic ni Internet Explorer ne les prennent en charge.

## <a name="see-also"></a>Voir aussi

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)
