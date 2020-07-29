---
title: Opérateurs de casting
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: 606e8b159bb7bdb7527d33a5211cb33a26913754
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221820"
---
# <a name="casting-operators"></a>Opérateurs de casting

Il existe plusieurs opérateurs de cast spécifiques au langage C++. Ces opérateurs ont pour but de supprimer une partie de l'ambiguïté et du risque inhérents aux casts en langage C de style ancien. Ces opérateurs sont :

- [dynamic_cast](../cpp/dynamic-cast-operator.md) Utilisé pour la conversion des types polymorphes.

- [static_cast](../cpp/static-cast-operator.md) Utilisé pour la conversion des types des non polymorphes.

- [const_cast](../cpp/const-cast-operator.md) Utilisé pour supprimer les **`const`** **`volatile`** attributs, et **`__unaligned`** .

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) Utilisé pour la réinterprétation simple de bits.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) Utilisé en C++/CLI pour produire du code MSIL vérifiable.

Utilisez **`const_cast`** et **`reinterpret_cast`** , en dernier recours, puisque ces opérateurs présentent les mêmes dangers que les anciens casts de style. Ils sont néanmoins encore nécessaires pour remplacer complètement les casts de style ancien.

## <a name="see-also"></a>Voir aussi

[Cast](../cpp/casting.md)
