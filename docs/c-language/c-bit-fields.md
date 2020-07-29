---
title: Champs de bits C
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
ms.openlocfilehash: 4878a9c8c206851b13484446b436952e655e06db
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234287"
---
# <a name="c-bit-fields"></a>Champs de bits C

En plus des déclarateurs pour les membres d’une structure ou une union, un déclarateur de structure peut également être un nombre de bits spécifié, appelé « champ de bits ». Sa longueur est définie à partir du déclarateur pour le nom de champ par un signe deux-points. Un champ de bits est interprété comme un type intégral.

## <a name="syntax"></a>Syntaxe

*déclarateur de struct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declarator*<sub>OPT</sub> **:** *constant-expression*

*expression constante* spécifie la largeur du champ en bits. Le *type-specifier* pour `declarator` doit être **`unsigned int`** , **`signed int`** , ou **`int`** , et l' *expression constante* doit être une valeur entière non négative. Si la valeur est zéro, la déclaration n’a aucun `declarator`. Les tableaux de champs de bits, pointeurs vers des champs de bits et fonctions qui retournent des champs de bits ne sont pas autorisés. Le `declarator` facultatif désigne le champ de bits. Les champs de bits peuvent uniquement être déclarés comme faisant partie d’une structure. L’opérateur address-of ( **&** ) ne peut pas être appliqué à des composants de champ de bits.

Les champs de bits sans nom ne peuvent pas être référencés et leur contenu lors de l’exécution est imprévisible. Ils peuvent être utilisés comme des champs « factices », à des fins d’alignement. Un champ de bits sans nom dont la largeur est spécifiée comme 0 garantit que le stockage du membre qui le suit dans *struct-declaration-list* commence sur une **`int`** limite.

Les champs de bits doivent également être suffisamment longs pour contenir le modèle binaire. Par exemple, les deux instructions suivantes ne sont pas autorisées :

```
short a:17;        /* Illegal! */
int long y:33;     /* Illegal! */
```

Cet exemple définit un tableau de structures à deux dimensions nommé `screen`.

```
struct
{
    unsigned short icon : 8;
    unsigned short color : 4;
    unsigned short underline : 1;
    unsigned short blink : 1;
} screen[25][80];
```

Le tableau contient 2 000 éléments. Chaque élément est une structure individuelle qui contient quatre membres de champ de bits : `icon`, `color`, `underline` et `blink`. La taille de chaque structure est de deux octets.

Les champs de bits ont la même sémantique que le type entier. Cela signifie qu'un champ de bits est utilisé dans les expressions exactement de la même façon qu’une variable du même type de base serait utilisée, quel que soit le nombre de bits dans le champ de bits.

**Spécifique à Microsoft**

Les champs de bits définis comme **`int`** sont traités comme **`signed`** . Une extension Microsoft de la norme C ANSI autorise **`char`** les **`long`** types et (à la fois **`signed`** et **`unsigned`** ) pour les champs de bits. Les champs de bits sans nom avec le type de base **`long`** , **`short`** ou **`char`** ( **`signed`** ou **`unsigned`** ) forcent l’alignement sur une limite appropriée au type de base.

Les champs de bits sont alloués dans un entier du bit de poids le plus faible au bit de poids le plus fort. Dans le code suivant

```
struct mybitfields
{
    unsigned short a : 4;
    unsigned short b : 5;
    unsigned short c : 7;
} test;

int main( void );
{
    test.a = 2;
    test.b = 31;
    test.c = 0;
}
```

les bits sont disposés comme suit :

```
00000001 11110010
cccccccb bbbbaaaa
```

Les processeurs de la gamme 8086 stockent l'octet faible des valeurs entières avant l'octet fort. L'entier `0x01F2` ci-dessus serait stocké en mémoire physique comme `0xF2` suivi de `0x01`.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarations de structure](../c-language/structure-declarations.md)
