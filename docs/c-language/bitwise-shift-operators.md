---
title: Opérateurs de décalage de bits
ms.date: 10/18/2018
helpviewer_keywords:
- operators [C++], bitwise
- shift operators, bitwise
- bitwise-shift operators
- operators [C++], shift
ms.assetid: d0485785-5c72-47e1-a7c0-0adde03ade23
ms.openlocfilehash: d0873e3975e69bbfac01d437006561f0bf88ee31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485356"
---
# <a name="bitwise-shift-operators"></a>Opérateurs de décalage de bits

Les opérateurs de décalage décalent leur premier opérande vers la gauche (**&lt;&lt;**) ou vers la droite (**>>**) du nombre de positions spécifié par le second opérande.

## <a name="syntax"></a>Syntaxe

*shift-expression* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression* **&lt;&lt;** *additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression* **>>** *additive-expression*

Les deux opérandes doivent être des valeurs intégrales. Ces opérateurs exécutent les conversions arithmétiques habituelles ; le type du résultat est le type de l'opérande gauche après conversion.

Pour les décalages vers la gauche, les bits droits libérés prennent la valeur 0. Pour les décalages vers la droite, les bits gauche libérés sont remplis en fonction du type du premier opérande après conversion. Si le type est `unsigned`, ils prennent la valeur 0. Sinon, ils sont remplis avec des copies du bit de signe. Pour les opérateurs à décalage vers la gauche sans dépassement de capacité, l'instruction

```C
expr1 << expr2
```

équivaut à la multiplication par 2<sup>expr2</sup>. Pour les opérateurs à décalage vers la droite,

```C
expr1 >> expr2
```

équivaut à la division par 2<sup>expr2</sup> si `expr1` est non signé ou a une valeur non négative.

Le résultat d’une opération de décalage est non défini si le second opérande est négatif ou si l’opérande droit est supérieur ou égal à la largeur en bits de l’opérande gauche promu.

Étant donné que les conversions exécutées par les opérateurs de décalage ne fournissent pas de conditions de dépassement de capacité positif ou négatif, les informations peuvent être perdues si le résultat d'une opération de décalage ne peut pas être représenté dans le type du premier opérande après conversion.

```C
unsigned int x, y, z;

x = 0x00AA;
y = 0x5500;

z = ( x << 8 ) + ( y >> 8 );
```

Dans cet exemple, `x` est décalé vers la gauche de huit positions et `y` est décalé vers la droite de huit positions. Les valeurs décalées sont additionnées, ce qui donne 0xAA55, et assignées à `z`.

Le décalage d'une valeur négative vers la droite produit la moitié de la valeur d'origine, arrondie à la valeur inférieure. Par exemple, -253 (11111111 00000011 en binaire) décalé d’un bit vers la droite génère la valeur -127 (11111111 10000001 en binaire). Un décalage positif de 253 vers la droite génère la valeur +126.

Les décalages vers la droite conservent le bit de signe. Lorsqu'un entier signé est décalé vers la droite, le bit le plus significatif reste défini. Lorsqu'un entier non signé est décalé vers la droite, le bits le plus significatif est effacé.

## <a name="see-also"></a>Voir aussi

[Opérateurs de décalage vers la gauche et vers la droite (>> et <<)](../cpp/left-shift-and-right-shift-operators-input-and-output.md)