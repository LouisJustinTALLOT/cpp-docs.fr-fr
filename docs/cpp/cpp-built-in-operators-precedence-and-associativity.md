---
description: 'En savoir plus sur : opérateurs intégrés C++, priorité et associativité'
title: Opérateurs, priorité et associativité C++ intégrés
ms.date: 07/23/2020
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
ms.openlocfilehash: ff8ae84a62ef47449364d0815922326d7b8566d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253960"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>Opérateurs, priorité et associativité C++ intégrés

Le langage C++ inclut tous les opérateurs C et en ajoute plusieurs nouveaux. Les opérateurs spécifient une évaluation à effectuer sur un ou plusieurs opérandes.

## <a name="precedence-and-associativity"></a>Priorité et associativité

La *priorité* des opérateurs spécifie l’ordre des opérations dans les expressions qui contiennent plusieurs opérateurs. L' *associativité* des opérateurs spécifie si, dans une expression qui contient plusieurs opérateurs ayant la même priorité, un opérande est groupé avec celui situé à sa gauche ou celui situé à sa droite.

## <a name="alternative-spellings"></a>Orthographes alternatives

C++ spécifie d’autres orthographes pour certains opérateurs. En C, les autres orthographes sont fournies sous forme de macros dans l' \<iso646.h> en-tête. En C++, ces alternatives sont des mots clés et l’utilisation de \<iso646.h> ou de l’équivalent C++ \<ciso646> est déconseillée. Dans Microsoft C++, l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) option du compilateur ou est requise pour activer l’orthographe alternative.

## <a name="c-operator-precedence-and-associativity-table"></a>Priorité des opérateurs C++ et table d’associativité

Le tableau suivant indique la priorité et l'associativité des opérateurs C++ (de priorité décroissante). Les opérateurs ayant le même numéro de priorité ont une priorité identique, à moins qu'une autre relation soit explicitement forcée par des parenthèses.

