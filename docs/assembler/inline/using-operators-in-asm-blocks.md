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
ms.openlocfilehash: b6ac9f7174baf1e0ebe41181c6a6f43e7bb3f5d1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169095"
---
# <a name="using-operators-in-__asm-blocks"></a>Utilisation d'opérateurs dans les blocs __asm

**Section spécifique de Microsoft**

Un bloc `__asm` ne peut pas utiliser C++ C ou des opérateurs spécifiques, tels que l’opérateur **<<** . Toutefois, les opérateurs partagés par C et MASM, tels que l’opérateur \*, sont interprétés comme des opérateurs de langage assembleur. Par exemple, en dehors d’un bloc de `__asm`, les crochets ( **[]** ) sont interprétés comme des indices de tableau englobants, que C adapte automatiquement à la taille d’un élément dans le tableau. Au sein d'un bloc `__asm`, ils s'affichent en tant qu'opérateur index MASM, qui produit un offset d'octet non mis à l'échelle à partir d'un objet de données ou d'une étiquette (pas uniquement d'un tableau). Le code suivant illustre l'utilisation la différence :

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

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
