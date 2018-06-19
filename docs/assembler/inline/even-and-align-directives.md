---
title: MÊME et ALIGNEZ les Directives | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: a43425a4038ffb140eeaa0a9d111a39fc5c11ff0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057953"
---
# <a name="even-and-align-directives"></a>MÊME et ALIGNEZ les directives
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Bien que l’assembleur inline ne prend pas en charge la plupart des directives MASM, il prend en charge `EVEN` et **aligner**. Ces directives placent **NOP** (aucune opération) des instructions dans le code de l’assembly en fonction des besoins pour aligner les étiquettes sur des limites spécifiques. Cela rend les opérations de récupération d’instruction plus efficaces pour certains processeurs.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)