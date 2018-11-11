---
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
ms.openlocfilehash: d7879f3382016e098db0c8073322b99d596e8f83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664917"
---
# <a name="c-floating-point-constants"></a>Constantes à virgule flottante C

Une « constante à virgule flottante » est un nombre décimal qui représente un nombre réel signé. La représentation d’un nombre réel signé comprend une partie entière, une partie fractionnaire et un exposant. Utilisez des constantes à virgule flottante pour représenter des valeurs à virgule flottante qui ne peuvent pas être modifiées.

## <a name="syntax"></a>Syntaxe

*floating-point-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*fractional-constant* *exponent-part*<sub>opt</sub> *floating-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *exponent-part* *floating-suffix*<sub>opt</sub>

*fractional-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence*<sub>opt</sub> **.** *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence*  **.**

*exponent-part* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *sign*<sub>opt</sub> *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**E** *sign*<sub>opt</sub> *digit-sequence*

*sign* : un des éléments suivants<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*digit-sequence* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*floating-suffix* : un des éléments suivants<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l F L**

Vous pouvez omettre les chiffres avant la virgule (la partie entière de la valeur) ou les chiffres après la virgule (la partie fractionnaire), mais pas les deux. Vous pouvez laisser la virgule uniquement si vous incluez un exposant. Aucun espace blanc ne peut séparer les chiffres ou caractères d’une constante.

Les exemples suivants illustrent certaines formes de constantes et expressions à virgule flottante :

```
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Les constantes à virgule flottante sont positives, à moins d’être précédées du signe moins (**-**). Dans ce cas, le signe moins est considéré comme un opérateur de négation arithmétique unaire. Les constantes à virgule flottante sont de type `float`, `double` ou `long double`.

Une constante à virgule flottante sans suffixe **f**, **F**, **l** ou **L** est de type `double`. Si la lettre **f** ou **F** est le suffixe, la constante est de type `float`. Si elle est suivie de la lettre **l** ou **L**, elle est de type `long double`. Exemple :

```
100L  /* Has type long double  */
100F  /* Has type float        */
```

Notez que le compilateur Microsoft C en interne représente `long double` de la même façon que le type `double`. Consultez [Stockage des types de base](../c-language/storage-of-basic-types.md) pour plus d’informations sur le type `double`, `float` et `long double`.

Vous pouvez omettre la partie entière de la constante à virgule flottante, comme indiqué dans les exemples suivants. Le nombre .75 peut être exprimé de plusieurs façons, notamment :

```
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Voir aussi

[Constantes C](../c-language/c-constants.md)
