---
title: Directives relatives aux macros MASM dans l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 38b73346fc52f6b5efe478f8eb960ad049fae924
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169277"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directives relatives aux macros MASM dans l'assembly inline

**Section spécifique de Microsoft**

L'assembleur inline n'est pas un macro-assembleur. Vous ne pouvez pas utiliser les directives de macro MASM (**macro**, `REPT`, **IRC**, `IRP`et `ENDM`) ou les opérateurs de macro ( **<>** , **!** , **&** , `%`et `.TYPE`). Un bloc `__asm` peut cependant utiliser des directives de préprocesseur C. Pour plus d’informations, consultez [utilisation de C ou C++ de blocs de __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) .

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
