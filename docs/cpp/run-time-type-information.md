---
title: Informations de type au moment de l'exécution
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
ms.openlocfilehash: b6d3652539572f094d0e7139e6672402341c956d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232233"
---
# <a name="run-time-type-information"></a>Informations de type au moment de l'exécution

Les informations de type au moment de l'exécution (RTTI) sont un mécanisme qui permet de déterminer le type d'un objet pendant l'exécution du programme. RTTI a été ajouté au langage C++ car de nombreux fournisseurs de bibliothèques de classes implémentaient cette fonctionnalité eux-mêmes. Cela provoquait des incompatibilités entre les bibliothèques. Par conséquent, il est devenu évident que la prise en charge des informations de type au moment de l'exécution s'avérait nécessaire au niveau du langage.

Pour des raisons de simplicité, cette discussion sur RTTI se limite presque exclusivement aux pointeurs. Toutefois, les concepts présentés également s'appliquent également aux références.

Il existe trois principaux éléments de langage C++ se rapportant aux informations de type au moment de l'exécution :

- Opérateur [dynamic_cast](../cpp/dynamic-cast-operator.md) .

   Utilisé pour la conversion des types polymorphes.

- Opérateur [typeid](../cpp/typeid-operator.md) .

   Utilisé pour identifier le type exact d'un objet.

- Classe [type_info](../cpp/type-info-class.md) .

   Utilisé pour contenir les informations de type retournées par l' **`typeid`** opérateur.

## <a name="see-also"></a>Voir aussi

[Cast](../cpp/casting.md)