| Description des opérateurs | Opérateur | Alternative |
|--|--|--|
| **Priorité du groupe 1, aucune associativité** |
| [Résolution d’étendue](../cpp/scope-resolution-operator.md) | [`::`](../cpp/scope-resolution-operator.md) |
| **Priorité du groupe 2, Association de gauche à droite** |
| [Sélection de membre (objet ou pointeur)](../cpp/member-access-operators-dot-and.md) | [`.` ni `->`](../cpp/member-access-operators-dot-and.md) |
| [Indice de tableau](../cpp/subscript-operator.md) | [`[]`](../cpp/subscript-operator.md) |
| [Appel de fonction](../cpp/function-call-operator-parens.md) | [`()`](../cpp/function-call-operator-parens.md) |
| [Incrément suffixé](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) | [`++`](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Décrément suffixé](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) | [`--`](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Nom de type](../cpp/typeid-operator.md) | [`typeid`](../cpp/typeid-operator.md) |
| [Conversion de type constant](../cpp/const-cast-operator.md) | [`const_cast`](../cpp/const-cast-operator.md) |
| [Conversion de type dynamique](../cpp/dynamic-cast-operator.md) | [`dynamic_cast`](../cpp/dynamic-cast-operator.md) |
| [Conversion de type réinterprété](../cpp/reinterpret-cast-operator.md) | [`reinterpret_cast`](../cpp/reinterpret-cast-operator.md) |
| [Conversion de type statique](../cpp/static-cast-operator.md) | [`static_cast`](../cpp/static-cast-operator.md) |
| **Priorité du groupe 3, associativité de droite à gauche** |
| [Taille d'objet ou de type](../cpp/sizeof-operator.md) | [`sizeof`](../cpp/sizeof-operator.md) |
| [Incrément préfixé](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) | [`++`](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Décrément préfixé](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) | [`--`](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Complément à 1](../cpp/one-s-complement-operator-tilde.md) | [`~`](../cpp/one-s-complement-operator-tilde.md) | **`compl`** |
| [Not logique](../cpp/logical-negation-operator-exclpt.md) | [`!`](../cpp/logical-negation-operator-exclpt.md) | **`not`** |
| [Négation unaire](../cpp/unary-plus-and-negation-operators-plus-and.md) | [`-`](../cpp/unary-plus-and-negation-operators-plus-and.md) |
| [Plus unaire](../cpp/unary-plus-and-negation-operators-plus-and.md) | [`+`](../cpp/unary-plus-and-negation-operators-plus-and.md) |
| [Adresse-de](../cpp/address-of-operator-amp.md) | [`&`](../cpp/address-of-operator-amp.md) |
| [Adressage indirect](../cpp/indirection-operator-star.md) | [`*`](../cpp/indirection-operator-star.md) |
| [Créer un objet](../cpp/new-operator-cpp.md) | [`new`](../cpp/new-operator-cpp.md) |
| [Supprimer un objet](../cpp/delete-operator-cpp.md) | [`delete`](../cpp/delete-operator-cpp.md) |
| [Procéder](../cpp/cast-operator-parens.md) | [`()`](../cpp/cast-operator-parens.md) |
| **Priorité du groupe 4, de gauche à droite** |
| [Pointeur vers membre (objets ou pointeurs)](../cpp/pointer-to-member-operators-dot-star-and-star.md) | [`.*` ni `->*`](../cpp/pointer-to-member-operators-dot-star-and-star.md) |
| **Priorité du groupe 5, Association de gauche à droite** |
| [Multiplication](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`*`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| [Division](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`/`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| [Young](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`%`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| **Priorité du groupe 6, Association de gauche à droite** |
| [Complément](../cpp/additive-operators-plus-and.md) | [`+`](../cpp/additive-operators-plus-and.md) |
| [Soustraction](../cpp/additive-operators-plus-and.md) | [`-`](../cpp/additive-operators-plus-and.md) |
| **Priorité du groupe 7, de gauche à droite** |
| [Décalage vers la gauche](../cpp/left-shift-and-right-shift-operators-input-and-output.md) | [`<<`](../cpp/left-shift-and-right-shift-operators-input-and-output.md) |
| [Décalage vers la droite](../cpp/left-shift-and-right-shift-operators-input-and-output.md) | [`>>`](../cpp/left-shift-and-right-shift-operators-input-and-output.md) |
| **Priorité du groupe 8, de gauche à droite** |
| [Inférieur à](../cpp/relational-operators-equal-and-equal.md) | [`<`](../cpp/relational-operators-equal-and-equal.md) |
| [Supérieur à](../cpp/relational-operators-equal-and-equal.md) | [`>`](../cpp/relational-operators-equal-and-equal.md) |
| [Inférieur ou égal à](../cpp/relational-operators-equal-and-equal.md) | [`<=`](../cpp/relational-operators-equal-and-equal.md) |
| [Supérieur ou égal à](../cpp/relational-operators-equal-and-equal.md) | [`>=`](../cpp/relational-operators-equal-and-equal.md) |
| **Priorité du groupe 9, de gauche à droite** |
| [Égalité](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | [`==`](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) |
| [Inégalité](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | [`!=`](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | **`not_eq`** |
| **Priorité du groupe 10 de gauche à droite** |
| [ET au niveau du bit](../cpp/bitwise-and-operator-amp.md) | [`&`](../cpp/bitwise-and-operator-amp.md) | **`bitand`** |
| **Priorité du groupe 11, de gauche à droite** |
| [OU exclusif au niveau du bit](../cpp/bitwise-exclusive-or-operator-hat.md) | [`^`](../cpp/bitwise-exclusive-or-operator-hat.md) | **`xor`** |
| **Priorité du groupe 12, de gauche à droite** |
| [Opération OR inclusive au niveau du bit](../cpp/bitwise-inclusive-or-operator-pipe.md) | [`|`](../cpp/bitwise-inclusive-or-operator-pipe.md) | **`bitor`** |
| **Priorité du groupe 13, de gauche à droite** |
| [ET logique](../cpp/logical-and-operator-amp-amp.md) | [`&&`](../cpp/logical-and-operator-amp-amp.md) | **`and`** |
| **Priorité du groupe 14, de gauche à droite** |
| [OU logique](../cpp/logical-or-operator-pipe-pipe.md) | [`||`](../cpp/logical-or-operator-pipe-pipe.md) | **`or`** |
| **Priorité de groupe 15, associativité de droite à gauche** |
| [Logique conditionnelle](../cpp/conditional-operator-q.md) | [`? :`](../cpp/conditional-operator-q.md) |
| **Priorité du groupe 16, associativité de droite à gauche** |
| [Affectation](../cpp/assignment-operators.md) | [`=`](../cpp/assignment-operators.md) |
| [Assignation de multiplication](../cpp/assignment-operators.md) | [`*=`](../cpp/assignment-operators.md) |
| [Assignation de division](../cpp/assignment-operators.md) | [`/=`](../cpp/assignment-operators.md) |
| [Assignation de modulo](../cpp/assignment-operators.md) | [`%=`](../cpp/assignment-operators.md) |
| [Assignation d'addition](../cpp/assignment-operators.md) | [`+=`](../cpp/assignment-operators.md) |
| [Assignation de soustraction](../cpp/assignment-operators.md) | [`-=`](../cpp/assignment-operators.md) |
| [Assignation de décalage vers la gauche](../cpp/assignment-operators.md) | [`<<=`](../cpp/assignment-operators.md) |
| [Assignation de décalage vers la droite](../cpp/assignment-operators.md) | [`>>=`](../cpp/assignment-operators.md) |
| [Assignation d'opération AND au niveau du bit](../cpp/assignment-operators.md) | [`&=`](../cpp/assignment-operators.md) | **`and_eq`** |
| [Assignation d'opération OR inclusive au niveau du bit](../cpp/assignment-operators.md) | [`|=`](../cpp/assignment-operators.md) | **`or_eq`** |
| [Assignation d'opération OR exclusive au niveau du bit](../cpp/assignment-operators.md) | [`^=`](../cpp/assignment-operators.md) | **`xor_eq`** |
| **Priorité de groupe 17, associativité de droite à gauche** |
| [expression throw](../cpp/try-throw-and-catch-statements-cpp.md) | [`throw`](../cpp/try-throw-and-catch-statements-cpp.md) |
| **Priorité du groupe 18, Association de gauche à droite** |
| [Comma](../cpp/comma-operator.md) | [,](../cpp/comma-operator.md) |

## <a name="see-also"></a>Voir aussi

[Surcharge d’opérateur](operator-overloading.md)
