---
title: Utilisation d’opérateurs dans les blocs __asm | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e1c7c4b8415655aff36327db9c6a9f866d82683
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051128"
---
# <a name="using-operators-in-asm-blocks"></a>Utilisation d'opérateurs dans les blocs __asm
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Un `__asm` bloc ne peut pas utiliser des opérateurs spécifiques C ou C++, telles que la **<<** opérateur. Toutefois, les opérateurs partagés par C et MASM, telles que le \* (opérateur), sont interprétés comme opérateurs de langage assembleur. Par exemple, à l’extérieur une `__asm` bloquer, crochets (**[]**) sont interprétés comme indices de tableau, que C ajuste automatiquement à la taille d’un élément dans le tableau englobants. Au sein d'un bloc `__asm`, ils s'affichent en tant qu'opérateur index MASM, qui produit un offset d'octet non mis à l'échelle à partir d'un objet de données ou d'une étiquette (pas uniquement d'un tableau). Le code suivant illustre l'utilisation la différence :  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 La première référence à `array` n'est pas mise à l'échelle, la seconde oui. Notez que vous pouvez utiliser la **TYPE** opérateur pour obtenir la mise à l’échelle basée sur une constante. Par exemple, les instructions suivantes sont équivalentes :  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)