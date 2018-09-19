---
title: Classes de base | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a6d6494cc1ef371cfeb51647bc310a74ac68bfb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059196"
---
# <a name="base-classes"></a>Classes de base

Le processus d'héritage crée une classe dérivée qui se compose des membres des classes de base et tous les nouveaux membres ajoutés par la classe dérivée. Dans un héritage multiple, il est possible de construire un graphique d'héritage, où la même classe de base fait partie de plusieurs classes dérivées. L'illustration suivante montre ce graphique.

![Plusieurs instances d’une classe de base](../cpp/media/vc38xn1.gif "vc38XN1") plusieurs Instances d’une classe de Base unique

Dans l'illustration, les représentations illustrées des composants de `CollectibleString` et de `CollectibleSortable` sont affichés. Toutefois, la classe de base, `Collectible`, est dans `CollectibleSortableString` via le chemin d'accès `CollectibleString` et le chemin d'accès `CollectibleSortable`. Pour éliminer cette redondance, ces classes peuvent être déclarées comme classes de base virtuelles lorsqu'elles sont héritées.