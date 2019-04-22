---
title: Opérateurs de casting
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: e2ac8e9079b1d30dca077363bbb6cef35960902e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768950"
---
# <a name="casting-operators"></a>Opérateurs de casting

Il existe plusieurs opérateurs de cast spécifiques au langage C++. Ces opérateurs ont pour but de supprimer une partie de l'ambiguïté et du risque inhérents aux casts en langage C de style ancien. Ces opérateurs sont :

- [dynamic_cast](../cpp/dynamic-cast-operator.md) utilisé pour la conversion des types polymorphes.

- [static_cast](../cpp/static-cast-operator.md) utilisé pour la conversion des types non polymorphes.

- [const_cast](../cpp/const-cast-operator.md) permet de supprimer le **const**, **volatile**, et **__unaligned** attributs.

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) utilisé pour la réinterprétation simple des bits.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) utilisé dans C++/CLI pour produire du code MSIL vérifiable.

Utilisez **const_cast** et **reinterpret_cast** en dernier recours, car ces opérateurs présentent les mêmes risques que les casts de style ancien. Ils sont néanmoins encore nécessaires pour remplacer complètement les casts de style ancien.

## <a name="see-also"></a>Voir aussi

[Cast](../cpp/casting.md)