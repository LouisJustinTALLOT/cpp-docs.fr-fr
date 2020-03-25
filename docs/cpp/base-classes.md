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
ms.openlocfilehash: 50bddef3ea1ee1462d8cf115c0980270c8deab25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181471"
---
# <a name="base-classes"></a>Classes de base

Le processus d'héritage crée une classe dérivée qui se compose des membres des classes de base et tous les nouveaux membres ajoutés par la classe dérivée. Dans un héritage multiple, il est possible de construire un graphique d'héritage, où la même classe de base fait partie de plusieurs classes dérivées. L'illustration suivante montre ce graphique.

![Plusieurs instances d’une classe de base](../cpp/media/vc38xn1.gif "Plusieurs instances d'une même classe de base") <br/>
Plusieurs instances d’une même classe de base

Dans l'illustration, les représentations illustrées des composants de `CollectibleString` et de `CollectibleSortable` sont affichés. Toutefois, la classe de base, `Collectible`, est dans `CollectibleSortableString` via le chemin d’accès `CollectibleString` et le chemin d’accès `CollectibleSortable`. Pour éliminer cette redondance, ces classes peuvent être déclarées comme classes de base virtuelles lorsqu'elles sont héritées.
