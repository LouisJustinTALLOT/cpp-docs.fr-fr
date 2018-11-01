---
title: 'Opérateurs plus et de négation unaires : + et -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: c1d5fc926b396f1ec44b9e44e79721e2ca4a0908
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580906"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Opérateurs plus et de négation unaires : + et -

## <a name="syntax"></a>Syntaxe

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ (opérateur)

Le résultat de l’opérateur plus unaire (**+**) est la valeur de son opérande. L’opérande de l’opérateur plus unaire doit être d’un type arithmétique.

La promotion d’un intégral est exécutée sur des opérandes intégraux. Le type résultant est le type vers lequel l’opérande est promu. Par conséquent, l’expression `+ch`, où `ch` est de type **char**, dans le type des résultats **int**; la valeur est inchangée. Consultez [Conversions Standard](standard-conversions.md) pour plus d’informations sur la façon dont la promotion est effectuée.

## <a name="--operator"></a>- (opérateur)

L’opérateur de négation unaire (**-**) produit la partie négative de son opérande. L’opérande de l’opérateur de négation unaire doit être un type arithmétique.

La promotion intégrale est exécutée sur les opérandes intégraux et le type résultant est le type vers lequel l’opérande est promu. Consultez [Conversions Standard](standard-conversions.md) pour plus d’informations sur la façon dont la promotion est effectuée.

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

La négation unaire des quantités non signées est exécutée en soustrayant la valeur de l’opérande de 2^n, n correspondant au nombre de bits dans un objet du type non signé donné.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)