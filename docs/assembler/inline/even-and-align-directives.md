---
title: Directives EVEN et ALIGN | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- align
- EVEN
dev_langs:
- C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06a1007c50e3490e5b14e4da886494557be0d37e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688299"
---
# <a name="even-and-align-directives"></a>MÊME et ALIGNEZ les directives

**Section spécifique à Microsoft**

Bien que l’assembleur inline ne prend pas en charge la plupart des directives MASM, il prend en charge `EVEN` et **ALIGN**. Ces directives placent **NOP** (aucune opération) des instructions dans le code de l’assembly en fonction des besoins pour aligner les étiquettes sur des limites spécifiques. Cela rend les opérations de récupération d’instruction plus efficaces pour certains processeurs.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>