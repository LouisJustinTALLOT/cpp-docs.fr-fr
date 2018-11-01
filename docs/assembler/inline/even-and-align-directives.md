---
title: MÊME et ALIGNEZ les directives
ms.date: 08/30/2018
f1_keywords:
- align
- EVEN
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 522d5689d680d0fc334743d2802abe21570dd6f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604356"
---
# <a name="even-and-align-directives"></a>MÊME et ALIGNEZ les directives

**Section spécifique à Microsoft**

Bien que l’assembleur inline ne prend pas en charge la plupart des directives MASM, il prend en charge `EVEN` et **ALIGN**. Ces directives placent **NOP** (aucune opération) des instructions dans le code de l’assembly en fonction des besoins pour aligner les étiquettes sur des limites spécifiques. Cela rend les opérations de récupération d’instruction plus efficaces pour certains processeurs.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>