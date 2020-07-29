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
ms.openlocfilehash: de90cd2068f9b701167a340fe0b335e2a6c93102
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225798"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Opérateurs plus et de négation unaires : + et -

## <a name="syntax"></a>Syntaxe

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ (opérateur)

Le résultat de l’opérateur plus unaire ( **+** ) est la valeur de son opérande. L'opérande de l'opérateur plus unaire doit être d'un type arithmétique.

La promotion d’un intégral est exécutée sur des opérandes intégraux. Le type résultant est le type vers lequel l'opérande est promu. Ainsi, l’expression `+ch` , où `ch` est de type **`char`** , produit le type **`int`** ; la valeur n’est pas modifiée. Pour plus d’informations sur la façon dont la promotion est effectuée, consultez [conversions standard](standard-conversions.md) .

## <a name="--operator"></a>- (opérateur)

L’opérateur de négation unaire ( **-** ) produit la valeur négative de son opérande. L'opérande de l'opérateur de négation unaire doit être un type arithmétique.

La promotion intégrale est exécutée sur les opérandes intégraux et le type résultant est le type vers lequel l'opérande est promu. Pour plus d’informations sur la façon dont la promotion est effectuée, consultez [conversions standard](standard-conversions.md) .

**Spécifique à Microsoft**

La négation unaire des quantités non signées est exécutée en soustrayant la valeur de l'opérande de 2^n, n correspondant au nombre de bits dans un objet du type non signé donné.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
