---
title: Directives relatives aux macros MASM dans l’Assembly Inline | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 35ad22a9a4b79a31665ab6b156f8174d395bb0ee
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "43687971"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Directives relatives aux macros MASM dans l'assembly inline

**Section spécifique à Microsoft**

L'assembleur inline n'est pas un macro-assembleur. Vous ne pouvez pas utiliser des directives relatives aux macros MASM (**MACRO**, `REPT`, **IRC**, `IRP`, et `ENDM`) ou d’opérateurs macro (**<>**, **!** , **&**, `%`, et `.TYPE`). Un bloc `__asm` peut cependant utiliser des directives de préprocesseur C. Consultez [à l’aide de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) pour plus d’informations.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>