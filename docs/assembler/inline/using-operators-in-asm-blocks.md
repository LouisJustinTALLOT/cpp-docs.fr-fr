---
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
ms.openlocfilehash: a871c19942252bf6a1a4901f8854b7b759700cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166501"
---
# <a name="using-operators-in-asm-blocks"></a>Utilisation d'opérateurs dans les blocs __asm

**Section spécifique à Microsoft**

Un `__asm` bloc ne peut pas utiliser des opérateurs spécifiques C ou C++, telles que la **<<** opérateur. Toutefois, les opérateurs partagés par C et MASM, telles que le \* opérateur, sont interprétés comme opérateurs de langage assembleur. Par exemple, à l’extérieur un `__asm` bloquer, crochets (**[]**) sont interprétés comme indices de tableau que C ajuste automatiquement à la taille d’un élément dans le tableau englobants. Au sein d'un bloc `__asm`, ils s'affichent en tant qu'opérateur index MASM, qui produit un offset d'octet non mis à l'échelle à partir d'un objet de données ou d'une étiquette (pas uniquement d'un tableau). Le code suivant illustre l'utilisation la différence :

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

La première référence à `array` n'est pas mise à l'échelle, la seconde oui. Notez que vous pouvez utiliser la **TYPE** opérateur pour obtenir la mise à l’échelle basée sur une constante. Par exemple, les instructions suivantes sont équivalentes :

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>