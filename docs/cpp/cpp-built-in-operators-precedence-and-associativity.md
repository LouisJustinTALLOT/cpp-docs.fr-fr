---
title: C++Opérateurs intégrés, priorité et associativité
ms.date: 11/04/2016
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
ms.openlocfilehash: 36e7ce77e24366be10b75f5bb4f8830363594301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180405"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++Opérateurs intégrés, priorité et associativité

Le langage C++ inclut tous les opérateurs C et en ajoute plusieurs nouveaux. Les opérateurs spécifient une évaluation à effectuer sur un ou plusieurs opérandes.

La *priorité* des opérateurs spécifie l’ordre des opérations dans les expressions qui contiennent plusieurs opérateurs. L' *associativité* des opérateurs spécifie si, dans une expression qui contient plusieurs opérateurs ayant la même priorité, un opérande est groupé avec celui situé à sa gauche ou celui situé à sa droite. Le tableau suivant indique la priorité et l'associativité des opérateurs C++ (de priorité décroissante). Les opérateurs ayant le même numéro de priorité ont une priorité identique, à moins qu'une autre relation soit explicitement forcée par des parenthèses.

### <a name="c-operator-precedence-and-associativity"></a>Priorité des opérateurs C++ et associativité

|Description des opérateurs|Opérateur|
|--------------------------|--------------|
|**Priorité du groupe 1, aucune associativité**|
|[Résolution d’étendue](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Priorité du groupe 2, Association de gauche à droite**|
|[Sélection de membre (objet ou pointeur)](../cpp/member-access-operators-dot-and.md)|[. ou->](../cpp/member-access-operators-dot-and.md)|
|[Indice de tableau](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Appel de fonction](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Incrément suffixé](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Décrémentation postfixé](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Nom du type](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Conversion de type constante](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[Conversion de type dynamique](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Conversion de type réinterprétée](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Conversion de type statique](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Priorité du groupe 3, associativité de droite à gauche**|
|[Taille de l’objet ou du type](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Incrément de préfixe](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Décrément de préfixe](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Complément à 1](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Not logique](../cpp/logical-negation-operator-exclpt.md)|[!](../cpp/logical-negation-operator-exclpt.md)|
|[Négation unaire](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Plus unaire](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Adresse](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Indirection](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Create object](../cpp/new-operator-cpp.md) (Créer un objet)|[nouveau](../cpp/new-operator-cpp.md)|
|[Détruire un objet](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[Cast](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Priorité du groupe 4, de gauche à droite**|
|[Pointeur vers membre (objets ou pointeurs)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; ou->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Priorité du groupe 5, Association de gauche à droite**|
|[Multiplication](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Division](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Young](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Priorité du groupe 6, Association de gauche à droite**|
|[Addition](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Soustraction](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Priorité du groupe 7, de gauche à droite**|
|[Décalage vers la gauche](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Décalage vers la droite](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Priorité du groupe 8, de gauche à droite**|
|[Inférieur à](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Supérieur à](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Inférieur ou égal à](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Supérieur ou égal à](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Priorité du groupe 9, de gauche à droite**|
|[Égalité](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Inégalité](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Priorité du groupe 10 de gauche à droite**|
|[AND au niveau du bit](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Priorité du groupe 11, de gauche à droite**|
|[Or exclusif au niveau du bit](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Priorité du groupe 12, de gauche à droite**|
|[Or inclusive au niveau du bit](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Priorité du groupe 13, de gauche à droite**|
|[ET logique](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Priorité du groupe 14, de gauche à droite**|
|[OU logique](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Priorité de groupe 15, associativité de droite à gauche**|
|[Conditionnel](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Priorité du groupe 16, associativité de droite à gauche**|
|[Affectation](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Assignation de multiplication](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Affectation de division](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Attribution de modulo](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Assignation d’addition](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Assignation de soustraction](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Assignation de décalage vers la gauche](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Assignation de décalage vers la droite](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Assignation au niveau du bit](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Assignation or inclusive au niveau du bit](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Assignation or exclusive au niveau du bit](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Priorité de groupe 17, associativité de droite à gauche**|
|[expression Throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Priorité du groupe 18, Association de gauche à droite**|
|[Virgule](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Voir aussi

[Surcharge d'opérateur](operator-overloading.md)
