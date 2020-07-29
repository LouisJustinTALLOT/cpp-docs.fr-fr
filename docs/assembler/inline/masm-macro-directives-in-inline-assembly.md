---
title: Directives relatives aux macros MASM dans l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 964f70aeef6e0e62ac4b941b2cc26d3e7c7ef466
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191792"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directives relatives aux macros MASM dans l'assembly inline

**Spécifique à Microsoft**

L'assembleur inline n'est pas un macro-assembleur. Vous ne pouvez pas utiliser les directives de macro MASM (**macro**, `REPT` , **IRC**, `IRP` , et `ENDM` ) ou les opérateurs de macro ( **<>** , **!**, **&** , `%` et `.TYPE` ). **`__asm`** Toutefois, un bloc peut utiliser des directives de préprocesseur C. Pour plus d’informations, consultez [utilisation de C ou C++ dans les blocs de __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
