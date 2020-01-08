---
title: Pourquoi les nombres à virgule flottante peuvent manquer de précision
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 373ce9fa2c2c96fac349940076873a4a637a9dbe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298712"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Pourquoi les nombres à virgule flottante peuvent manquer de précision

En général, les valeurs décimales à virgule flottante n’ont pas de représentation binaire exacte. Il s’agit d’un effet secondaire de la façon dont l’UC représente des données à virgule flottante. Pour cette raison, vous pouvez constater une perte de précision et certaines opérations à virgule flottante peuvent produire des résultats inattendus.

Ce comportement est le résultat de l’un des éléments suivants :

- La représentation binaire du nombre décimal n’est peut-être pas exacte.

- Il existe une incompatibilité de type entre les nombres utilisés (par exemple, en mélangeant float et double).

Pour résoudre le comportement, la plupart des programmeurs vérifient que la valeur est supérieure ou inférieure à ce qui est nécessaire, ou ils obtiennent et utilisent une bibliothèque de nombres décimaux codés binaires (BCD) qui conserveront la précision.

La représentation binaire des valeurs à virgule flottante affecte la précision et l’exactitude des calculs à virgule flottante. Microsoft Visual C++ utilise [le format à virgule flottante IEEE](ieee-floating-point-representation.md).

## <a name="example"></a>Exemple

```c
// Floating-point_number_precision.c
// Compile options needed: none. Value of c is printed with a decimal
// point precision of 10 and 6 (printf rounded value by default) to
// show the difference
#include <stdio.h>

#define EPSILON 0.0001   // Define your own tolerance
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))

int main() {
   float a, b, c;

   a = 1.345f;
   b = 1.123f;
   c = a + b;
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result
   if (c == 2.468)            // Comment this line for correct result
      printf_s("They are equal.\n");
   else
      printf_s("They are not equal! The value of c is %13.10f "
                "or %f",c,c);
}
```

```Output
They are not equal! The value of c is  2.4679999352 or 2.468000
```

## <a name="comments"></a>Comments

Pour EPSILON, vous pouvez utiliser les constantes FLT_EPSILON, qui est défini pour float comme 1.192092896 e-07F, ou DBL_EPSILON, qui est défini pour double comme 2, 2204460492503131e e-016. Vous devez inclure float. h pour ces constantes. Ces constantes sont définies comme étant le plus petit nombre positif x, de sorte que x + 1,0 n’est pas égal à 1,0. Étant donné qu’il s’agit d’un très petit nombre, vous devez utiliser la tolérance définie par l’utilisateur pour les calculs impliquant de très grands nombres.

## <a name="see-also"></a>Voir aussi

[Optimisation du code](optimizing-your-code.md)
