---
description: 'En savoir plus sur les éléments suivants : assignation composée C'
title: Assignation composée C
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 73c47a506960d5c80e2a7f5693dcbacf770dbf02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211529"
---
# <a name="c-compound-assignment"></a>Assignation composée C

Les opérateurs d'assignation composée combinent l'opérateur d'assignation simple à un autre opérateur binaire. Ils exécutent l'opération spécifiée par l'opérateur supplémentaire, puis assignent le résultat à l'opérande gauche. Par exemple, une expression d'assignation composée telle que

> *expression1* **+=** *Expression2*

peut être comprise comme

> *expression1* **=** *expression1* **+** *Expression2*

Toutefois, l’expression d’assignation composée n’équivaut pas à la version développée, car elle évalue *expression1* une seule fois, tandis que la version développée évalue *expression1* deux fois : dans l’opération d’addition et dans l’opération d’assignation.

Les opérandes d’un opérateur d’assignation composée doivent être de type intégral ou flottant. Chaque opérateur d’assignation composée exécute les conversions effectuées par l’opérateur binaire correspondant et restreint les types de ses opérandes en conséquence. Les `+=` opérateurs d’assignation d’addition () et de soustraction-assignation ( **-=** ) peuvent également avoir un opérande gauche de type pointeur, auquel cas l’opérande de droite doit être de type intégral. Le résultat d’une opération d’assignation composée a la valeur et le type de l’opérande gauche.

```C
#define MASK 0xff00

n &= MASK;
```

Dans cet exemple, une opération AND inclusive au niveau du bit est exécutée sur `n` et `MASK`, et le résultat est assigné à `n`. La constante de manifeste `MASK` est définie avec une directive de préprocesseur [#define](../preprocessor/hash-define-directive-c-cpp.md).

## <a name="see-also"></a>Voir aussi

[Opérateurs d’assignation C](../c-language/c-assignment-operators.md)
