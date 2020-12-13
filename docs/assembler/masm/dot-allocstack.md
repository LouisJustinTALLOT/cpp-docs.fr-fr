---
description: En savoir plus sur :. ALLOCSTACK
title: .ALLOCSTACK
ms.date: 12/17/2019
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: 6075b0900df104ae5faeaaff1dc0de2d3727b437
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132364"
---
# <a name="allocstack"></a>.ALLOCSTACK

Génère un **UWOP_ALLOC_SMALL** ou un **UWOP_ALLOC_LARGE** avec la taille spécifiée pour l’offset actuel dans le prologue.

## <a name="syntax"></a>Syntaxe

> **.** *Taille* de ALLOCSTACK

## <a name="remarks"></a>Notes

MASM choisit l’encodage le plus efficace pour une taille donnée.

**. ALLOCSTACK** permet ml64.exe aux utilisateurs de spécifier la façon dont une fonction Frame se déroule et est uniquement autorisée dans le prologue, qui s’étend de la déclaration d’image [proc](proc.md) à [. Directive ENDPROLOG](dot-endprolog.md) . Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata` . **. Les ALLOCSTACK** doivent être précédées d’instructions qui implémentent réellement les actions à déenrouler. Il est recommandé d’inclure dans un wrapper les directives de déroulement et le code qu’ils sont censés dérouler dans une macro pour garantir l’accord.

L’opérande de *taille* doit être un multiple de 8.

Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Exemple

L’exemple suivant montre comment spécifier un gestionnaire de déroulement/exception :

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
