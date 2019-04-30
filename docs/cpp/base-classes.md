---
title: Classes de base
ms.date: 11/19/2018
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
ms.openlocfilehash: 59c474f54ea439acf83cf6923eba6e167901dd37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392407"
---
# <a name="base-classes"></a>Classes de base

Le processus d'héritage crée une classe dérivée qui se compose des membres des classes de base et tous les nouveaux membres ajoutés par la classe dérivée. Dans un héritage multiple, il est possible de construire un graphique d'héritage, où la même classe de base fait partie de plusieurs classes dérivées. L'illustration suivante montre ce graphique.

![Plusieurs instances d’une classe de base](../cpp/media/vc38xn1.gif "plusieurs instances d’une classe de base") <br/>
Plusieurs instances d’une classe de base unique

Dans l'illustration, les représentations illustrées des composants de `CollectibleString` et de `CollectibleSortable` sont affichés. Toutefois, la classe de base, `Collectible`, est dans `CollectibleSortableString` via le chemin d’accès `CollectibleString` et le chemin d’accès `CollectibleSortable`. Pour éliminer cette redondance, ces classes peuvent être déclarées comme classes de base virtuelles lorsqu'elles sont héritées.