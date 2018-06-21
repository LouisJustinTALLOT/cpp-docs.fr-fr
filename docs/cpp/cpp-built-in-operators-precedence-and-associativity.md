---
title: Les opérateurs C++ intégrés, priorité et associativité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4d2bb339d4147e6ea82c713d83a046e0e9780bb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418427"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>Les opérateurs C++ intégrés, priorité et associativité

Le langage C++ inclut tous les opérateurs C et en ajoute plusieurs nouveaux. Les opérateurs spécifient une évaluation à effectuer sur un ou plusieurs opérandes.

Opérateur *priorité* Spécifie l’ordre des opérations dans les expressions qui contiennent plusieurs opérateurs. Opérateur *associativité* Spécifie si, dans une expression qui contient plusieurs opérateurs ayant la même priorité, un opérande est groupé avec celui situé à sa gauche ou celui situé à sa droite. Le tableau suivant indique la priorité et l'associativité des opérateurs C++ (de priorité décroissante). Les opérateurs ayant le même numéro de priorité ont une priorité identique, à moins qu'une autre relation soit explicitement forcée par des parenthèses.

### <a name="c-operator-precedence-and-associativity"></a>Priorité des opérateurs C++ et associativité

|Description des opérateurs|Opérateur|
|--------------------------|--------------|
|**Groupe de 1 priorité, aucun associativité**|
|[Résolution de portée](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Priorité du groupe 2, de gauche à droite associativité**|
|[Sélection de membre (objet ou pointeur)](../cpp/member-access-operators-dot-and.md)|[. ou ->](../cpp/member-access-operators-dot-and.md)|
|[Indice de tableau](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Appel de fonction](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Incrément suffixé](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Décrément suffixé](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Nom de type](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Conversion de type de constante](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[Conversion de type dynamique](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Conversion de type réinterprété](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Conversion de type statique](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Priorité du groupe 3, de droite à gauche associativité**|
|[Taille de l’objet ou un type](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Incrément préfixé](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Décrément préfixé](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Complément à 1](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Not logique](../cpp/logical-negation-operator-exclpt.md)|[\!](../cpp/logical-negation-operator-exclpt.md)|
|[Négation unaire](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Plus unaire](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Adresse](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Indirection](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Création d’objet](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[Détruire un objet](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[Cast](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Priorité de groupe 4, de gauche à droite associativité**|
|[Pointeur vers membre (objets ou pointeurs)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; ou ->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Priorité du groupe de 5, de gauche à droite associativité**|
|[Multiplication](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Division](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Priorité de groupe 6, de gauche à droite associativité**|
|[Addition](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Soustraction](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Groupe de priorité 7, de gauche à droite associativité**|
|[Décalage vers la gauche](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Décalage vers la droite](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Priorité de groupe 8, de gauche à droite associativité**|
|[Inférieur à](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Supérieur à](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Inférieur ou égal à](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Supérieur ou égal à](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Groupe de priorité 9, de gauche à droite associativité**|
|[Égalité](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Inégalité](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[\!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Priorité de groupe 10 de gauche à droite associativité**|
|[AND au niveau du bit](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Priorité de groupe 11, de gauche à droite associativité**|
|[Opérateur de bits OR exclusif](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Priorité de groupe 12, de gauche à droite associativité**|
|[Opérateur de bits OR inclusif](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Priorité de 13 de groupe, de gauche à droite associativité**|
|[AND logique](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Priorité de groupe 14, de gauche à droite associativité**|
|[OR logique](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Priorité du groupe 15, de droite à gauche associativité**|
|[Conditionnel](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Priorité du groupe 16, de droite à gauche associativité**|
|[Attribution](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Assignation de multiplication](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Assignation de division](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Assignation de modulo](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Assignation d’addition](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Assignation de soustraction](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Assignation de décalage vers la gauche](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Assignation de décalage vers la droite](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Assignation d’opération AND au niveau du bit](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Au niveau du bit assignation d’opération OR inclusive](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Au niveau du bit assignation OR exclusive](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Priorité du groupe 17, de droite à gauche associativité**|
|[expression throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Priorité de groupe 18, de gauche à droite associativité**|
|[Virgule](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Voir aussi

[Surcharge d'opérateur](operator-overloading.md)


