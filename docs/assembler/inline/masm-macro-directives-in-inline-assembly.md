---
title: Directives de Macro MASM dans l’Assembly Inline | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfd8e3ca5fb6bf65a288c17b1754d567b2b081a8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049849"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directives relatives aux macros MASM dans l'assembly inline
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 L'assembleur inline n'est pas un macro-assembleur. Vous ne pouvez pas utiliser les directives de macro MASM (**MACRO**, `REPT`, **IRC**, `IRP`, et `ENDM`) ou des opérateurs de macro (**<>**, **!** , **&**, `%`, et `.TYPE`). Un bloc `__asm` peut cependant utiliser des directives de préprocesseur C. Consultez [à l’aide de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) pour plus d’informations.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)