---
description: 'En savoir plus sur les constantes : C Floating-Point'
title: Constantes à virgule flottante C
ms.date: 11/04/2016
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
ms.openlocfilehash: 0bad45db33cd40060c4d20312c5318d443efc60f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293558"
---
# <a name="c-floating-point-constants"></a>Constantes à virgule flottante C

Une « constante à virgule flottante » est un nombre décimal qui représente un nombre réel signé. La représentation d’un nombre réel signé comprend une partie entière, une partie fractionnaire et un exposant. Utilisez des constantes à virgule flottante pour représenter des valeurs à virgule flottante qui ne peuvent pas être modifiées.

## <a name="syntax"></a>Syntaxe

*floating-point-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*fractional-constant* *exponent-part*<sub>opt</sub> *floating-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *exponent-part* *floating-suffix*<sub>opt</sub>

*fractional-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;option *de séquence numérique*<sub></sub> **.** *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*chiffre-séquence*  **.**

*partie exposant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;chiffre d'<sub>annulation</sub> de *signe* **e** *-séquence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Chiffre d'<sub>annulation</sub> de *signe* **E** *-séquence*

*sign* : un des éléments suivants<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*chiffre-séquence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*caractères*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*floating-suffix* : un des éléments suivants<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l F L**

Vous pouvez omettre les chiffres avant la virgule (la partie entière de la valeur) ou les chiffres après la virgule (la partie fractionnaire), mais pas les deux. Vous pouvez laisser la virgule uniquement si vous incluez un exposant. Aucun espace blanc ne peut séparer les chiffres ou caractères d’une constante.

Les exemples suivants illustrent certaines formes de constantes et expressions à virgule flottante :

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Les constantes à virgule flottante sont positives, sauf si elles sont précédées d’un signe moins ( **-** ). Dans ce cas, le signe moins est considéré comme un opérateur de négation arithmétique unaire. Les constantes à virgule flottante ont le type **`float`** , **`double`** ou **`long double`** .

Une constante à virgule flottante sans suffixe **f**, **f**, **l** ou **l** est de type **`double`** . Si la lettre **f** ou **f** est le suffixe, la constante est de type **`float`** . En cas de suffixe par la lettre **l** ou **l**, le type est **`long double`** . Par exemple :

```C
10.0L  /* Has type long double  */
10.0F  /* Has type float        */
```

Notez que le compilateur Microsoft C représente en interne **`long double`** le même type que le type **`double`** . Pour plus d’informations sur le type, et, consultez [stockage des types de base](../c-language/storage-of-basic-types.md) **`double`** **`float`** **`long double`** .

Vous pouvez omettre la partie entière de la constante à virgule flottante, comme indiqué dans les exemples suivants. Le nombre .75 peut être exprimé de plusieurs façons, notamment :

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Voir aussi

[Constantes C](../c-language/c-constants.md)
