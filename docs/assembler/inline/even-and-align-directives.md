---
description: 'En savoir plus sur : directives paires et d’alignement'
title: MÊME et ALIGNEZ les directives
ms.date: 08/30/2018
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: adf633e99f1cb52a7849de24751d065a0344798f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117794"
---
# <a name="even-and-align-directives"></a>MÊME et ALIGNEZ les directives

**Spécifique à Microsoft**

Bien que l’assembleur inline ne prenne pas en charge la plupart des directives MASM, il prend en charge `EVEN` et **aligne**. Ces directives placent les instructions **NOP** (aucune opération) dans le code assembleur en fonction des besoins pour aligner des étiquettes sur des limites spécifiques. Cela rend les opérations de récupération d’instruction plus efficaces pour certains processeurs.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
