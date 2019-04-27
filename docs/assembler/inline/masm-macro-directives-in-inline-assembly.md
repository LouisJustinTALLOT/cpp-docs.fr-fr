---
title: Directives relatives aux macros MASM dans l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 7e1bed782d28a5bf7c934c3f57f50aae70038578
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167255"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directives relatives aux macros MASM dans l'assembly inline

**Section spécifique à Microsoft**

L'assembleur inline n'est pas un macro-assembleur. Vous ne pouvez pas utiliser des directives relatives aux macros MASM (**MACRO**, `REPT`, **IRC**, `IRP`, et `ENDM`) ou d’opérateurs macro (**<>**, **!** , **&**, `%`, et `.TYPE`). Un bloc `__asm` peut cependant utiliser des directives de préprocesseur C. Consultez [à l’aide de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) pour plus d’informations.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>