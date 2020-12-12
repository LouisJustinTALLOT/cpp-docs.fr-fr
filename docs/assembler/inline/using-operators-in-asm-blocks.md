---
description: 'En savoir plus sur : utilisation d’opérateurs dans les blocs __asm'
title: Utilisation d'opérateurs dans les blocs __asm
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: 266d840e6cb407d45c1d3a49bed6a2390e52aa2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121847"
---
# <a name="using-operators-in-__asm-blocks"></a>Utilisation d'opérateurs dans les blocs __asm

**Spécifique à Microsoft**

Un **`__asm`** bloc ne peut pas utiliser des opérateurs spécifiques C ou C++, tels que l' **<<** opérateur. Toutefois, les opérateurs partagés par C et MASM, tels que l' \* opérateur, sont interprétés comme des opérateurs de langage assembleur. Par exemple, en dehors d’un **`__asm`** bloc, les crochets (**[]**) sont interprétés comme des indices de tableau englobants, que C met automatiquement à l’échelle en fonction de la taille d’un élément dans le tableau. Dans un **`__asm`** bloc, ils sont considérés comme l’opérateur d’index MASM, qui produit un décalage d’octet non mis à l’échelle à partir de n’importe quel objet ou étiquette de données (pas seulement un tableau). Le code suivant illustre l'utilisation la différence :

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

La première référence à `array` n'est pas mise à l'échelle, la seconde oui. Notez que vous pouvez utiliser l’opérateur **type** pour obtenir une mise à l’échelle basée sur une constante. Par exemple, les instructions suivantes sont équivalentes :

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
