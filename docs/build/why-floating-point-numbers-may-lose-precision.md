---
title: Pourquoi les nombres à virgule flottante peuvent manquer de précision
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 387b2f4a7156e42e59bd70c5a6f747943fb54ca7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313582"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Pourquoi les nombres à virgule flottante peuvent manquer de précision

Les valeurs décimales à virgule flottante n’ont généralement pas une représentation binaire exacte. Il s’agit d’un effet secondaire de la façon dont l’UC représente les données à virgule flottante. Pour cette raison, vous pouvez rencontrer une certaine perte de précision, et certaines opérations à virgule flottante peuvent produire des résultats inattendus.

Ce comportement est le résultat d’un des éléments suivants :

- La représentation binaire du nombre décimal n’est peut-être pas exacte.

- Il existe une incompatibilité de type entre les numéros utilisés (par exemple, mélange float et double).

Pour résoudre le problème, vérifiez que la valeur est supérieure ou inférieure à ce qui est nécessaire, ou ils obtiennent et utilisent une bibliothèque Binary Coded Decimal (BCD) qui préserve la précision de la plupart des programmeurs.

Représentation binaire des valeurs à virgule flottante affecte la précision et l’exactitude des calculs en virgule flottante. Microsoft Visual C++ utilise [format à virgule flottante IEEE](ieee-floating-point-representation.md).

## <a name="example"></a>Exemple

```
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

## <a name="comments"></a>Commentaires

Pour EPSILON, vous pouvez utiliser les constantes FLT_EPSILON, qui est défini pour float en tant que 1.192092896e-07F, ou DBL_EPSILON, qui est défini pour double en tant que la précision est 2.2204460492503131e-016. Vous devez inclure float.h pour ces constantes. Ces constantes sont définies en tant que le plus petit positif number x, tel que x + 1,0 n’est pas égal à 1,0. Comme il s’agit d’un très petit nombre, vous devez employer la tolérance définie par l’utilisateur pour les calculs impliquant de très grands nombres.

## <a name="see-also"></a>Voir aussi

[Optimisation du code](optimizing-your-code.md)
